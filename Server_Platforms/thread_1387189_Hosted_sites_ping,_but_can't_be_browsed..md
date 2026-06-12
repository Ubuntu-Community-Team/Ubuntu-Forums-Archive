---
title: "Hosted sites ping, but can't be browsed."
date: 2010-01-21
forum: Server Platforms
---

### Post by Whelk on 2010-01-21
I've got an Ubuntu 8.10 (Intrepid) server hosting several sites.  Things were fine for quite a while until today, the sites stopped showing up in firefox.  I can ping the sites by name and get a reply from the correct IP, but they won't come up in a browser; I get the "Firefox can't establish a connection to the server at [www.site.com](www.site.com).  Though the site seems valid, the browser was unable to establish a connection" error from both Windows and Ubuntu.

I've tried restarting the server and restarting apache2.  The sites appear to still be in sites-available and sites-enabled.  Any suggestions?

---

### Post by cdenley on 2010-01-21
> **Whelk said:**
> I've got an Ubuntu 8.10 (Intrepid) server hosting several sites.  Things were fine for quite a while until today, the sites stopped showing up in firefox.  I can ping the sites by name and get a reply from the correct IP, but they won't come up in a browser; I get the "Firefox can't establish a connection to the server at [www.site.com](www.site.com).  Though the site seems valid, the browser was unable to establish a connection" error from both Windows and Ubuntu.

I've tried restarting the server and restarting apache2.  The sites appear to still be in sites-available and sites-enabled.  Any suggestions?

Is apache listening for remote connections on port 80?
```

sudo netstat -tlnp

```
Is it responding locally?
```

echo -e "GET / HTTP/1.0\n"|nc 127.0.0.1 80

```
Are you sure it isn't a networking or ISP issue? Is your server behind a router? Does your ISP allow web servers?

---

### Post by Whelk on 2010-01-21
> **cdenley said:**
> Is apache listening for remote connections on port 80?
```

sudo netstat -tlnp

```

I believe so:
```

tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      8017/apache2

```

> **cdenley said:**
> Is it responding locally?
```

echo -e "GET / HTTP/1.0\n"|nc 127.0.0.1 80

```


(Edit - Previously typoed the command) Yes.  It sends me the HTML code of the index page.

> **cdenley said:**
> 
Are you sure it isn't a networking or ISP issue? Is your server behind a router? Does your ISP allow web servers?


Nothing with the router has changed, and I've been on the same ISP for years and haven't had problems hosting sites.

---

### Post by cdenley on 2010-01-22
Well, your web server is working correctly. It is either a networking issue or an ISP issue, since you said name resolution was working properly.

---

### Post by BkkBonanza on 2010-01-22
Have you configured your router for dynamic dns? If not then it's possible your ISP changed your IP on you. Your name may be resolving to the old IP and though ping works, your web server isn't at that IP any more.

Two tests to do: load the page whatsmyip.org and compare your current IP with what you get from,

nslookup yourdomainname

If the IPs aren't the same then it means it's changed (assuming you are using the web from the same ISP connection as your web server). If this rarely happens and you don't want to config dynamic dns then go manually update your dns with the new IP. The better way is to config your router to use dynamic dns to get updated when it changes.

If the IP is the same as expected then it may be either your ISP is now filtering your IP for port 80 or your router is no longer forwarding port 80 to your server correctly.

And of course it's also always possible that you have some network issue between your web server and the router. Login to the router and ping the web server to check that.

---

### Post by Whelk on 2010-01-22
Well, this is a bit embarrassing.  The last number of the IP ***did*** change.  It's been the same for over a year, till now.  Thanks for pointing out something that really should have been one of the first things I checked.

---

