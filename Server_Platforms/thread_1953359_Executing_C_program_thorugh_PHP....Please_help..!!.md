---
title: "Executing C program thorugh PHP....Please help..!!!"
date: 2012-04-06
forum: Server Platforms
---

### Post by satyamM on 2012-04-06
Hello everyone,

I have a c program which produces a desired output on executing it ( gcc prog.c and then ./a.out)....

But I am not able to configure how to rum this program through php....I have seen at some sites that it can done by exec function..

I am using a Ubuntu 10.04 OS where apache server is installed and localhost is located at /var/www ....I am putting my C program file here, ./a.out executable and a file.php file in which i am writing something like 

```

<?php
execl("/var/www", "./a.out" , "NULL", (char *)0););
?>

```
But its not working....obvioulsy there is something which I dont know.....please tell me how to do it.

---

### Post by SeijiSensei on 2012-04-06
First, I suggest reading the PHP manual if you're trying to use PHP.  Here's the [page describing the exec() function]("http://php.net/manual/en/function.exec.php").

What exactly are you trying to do?  Do you need to have the output from the program put into a string and displayed in a web page?  If so, I recommend using the [system()]("http://www.php.net/manual/en/function.system.php") command instead.
```

<?php
$prog_output=system('/path/to/a.out');
echo $prog_output; 
?>
```
system() is functionally equivalent to the "backtick" operator or the $() construct in bash.

There's an additional issue that you need to consider, permissions.  The apache webserver runs as a pseudo-user "www-data" and has only the same permissions as that user does.  That means your program must be readable and executable by the www-data user.  The simplest way to test this is to use "sudo su -" to become the root user, followed by "su www-data" to become the www-data user.  Now try to run the program from the command prompt using its full path.  If that works, then you should be fine running the program from within a PHP script.  If not, you need to fix the permissions on the program so that the www-data user can read and execute it.

---

### Post by Cheesemill on 2012-04-06
> **SeijiSensei said:**
> The simplest way to test this is to use "sudo su -" to become the root user, followed by "su www-data" to become the www-data user.  Now try to run the program from the command prompt using its full path. 

Or just:
```
sudo -u www-data /path/to/command
```

---

### Post by satyamM on 2012-04-09
[@SeijiSensei]("http://ubuntuforums.org/member.php?u=698195")  My program is running on apache server......it is all ok with localhost....no problem with that...

**Problem is happening whenever I am hosting my files on local college server......I am not getting desired output when hosted on local college server......but perfectly working on Localhost(apache server) as told......please help...!!!!**

---

### Post by SeijiSensei on 2012-04-10
You need to talk to the college IT management, then.  We really can't diagnose a configuration like that.  It may be heavily locked down, or perhaps it requires you to use cgi-bin methods rather than PHP to run executables.  Only they can tell you what you need to do.

---

