---
title: "Getting Index Page on my domain Ubuntu Server 11.10"
date: 2012-08-06
forum: Server Platforms
---

### Post by shibby4555 on 2012-08-06
So I guess this isn't strictly related to Ubuntu Server and more of an Apache issue.
Very new to Ubuntu Server. So I have been experimenting with launching a website from it. Successfully have done so. Problem is, when in the URL I type: example.com **instead of** *[www.example.com](www.example.com)*, it comes up with the index page. Index of/

I feel like its an issue with file permissions. This is a very recent problem as of today, don't know what I did.

---

### Post by HugoSerrano on 2012-08-07
Hello!

Don't really know if I get it, but let's try!

Apache in Ubuntu got his / in /var/www/ and by default there's a file index.html in there.

So when you access the domain you will get that index. 
Now, if you got a folder inside /var/www/ called example you will access it by typing [www.example.com/example](www.example.com/example). 
To directly access that folder in the url, you need to move all the content of example to /var/www/ or change the root of apache in the apache configuration file.

Hope it helps!

Best Regards.

---

### Post by mikeatvillage on 2012-08-07
shibby4555,
 
Do you mean ..
 
[http://www.example.com](http://www.example.com) displays your 'home' page
 
but
 
[http://example.com](http://example.com) just displays a directory listing
 
If so look at the httpd.conf in Apache. (I found this on the internet)
 
<VirtualHost *:80>
ServerName [www.example.com]("http://www.example.com")
ServerAlias example.com
RewriteEngine On RewriteRule ^/(.*) http://www.example.com/$1 [L,R=301]
</VirtualHost> 
 
The RewriteRule is not neccesary but it is recommended to do so to be SEO friendly.

---

### Post by shibby4555 on 2012-08-07
> **HugoSerrano said:**
> Hello!

Don't really know if I get it, but let's try!

Apache in Ubuntu got his / in /var/www/ and by default there's a file index.html in there.

So when you access the domain you will get that index. 
Now, if you got a folder inside /var/www/ called example you will access it by typing [www.example.com/example]("http://www.example.com/example"). 
To directly access that folder in the url, you need to move all the content of example to /var/www/ or change the root of apache in the apache configuration file.

Hope it helps!

Best Regards.


Yes, correct. I can move all my files to /var/www/
But I'm trying to keep them in a separate subfolder of /var/www/website1
So that way I figure I can add other websites with greater ease in the future. 

mikeatvillage:

You were right, instead of editing the httpd.conf file, I appended the sites-enabled file with
ServerAlias *example.com

Wildcard completely fixed the issue.
Totally forgot about that. Must have deleted it or something.
Thanks!!

---

### Post by HugoSerrano on 2012-08-07
Right!

And this it's the way it should be done: /var/www/website1

Regards!

---

