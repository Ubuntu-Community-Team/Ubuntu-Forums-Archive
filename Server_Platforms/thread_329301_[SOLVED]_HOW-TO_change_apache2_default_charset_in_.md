---
title: "[SOLVED] HOW-TO change apache2 default charset in Ubuntu"
date: 2007-01-01
forum: Server Platforms
---

### Post by soheil.moradi on 2007-01-01
You can do following help to change apache2 default charset in the Ubuntu:

First of everything:
```
sudo gedit /etc/apache2/apache2.conf
```

Now, press keys : **Ctrl+F** to open Find window
Enter **AddDefaultCharset** and click on Find

next you should change the line :
```
#AddDefaultCharset	ISO-8859-1
```

to

```
AddDefaultCharset	{YOUR_DEFAULT_CHARSET | Example: UTF-8}
```

and now save the file and press **Ctrl+C** in the terminal

Next you should restart the apache, you can do following commands:

```
cd /usr/sbin/
./apache2 -k restart
```

Enjoy with your default charset in the Apache 2

Also see my website and help me with you comments : :KS [http://www.irtik.com]("http://www.irtik.com")

---

### Post by MikeDX on 2007-11-30
This is incorrect, for all versions of the ubuntu server from at least 6.06 to 7.10 inclusive.

The correct way is to edit the charset file located at:

```
/etc/apache2/conf.d/charset
```

and edit the file to suit your needs.

For some reason, the default charset for apache in ubuntu (and possibly debian) is UTF-8 yet the default charset for mysql is latin1-swedish, which are incompatible.

---

### Post by richwils on 2008-01-29
I've got this problem and I have changed the /etc/apache2/conf.d/charset file to the following

#AddDefaultCharset UTF-8
AddDefaultCharset ISO-8859-1

However when I validate my web page I get the 

"Character Encoding mismatch!

The character encoding specified in the HTTP header (utf- 8 ) is different from the value in the <meta> element (iso-8859-1). I will use the value from the HTTP header (utf- 8 ) for this validation. "

Why is my web server still serving utf-8 HTTP header?  I have restarted apache2 (In fact I rebooted to make sure)

Help appreciated

---

### Post by richwils on 2008-01-29
Solved it.  

I tried a plain html page and that did not give the warning, so the http header with utf-8 was not coming from apache2. 

I'm using "cms made simple" and that was the culprit.  There is a setting in the config.php which sets the character set.  

Cheers

---

### Post by LLRNR on 2008-02-13
Hello,

Until a few days ago I was able to specify the default charset I wanted to use (UTF-8 in my case) with this method: editing /etc/apache2/conf.d/charset such that it contained the line

```

AddDefaultCharset UTF-8

```

and also making sure this was included:

```

grep -i include /etc/apache2/apache2.conf | grep conf.d
Include /etc/apache2/conf.d/

```

The problem is that, since a few days ago (after an apache update) I'm not able to make use of the AddDefaultCharset directive anymore. Nothing in my setup changed but now all my files (my server is comprised of directory listings only) are encoded with a... wrong encoding and I can't seem to get it to use the UTF-8 encoding.

Anyone experienced this too? Any ideas?

Thank you.

---

### Post by LLRNR on 2008-02-14
// Bump

Anyone?...

---

### Post by LLRNR on 2008-02-27
For the ones who might experience the same problem:

Solved... finally. Actually it's more of a workaround and not an actual explanation for why the 

AddDefaultCharset UTF-8 

directive in /etc/apache2/apache2.conf or /etc/apache/conf.d/charset or /usr/local/apache2/conf/httpd.conf doesn't work as of Apache 2.2.4...

The 'workaround' is to forget all about "AddDefaultCharset" and to add a line to /etc/apache2/apache2.conf or /usr/local/apache2/conf/httpd.conf - depending on your setup:

IndexOptions Charset=UTF-8

(or whatever charset you need instead of 'UTF-8')

Then restart apache and it should all get back to the normal behaviour.

---

