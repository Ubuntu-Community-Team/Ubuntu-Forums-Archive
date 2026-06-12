---
title: "What firewall and A/V do you recommend?"
date: 2010-07-09
forum: Security
---

### Post by Bernie Gallagher on 2010-07-09
I'm a recent convert to Linux.  I installed Ubuntu on one of my PCs last weekend.  I see that the Ubuntu Software Center has several firewalls to choose from.  Does it make a big difference which one I install?   And what about A/V?  My machine is rather under-powered, so I don't want one that runs in the background constantly; just run a nightly scan and warn me if I attempt to run a malware email attachment or file download.  Recommendations?

---

### Post by libssd on 2010-07-09
This is not a rhetorical question: but what problem are you trying to solve? For all intents and purposes, you don't need to worry about viruses with Linux. AppArmor is enabled by default, and provides quite a bit of protection, especially if you update the profiles: [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

**See also:**
[http://ubuntuforums.org/showthread.php?t=1521599](http://ubuntuforums.org/showthread.php?t=1521599)
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

If you get the idea that bodhi.zazen is the guru in this area, you are right.

I turned ufw on briefly, but it interfered with CUPS printing, and I haven't yet figured out how to avoid that, so I just turned it off. Unless you are running a server, you can relax; Linux is not Windows (thank goodness).

---

### Post by bodhi.zazen on 2010-07-10
> **Bernie Gallagher said:**
> I'm a recent convert to Linux.  I installed Ubuntu on one of my PCs last weekend.  I see that the Ubuntu Software Center has several firewalls to choose from.  Does it make a big difference which one I install?   And what about A/V?  My machine is rather under-powered, so I don't want one that runs in the background constantly; just run a nightly scan and warn me if I attempt to run a malware email attachment or file download.  Recommendations?

For a firewall, what do you want to accomplish with a firewall ? Ubuntu has no significant open ports by default so there is nothing to firewall. In addition most people are behind a router which has a built in firewall, so enabling a firewall on your Desktop is redundant.

If you must, ufw is the default fron end for iptables. If you wish a graphical interface, use gufw.

For the vast majority of users, ```
sudo ufw enable
```is all that is needed.

See:

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Likewise there are no know active viruses for Linux. If you wish, you can try clamav

[http://ubuntuforums.org/showpost.php?p=9265657&postcount=9](http://ubuntuforums.org/showpost.php?p=9265657&postcount=9)

I suggest you start with : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by HermanAB on 2010-07-10
You are a new user and installed using the defaults?

In that case, congratulations! You don't need to do anything. Ubuntu is perfectly fine as is.  Relax and enjoy your nice new secure system.

---

### Post by d3v1150m471c on 2010-07-10
Here is the extent of my paranoia:
Firestarter, first and foremost
psad
rkhunter
clamav
a few useful bash scripts

---

### Post by Bernie Gallagher on 2010-07-10
> **libssd said:**
> This is not a rhetorical question: but what problem are you trying to solve?

No problem.  I just want to protect my computer from viruses.  I use Norton on my Windoze machine, but they don't seem to have a version for Linux (same old story, eh?).

---

### Post by Bernie Gallagher on 2010-07-10
> **bodhi.zazen said:**
> In addition most people are behind a router which has a built in firewall, so enabling a firewall on your Desktop is redundant.

If you must, ufw is the default fron end for iptables. If you wish a graphical interface, use gufw.

I'm behind a router.  But I don't know if it has a built-in firewall.  It's a Linksys Wireless A+G.  All my computers, my printer, and my Xbox are all behind that one router, and my Windoze machine got a really nasty virus last weekend that forced me to wipe my hard drive and reinstall Windoze from scratch (I came -THIS- close to trashing Windoze and putting Linux on that machine).  I've heard people have trouble with ufw sharing network printers and such, so I'll take a wait-and-see attitude for now.  Thanks!

---

### Post by oldos2er on 2010-07-10
> **Bernie Gallagher said:**
> No problem.  I just want to protect my computer from viruses.  I use Norton on my Windoze machine, but they don't seem to have a version for Linux (same old story, eh?).

Windows software (including viruses and malware) does not run natively on Linux.

You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by bodhi.zazen on 2010-07-10
> **d3v1150m471c said:**
> Here is the extent of my paranoia:
Firestarter, first and foremost
psad
rkhunter
clamav
a few useful bash scripts

And have you ever found anything other then false alerts ?

---

### Post by bodhi.zazen on 2010-07-10
> **Bernie Gallagher said:**
> No problem.  I just want to protect my computer from viruses.  I use Norton on my Windoze machine, but they don't seem to have a version for Linux (same old story, eh?).

As indicated in this thread, viruses are a non-issue. They can happen, but there are no know active viurses at this time, your system was patched long ago to known viruses of any significance.

There is no need for "Norton" on Linux.

You can look at the security sticky if you like, look at the HIDS thread.

Linux is not windows and not much of what you are asking about applies to Linux. That is not to say that Linux is invulnerable, you will need to learn a few new tricks is all.

---

### Post by wacky_sung on 2010-07-11
Personally i feel iptables is still the best firewall incorporated by default in Ubuntu.It just require some knowledge of learning and so customize to any needs.

---

### Post by bodhi.zazen on 2010-07-11
> **wacky_sung said:**
> Personally i feel iptables is still the best firewall incorporated by default in Ubuntu.It just require some knowledge of learning and so customize to any needs.

I agree. The problem as you point out, new users usually do not know how to configure iptables.

IMO it is easier to start with UFW/GUFW , and ufw in particular eases the transition to iptables (the syntax is very similar).

---

