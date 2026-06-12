---
title: "Here is an awesome idea for a squid server, but I need your help"
date: 2009-09-29
forum: Server Platforms
---

### Post by Coder543 on 2009-09-29
Is there an easy way to set up a squid server on Ubuntu? Because I would really like to set one up. Here is what I think would be really cool: the squid server would (obviously) be a proxy to the rest of the house; and it would store all content for 5 minutes; with the exception of *.iso, *.tar.gz, and maybe other big files; which would be stored for a longer duration. (such as a couple of hours or days)

This way, when you are browsing the web, everything loads almost instantly, (like when you hit the back button) and when you download an Ubuntu disk image; it only takes a long time once, then all the other computers in the house can download the image lightning fast, if they try within the given duration.

I'm not sure, but i think this would be really nifty, and it would make the house feel like it has extraordinarily fast internet.

Can anyone help with this? I have a machine running Ubuntu Server, but all machines in the house are connected into a wireless access point. (either by wire, or by wireless)

Mainly what I need to know is whether or not it would be easy to get this set up and going, i am a technical user, but i have no experience with squid. Thanks in advance.

---

### Post by i.r.id10t on 2009-09-29
apt-get install squid

Then set the browser to use the ip of the ubuntu box on the proper port (3128 IIRC) as the http proxy.

---

### Post by Lars Noodén on 2009-09-29
Yes.  Installation is done with your normal package manager.  You'll want to adjust the ACLs in the configuration file to make squid behave as you wish.  

```

sudo vi /etc/squid/squid.conf
sudo /etc/init.d/squid reload

```

Look for the line in the configuration file that says "*# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS*" to control the access.  

What to cache and how long, is up to you.  


[http://www.squid-cache.org/Versions/v2/2.7/cfgman/](http://www.squid-cache.org/Versions/v2/2.7/cfgman/)
[http://www.visolve.com/squid/](http://www.visolve.com/squid/)
[http://wiki.squid-cache.org/ConfigExamples](http://wiki.squid-cache.org/ConfigExamples)

---

### Post by scrooge_74 on 2009-09-29
The cache part is what AOL used to do or still does, some small ISP at the ends of the 90's did that since everybody was on dialup they would do that and people would thinkg they were ubber fast.

---

### Post by Coder543 on 2009-09-30
ok thanks, when i get time to test this i will, and then i will try to report my experience... but also, what if i want to make it a system-wide proxy... to be sure it catches all the sneaky background http/ftp stuff, not just the browser? (like update manager, etc.) :)

---

### Post by Thirtysixway on 2009-10-02
> **Coder543 said:**
> ok thanks, when i get time to test this i will, and then i will try to report my experience... but also, what if i want to make it a system-wide proxy... to be sure it catches all the sneaky background http/ftp stuff, not just the browser? (like update manager, etc.) :)

Well with ubuntu can't you set the proxy for the whole system?

System > Preferences > Network Proxy

Not exactly sure how to set this up on Windows, maybe in the network connection settings somewhere.

---

### Post by scrooge_74 on 2009-10-03
if not mistaken in Windows there a options for that, besides the moment you point the gateway to the proxy IP, everything has to go through it

---

