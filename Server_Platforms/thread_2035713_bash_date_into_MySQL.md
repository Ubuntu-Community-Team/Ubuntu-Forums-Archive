---
title: "bash date into MySQL?"
date: 2012-07-31
forum: Server Platforms
---

### Post by SlugSlug on 2012-07-31
am having a little trouble using the output of bash date with a MySQL string in PHP..

Every thing fine when I take out the WHERE cause but I want the output to show THIS month and then I want another output to show LAST month...


snip of config.php
```
$first = `date -d "-$(($(date +%d)-1)) days" +%Y-%m-%d`;
$last = `date -d "+1 month -$(date +%d) days" +%Y-%m-%d`;
$lastmonth = `date --date="last month" +%Y-%m-%d`;
```snip of index.php
```
$sql = mysql_query('SELECT COUNT(user) AS total, user FROM '.$mysql_table.' WHERE time between "'$first' 00:00:00" AND "'$last' 23:59:59"
 < GROUP BY user ORDER BY COUNT(user) DESC');

```

---

### Post by steeldriver on 2012-07-31
is there any particular reason you need to use shell dates? can't you do it with the mysql builtin datetime functions (curdate + date_add or adddate?)

---

### Post by SlugSlug on 2012-07-31
am not sure?

I want a webpage showing like top 50 of this month and top 3 of last month

---

### Post by steeldriver on 2012-07-31
```
mysql> SELECT DATE_ADD(CURDATE(), INTERVAL -1 MONTH);
+----------------------------------------+
| DATE_ADD(CURDATE(), INTERVAL -1 MONTH) |
+----------------------------------------+
| 2012-06-30                             |
+----------------------------------------+
1 row in set (0.00 sec)

mysql> SELECT DATE_ADD(CURDATE(), INTERVAL +1 MONTH);
+----------------------------------------+
| DATE_ADD(CURDATE(), INTERVAL +1 MONTH) |
+----------------------------------------+
| 2012-08-31                             |
+----------------------------------------+
1 row in set (0.00 sec)

```allows you to do stuff like

```
SELECT * FROM recorded WHERE progend BETWEEN DATE_ADD(CURDATE(), INTERVAL -1 MONTH) AND CURDATE();
```

---

### Post by spjackson on 2012-07-31
> **SlugSlug said:**
> 
```
$first = `date -d "-$(($(date +%d)-1)) days" +%Y-%m-%d`;
$last = `date -d "+1 month -$(date +%d) days" +%Y-%m-%d`;
$lastmonth = `date --date="last month" +%Y-%m-%d`;
```snip of index.php
```
$sql = mysql_query('SELECT COUNT(user) AS total, user FROM '.$mysql_table.' WHERE time between "'$first' 00:00:00" AND "'$last' 23:59:59"
 < GROUP BY user ORDER BY COUNT(user) DESC');

```
It is very odd to shell out to date for this. Note that $first, $last and $lastmonth all end with a newline character, which you probably ought to remove with
```

$first = trim($first);
$last = trim($last);
$lastmonth = trim($lastmonth);

```
However, it is simpler in my view to use php functions (or possibly MySQL functions). i.e. I'd write
```

$first = date( "Y-m-d", strtotime("first day of " . date("F Y")));
$last = date( "Y-m-d", strtotime("last day of " . date("F Y")));

```(In this case, there's no need to trim.) This will work also on webservers that don't permit php to call out to the shell.

However, your main problem is that you have your quotes in the wrong place. And what's that less than sign doing before GROUP BY? Try this.
```

$sql = mysql_query('SELECT COUNT(user) AS total, user FROM '.$mysql_table.' WHERE time between '."'$first 00:00:00' AND '$last 23:59:59'" . ' GROUP BY user ORDER BY COUNT(user) DESC');

```

---

### Post by SlugSlug on 2012-07-31
Thanks Guys!

sorry about the rouge <   :)

[spjackson]("http://ubuntuforums.org/member.php?u=1128302") have you got a php thingy for $lastmonth  I could pinch? ;)

---

### Post by spjackson on 2012-07-31
> **SlugSlug said:**
> 
[spjackson]("http://ubuntuforums.org/member.php?u=1128302") have you got a php thingy for $lastmonth  I could pinch? ;)
I wasn't quite sure what you wanted on that. Running your shell code today results in 2012-07-01 (because there is no 31 June). The php equivalent is
```

$lastmonth = date( "Y-m-d", strtotime("last month"));

```

---

### Post by SlugSlug on 2012-07-31
Thanks for that :)

---

### Post by steeldriver on 2012-07-31
sorry - thought you wanted month intervals - if you want this / last calendar months you could do that right in sql using

```
WHERE MONTH(*yourdate*) = MONTH(CURDATE())
```and

```
WHERE MONTH(*yourdate*) = MONTH(CURDATE) - 1
```(assuming the *yourdate* record is a mysql date type)

---

### Post by SlugSlug on 2012-07-31
ahh ok thanks to both of you - I'll have a play later :)

---

### Post by SeijiSensei on 2012-07-31
I rarely store formatted dates in databases.  I much prefer storing the Unix timestamp as a 32-bit integer and using the PHP date() function to display the date in the desired format.

You can identify months by simply determining the start and end dates.  For instance, the start of February, 2012, is:

```

$febstart=mktime(0,0,0,2012,2,1);

```

That returns 1328072400, the same as the shell command "date +%s --date='00:00:00 01-feb-2012'".  Applying the same approach to 23:59:59 on February 29th gives 1330577999.  Thus entries in the database for February can be identified as 

```

SELECT...  WHERE timestamp>=1328072400 AND timestamp<1330577999

```

PHP has a whole raft of native time and date functions.  I generally use those over some type of shell-script massaging like you're doing now.

---

