---
title: "Can Firestarter do this....."
date: 2009-07-10
forum: Security
---

### Post by Victor43 on 2009-07-10
Does anyone know if its possible to allow only certain applications access to the internet ? Another words can I add a rule that says Firefox is allowed and gFTP is allowed. I do not want to make a rule which says any outgoing data on port 80 and 21 is allowed. I hope I am making myself clear. If FS cannot do this how then would it be possible ?  Thanks in advance

---

### Post by Dr Small on 2009-07-10
What would be the purpose? Firefox uses port 80 to communicate with webservers, and gFTP uses port 21 to connect to FTP servers. Why would a whitelist of selected protocols/ports be acceptable?

---

### Post by Rubicon_82 on 2009-07-11
This *used* to be possible with iptables.*  For example, the following iptables rule would prevent firefox from sending packets:
```

-A OUTPUT -m owner --cmd-owner /usr/bin/firefox -j DROP
```

However, this is only possible with single-core processors. **It will not work on SMP chips (i.e. multi-core)**
(From [http://linux.die.net/man/8/iptables](http://linux.die.net/man/8/iptables))
> 
**--cmd-owner** *name*
    Matches if the packet was created by a process with the given command name. (this option is present only if iptables was compiled under a kernel supporting this feature)
**NOTE: pid, sid and command matching are broken on SMP**

I do not understand why iptables can no longer do command matching.  Maybe someone more knowledgeable about the implementation of iptables within the Linux kernel could explain this.

*) Note that iptables is the Linux firewall. Programs such as Firestarter and [g]ufw are simply frontends to iptables.

---

### Post by lovinglinux on 2009-07-11
> **Victor43 said:**
> Does anyone know if its possible to allow only certain applications access to the internet ? Another words can I add a rule that says Firefox is allowed and gFTP is allowed. I do not want to make a rule which says any outgoing data on port 80 and 21 is allowed. I hope I am making myself clear. If FS cannot do this how then would it be possible ?  Thanks in advance

What are you trying to achieve? Are you afraid that some application will connect using port 80 or 21 without your knowledge? 

Users coming from Windows (myself included a few months ago) like to control which application can access the network, because Windows is full of ad-aware and unauthorized outgoing connections. ET phone home!

Linux is different. The software from the repositories is tested and the code can be inspected, so there is no need to block outgoing connections based on applications. 

I recommend reading the tutorial [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421)

BTW, if you want full control of your firewall, then use iptables commands, not Firestarter, which by they is outdated. If you need a graphical firewall manager use [gufw](apt:gufw)[apt-get]

> [color=#CC0000]**Note:**[/color] when you see [apt-get] after a link on my posts it means that you just need to click it to install the software. This is basically an easy way to perform an installation from the [repositories](http://en.wikipedia.org/wiki/Software_repository)  without running the command on a terminal. This is the same as running the command *sudo apt-get install* followed by the name of the program.

---

### Post by Victor43 on 2009-07-11
> **lovinglinux said:**
> What are you trying to achieve? Are you afraid that some application will connect using port 80 or 21 without your knowledge? 

 Users coming from Windows (myself included a few months ago) like to control which application can access the network, because Windows is full of ad-aware and unauthorized outgoing connections. ET phone home!

Linux is different. The software from the repositories is tested and the code can be inspected, so there is no need to block outgoing connections based on applications. 

I recommend reading the tutorial [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=765421")

BTW, if you want full control of your firewall, then use iptables commands, not Firestarter, which by they is outdated. If you need a graphical firewall manager use [gufw]("apt:gufw")[apt-get]

 Thanks for the reply.   Yes I am concerned that rogue scripts which can be installed *unknowingly* via websites you visit or by clickjacking on your computer can collect personal data i.e. Paypal/eBay site login details and then send their data abroad. I have read that malicious scripts can be installed on Linux and not just on Windows. Will look into using gufw.   Thanks  Victor

---

### Post by lovinglinux on 2009-07-11
> **Victor43 said:**
> Thanks for the reply.   Yes I am concerned that rogue scripts which can be installed *unknowingly* via websites you visit or by clickjacking on your computer can collect personal data i.e. Paypal/eBay site login details and then send their data abroad. I have read that malicious scripts can be installed on Linux and not just on Windows. Will look into using gufw.   Thanks  Victor

Maybe [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) could protect you from that.

---

