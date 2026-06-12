---
title: "Security Inprrmation"
date: 2013-08-15
forum: Server Platforms
---

### Post by ConcreteDonkey on 2013-08-15
Hello,

I've been tinkering with an Ubuntu Server for a while now but there's something I've noticed there is a lack of a precise guide on best security practices the Ubuntu guide is good but I'm always been looking something more detailed and in-depth. Any suggestions will be appreciated.

---

### Post by TheFu on 2013-08-15
> **badboy4life said:**
> Hello,

I've been tinkering with an Uubunt Server for a while now but there's somehthing I've noticed there is a lack of a prescise quide on best sexurity practices the Ubuntu guide is good but I'm always been looking something more detailed and indepth. Any suggestions will be appreciated.

There are billions of different server configurations. It is impossible to have a "best practices" that covers everything.  Attacks change daily, so countermeasures change constantly too.  If you said what programs you were planning, we might be able to provide specific references.

However, there are commonly known things to be done to get you started.  The Ubuntu community has created a few security guides. Google "ubuntu security" to find them.  For every server app/service that you deploy, you can do the same search "ubuntu security {insert-app-name}" and "ubuntu best practices {insert-app-name}" too. Here's one: [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

Basic Linux/UNIX security hasn't really changed over the years. The ideas are the same, just some of the tools have gotten better or been replaced by a new wiz-bang tool. A solid understanding of file and user permissions is the basis for everything on a server. Got that nailed? Excellent.

Don't forget that most of system attacks are actually handled at the network layer - before any traffic gets to a server.  Understanding security architectures is critical to avoid having your network and then your servers cracked.  I've seen lots of admins claim that they know security because their servers have never been hacked.  That just isn't true. Being hacked ... twice ... (both before 2002) were the main things that got me interested in all parts of security architecture and deployment. When your box tells you to "**go away, you don't exist**" that is a real eye opening experience.  Then finding the root password has been changed freaked me out even more.  It is hard to explain that feeling.

I will say that **versioned backups** are the #1 thing for the security minded admin.  #2 is configuration management consistency and #3 is monitoring.  Monitoring security notices [http://www.ubuntu.com/usn/](http://www.ubuntu.com/usn/) is important too.

BTW, there have been more than a few general security questions asked here over the years.
* [http://ubuntuforums.org/showthread.php?t=2092929](http://ubuntuforums.org/showthread.php?t=2092929)
* [http://ubuntuforums.org/showthread.php?t=2115686](http://ubuntuforums.org/showthread.php?t=2115686)
* heck - just start here: [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

For more in-depth knowledge, seek out CISSP and SANS training.  Find a local Defcon group [https://www.defcon.org/html/defcon-groups/dc-groups-index.html](https://www.defcon.org/html/defcon-groups/dc-groups-index.html) - those exist all over the world and are full of security professionals.

So - this reply is really a shotgun of information. Hopefully, something in here addresses your real question. Hopefully. ;)

---

### Post by ConcreteDonkey on 2013-08-15
I currently have SSH, nginx (PHP, MySQL), Samba and a Minecraft server if it helps. All are low traffic and pretty much just for personal/friends to use but I notice in my nginx logs that the server gets attacked daily.

---

### Post by TheFu on 2013-08-16
Php, Samba and Java probably shouldn't be on the internet if you care about security. This is the general opinion of IT security professionals, not just mine. If you must use programs based on php or java, put them behind a VPN. The same applies to Samba.  For internet access, samba is the last thing you should use - sftp with keys would be better, but if you have a secure VPN setup (not PPTP!), samba should be completely fine.

There are more than a few best practice articles for ssh and nginx. It is best if you find them yourself vs reading the articles that I've written. Check multiple sources.  These are mine.
* [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)
* [http://blog.jdpfu.com/2011/10/12/web-based-administrative-tools](http://blog.jdpfu.com/2011/10/12/web-based-administrative-tools)
* [http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers](http://blog.jdpfu.com/2011/08/18/readers-ask-about-reverse-proxy-servers)

With MySQL - I'd run it on a different machine from wherever the web server runs. Part of security architecture.  I'd block all requests to the SQL except from the 1 machine that needs it and I'd read up on XSS attacks.

**Just because something works, doesn't mean it is secure.**

---

