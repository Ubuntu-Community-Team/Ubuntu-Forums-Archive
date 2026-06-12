---
title: "Phamm"
date: 2010-04-08
forum: Server Platforms
---

### Post by bluedrakonis on 2010-04-08
I am following this guide
[http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-as-imap-pop3-server-on-ubuntu-karmic-koala-9.10-p5](http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-as-imap-pop3-server-on-ubuntu-karmic-koala-9.10-p5)

and when i try [http://mysite.com/phamm](http://mysite.com/phamm)

it redirects me to [http://www.mysite.com/phamm/www-data/main.php](http://www.mysite.com/phamm/www-data/main.php)

any ideas

---

### Post by cdenley on 2010-04-08
That is what it is supposed to do.
```

cat /var/www/phamm/index.php

```
[PHP]
<?php

// Redirect to main file
header('Location: www-data/main.php');

?>
<html></html>
[/PHP]

---

### Post by bluedrakonis on 2010-04-08
i know the guide said i should be able to login or something to that effect all i get is a white screen

---

### Post by cdenley on 2010-04-08
```

echo -e "GET /phamm/www-data/main.php HTTP/1.0\nHost: mysite.com\n"|nc mysite.com 80

```

---

### Post by bluedrakonis on 2010-04-08
ok where should i put that line and it goes into the main.php right

---

### Post by cdenley on 2010-04-08
> **bluedrakonis said:**
> ok where should i put that line and it goes into the main.php right

No, that is a command. You type it in the terminal. It sends an HTTP request to your server for /phamm/www-data/main.php, so we can see exactly how the server responds. A white browser page doesn't really help to diagnose any problem.

---

### Post by bluedrakonis on 2010-04-08
i typed in the command about five minutes or so ago and now the terminal just sits their and wont let me enter any more commands, i can type just not execute anything

---

### Post by cdenley on 2010-04-08
> **bluedrakonis said:**
> i typed in the command about five minutes or so ago and now the terminal just sits their and wont let me enter any more commands, i can type just not execute anything

Did you substitute your domain name, since you never gave me your real one? Here is the same command with a 5 second timeout. Obviously it will fail to connect to mysite.com. You have to substitute both instances with your correct domain name.
```

echo -e "GET /phamm/www-data/main.php HTTP/1.0\nHost: **mysite.com**\n"|nc -w 5 **mysite.com** 80

```

---

### Post by bluedrakonis on 2010-04-08
running it with the www in front of my domain i get this

HTTP/1.1 404 Not Found
Date: Thu, 08 Apr 2010 20:13:47 GMT
Server: Apache/2.2.12 (Ubuntu)
Vary: accept-language,accept-charset,Accept-Encoding
Accept-Ranges: bytes
Connection: close
Content-Type: text/html; charset=iso-8859-1
Content-Language: en
Expires: Thu, 08 Apr 2010 20:13:47 GMT

<?xml version="1.0" encoding="ISO-8859-1"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
<head>
<title>Object not found!</title>
<link rev="made" href="mailto:webmaster@localhost" />
<style type="text/css"><!--/*--><![CDATA[/*><!--*/
    body { color: #000000; background-color: #FFFFFF; }
    a:link { color: #0000CC; }
    p, address {margin-left: 3em;}
    span {font-size: smaller;}
/*]]>*/--></style>
</head>

<body>
<h1>Object not found!</h1>
<p>


    The requested URL was not found on this server.



    If you entered the URL manually please check your
    spelling and try again.



</p>
<p>
If you think this is a server error, please contact
the <a href="mailto:webmaster@localhost">webmaster</a>.

</p>

<h2>Error 404</h2>
<address>
  <a href="/">www.harlanclubhouse.com</a><br />

  <span>Thu Apr  8 16:13:47 2010<br />
  Apache/2.2.12 (Ubuntu)</span>
</address>
</body>
</html>

without the www i get this
harlanclubhouse.com [98.19.171.184] 80 (www) : Connection timed out

---

### Post by cdenley on 2010-04-08
[www.harlanclubhouse.com](www.harlanclubhouse.com) is an ubuntu 9.10 web server. However, there is no /phamm directory for the default site (or [www.harlanclubhouse.com](www.harlanclubhouse.com)).

harlanclubhouse.com resolves to a different IP address, which doesn't have any remotely accessible servers.

How exactly are you accessing your site? Run this from the web server.
```

ls -ld /var/www/phamm
cat /etc/apache2/sites-enabled/*
wget -q -O - http://whatismyip.org/ && echo

```

Or you can just forget about how your site is accessed remotely, and assuming your default site's DocumentRoot is /var/www, and phamm is located at /var/www/phamm:
```

echo -e "GET /phamm/www-data/main.php HTTP/1.0\n"|nc 127.0.0.1 80

```

---

### Post by bluedrakonis on 2010-04-08
sorry forgot that i had a little trouble setting phamm up and had to set it up as phamm-0.5.18

when i re ran the echo with the www i get

HTTP/1.1 200 OK
Date: Thu, 08 Apr 2010 20:34:13 GMT
Server: Apache/2.2.12 (Ubuntu)
Set-Cookie: PHPSESSID=2927f7fbd17cd29c635a226948c1d453; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Pragma: no-cache
Vary: Accept-Encoding
Content-Length: 444
Connection: close
Content-Type: text/html; charset=utf-8

<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE html
        PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
        "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
        <title>Phamm</title>
        <style type="text/css" media="all">@import "./style/phamm/main.css";</style>
        <script type="text/javascript" src="functions.js"></script>
</head>
<body onLoad='disableAutocomplete()'>

without www
harlanclubhouse.com [98.19.171.184] 80 (www) : Connection timed out

---

### Post by bluedrakonis on 2010-04-08
my server is setup using a dynamic internet connection and i am accessing it through putty by using the domain name if that helps any

---

### Post by cdenley on 2010-04-08
It is odd that it doesn't give any error message, but it seems to fail when it attempts to connect to your LDAP server. I would go through the guide and make sure you did all the steps correctly. I don't know much about LDAP, and nothing about phamm.

---

### Post by bluedrakonis on 2010-04-23
yeah i found that strange as well

---

