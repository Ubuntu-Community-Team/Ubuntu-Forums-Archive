---
title: "Is getting pinged this much normal?"
date: 2009-12-11
forum: Security
---

### Post by pepsifx357 on 2009-12-11
I was looking through my log today on my router and noticed that My webserver was getting pinged over 200 times a day by a few different IP addresses from different countries.  China, Turkey, Honduras, and Italy.

They were pinging hi port numbers on my webserver random pings from 48000 down to 28000.

My first webserver, so I wasn't sure.

---

### Post by pepsifx357 on 2009-12-11
I found in one of the forums, how to check for ssh logins and I found this:

> Dec 11 15:56:01 BenNet sshd[11015]: Failed password for root from 212.156.5.254 port 48627 ssh2
Dec 11 15:56:02 BenNet sshd[11023]: Address 212.156.5.254 maps to static.turktelekom.com.tr, but this does not map back to the address - POSSIBLE BREAK-IN ATTEMPT!


Some ahole from Turkey

---

### Post by pricetech on 2009-12-11
fail2ban

Install it using Package Manager.  It'll help.

---

### Post by ubudog on 2009-12-11
Yes, fail2ban should work.  Seems like a nice program.  Might try it.

---

### Post by pepsifx357 on 2009-12-11
Awesome, thanks!

---

### Post by bodhi.zazen on 2009-12-11
fail2ban and deny hosts are nice, but so is iptables.

You can limit pings (although honestly 200 pings is nothing) and block repeated attempts to access services, such as ssh.

You can rate limit ping and http ...

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by Cheesemill on 2009-12-12
Yes, it's completely normal for a default web-server/ssh-server install.

There are hundreds of thousands of script-kiddies out there trying to compromise unsecured machines.

This is one of the reasons that Ubuntu has the root account disabled by default, it is the main user-name that people will try and hack.

Take a look here for more info:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

