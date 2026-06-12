---
title: "how to setup web proxy?"
date: 2011-01-16
forum: Server Platforms
---

### Post by Meph1st0 on 2011-01-16
I've got LAMP up and working and I'm currently hosting a joomla install on the server.  I was wondering if there's an easy way to get a web proxy working on my site.  I'd like to be able to use it just like you would at hidemyass.com.  By simply supplying a url it'll provide the proxy services for me.  I've looked through joomla's extensions library and don't see any extensions that'd provide that functionality.  I was hoping that there'd just be some prepackaged web proxy application I could install.

Anyone out there know of any simple way of getting this up and running.  I've looked at Squid but that looks like it's primarily a proxy server intended for internal network users.  I didn't see any sort of web proxy feature to install on a web server there.  Any advice on this would be greatly appreciated.

Jonathan

---

### Post by Sh1n1g4m1 on 2011-01-16
I use this one
[http://www.torproject.org/](http://www.torproject.org/)


How to install [http://www.ubuntugeek.com/how-to-install-tor-to-surf-anonymously-in-ubuntu-feisty-with-firefox.html](http://www.ubuntugeek.com/how-to-install-tor-to-surf-anonymously-in-ubuntu-feisty-with-firefox.html)


hope i was of any help

---

### Post by RobbanC on 2011-01-16
I believe you are searching for something like Glype Proxy?
[http://www.glype.com/]("http://www.glype.com/")

---

### Post by Meph1st0 on 2011-01-17
RobbanC,

That's exactly the sort of thing I'm looking for.  Thank you for your response.

Sh1n1g4m1,

TOR is a cool tool that I've used in the past for anonymous browsing.  But it wasn't exactly what I was looking for in this instance though.  Thanks for the suggestion anyway.

Jonathan

---

### Post by RobbanC on 2011-01-17
> **Meph1st0 said:**
> RobbanC,

That's exactly the sort of thing I'm looking for.  Thank you for your response.

Sh1n1g4m1,

TOR is a cool tool that I've used in the past for anonymous browsing.  But it wasn't exactly what I was looking for in this instance though.  Thanks for the suggestion anyway.

Jonathan
Great! Glad I could help. :)

I tried Glype myself last night, just to test. The installation is simple, simply download, unpack and upload the contents to your server.

First all I got was a white, blank screen when I tried to use the proxy. Found out the curl-package was not installed.

If that happens to you, just
```

sudo apt-get install curl

```
and
```

sudo apt-get install php5-curl

```
after that, restart Apache
```

sudo /etc/init.d/apache2 restart

```
Now it should work. At least, that is what I had to do. 
Good luck.:)

---

