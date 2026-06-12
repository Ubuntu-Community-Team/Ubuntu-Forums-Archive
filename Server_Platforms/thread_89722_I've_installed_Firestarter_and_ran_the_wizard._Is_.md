---
title: "I've installed Firestarter and ran the wizard. Is the PC sure now?"
date: 2005-11-13
forum: Server Platforms
---

### Post by kimvall on 2005-11-13
Hello all, I just installed Firestarter and then ran the wizard on startup.

Does this mean that my Linux machine is fairly protected now? I am not that familiar with firewall configurations, so I am hoping that's really all I have to do. Or is additional configuration needed?

Also, does it work like the Windows XP firewall? What I mean by that is that once it's there, it does it's stuff without notifying me all the time about various packages being reject and accepted? Or should I assume that domething is wrong when it doesn't notify me about anything?

Thanks in advance.

---

### Post by mit on 2005-11-13
Ubuntu is secure without Firestarter so now you have it really is the icing on the cake!

I installed it because sometimes i use my laptop outisde my gateway which means i want the added protection. 

It works silently, although you can look at the logs and see what is what if you want. :)

---

### Post by frodon on 2005-11-13
These links allow you to see that your firewall works : 
[http://scan.sygatetech.com/](http://scan.sygatetech.com/)
[https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2)

The first should return : Unable to detect any running services!
The second : all ports as stealted

---

### Post by kimvall on 2005-11-13
Excellent. Thanks!

---

### Post by kimvall on 2005-11-13
Hmm, I am not quite sure I follow you. It is secure but in certain places, like outside your gateway, it could be insecure? What's the difference between being outside your gateway (uness your gateway is a firewall that is)?

I don't have any kind of firewall at the moment (my d-link firewall switch died last night).

[QUOTE=mit]Ubuntu is secure without Firestarter so now you have it really is the icing on the cake!

I installed it because sometimes i use my laptop outisde my gateway which means i want the added protection. 

It works silently, although you can look at the logs and see what is what if you want. :)[/QUOTE]

---

### Post by Biased turkey on 2005-11-13
[QUOTE=frodon]These links allow you to see that your firewall works : 
[http://scan.sygatetech.com/](http://scan.sygatetech.com/)
[https://grc.com/x/ne.dll?bh0bkyd2](https://grc.com/x/ne.dll?bh0bkyd2)

The first should return : Unable to detect any running services!
The second : all ports as stealted[/QUOTE]

I'm not a security Guru lol, but your reply confirms the one I got from another post:
[http://www.ubuntuforums.org/showthread.php?t=87993]("http://www.ubuntuforums.org/showthread.php?t=87993")
It was suggested by Lotusleaf.
I ran the scan from sygatetech and the report states that all the ports are blocked.
What puzzles me is that stealthscan doesn't mention the CUPS printing port because that port 631 is open on my LAN ( I have a 2 computers LAN, a firewall-router-ssh server and printer-server )
Anyway, I think that a single rig doesn't require any firewall, I installed Ubuntu on my mother's computer ( she is 83, probably the oldest Ubunu user )  without firewall but installed firestarter on my Ubuntu router because I have a LAN.

---

### Post by frodon on 2005-11-13
Yes that's true, you don't really need a firewall, ubuntu is enough secure. Running a firewall is usefull if don't want anybody to know the name of your computer or when you run, like me, some services.
For example i need a firewall in order to allow or not the IP of my friends which will use my ftp server, so i'm sure to allow only known incoming IP's for my server.

---

### Post by kimvall on 2005-11-13
Ok, then I know. Thanks for the help, both of you.

---

### Post by jdong on 2005-11-14
Ubuntu's default configuration is secure by default, meaning that it doesn't open any ports by default. Closed ports and stealth ports are equally secure -- don't listen to any garbage about Stealthing that Windows Firewall vendors try to trick you with.


Firewalls are useful as a "2nd layer" of protection, just in case:

(1) you **accidentally** open up a port while installing a new service... Some of them are configured to listen publicly by default (like SSH)
(2) An unwelcome user/program opens up a port (they're allowed to open any port 1024 and above). This needs a firewall to protect against, since only the root user (or someone using sudo) can bypass this layer of protection.


Please don't use firewalls as a cover-up for misconfiguration... that's just asking for trouble one day! Firewalls should only be used to protect the above two scenarios.

---

### Post by Zerocool10482 on 2005-11-16
What about a virus? Do I use ClamAV?

---

### Post by jdong on 2005-11-16
I have never ever seen a live Linux virus before.... ever. ClamAV is more for checking stuff that Windows systems access (Samba file sharing server, e-mail, proxy, etc)...

Look into **chkrootkit** if you run a server, since attackers like to install rootkits if they ever get in.

---

