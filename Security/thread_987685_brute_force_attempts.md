---
title: "brute force attempts"
date: 2008-11-19
forum: Security
---

### Post by [pl]ice on 2008-11-19
Hi,
got ubuntu server, and i get heaps of brute force attempts for my ssh ftp, u name it.
 I know that there is a possibility to setup firewall to ban the IP after e.g. 3 trial login failed. How to do it? i'm gonna do more reseach now. I'll contact the ISP as well, and let them know, its getting ridiculas now.

thanks guys!

Polish

---

### Post by talen.quickblade on 2008-11-19
Have you looked into implementing the DenyHosts package? I've deployed it at my own house to much success. I can even have it email out a note, so I know when the system is actively denying connections. I think it will accomplish what you need.

---

### Post by teddks on 2008-11-19
sshguard is very good and has minimal installation.

---

### Post by rhcm123 on 2008-11-19
> **talen.quickblade said:**
> Have you looked into implementing the DenyHosts package? I've deployed it at my own house to much success. I can even have it email out a note, so I know when the system is actively denying connections. I think it will accomplish what you need.

I would agree with Quickblade.
I run a web server (for remote access), and it's constantly being brute forced
but always from the same block of ip's.
I got denyhosts and just blocked xxx.xxx.34.yyy
(I censored the x's for some privacy, the y is there cause everything on the subnet 34 is blocked)

subnets blocked... although they still try to connect :)

---

### Post by [pl]ice on 2008-11-19
Hi guys,

 Just had a look at DenyHost. Its only for ssh, and I got more services running.

Instead I found 
[http://www.fail2ban.org/wiki/index.php/Features](http://www.fail2ban.org/wiki/index.php/Features)

fail2ban, scans the selected logs, then bans the IPs; will work with different services. So I guess, I even could configure it for TorrentFlux logins, or even samba etc.
 I'll try that tomorrow. Had enough of knocking at my box :)

thanks guys for quick response!!!
EDIT:talen.quickblade, how did u setup the email notification? did u need to instal a mailserver? i don't know it, so i don't really want to run a mail service if i'm not familiar with it etc

thanks :)

---

### Post by cariboo on 2008-11-19
Fail2ban and denyhosts are in the repositories, exim4 usually gets installed as a dependency. Exim4 is easy to setup. There will be a setup window that pops up during installation.

Jim

---

### Post by talen.quickblade on 2008-11-19
DenyHosts will allow you to deny connection to any services on your system. This can be defined in the config file.  Additionally, the config file allows you to set up a mail notification. It requires an smtp server be defined in the config. I do run a postfix server, however denyhosts could easily be pointed to your provider's smtp server just as easily.

Look at the BLOCK_SERVICE information for denyhosts. Additionally look at the SECURE_LOG information, as this allows you to define the auth.log location. By default the package is configured only for sshd, but other services can be added.

---

### Post by coastdweller on 2008-11-20
I really like [http://www.configserver.com/cp/csf.html](http://www.configserver.com/cp/csf.html)

Easy to install, easy to work with. No guy for ubuntu but easy enough through console to understand what to do.

It will e-mail ya when you're getting hit. It will monitor file/folder locations for changes and e-mail ya.

It tastes like chocolate as well, not sure why.

---

### Post by bodhi.zazen on 2008-11-20
Personally I like OSSEC

You can also look at this :

[http://e18.physik.tu-muenchen.de/~tnagel/ipt_recent/](http://e18.physik.tu-muenchen.de/~tnagel/ipt_recent/)

---

### Post by [pl]ice on 2008-11-20
> **bodhi.zazen said:**
> Personally I like OSSEC

You can also look at this :

[http://e18.physik.tu-muenchen.de/~tnagel/ipt_recent/](http://e18.physik.tu-muenchen.de/~tnagel/ipt_recent/)

cool i'll check them all tomorrow. My only problem now is that my email service provider is checking the IP of the sending PC, if it doesn't match the hostname, then won't allow to send (apparantly its anty spam rule, by law). So i'm stuck sending logs from remote PC (as server got its own IP)

thanks for replays :):popcorn:

---

### Post by Lars Noodén on 2008-11-22
Many services are tcpd-aware, so you may look into using that while you are figuring out what rules to use in IP Tables.

[INDENT][http://linux.die.net/man/8/tcpd](http://linux.die.net/man/8/tcpd)[/INDENT]

You'll want to add the annoying host to /etc/hosts.deny

[INDENT][http://linux.die.net/man/5/hosts.deny](http://linux.die.net/man/5/hosts.deny)[/INDENT]

If you look around on the net you can find some recipes and examples.

You've found Oskar Andreasson's IP Table's tutorial, I hope:

[INDENT][http://iptables-tutorial.frozentux.net/iptables-tutorial.html#LIMITMATCH](http://iptables-tutorial.frozentux.net/iptables-tutorial.html#LIMITMATCH)[/INDENT]

---

