---
title: "Random Internet Fault"
date: 2010-09-10
forum: Server Platforms
---

### Post by max-power2717 on 2010-09-10
Hi Forum, 

I have a problem with my Internet connection while I'm changing Wordpress websites on a test web/ftp server I run on my home LAN. The server is running ubuntu 9.10 server edition, and I have the usual services for a LAMP server (Apache, MySQL, PHP5 - all installed with apt utility from the repositories as far as I can remember). I added on the rewrite and security modules to Apache as well (I don't know the precise versions of these software packages, but can find out if anyone thinks that will be helpful). 

Now, I have a free dynamic dns hostname configured to my IP address. Internet traffic arrives at my house at a D-LINK ADSL router / 10/100 switch. I have configured the router to redirect certain ports to my server for various services I open up temporarily from time to time to the outside world. This network configuration serves my needs and has worked fine for me for over a year. 

However, since I started using wordpress, a very frustrating problem has started occurring: Quite randomly (and quite often) my LAN will be deprived Internet access because the router has frozen up. Lights blink on the router, and the LAN switching still happens, but no ADSL Internet connection is available. Also the router's web based configuration interface is not available when this happens. The ONLY way to recover from this failure is to unplug the router from the wall to power it down, and reconnect it. This is a huge hassle, and I have to do it a couple of times an hour when editing wordpress sites. 

Since these problems only happen when I'm changing a wordpress site, there's obviously something happening on my web server (or some sort of traffic it's sending) that the router chokes up on and causes it to hang when using the wordpress admin back-end. That could be something wordpress its self is doing, or prehaps PHP, MySQL, Apache... I really don't know what to blame for this. I would like very much to narrow down what it could be so as I can work on changing configuration to prevent it from happening. Problem, I have no idea where to start (what service causes the ADSL Router to choke up?).

I wonder if anyone can offer any suggestions? Perhaps some logs that might indicate precisely when the Internet connection fails? Perhaps then I could identify the service that caused the failure.

I'm really at a loss in this situation. I don't want to have to replace what is otherwise a perfectly good ADSL router, and I'm not even sure that'd make my problem go away. I would really like to find some sort of explanation.

Any ideas or insights at all will be greatly appreciated.

---

