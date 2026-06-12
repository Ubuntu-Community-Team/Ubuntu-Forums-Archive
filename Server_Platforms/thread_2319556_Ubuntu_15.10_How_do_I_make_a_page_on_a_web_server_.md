---
title: "Ubuntu 15.10: How do I make a page on a web server login only?"
date: 2016-04-05
forum: Server Platforms
---

### Post by Michael_McKenney on 2016-04-05
I have a home web server with pictures of our daughter on it.  I want to make that page login access only.  You need a login and password to access it.

---

### Post by Bucky Ball on 2016-04-05
*[I]Thread moved to **Server Platforms**.*[/I]

Why in ***New to Ubuntu***? That will decrease your chances of support with this.

Think you're going to need to give a lot more info than you have.

---

### Post by Michael_McKenney on 2016-04-05
Thanks for moving it.  I was looking for web server.

---

### Post by Michael_McKenney on 2016-04-05
HTTP/1.1 200 OK
Date: Tue, 05 Apr 2016 17:00:20 GMT
Server: Apache/2.4.12 (Ubuntu)
Last-Modified: Sat, 02 Apr 2016 02:09:12 GMT
ETag: "f7c-52f76fb4a9cf8"
Accept-Ranges: bytes
Content-Length: 3964
Vary: Accept-Encoding
Connection: close
Content-Type: text/html
 
Connection to host lost.
C:\Windows\system32>

---

### Post by SeijiSensei on 2016-04-05
Use "basic authentication" as described here: [http://httpd.apache.org/docs/current/howto/auth.html](http://httpd.apache.org/docs/current/howto/auth.html)

---

### Post by Michael_McKenney on 2016-04-05
Any gotchas I need to worry about?  Does not look hard to do.   Do I need SSL enabled for it to work?

---

### Post by Graham_Willis on 2016-04-05
Strictly speaking, you don't need SSL enabled in order to turn on BasicAuth, but it is a good idea to apply basic auth only over HTTPS because otherwise the login credentials going through the net will be just base64-encoded text meaning that practically everyone will be able to read them (encoding is by no means encrypting). Also, you should be aware that these passwords will remain cached in your browser at least as long as you're on the page (and possibly longer). And yet another factor is that if someone breaks into your webserver/hosting account, he will have access to these credentials, too.

---

### Post by Michael_McKenney on 2016-04-06
I was thinking the same thing about SSL and authentication.

---

### Post by SeijiSensei on 2016-04-07
To my mind it depends on what you're trying to protect.  Sure you'll be sending your credentials in plain text over the Internet, but who really will be listening?  These credentials don't provide any means to hack the server; they're exclusive to Apache.  Now if you have sensitive information to protect, you should definitely be using SSL.  But to protect pictures of your daughter?  I don't see the necessity.

---

### Post by Michael_McKenney on 2016-04-08
SSL certs are expensive.  I took the pictures off we were worried about.   I was thinking about Apache rights vs. Ubuntu rights.   You are correct about the sensitive nature.  The pictures from the delivery room are now only on my workstation.  

[http://www.scsiraidguru.com/FirstChild/index.html](http://www.scsiraidguru.com/FirstChild/index.html)

---

### Post by SeijiSensei on 2016-04-08
You can use a "self-signed" SSL certificate like the one that comes with Ubuntu. 
```

sudo a2enmod ssl
sudo a2ensite default-ssl

```
Now if you visit [https://localhost/](https://localhost/) you'll get a warning from your browser that the connection is "untrusted."  You can follow the steps to accept the certificate, and you should see the default home page in /var/www/html.  If you're only supporting a few friends and family, you can tell them to follow the same steps to accept the certificate if you want to apply SSL encryption to the connection.

You can also generate your own self-signed certificate with the [tools provided by OpenSSL]("https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04").

---

