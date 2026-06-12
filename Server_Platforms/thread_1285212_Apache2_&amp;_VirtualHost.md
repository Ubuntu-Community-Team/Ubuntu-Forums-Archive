---
title: "Apache2 &amp; VirtualHost"
date: 2009-10-07
forum: Server Platforms
---

### Post by jph989 on 2009-10-07
Ok this is embarrassing, I bet I have 5-10 hours over the past 3 days invested in trying to host sub-domains. My Google-fu is weak...

Goal:

Set up VirtualHost so that [www.mydomain.us]("http://www.mydomain.us") point to /var/www  and subdomain.mydomain.us points to /home/user/public_html

I will be refreshing and monortring this page for the next few hours and will respond with any information needed.

I need someone to walk me through setting this up for my first sub-domain so that i can move on with this development.

Thank-you,
JPH

---

### Post by cdenley on 2009-10-07
Assuming you're using ubuntu 9.04, currently have a default apache configuration, and have a desktop environment.
```

cd /etc/apache2/sites-available
sudo cp default subdomain
gksu gedit subdomain

```
-Change "DocumentRoot /var/www" to "DocumentRoot /home/user/public_html"
-Add "ServerName subdomain.mydomain.us" above that line.
-Save, close
```

sudo a2ensite subdomain
sudo /etc/init.d/apache2 reload

```
You have now configured a new vhost at subdomain.mydomain.us. Your web browser may still have your default vhost cached for [http://subdomain.mydomain.us/](http://subdomain.mydomain.us/). I like using netcat to test vhost configurations.
```

echo -e "GET / HTTP/1.0\nHost: subdomain.mydomain.us\n"|nc localhost 80

```

---

### Post by jph989 on 2009-10-07
thanks let me go try that

---

### Post by jph989 on 2009-10-07
I am going to hit google with this but any help would be great....

after a2ensite I get this

/etc/apache2/sites-available$ sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Oct 07 14:55:14 2009] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                         [ OK ]


thanks for the help,
JPH

---

### Post by cdenley on 2009-10-07
> **jph989 said:**
> I am going to hit google with this but any help would be great....

after a2ensite I get this

/etc/apache2/sites-available$ sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Oct 07 14:55:14 2009] [warn] NameVirtualHost *:0 has no VirtualHosts
                                                                         [ OK ]


thanks for the help,
JPH

I'm guessing you don't have ubuntu 9.04?
```

lsb_release -id

```

Anyway, there should be no "NameVirtualHost" line in /etc/apache2/sites-available/subdomain if it uses port 80. In 8.04, the default vhost contained such a line. By 9.04, it was moved to ports.conf.

---

### Post by jph989 on 2009-10-07
Using Ubuntu 8.04.2

deleted NameVirtualHost line from top of subdomain

still have this error after reload

---

 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                     

---

and subdomain.mydomain.us still displays [www.mydomain.us](www.mydomain.us) homepage both using the command line option you send and refreshing my browser...

thoughts?

thank-you,
JPH

---

### Post by jph989 on 2009-10-07
This page [http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/](http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/)

ants me to add 
ServerName localhost

to the file
httpd.conf

thoughts?

---

### Post by cdenley on 2009-10-07
That is not an error, but a warning (and a harmless one). Adding "ServerName localhost" will suppress the warning, I believe, but isn't necessary. Don't worry about it at the moment.

First, I guess you can try restarting apache, but I think a reload should be sufficient.
```

sudo /etc/init.d/apache2 restart

```
Copy and paste this output from your terminal:
```

grep "Server[NA][al]" /etc/apache2/*.conf /etc/apache2/conf.d/* /etc/apache2/sites-enabled/*
cat /var/www/index.html
cat /home/user/public_html/index.html
echo -e "GET / HTTP/1.0\nHost: subdomain.mydomain.us\n"|nc localhost 80

```

---

