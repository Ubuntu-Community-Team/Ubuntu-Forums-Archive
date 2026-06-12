---
title: "Firestarter and firewall question"
date: 2007-07-25
forum: Server Platforms
---

### Post by twistedtwig on 2007-07-25
Hi all,

I recently had my server box compromised so I am ensuring all is backed up and then going to reinstall with Feisty (started with 5.10 and did upgrades over time)..

It looks like I may have got a trojan (could be through something I installed (although I hardly install antyhign on the server these days as she runs as I want).. so thinking it coudl have come from the nasty net.

[http://ubuntuforums.org/showthread.php?t=508661&highlight=firewall](http://ubuntuforums.org/showthread.php?t=508661&highlight=firewall)

this thread seems sensible about a bit of protecton.

What I would like to know is, is firestarter an addition to IPTables?  I have iptables running blocking all ports then opening the few that I use (will be changing SSH to not run on 22 this time).

I just want to make sure she is as secure as possible this time to minize the chance of it happening again.

any and all advice would be great.  

Thank you

---

### Post by weth on 2007-07-25
Firestarter is just a grafical interface for your iptables which makes it easier to modify some aspects of the firewall. You can also easily share you internet connection through it. Here is the online manual for detailed information:

[http://www.fs-security.com/docs.php#docsdownload](http://www.fs-security.com/docs.php#docsdownload)

It will be wise to install Bastille as well.

enjoy :)

---

### Post by wieman01 on 2007-07-25
I second that as well. Firestarter is a good option which lets you configure IP tables easily. I don't know if you happen to have a GUI though.

I have been using Firestarter for a while and I am fairly happy with it.

---

### Post by Wim Sturkenboom on 2007-07-25
Consider passwordless SSH (use key to access box); also do not allow users with root privileges (or that can gain root privileges using sudo) to use SSH.
Further, if you have a FTP server running, use SSL with it so passwords can not be sniffed. It's quite useless to send yourusername / password in the clear using FTP and using the same username / password in SSH :)

---

### Post by twistedtwig on 2007-07-25
Thank you for all the info.

I have no need or desire for FTP really.  had VPN setup SSH (will do the none root user bit on that, didn't have that before).

Will look at Bastille as well.

I will have gnome (I do like it at times but I know it adds over head).

With Firestarter I presume I can still edit the IPTables firewall directly if I wanted to as well as use its interface?  I am guessing it is just a nice GUI interface that would do the same as manually typing it in (but reducing the chance of me messing things up)!

Thanks again

---

