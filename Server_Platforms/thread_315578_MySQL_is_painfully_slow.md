---
title: "MySQL is painfully slow"
date: 2006-12-09
forum: Server Platforms
---

### Post by Xaiter on 2006-12-09
MySQL is painfully, painfully slow with remote connections.  Not even queries, connections.  It takes a solid 10 or so seconds to open and close a connection without even performing a query.  I can't possibly use it for anything if it's going to be like this - what in the blazes could cause it to lag so bad?  I'm certain it isn't hardware - the machine never gets over 2% load!

---

### Post by tturrisi on 2006-12-09
remote connections how?  A php script or vpn or other?

---

### Post by Xaiter on 2006-12-09
Right, sorry.

MyODBC connections from an XP SP2 development machine.  I'm reading up on some PHP right now to set up a PHP script to see if it IS just a crappy driver.

---

### Post by tturrisi on 2006-12-10
If you have a www server installed, put this php file there as a test.  It will display a select menu of all existing databases and gives you a textarea which can be used as a terminal to run sql commands.

[COLOR="Red"]CAUTION! SECURITY! CAUTION!: after testing, remove the php file because it will display ALL sql databases.[/COLOR]  

0. save below code as mysql_shell.php
1. load page in browser: [http://local-ip-of-server/mysql_shell.php](http://local-ip-of-server/mysql_shell.php)
2. select database named mysql from dropdown list3. run this sql command in the textarea:
[COLOR="DarkRed"]SELECT Host,User,Password FROM user[/COLOR]
```
<?php
// FILL THESE IN WITH YOUR SERVER'S DETAILS
$mysqlhost = 'localhost';
$mysqlusr = 'root';
$mysqlpass = 'your-password';
mysql_connect($mysqlhost,$mysqlusr,$mysqlpass);
?>

<html>
<head><title>MySQL Shell</title>
</head>
<body>

<?php
if (isset($_POST['submitquery'])) {
if (get_magic_quotes_gpc()) $_POST['query'] = stripslashes($_POST['query']);
echo('<p>Query:&nbsp;&nbsp;'.nl2br($_POST['query']).'</p>');
mysql_select_db($_POST['db']);
$result = mysql_query($_POST['query']);
if ($result) {
if (@mysql_num_rows($result)) {
?>

<table cellpadding="1" cellspacing="1" border="1">
<tr>

<?php
for ($i=0;$i<mysql_num_fields($result);$i++) {
echo('<th>'.mysql_field_name($result,$i).'</th>');
}
?>

</tr>

<?php
while ($row = mysql_fetch_row($result)) {
echo('<tr>');
for ($i=0;$i<mysql_num_fields($result);$i++) {
echo('<td>&nbsp;'.$row[$i].'</td>');
}
echo('</tr>');
}
?>

</table>

<?php
} else {
echo('<p>Query OK: '.mysql_affected_rows().' rows affected.</p>');
}
} else {
echo('<p>Query Failed: '.mysql_error().'</p>');
}
}
?>

<form action="<?$_SERVER['PHP_SELF']?>" method="POST">
<p>Database:
<select style="border:solid 1px #000000;" name="db">

<?php
$dbs = mysql_list_dbs();
for ($i=0;$i<mysql_num_rows($dbs);$i++) {
$dbname = mysql_db_name($dbs,$i);
if ($dbname == $_POST['db'])
echo("<option selected>$dbname</option>");
else
echo("<option>$dbname</option>");
}
?>

</select>
</p>
<p>MySQL Query:<br>
<textarea style="border:solid 1px #000000;" onFocus="this.select()" cols="70" rows="10" name="query"><?=htmlspecialchars($_POST['query'])?></textarea>
</p>
<p><input type="submit" name="submitquery" value="Search" accesskey="S" /></p>
</form>
</body>
</html>
```

---

### Post by blueCommand on 2006-12-10
Also, make sure your DNS settings are correct. I have had some funny slowdowns when it couldn't do reverse lookups and / or lookup its own hostname

---

### Post by mgranado on 2007-09-26
I have a kind of similar problem, I have my PHP, Apache and MySql running pretty fast if im running local.

The problem is, that I really need a database design tool... and I could only find a tool that runs in windows. So I created a virtual machine with windows and installed the software. The tool runs directly on the DB, but the connection to the DB is being really slow(really slow... just seing to belive)...

 my internet  connection, or network connection with the ubuntu machine, is really fast.

thanx

---

### Post by h.aling on 2007-09-30
I've had the same problem here. It was caused by reverse name lookup.

Adding "skip-name-resolve" to the [mysqld] section of /etc/mysql/my.cnf solved it for me.

The downside of this fix is that you can only use IP addresses in the permissions...

You can also try to set your hostname and ip address in /etc/hosts on your server.


-H-

---

