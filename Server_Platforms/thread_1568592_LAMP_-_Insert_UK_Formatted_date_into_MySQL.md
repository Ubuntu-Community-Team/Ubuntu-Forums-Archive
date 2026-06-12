---
title: "LAMP - Insert UK Formatted date into MySQL"
date: 2010-09-05
forum: Server Platforms
---

### Post by TheFuturian on 2010-09-05
Hi All,

I'm fairly new to PHP, however seem to be slowly getting the grasp of it.. There's just one annoyance that's starting to annoy me, it's been pecking my head all weekend! Trying to take a UK formatted date (30/12/2010) and insert it into Mysql (2010-12-30) is just not going to plan. I have a feeling I'm getting close, however it's just not working out. Please can anyone point me in the right direction as to where I'm going wrong?
```

if ((isset($_POST["MM_insert"])) && ($_POST["MM_insert"] == "form1")) {
  $unformatted_date = $_POST['date'];
  $formatted_date = substr($unformatted_date,6,4) . "-" . substr($unformatted_date,3,2) . "-" . substr($unformatted_date,0,2);
  $insertSQL = sprintf("INSERT INTO dates (`date`) VALUES ($formatted_date)");

  mysql_select_db($database_webserver_datetest, $webserver_datetest);
  $Result1 = mysql_query($insertSQL, $webserver_datetest) or die(mysql_error());

  $insertGoTo = "dateinput.php";
  if (isset($_SERVER['QUERY_STRING'])) {
    $insertGoTo .= (strpos($insertGoTo, '?')) ? "&" : "?";
    $insertGoTo .= $_SERVER['QUERY_STRING'];
  }
  header(sprintf("Location: %s", $insertGoTo));
}
```

---

### Post by TheFuturian on 2010-09-14
I found my solution! :-D

```

if ((isset($_POST["MM_insert"])) && ($_POST["MM_insert"] == "form1")) {
  $unformatted_birthdate = $_POST['birth_date'];
  $formatted_birthdate = date('Y-m-d', strtotime($unformatted_birthdate));
  $unformatted_hiredate = $_POST['hire_date'];
  $formatted_hiredate = date('Y-m-d', strtotime($unformatted_hiredate));
  $insertSQL = sprintf("INSERT INTO employees (birth_date, first_name, last_name, gender, hire_date) VALUES (%s, %s, %s, %s, %s)",
                       GetSQLValueString($formatted_birthdate, "text"),
                       GetSQLValueString($_POST['first_name'], "text"),
                       GetSQLValueString($_POST['last_name'], "text"),
                       GetSQLValueString($_POST['gender'], "text"),
                       GetSQLValueString($formatted_hiredate, "text"));
  
  mysql_select_db($database_webserver_employees, $webserver_employees);
  $Result1 = mysql_query($insertSQL, $webserver_employees) or die(mysql_error());

  $insertGoTo = "employeeinput.php";
  if (isset($_SERVER['QUERY_STRING'])) {
    $insertGoTo .= (strpos($insertGoTo, '?')) ? "&" : "?";
    $insertGoTo .= $_SERVER['QUERY_STRING'];
  }
  header(sprintf("Location: %s", $insertGoTo));
}
```

---

### Post by Richard1979 on 2010-09-14
Is that GetSQLValueString() function safe?
What happens if you set $first_name to the literal:

'--

Are you calling addslashes() and stripping high/low ASCII on your input?
You're putting $_POST values directly into your database, which bothers me.

If you think I'm crying wolf, have a read of this:
[http://isc.sans.edu/diary.html?storyid=9397](http://isc.sans.edu/diary.html?storyid=9397)

---

### Post by TheFuturian on 2011-05-06
Nothing eventful, simply get's populated into the SQL database as far as I can tell..?!?

[IMG]http://img824.imageshack.us/img824/3939/nofailsql.png[/IMG]

---

