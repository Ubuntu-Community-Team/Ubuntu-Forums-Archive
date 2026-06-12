---
title: "HTTPS Forced Protocol"
date: 2011-05-22
forum: Server Platforms
---

### Post by Thegmandrive on 2011-05-22
I have set up certain portions of my web site to be forced https://

How do I force, non https:// protocols. I know this sounds confusing, so let me give you an example. 

#ForceLogin HTTPS
RewriteEngine On 
RewriteCond %{SERVER_PORT} 80 
RewriteCond %{REQUEST_URI} wp-login.php 
RewriteRule ^(.*)$ https://www.mywebsite.com/wp-login.php/$1 [R,L]

When I go to my home page 
[http://www.mywebsite.com/](http://www.mywebsite.com/) is using the http protocol 

when i go to the wp-login.php  it changes to [https://www.mywebsite.com/wp-login.php/](https://www.mywebsite.com/wp-login.php/) which is exactly what i wanted. 

However, when I click on any other links to my web site it keeps the https protocol. 

I want to be able to force NON encrypted protocols on certain pages (in order to save on processes for my server)

any ideas?

Im a total noob, so please forgive me if this is a stupid question.

---

### Post by tapi0n on 2011-05-22
Did you update your hosts?

For example if you're using virtual hosts in Apache2 you have to add

```
RewriteEngine on
```

to your virtual host because the default is **off **

---

### Post by Thegmandrive on 2011-05-25
> **tapi0n said:**
> Did you update your hosts?

For example if you're using virtual hosts in Apache2 you have to add

```
RewriteEngine on
```to your virtual host because the default is **off **


Thanks for the reply... sorry it took me so long.. I have been studying, and just took the GRE.

yeah I added this to my virtual server .htaccess file. 

#ForceLogin HTTPS
RewriteEngine On 
RewriteCond %{SERVER_PORT} 80 
RewriteCond %{REQUEST_URI} wp-login.php 
RewriteRule ^(.*)$ https://www.mywebsite.com/wp-login.php/$1 [R,L


I have a feeling I'm not being clear enough... I guess what I'm wanting to do is force HTTPS on some pages, and then force NON encrypted pages on others, to help save on my servers processing.

---

### Post by psusi on 2011-05-25
This should be painfully obvious: use http instead of https in your rewrite rule.

But really you shouldn't be doing that.  I sometimes manually use https to access a web site since I don't want a dumb network transparent proxy sniffing the connection and messing with it.  I can't stand it when the damn server keeps redirecting me to the non SSL connection that doesn't work.

---

### Post by Thegmandrive on 2011-05-25
> **psusi said:**
> This should be painfully obvious: use http instead of https in your rewrite rule.
 
But really you shouldn't be doing that. I sometimes manually use https to access a web site since I don't want a dumb network transparent proxy sniffing the connection and messing with it. I can't stand it when the damn server keeps redirecting me to the non SSL connection that doesn't work.
 
 
I'm either not making my self clear, 
 
or im just not understanding... 
 
So let me try one more time. 
 
When i go to my web site is regular old http
[http://www.mywebsite.com/](http://www.mywebsite.com/)
 
I then want to login to my wordpress admin, 
I set the .htaccess file to force https on that page 
for example when if i were to try [http://www.mywebsite.com/login.php](http://www.mywebsite.com/login.php) it is forced to be [https://www.mywebsite.com/login.php](https://www.mywebsite.com/login.php)... 
 
Now this is where im trying to force. when I logout and go back to my index page. the Https protocol is still being forced, does that make any sense?
 
are you saying all i should need to do is, add , another line like this?
 

RewriteEngine On 
RewriteCond %{SERVER_PORT} 80 
RewriteCond %{REQUEST_URI} / 
RewriteRule ^(.*)$ [http://www.mywebsite.com/$1](http://www.mywebsite.com/$1) [R,L

---

### Post by psusi on 2011-05-25
> **Thegmandrive said:**
> are you saying all i should need to do is, add , another line like this?
 

RewriteEngine On 
RewriteCond %{SERVER_PORT} 80 
RewriteCond %{REQUEST_URI} / 
RewriteRule ^(.*)$ [http://www.mywebsite.com/$1](http://www.mywebsite.com/$1) [R,L

Yes, except the part about port 80 sine that is the http port.  Rather than do this though, it would be better to simply change the logout link to go to [http://.](http://.)  The rewrite rule will force all connections to go back to http, even if they explicitly type https in the url.  Changing the logout link will only move them back to http when they log out.

---

### Post by Thegmandrive on 2011-05-25
Thank you! I will try that and let you know how it goes.. 
 
I did make it more painful than I needed to :)

---

### Post by Thegmandrive on 2011-06-09
tried it, and worked :)

Thanks.

---

