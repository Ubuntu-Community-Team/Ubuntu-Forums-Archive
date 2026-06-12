---
title: "How to make Apache look at /etc/hosts.deny?"
date: 2008-05-06
forum: Security
---

### Post by CaptSaltyJack on 2008-05-06
I just beefed up security on my home Linux box so that brute force attacks on sshd are auto blocked (IPs are added to hosts.deny by the 'denyhosts' service).  However, even putting "ALL: w.x.y.z" into hosts.deny doesn't prevent them from going to my Apache server.  I suppose it's because Apache runs as a separate process, outside the TCP wrapper.

How do I make Apache2 use hosts.deny/hosts.allow? (I just did the basic install of Apache via apt-get install apache2)

Thanks

---

### Post by HermanAB on 2008-05-06
I believe you need to compile Apache with Libwrap support.

---

### Post by CaptSaltyJack on 2008-05-06
Ah well, I guess that's out!  I'm not really one for compiling stuff, I really prefer using apt-get to install things.  It's not that important to me anyway.  Was just curious if there was another way.

---

### Post by wirelessmonkey on 2008-05-06
It is much easier to include in your Apache Allow/Deny directives, and I don't think it would be too difficult to generate a dynamic .htaccess file from your hosts.deny file. I may give it a try, if it works I'll let you know how I did it.

Best of Luck

---

### Post by cbobb@alinean.com on 2008-05-08
As wirlessmonkey said check how to use proper authentication or allow/deny directives from within the apache2.conf.  You can set them by IP or allow authenticated and generate .htaccess user credentials.

---

