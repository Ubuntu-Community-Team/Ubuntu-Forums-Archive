---
title: "Apache2 basic authentication problem"
date: 2009-10-08
forum: Server Platforms
---

### Post by daedalus666 on 2009-10-08
Hi,

I've got a problem with the basic authentication of my apache2 server. I configured a .htaccess-file according to the tutorial [http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)
When I try to access the file (with directorys it's the same problem) and try to login it always opens up the login screen again and again.

Here's the content of the .htaccess:
<Files "./hallo.txt">
    AuthType Basic
    AuthName Passwort
    AuthUserFile /var/www/docs/.htusers
    Require valid user
</Files>

Any suggestions to this problem??

greets daedalus

---

### Post by Lars Noodén on 2009-10-08
What is the exact line from the apache access or error log?

How did you create /var/www/docs/.htusers ?

---

### Post by daedalus666 on 2009-10-08
From the error.log:

[Thu Oct 08 14:32:20 2009] [error] [client xxx.xxx.xxx.xxx] user Hallo: authentication failure for "/docs/hallo.txt": Password Mismatch
[Thu Oct 08 14:32:29 2009] [error] [client xxx.xxx.xxx.xxx] access to /docs/hallo.txt failed, reason: require directives present and no Authoritative handler.

I created the .htuser with:
       sudo htpasswd /var/www/docs/.htusers Hallo

---

### Post by Lars Noodén on 2009-10-09
Ok.  The user and/or password you are entering into the web browser's authentication dialog does not match the one you have in the password file.  

> **daedalus666 said:**
> 
<Files "./hallo.txt">
    AuthType Basic
    AuthName Passwort
    AuthUserFile /var/www/docs/.htusers
    Require valid user
</Files>


```

     htpasswd /var/www/docs/.htusers newuser  

```

Then log in with the username 'newuser' and the password you just entered.

Also, the location of /var/www/docs/.htusers looks suspicious.  Is /var/www/docs/ visible to the world?  If so, then moving .htusers somewhere else would be a Very Good Idea(tm).

---

### Post by daedalus666 on 2009-10-09
I'm actually testing the basic authentication because I ran into that error with is. I'm securing up the server when I got rid of this error ;)


I just created a new user with the command you posted, tried the username and password and didn't get access. The error.log says:
[Fri Oct 09 16:16:53 2009] [error] [client x.x.x.x] access to /docs/hallo.txt failed, reason: require directives present and no Authoritative handler.
[Fri Oct 09 16:17:12 2009] [error] [client x.x.x.x] access to /docs/hallo.txt failed, reason: require directives present and no Authoritative handler.

It's sure that the problem is not the password...

---

### Post by Lars Noodén on 2009-10-11
[Require valid**-**user](http://httpd.apache.org/docs/2.2/mod/core.html#require)

'valid user' should read 'valid-user'  Sorry I missed that earlier.

---

### Post by daedalus666 on 2009-10-11
Hey Lars,

this was it. Many thanks.

Greetings Daedalus

---

