---
title: "Server 7.10 memory leak?"
date: 2008-04-08
forum: Server Platforms
---

### Post by tessmonsta on 2008-04-08
I recently installed Ubuntu Server 7.10 to power my website after a long period of using Gentoo. Since the install, I've been having nothing but problems with the new OS. 

It seems every 32 to 48 hours, the server will become unresponsive. Apache won't serve pages, mysql seems to die, and even SSHD grinds to a halt. I have little choice but to restart the box to get it working again. 

I believe I've tracked down the problem to an out of memory error -- the system logs and dmesg seems to indicate it. I've been periodically checking with top and I'm finding the system consuming more and more memory over time. There's 512mb on the box now. Fresh from restart I have 200mb free, but over 32 to 48 hours, that'll drop down to 8mb or less. 

Does anyone else have the same problem?

---

### Post by cdenley on 2008-04-08
I've been running two gutsy lamp servers without a problem. When monitoring memory, make sure you ignore the disk cache since it normally uses any available memory until it is needed. Try using htop, you can sort by memory usage to see if a single program is using all your memory. Are you running any unusual services? Could it be a php script or a mysql command that is eating all your memory? DoS attack? Have you installed all the security updates?

---

### Post by freebeer on 2008-04-08
I run 7.10, apache2, mysql, samba etc. My uptime is currently at 36 days with 100% CPU usage (I'm running one instance of folding@home) on a dual core.

I'm not really using apache2 to server web pages, though.  (Mostly for gui-based admin stuff like webmin.)  And that may be a hint to the issue: if you are getting memory leaks and it's apache related, it's more likely the code/scripts that you're running than apache or 7.10 itself.

Anyway, just thought I'd toss that out in case it helps you diagnose the issue.

---

### Post by Sapphiron on 2008-04-10
I have got the same problem with 7.10 my client's server

We use it to run their web based application server (jboss, Java SDK, MySQL, FTP and SSH are the only things intalled on the box).  It has quite some serious hardware in it though.

Core 2 E8400 dual 3Ghz
ASUS P5E-VM DO Q35 chipset motherboard
2GB DDR2 667 RAM
250GB SATA hard drive.

I run the same software on my own VMserver on only 512mb RAM, but this server, after running for about 48 hours consumes all its ram.

Same as tessmonsta even the SSH stops working.  Running TOP I can see all ram is allocated with about 8mb free. I can account for about a GB of the ram totalling all the services (java (700mb), mysql (128mb) etc).  Top does not specify any other memory user.

Help, I cant run the 24 hour reboot script on this box indefinitely.

---

### Post by gtdaqua on 2008-04-10
wats the swap using you are using. it must be minimum 1.5x the physical memory and not more than 2x. type 'free' in terminal and paste the output. If your swap is not correct, then you may run into the problems you have mentioned. I had that once and it was because of swap was not being used and CPU hit 100% and froze.

I run Gutsy on half a dozen  production servers - nothing has failed but one because of a storage driver problem.

---

### Post by cdenley on 2008-04-10
Maybe [this]("http://ubuntuforums.org/showthread.php?t=749836") is your problem? Are you using multiple sockets or SSL?

---

