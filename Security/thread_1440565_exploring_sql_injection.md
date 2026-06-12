---
title: "exploring sql injection"
date: 2010-03-27
forum: Security
---

### Post by band-aid on 2010-03-27
I am a computer science major and as part of my required courses I have taken classes dealing with server side programming and SQL. Both of these classes talked about the dangers of SQL injection and the importance of sanitizing user input but they never demonstrated it. To this end, I have set up apache2, mysql, and PHP on an ubuntu virtual machine with the goal of writing some vulnerable web pages and experimenting with them. The issue I am encountering is, examples I have seen on the internet do not appear to work. This will be easier to explain with code.

This is the portion of my PHP script that makes the vulnerable query to my mysql database.
```

if(isset($_POST['USERNAME']) && isset($_POST['PASSWORD']))
            {
                $connection = mysql_connect("IP ADDRESS REDACTED", "USERNAME REDACTED", "PASSWORD REDACTED");
                if(is_null($connection))
                {
                    die("Connection failed: " . mysql_error());
                }
                mysql_select_db("DATABASE REDACTED");
                $query = "select ADMINS.USERNAME from ADMINS where ADMINS.USERNAME = '" . $_POST["USERNAME"] . "' and ADMINS.PASSWORD = '" . $_POST["PASSWORD"] . "'";
                print $query;
                
                $results = mysql_query($query);
          



                if(mysql_num_rows($results) != 0)
                {
                    $row = mysql_fetch_array($results, MYSQL_ASSOC);
                    print $row["USERNAME"];
                    print $row["password"];

                }

```
The method I am attempting is 
```

' or 1=1;--

```
for the USERNAME input and some random characters for the PASSWORD input. In my mind this should generate the query
```

select ADMINS.USERNAME from ADMINS where ADMINS.USERNAME = '' or 1=1;--' and ADMINS.PASSWORD = 'asdf'

```
If I print out my query I get
```

select ADMINS.USERNAME from ADMINS where ADMINS.USERNAME = '' or 1=1;--' and ADMINS.PASSWORD = 'asdf'

```
Which looks correct to me.

The issue is that the query does not execute. I get the error
```

Warning: mysql_num_rows(): supplied argument is not a valid MySQL result resource in /home/band-aid/www/BrokenThings/brokenthings/index.php  on line 29

```

Is there some kind of safety mechanism in mysql that allows it to identify potential attacks and not run them? Is PHP doing something to my query behind the scenes?

Like I said, this is just for curiosity's sake. It drives me crazy when I can't figure something like this out.

Thanks for the help

---

### Post by band-aid on 2010-03-27
I believe I have solved it...
for whatever reason putting a space after the double-dash (--) cause it to work. The reason for this is completely unknown to me. If anyone can shed any light on the subject I would greatly appreciate it.

---

### Post by noway2 on 2010-03-28
Website security is a big, and growing, issue for anyone who wants to create an interactive site, which I am currently in the process of doing.  As you pointed out, a lot of times the dangers and the need to sanitize are mentioned, but lacking information on how to correctly do this. 

Does anyone have suggestions for good resources that are helpful in learning these important techniques?

---

### Post by bodhi.zazen on 2010-03-28
Thread closed. This type of activity is not supported here. 

First, this seems close to course work and you are expected to do the work yourself.

Second, the subject of such sql injections if gray hat at best , and this information can certainly be misused. 

I suggest you try an alternate web site.

---

