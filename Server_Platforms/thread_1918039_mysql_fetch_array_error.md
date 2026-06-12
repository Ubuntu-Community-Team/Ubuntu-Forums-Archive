---
title: "mysql_fetch_array error"
date: 2012-01-31
forum: Server Platforms
---

### Post by subhojit on 2012-01-31
i am trying to run the following code:

$result = mysql_query ("select * from employee", $con);

and fetching the data using code:

while ($row = mysql_fetch_array ($result))
{
echo $row['fistname'];
....
}

and, getting error:
PHP Warning:  mysql_fetch_array() expects parameter 1 to be resource, boolean given in /var/www/PHPPrograms/ViewData.php on line 15

any help please..

---

### Post by maverickaddicted on 2012-02-03
Try to use it inside if else statement and echo the mysql error in the else statement
```
echo 'Invalid query: ' . mysql_error() . "\n";
    echo 'Whole query: ' . $query;
```
Try to run the query displayed by the error in the phpmyadmin.

---

