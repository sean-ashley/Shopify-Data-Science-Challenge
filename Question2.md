### By : Sean Ashley, email : s2ashley@uwaterloo.ca, phone number: 647-224-6075

# Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

## a. How many orders were shipped by Speedy Express in total?

Query:

```
SELECT COUNT(OrderID) FROM Orders
JOIN Shippers ON Orders.ShipperID=Shippers.ShipperID
WHERE ShipperName='Speedy Express';
```

Answer : 54

## b. What is the last name of the employee with the most orders?

Query:

```
SELECT LastName FROM Employees
JOIN Orders ON Orders.EmployeeID=Employees.EmployeeID
GROUP BY LastName
ORDER BY COUNT(LastName) DESC
LIMIT 1;
```

Answer : Peacock

## c. What product was ordered the most by customers in Germany?

I am assuming this means product with the highest total ordered quantity.

Query:

```
SELECT ProductName FROM Products
JOIN OrderDetails ON Products.ProductID=OrderDetails.ProductID
JOIN Orders ON OrderDetails.OrderID=Orders.OrderID
JOIN Customers ON Orders.CustomerID=Customers.CustomerID
WHERE Customers.Country='Germany'
GROUP BY OrderDetails.ProductID
ORDER BY SUM(Quantity) DESC
LIMIT 1;
```
Answer: Boston Crab Meat