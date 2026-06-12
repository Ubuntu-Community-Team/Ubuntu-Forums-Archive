---
title: "Ho to Protect Web Server Password File"
date: 2009-11-23
forum: Security
---

### Post by Civil_777 on 2009-11-23
I am running a Ubuntu server to host some PHP scripts.  I have a password file called passwords.php which has passwords to MySQL.  I want to protect this file so that no one in the outside world can see it.

Here is what I am doing:

I put the file in www/ directory.  I change its permissions to -r-xr-x--- and I change the owner and group to www-data:www-data (which is the user used by Apache when executing PHP scripts).  Is there anything else I need to do to protect this file?  Why do I see some places that people are putting the file one directory above www/?

---

### Post by Dr Small on 2009-11-23
If your password is stored in a php file, like:
```
<?php
$password = "abcd3fg";
?>
```

Then if anyone accesses the file, the $password variable is set, but it is not printed on the webpage. Only people with FTP/SSH access could read the contents of the file.

---

### Post by Civil_777 on 2009-11-23
Thanks, that's what I thought.  Just wanted to make sure.

---

### Post by Lars Noodén on 2009-11-24
> **Dr Small said:**
> If your password is stored in a php file, like:
```
<?php
$password = "abcd3fg";
?>
```

Then if anyone accesses the file, the $password variable is set, but it is not printed on the webpage. Only people with FTP/SSH access could read the contents of the file.

It depends on where that file is.  If it is in a directory readable to a web-user via the web server, then it is also public.

---

### Post by Dr Small on 2009-11-24
> **Lars Noodén said:**
> It depends on where that file is.  If it is in a directory readable to a web-user via the web server, then it is also public.
Please explain?
Php is hypertext preprocessor, so it gets executed before any data is sent back to the browser. Unless you supply an `echo` or `print` in there somewhere for $password, the data held in the variable $password is not going to be returned to the browser.

---

### Post by Lars Noodén on 2009-11-25
It is a file, no more no less.  Not all the configurations that would allow access to that file via the webserver would force it through the php parser.  The first step in keeping it out of the public's eye is moving it out of the web server's document root.

---

### Post by BkkBonanza on 2009-11-25
Something to keep in mind here is that attackers to your site will not play nice. They can use techniques to expose more than you think in your php code if it is not well written. Just because the file passwords.php has permissions making it not viewable does not mean other methods would not expose the value. What I am saying is that to be secure you need to evaluate all your code for possible misuse of user input data. It ain't so easy but fortunately most sites don't have much of value to attack.

---

### Post by Lars Noodén on 2009-11-26
> **BkkBonaza said:**
> fortunately most sites don't have much of value to attack.
The network connection is very valuable in and of itself.  So is any disk space.

---

