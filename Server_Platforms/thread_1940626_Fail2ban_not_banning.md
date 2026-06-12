---
title: "Fail2ban not banning"
date: 2012-03-14
forum: Server Platforms
---

### Post by FraggyMDL on 2012-03-14
Hey
I'm new on this forum so my post might not be perfect, I will edit it if you need.
So I recently got an Ubuntu server as a gift from a friend, in Netherlands; he never used it and I configured all my stuff (Apache, VNC, FTP...).
But I have a LOT of attacks on the server, principally "w00tw00t" on Apache, and A LOT of SSH attacks (bruteforcing the root password and random users). I just got this server 5 days ago, and now the SSH auth.log is already 2MB, full of error messages for authentication.
So I decided to install fail2ban, configured, etc.
But the attacks continue, mostly from the same IP (1 IP per day it seems); even though in fail2ban.log this IP is marked as "banned".
I have a lot of these messages : "iptables -n -L INPUT | grep -q fail2ban-ssh returned 100" in the logfile, at every banning. So is this the cause of the problem?
I run as root user, so I can do everything I want to solve that problem.

Thanks ;)
The server is Ubuntu 10.10 Server, upgraded to 11.10 (by modifying the packages sources, from maverick to natty then from natty to oneiric, upgrade manager didn't want to install).

---

### Post by Holdolin on 2012-03-14
Sounds to me like you've been compromised.  In such a case, the attacker can manipulate anything they wish.  They can modify the output of any program you have to detect/stop further attacks.  In most intrusion cases i've seen, the first thing they do when they get control of your system is to disable or otherwise modify any program that would stop them from doing as they please.  

My suggestion would be to back up any data (not settings or such, as they may well be compromised as well) and re-install your server.  This is actually for 2 reasons: 
First, it will obiously re-secure your system.  Once somebody as compromised your system, there's really no reliable way to tell what has or has not been tampered with.
Secondly, though it is supported, I don't personally reccomend upgrading via the update manager.  I always do a clean install.

Also, what do you have as a firewall?  It is reccomended that you have a hardware firewall sitting between your server(s) and the internet.

The guides I use to secure my servers are:
[http://www.debian.org/doc/manuals/securing-debian-howto/]("http://www.debian.org/doc/manuals/securing-debian-howto/")
or, if you want a quicker, get right to it then you might find
[http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/]("http://www.tldp.org/HOWTO/Security-Quickstart-HOWTO/")

I know these manuals are geared towards Debian, but the principles are the same.  I also know it's a lot of reading, but let's face it, the internet is a bad bad place to go unprotected.  Knowledge is your power.  Wield it with relentless effort.

Also, welcome to the forums, and the goodness that is Ubuntu :)

---

### Post by FraggyMDL on 2012-03-15
Hey, I just found the root of the problem, now I need to solve it.
When I do any iptables command here is the message I have :
WARNING: Couldn't open directory /lib/modules/2.6.35.4: No such file or directory
FATAL: Could not open /lib/modules/2.6.35.4/modules.dep.temp for writing: No such file or directory
My kernel is 3.0 not 2.6... How to make depmod understand I have kernel 3.0?


EDIT : problem solved, reinstalled the whole system.

---

### Post by d4m1r on 2012-03-16
Another tip: change the default ports, especially for SSH. If you set your SSH port to something random, nobody will ever know where to even connect to your server.

---

### Post by Holdolin on 2012-03-16
> **d4m1r said:**
> Another tip: change the default ports, especially for SSH. If you set your SSH port to something random, nobody will ever know where to even connect to your server.

Ya know, while I know I'm no security guru or anything, I thought I had a decent working knowledge of security.  I never thought of changing default ports (which is easy enough.)  Lesson learned here as well, thanks :)

---

