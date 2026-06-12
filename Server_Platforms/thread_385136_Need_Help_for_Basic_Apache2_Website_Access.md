---
title: "Need Help for Basic Apache2 Website Access"
date: 2007-03-15
forum: Server Platforms
---

### Post by jenhsun on 2007-03-15
I'm new babe on setup a home base webserver. I can let people link to see my folder index from external network (internet), but can't go into see my webpage. I can see my page from internal network and everything is fine.
Is that the file permission problem or the apache setup? What am I suppose to do?

---

### Post by bukwirm on 2007-03-15
Post the result of "ls -l *whatever_your_web_directory_is*"

---

### Post by jenhsun on 2007-03-15
sorry that I use edgy server in console mode. I don't know how to copy the terminal information. But I follow your command that shows:

drwxr-xr-x 2 root root 4096 2007-03-15 08:15 apache2-default
-rw-r--r--    1 root root     20 2007-03-15 08:16 test.php

---

### Post by jfinkels on 2007-03-15
Do you get an error when you try to visit your webpage ("test.php")? What does your web browser say?

---

### Post by jenhsun on 2007-03-15
The browser just keep looping without anything shows up.
But I can see the test.php result from internal network (router).

---

### Post by jenhsun on 2007-03-15
Oh, by the way, I already setup port fowarding 80 and also DMZ to the internal IP. And I sure my isp doesn't block my port 80. 
I can let people see my folder index...but can't go into the page.

---

### Post by jenhsun on 2007-03-15
And I follow this link [http://www.mysql-apache-php.com/](http://www.mysql-apache-php.com/) 
to setup by server. I don't know what's going on....

---

### Post by jfinkels on 2007-03-15
Perhaps it's the contents of test.php that's causing you problems, maybe something in your PHP code fails to terminate. Try putting in a simple HTML file, and see if you can view that from your browser: <HTML><BODY>Hello, world</BODY></HTML>

EDIT: and I see from the website you posted that the test.php file is just a phpinfo() call. You may have a problem with PHP then, which I can't really help you with :P

---

### Post by jenhsun on 2007-03-15
Yes, I can see the "hello world" html without problem.
But still can see the php file.
If I change the /etc/apache2/sites-enabled/000-default  in order to redirectmatch to /apache2-default   I can't even see the apache2 default welcome message...
weired...

What am I supposed to do now?

---

### Post by jenhsun on 2007-03-15
sorry...still "CAN'T " see the php page

---

### Post by jfinkels on 2007-03-15
Does your test.php file look exactly like this? Double-check.
```
<?php phpinfo(); ?>
```
If it does and you're still getting a page that never resolves, I can't help you anymore, I hope somebody else comes along :):

By the way, did you know that you can edit your own posts after you've posted? Click on the little button that says "> EDIT" at the bottom of your post. :D

---

### Post by jenhsun on 2007-03-15
Yes, I am sure my php code is right.
that's so strange...even I can't see the default apache page

---

