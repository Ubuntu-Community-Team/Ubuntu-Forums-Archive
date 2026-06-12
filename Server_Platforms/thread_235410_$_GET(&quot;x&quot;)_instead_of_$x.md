---
title: "$_GET(&quot;x&quot;) instead of $x ???"
date: 2006-08-13
forum: Server Platforms
---

### Post by amigo-d on 2006-08-13
I installed LAMP (ubuntu dapper) using instructions from wiki and everything seems to run fine. Apache does, phpinfo(); lists info, mysql ok, phpmyadmin too... So I finally wanted to get to work. However, somehow variables no longer pass to the next page?! For example: a link to test.php?x=hello does not give me a workable $x in test.php. Strangely enough, $_GET("x") does work?!? 

Does it have anything to do with file permissions? Phpmyadmin does work (installed as root) using normal passing of variables. No $_GET to be seen there.

I really hope one of you knows!

jeroen

---

### Post by involutaryhaxor on 2006-08-13
You need to tell it that you want to get "x" from the URL or else it will just ignore it.

---

### Post by kostkon on 2006-08-13
You have to edit your PHP.ini file and find the line where it says *register_globals = Off* and change it to *register_globals = On*.

But be warned, if you change it that way you will be more vulnerable to attacks if your web server is going to go live on the net. Changing to *register_globals = On* is a security risk.

---

### Post by dabear on 2006-08-13
I suppose you mean $_GET["x"] rather than $_GET("x"). This has the standard behaviour since php 4.2. If you wonder why, read this: 
[http://no.php.net/register_globals](http://no.php.net/register_globals)

---

### Post by amigo-d on 2006-08-13
Thanks so much!

At least I know now why it did not work. It did not even know about this - meaning the (external) server my site is hosted on must have globals set to ON. What is common pratice? Should I start using $_GET[" "] ? (with brackets indeed)

Why is phpmyadmin then not written in this secure way? I mean, especially the mysql-database is not a place you would want to be exposed. If you store orders, payment status, passwords etc...

Thanks once more, good impression so shortly after joining the linux community (used xampp on xp before (shame shame)). Hope to answer some questions myself in the future :)

---

### Post by kostkon on 2006-08-13
> **amigo-d said:**
> Thanks so much!

At least I know now why it did not work. It did not even know about this - meaning the (external) server my site is hosted on must have globals set to ON. What is common pratice? Should I start using $_GET[" "] ? (with brackets indeed)

Why is phpmyadmin then not written in this secure way? I mean, especially the mysql-database is not a place you would want to be exposed. If you store orders, payment status, passwords etc...

Thanks once more, good impression so shortly after joining the linux community (used xampp on xp before (shame shame)). Hope to answer some questions myself in the future :)

My friend, welcome to the friendly Ubuntu community. Now, just something for clarification:

When you have *register_globals = On* it does not mean that you cannot follow the $_GET["x"], $_POST["x"], $_REQUEST["x"] way. Yes you can, and that's the important thing: When you have *register_globals = On* then important thing is not to get into the trap and not use the $_GET["x"] convention but instead use the variable names. Thus, even if the web server you use has *register_globals = On*, Phpmyadmin is written as if register_globals was off, the secure way.

---

### Post by Kurt` on 2006-08-13
> **amigo-d said:**
> What is common pratice?
The most common practice I see on webhosts is to leave it on, as some legacy scripts may require it.

However, most larger projects (e.g. MediaWiki) turn it off at the top of their scripts via [ini_set()](http://php.net/ini_set).

---

### Post by amigo-d on 2006-08-13
All right, I'll start doing it proper then. After all, this 'new' referencing applies only to variables passing pages. Not so very different. 

Security-wise, is behaving 'as if' a webhost has globals ON (using _GET even though globals were OFF) as safe as if the webhost actually had them ON?

---

### Post by kostkon on 2006-08-13
I think yeah, if you access your form variables only through the $_POST[..], $_GET[..], $_REQUEST[..] arrays, you'll be safe as if *register_globals* was *Off*.

---