### Post by jph989 on 2009-10-07
$ grep "Server[NA][al]" /etc/apache2/*.conf /etc/apache2/conf.d/* /etc/apache2/sites-enabled/*

no output


$ cat /var/www/index.html

output

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
        "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
    <title>ServeMe.us - Home Page</title>
    <style type="text/css"> @import url("style/001.css");</style>
</head>
<body>
        <h1>Welcome to ServeMe.us - The project server box of my firends</h1>
    <div id="nav">
        <li><a href="login/login.php">Sign In</a></li>
        <li><a href="contact/index.html">Sign Up</a></li>
        <li><a href="contact/index.html">Contact Us</a></li>
    </div>
    <div id="home">
        <p>ServeMe.us is a project development and file server for a small group of friends who have been separated geographically.  We still have those 4am strokes of genius (or madness) and needed a place to share idea, data, and collaborate with each other</p>
        <p>If you have just stumbled upon us or have followed a link from a image or file that this server has hosted, we thank you for visiting our humble site but we regret to inform you that we are not accepting new public member at this time.</p>
        <p>If you have been sent here by a member of ServeMe.us or if you want to offer us a crazy sum of money for our domain name then feel free to <a href="contact/index.html">Contact Us</a>.</p>
    </div>
    <div id="footer">
        <p>&#169; 2009 - <a href="http://www.serveme.us">www.serveme.us</a>, ServeMe.us&#153, <a href="mailto:webmaster@serveme.us">webmaster@serverme.us</a></p>
    </div>
</body>
</html>


cat /home/charlie/public_html/index.html

output

<html>
<body>
<p>Charlie's Home - Place Holder</p>
</body>
</html>


$ echo -e "GET / HTTP/1.0\nHost: charlie.serveme.us\n"|nc localhost 80

output

HTTP/1.1 200 OK
Date: Wed, 07 Oct 2009 19:52:03 GMT
Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch
Last-Modified: Mon, 05 Oct 2009 20:22:20 GMT
ETag: "20733-5ac-47535dee35700"
Accept-Ranges: bytes
Content-Length: 1452
Connection: close
Content-Type: text/html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
        "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
    <title>ServeMe.us - Home Page</title>
    <style type="text/css"> @import url("style/001.css");</style>
</head>
<body>
        <h1>Welcome to ServeMe.us - The project server box of my firends</h1>
    <div id="nav">
        <li><a href="login/login.php">Sign In</a></li>
        <li><a href="contact/index.html">Sign Up</a></li>
        <li><a href="contact/index.html">Contact Us</a></li>
    </div>
    <div id="home">
        <p>ServeMe.us is a project development and file server for a small group of friends who have been separated geographically.  We still have those 4am strokes of genius (or madness) and needed a place to share idea, data, and collaborate with each other</p>
        <p>If you have just stumbled upon us or have followed a link from a image or file that this server has hosted, we thank you for visiting our humble site but we regret to inform you that we are not accepting new public member at this time.</p>
        <p>If you have been sent here by a member of ServeMe.us or if you want to offer us a crazy sum of money for our domain name then feel free to <a href="contact/index.html">Contact Us</a>.</p>
    </div>
    <div id="footer">
        <p>&#169; 2009 - <a href="http://www.serveme.us">www.serveme.us</a>, ServeMe.us&#153, <a href="mailto:webmaster@serveme.us">webmaster@serverme.us</a></p>
    </div>
</body>
</html>



Thank-you for your help today,
JPH

---

### Post by cdenley on 2009-10-07
Go over my first post again. If you added this line
```

ServerName subdomain.mydomain.us

```
to /etc/apache2/sites-available/subdomain, then ran this command
```

sudo a2ensite subdomain

```
then this command
```

grep "Server[NA][al]" /etc/apache2/*.conf /etc/apache2/conf.d/* /etc/apache2/sites-enabled/*

```
should at least give you this output
```

/etc/apache2/sites-enabled/subdomain: ServerName subdomain.mydomain.us

```
If you don't define a ServerName or ServerAlias for your new vhost, apache won't know when to use it.

---

### Post by jph989 on 2009-10-07
/etc/apache2/sites-enabled/charlie:    ServerName charlie.serveme.us


Thank-you so much.  It works.

Last question, from a security standpoint should I go back and edit any of these post and remove all the dir names and ULRs so they aren't sitting here as public record forever?

again thanks,
JPH

---

### Post by cdenley on 2009-10-07
> **jph989 said:**
> /etc/apache2/sites-enabled/charlie:    ServerName charlie.serveme.us


Thank-you so much.  It works.

Last question, from a security standpoint should I go back and edit any of these post and remove all the dir names and ULRs so they aren't sitting here as public record forever?

again thanks,
JPH

I wouldn't worry about it, but you can remove or edit your posts if it bothers you.

---

