---
title: "Server Webhosting Help"
date: 2011-01-03
forum: Server Platforms
---

### Post by deluxnate on 2011-01-03
This past month I've been tasked with setting up a web hosting server, and while I thought the task was within my knowledge, I'm afraid I need a bit of help. 

I'm running Ubuntu Server Edition 10.10 btw.

I've installed LAMP, set up my static IP with port 80 open, made an index page in /var/www/ and am able to view it outside my LAN with my server IP so no worries there. The trouble I'm running into now is using domain names for multiple sites. In the future, obviously I'll have to hand out a nameserver to clients so their domains point to my server. But I guess the problem is knowing where to get started with that. 

I know the trouble ahead lies with DNS and setting up a nameserver, but where/how do I get started with that? And would I be able to run the nameserver on the same box thats hosting the sites? 

I apologize in advance for the newbish questions, just frustrated with my lack of know-how. I'm expecting to host multiple sites on this box, and without knowing how to map domain names to their files on my server is a big problem on my part.

Thanks in advance for any help.

---

### Post by HermanAB on 2011-01-03
Hmm, it would have been a lot easier if you used a Linux distribution with proper wizards, such as Suse.  However, doing it the hard way with buntu will make you learn a lot.

What you need is Webmin, Usermin and Virtualmin.

---

### Post by cbarron on 2011-01-03
I use Webmin and EHCP. EHCP is nice and provides a GUI to use via web interface to set up email and users ect. [www.ehcp.net](www.ehcp.net) I found it really helpful when I was starting out.

---

### Post by woodman231 on 2011-01-03
Yes and hopefully the instructions here help you as well:

[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)

Thanks,
Sean W.

---

### Post by James78 on 2011-01-03
A guide on how to setup Virtualmin/Webmin/Usermin.
[http://wwww.ubuntuforums.org/showthread.php?t=1197883](http://wwww.ubuntuforums.org/showthread.php?t=1197883)

---

### Post by deluxnate on 2011-01-04
Thank you guys for the help, just what I was looking for.

---

