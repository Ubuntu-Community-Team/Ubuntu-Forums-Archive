---
title: "replacing certain web domains with local page on local machine."
date: 2010-01-19
forum: Security
---

### Post by louis--taylor on 2010-01-19
Hi there!
Does anyone know how to block an ip address, e.g. 69.63.181.11, and redirect the user to a local webpage/html file?
I want to block users to facebook.com (or any other domain) and give a waning message saying something like `this domain has been blocked, if you need to access this domain, please contact [someone]'.
This only has to work on the local machine, not on the whole network.
Any help would be nice thanks!

---

### Post by wirelessmonkey on 2010-01-19
Sure, just open up the /etc/hosts file, and put in something like this:

```

#this redirects to the local box
127.0.0.1 facebook.com

#this redirects to a machine on the local network, assuming 192.168.x.x addresses

192.168.5.5 facebook.com


```

So long as there is a web server running on the redirected box, you're set.

This is super basic, but will hopefully give you the idea.

---

### Post by kewlrichie on 2010-01-20
If this is for work I would highly suggest setting up a transparent proxy server using squid and dansguardian for web filtering of your users. There both great programs and I use this same method at my job and it does a very good job at it. If you need any help I would be glad to help.

---

### Post by bodhi.zazen on 2010-01-20
> **kewlrichie said:**
> If this is for work I would highly suggest setting up a transparent proxy server using squid and dansguardian for web filtering of your users. There both great programs and I use this same method at my job and it does a very good job at it. If you need any help I would be glad to help.

For a single machine and a single or a few sites, just use /etc/hosts. If you want to display a web page, install nginx somewhere (nginx is very light weight and will serve out static pages very very fast).

---

### Post by louis--taylor on 2010-01-21
Thanks a lot, these are very helpful and perfect for my needs.

P.S sorry for the late reply, been away from computer

---

### Post by hanzj on 2010-02-13
2 Things.

[SIZE=3]1st Thing:[/SIZE]
In my /etc/hosts file, I added 
```
127.0.0.1 facebook.com
```.When someone types in facebook.com into the URL bar of a browser, it will be blocked.
But what won't be blocked is [www.facebook.com]("http://www.facebook.com"). So I needed to add this line, too:
```
127.0.0.1 www.facebook.com
```I'm happy to see that it blocks both http:// and https:// 




[SIZE=3]2nd Thing[/SIZE]
  Is it possible that when a person (including myself 8-)) gets to a blocked site like facebook.com, the websurfer gets a personalized page/file on my computer? For example, a jpeg on my hard drive that looks like this...
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=146926&stc=1&d=1266042859[/IMG]

---

### Post by wirelessmonkey on 2010-02-13
Yes, you can do that easiest (imho) by changing one of the default apache error pages, as appropriate.

---

### Post by hanzj on 2010-02-15
wirelessmonkey,
how?

---

