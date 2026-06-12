---
title: "LAMP issue"
date: 2012-11-07
forum: Server Platforms
---

### Post by jeger003 on 2012-11-07
hello,
i installed ubuntu and lamp on a virtualbox. put all my files in var/www and when i got to index.php it only reads html or at least thats what it looks like. my website wont run properly for some reason. php5 is installed i can echo "anything" but it seems like it wont read it. what am i doing wrong?

---

### Post by Lars Noodén on 2012-11-07
Welcome.

About your PHP issue, check to be sure that you have installed the package PHP5.  It will give you basic PHP support.  

```

sudo apt-get install php5

```

Then check to ensure that you have enabled Apache's mod_php.

```

sudo a2enmod php5

```

Then you can try putting some test code in index.php.

```

<?php
phpinfo( );
?>

```

Does that code produce output for you?

---

### Post by jeger003 on 2012-11-07
it tells me that they are all installed and working. phpinfo() also works but my pages are not displaying. i did a complete transfer so its fully functional from wamp

---

### Post by CharlesA on 2012-11-07
Check the apache error log in /var/log/apache2/

---

### Post by sandyd on 2012-11-07
moved to server platforms

---

### Post by Lars Noodén on 2012-11-07
> **CharlesA said:**
> Check the apache error log in /var/log/apache2/

One easy way to do that is to open up a terminal and then use [tail](http://manpages.ubuntu.com/manpages/precise/en/man1/tail.1.html) to track the end of the error log.

```

tail -f  /var/log/apache2/error.log 

```

That way you can have the web browser and error log side by side.

---

### Post by CharlesA on 2012-11-07
+1 Lars.

---

### Post by jeger003 on 2012-11-07
now we're getting somewhere. I got error opening include file in php. but it opens properly in wamp. do i need to change permissions in lamp for files and folders?

---

### Post by j2bv16 on 2012-11-07
You can install xampp [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by CharlesA on 2012-11-07
> **jeger003 said:**
> now we're getting somewhere. I got error opening include file in php. but it opens properly in wamp. do i need to change permissions in lamp for files and folders?

Check the permissions before messing with anything else.

Can you post the exact error message from the log?

---

### Post by Lars Noodén on 2012-11-07
What was the exact error message?

Edit: oops, too slow. :)

---

### Post by jeger003 on 2012-11-07
```
[Wed Nov 07 14:41:48 2012] [error] [client 127.0.0.1] PHP Warning:  include(): Failed opening '/include/bottom.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/index.php on line 134
[Wed Nov 07 14:41:48 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Nov 07 14:41:48 2012] [error] [client 127.0.0.1] PHP Warning:  include(/include/top.php): failed to open stream: No such file or directory in /var/www/index.php on line 7
[Wed Nov 07 14:41:48 2012] [error] [client 127.0.0.1] PHP Warning:  include(): Failed opening '/include/top.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/index.php on line 7
[Wed Nov 07 14:41:48 2012] [error] [client 127.0.0.1] PHP Warning:  include(/include/bottom.php): failed to open stream: No such file or directory in /var/www/index.php on line 134
[Wed Nov 07 14:41:48 2012] [error] [client 127.0.0.1] PHP Warning:  include(): Failed opening '/include/bottom.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/index.php on line 134
[Wed Nov 07 14:41:48 2012] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Nov 07 14:41:49 2012] [error] [client 127.0.0.1] PHP Warning:  include(/include/top.php): failed to open stream: No such file or directory in /var/www/index.php on line 7
```

---

### Post by jeger003 on 2012-11-07
thank you charles for the edit

---

### Post by CharlesA on 2012-11-07
Bah, I thought I hit submit, but I guess not.

Anyway, are you using the full path to the php files, or the relative path?

I checked one of my php files and I had this:

```
<?php
# Enter relative path to site's root directory
$rootpath='./';
include_once ($rootpath."templates/header.php");
include_once ($rootpath."templates/nav.php");
?>

```

---

### Post by jeger003 on 2012-11-07
the php page bottom.php is like this in the index.php page

include '/include/bottom.php';

exactly like that so I'm not sure why it wont call it if its in the same directory (/var/www/include)

---

### Post by Lars Noodén on 2012-11-07
> **jeger003 said:**
> include '/include/bottom.php';


PHP seems to want to have full UNIX paths, not anything with the web server.  Two work-arounds exist.  

One is to give the full path.  

```

include '/var/www/include/bottom.php';

```

The other is to use a relative path.

```

include './include/bottom.php';

```

I expect that there is a third way, the way that is actually correct, but these are the two obivous options.

---

### Post by Lars Noodén on 2012-11-07
It might be due to an inconsistency or defect in PHP itself:
[http://php.net/manual/en/function.include.php#94392](http://php.net/manual/en/function.include.php#94392)

Here's yet another work-around:
[http://roshanbh.com.np/2008/01/absolute-path-and-relative-path-file-inclusion-in-php.html](http://roshanbh.com.np/2008/01/absolute-path-and-relative-path-file-inclusion-in-php.html)

---

### Post by CharlesA on 2012-11-07
> **Lars Noodén said:**
> It might be due to an inconsistency or defect in PHP itself:
[http://php.net/manual/en/function.include.php#94392](http://php.net/manual/en/function.include.php#94392)

Here's yet another work-around:
[http://roshanbh.com.np/2008/01/absolute-path-and-relative-path-file-inclusion-in-php.html](http://roshanbh.com.np/2008/01/absolute-path-and-relative-path-file-inclusion-in-php.html)
Thanks for the explanation. I have always used the relative path on my pages.

---

### Post by koenn on 2012-11-08
> **Lars Noodén said:**
> I expect that there is a third way, the way that is actually correct, but these are the two obivous options.

I suspect the way to go is set an include_path, pointing to one or more directories where you collect your includes (that then can be referenced by bare filename in your code). And use includes (with relative or absolute path) as fallback, for special cases. 

[http://www.php.net/manual/en/ini.core.php#ini.include-path](http://www.php.net/manual/en/ini.core.php#ini.include-path)

---

### Post by jeger003 on 2012-11-08
thank you guys!!! it works great!!!

---

