---
title: "mysql_fetch_array error"
date: 2012-01-31
forum: Server Platforms
---

### Post by subhojit on 2012-01-31
hello, i am trying to run the code:

$result = mysql_query ("select * from employee", $con);

and, fetching the data using:

while ($row = mysql_fetch_array($result))
{
echo $row['firstname'];
...
}

and getting the error:

PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/PHPPrograms/ViewData.php on line 15

please help...

---

### Post by richardjh on 2012-01-31
The error means the value of $result is a boolean, most likely "FALSE" in this case.

It suggests here that the return value of mysql_query ("select * from employee", $con); is "FALSE" , this means your connection to the database failed.

Can you check the connection to mysql first? 
A simple  

echo $con; 

should show something like "Resource id #4"

---

### Post by subhojit on 2012-02-01
> **richardjh said:**
> The error means the value of $result is a boolean, most likely "FALSE" in this case.

It suggests here that the return value of mysql_query ("select * from employee", $con); is "FALSE" , this means your connection to the database failed.

Can you check the connection to mysql first? 
A simple  

echo $con; 

should show something like "Resource id #4"

thank you :)

---

### Post by richardjh on 2012-02-01
You're welcome.

---

