---
title: "Remote Proxy Server with Squid"
date: 2012-03-24
forum: Server Platforms
---

### Post by Hank_The_Dog on 2012-03-24
I would like to use my existing home server, as a web based proxy server, from all over the globe.

I have squid installed on the server. I have port forwarding set up on my network switch.
Whenever I use a browser to try to surf the web I get the following error.

```
 **ERROR**

 **The requested URL could not be retrieved**

 
    The following error was encountered while trying to retrieve the URL: [http://ubuntu.com/](http://ubuntu.com/)
  [INDENT] **Access Denied.**
 [/INDENT]  Access  control configuration prevents your request from being allowed at this  time. Please contact your service provider if you feel this is  incorrect.
  Your cache administrator is [EMAIL="webmaster%W"]webmaster[/EMAIL].

```



When I change my browsers proxy settings back to null, works like a charm.

I am pretty sure the issue lies in /etc/squid/squid.conf

But I have been reading/writting/experimenting all day in the conf file without any luck.


Any help would be great.

Thanks again.):P

---

### Post by bubylou on 2012-03-24
By default i believe squid only allows local ips to connect to it. 

Find something like this and comment it out.
acl our_networks src 192.168.1.0/24

and add or change something like this.
http_access allow all

Remember that this allows anyone to use your proxy server.

---

### Post by Hank_The_Dog on 2012-03-24
Thanks I will give that a try and post my results.

---

### Post by Hank_The_Dog on 2012-03-24
Tried everything along those lines but to no avail.

Stumped.:confused:

---

### Post by Insomn1a on 2012-03-24
[http://justlinux.com/forum/showthread.php?t=55045](http://justlinux.com/forum/showthread.php?t=55045)


check this out, not all of it is related to you but this guy is trying to do the same thing.

---

### Post by Hank_The_Dog on 2012-03-24
Hate to beat a dead horse, but as I'd imagine most users know about_ _[webmin]("http://www.webmin.com/")

(apparently I missed the memo)

.. Either way this has made my life 10X easier. 

I have been posting numerous threads in 'Server Platforms' and this could have solved a lot of my issues.


I will post if this can resolve my current problem, but from the looks of it.. it will answer a lot more questions as well.

Great interface!

---

### Post by collisionystm on 2012-03-25
Keep in mind hosting a proxy server is going to require a lot of bandwidth. ( first hand experience )

---

