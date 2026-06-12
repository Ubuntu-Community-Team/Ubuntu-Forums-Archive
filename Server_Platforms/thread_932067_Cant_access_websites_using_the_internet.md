---
title: "Cant access websites using the internet"
date: 2008-09-28
forum: Server Platforms
---

### Post by amai on 2008-09-28
on server using the internet.
BUT
I am able to access the sites with a directly connected PC.
AFTER
I have installed Bind9, still sites are not accessible from outside world.
INSTALLED bind9, following this link
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)

-So what else do i need to configure so that the sites can be accessible from the internet.
-How do i configure the server so that it knows it WAN ip address
(I am using a static ip address but have three sites configured)
-what need to be changed or configured so that the sites are accessible.

Thanks...

---

### Post by baudday on 2008-09-28
is the domain being forwarded to your server's ip? and do you have all the dns settings on the domain correct?

---

### Post by amai on 2008-09-28
To be sure "where do I check if domain is pointing to my server ip"

---

### Post by dividenot on 2008-09-28
I'm pretty sure you have to check the settings with the DN server you're using.  If you registered a domain, look on the website or contact the people that you registered the domain with.

---

### Post by amai on 2008-09-28
the DNS setting are all set up ok.
When i do dig melearning.com
or
host - a melearning.com
or
nslookup
melearning.com

I got the correct DNS and ip address information.
So i think changes need to be done on the server side.


Hence asking what should i be looking on the server setting

---

### Post by volkswagner on 2008-09-28
Is your server behind a router?  You will need to forward port 80 (Apache2 default port) to the server, in your router settings.

---

### Post by amai on 2008-09-28
Yes have port forwarded port 80 on the router.....

---

### Post by baudday on 2008-09-28
So don't get frustrated, but just to be certain. Your domain is being forwarded to your server's EXTERNAL ip? That's something you change on the domain's side, not server.

---

### Post by amai on 2008-09-28
I am still hanging in there.
So what will be the best logical way of troubleshooting this.

Any commands to run
Any files to check.
Any logs to be looking at

(A directly connected PC to server works BUT server cant be accessed from the internet)

---

### Post by cariboo on 2008-09-29
Have you checked with something like [canyouseeme]("http://www.canyouseeme.org/") to make sure that your isp isn't blocking port 80.

Jim

---

### Post by volkswagner on 2008-09-29
You may need to add your external ip address to /etc/hosts.  I thought bind9 would make this not needed.  It is worth a shot.  It worked for this user.

[http://ubuntuforums.org/showthread.php?t=930401]("http://ubuntuforums.org/showthread.php?t=930401")

---

