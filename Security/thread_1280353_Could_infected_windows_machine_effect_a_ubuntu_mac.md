---
title: "Could infected windows machine effect a ubuntu machine on the same network?"
date: 2009-10-01
forum: Security
---

### Post by millstone on 2009-10-01
I have googled,ect. ect. But I just wanted to confirm this.
Could infected windows machine effect a ubuntu machine on the same network?
Thanks. Also. could you please explain why?

---

### Post by oboedad55 on 2009-10-01
> **millstone said:**
> I have googled,ect. ect. But I just wanted to confirm this.
Could infected windows machine effect a ubuntu machine on the same network?
Thanks. Also. could you please explain why?

Linux has very few viruses first of all. Second, to the best of my knowledge, a Windows virus can't infect a Linux machine and vice versa. Last, to be ultra safe use a Linux anti-virus program like AVG, which is free.

---

### Post by undecim on 2009-10-02
> **oboedad55 said:**
> Linux has very few viruses first of all. Second, to the best of my knowledge, a Windows virus can't infect a Linux machine and vice versa. Last, to be ultra safe use a Linux anti-virus program like AVG, which is free.

No, Windows' viruses do not affect Ubuntu.

You don't need to worry about using anti-virus software, unless you are scanning files that have come from a windows computer (and even then, the viruses there don't affect the Linux machine. Only other windows computers that will be using those files.)

---

### Post by __p1n__ on 2009-10-02
There's more to it than just virii though.  A windows machine infected with a botnet client can easily be used as a platform to scan/attack other nodes on the network, other nodes possibly running active ubuntu os images.  So yes, an infected windows machine could at a minumum affect a ubuntu machine with a DOS attack and depending upon other factors, possibly do more.

---

### Post by scorp123 on 2009-10-02
> **oboedad55 said:**
> Linux has very few viruses first of all.  I use Linux since 1996 and I have not seen any Linux virus in the wild so far. And those AV scanners for Linux are scanning for Windows viruses anyway. So you can save yourself the hassle and don't need to bother about such software. Let Windows users fix their own problems.

---

### Post by dixonstalbert on 2009-10-02
The default configuration of Ubuntu doesnt allow  write privileges to other network users to your home directory and I believe Samba default disallows guest account.

Also all linuxs generally keep system executables in directorys that only the root user can modify.

(This is the big difference with Linux and Windows. Microsoft set up Windows so any downloaded application has full access to alter system files. This made it easier for developers to recycle large chunks of code already in the Windows directory- but what a security nightmare!)   

However, if you customize your ubuntu configuration by allowing net users write privileges, and/or the infected windows machine has a password cracking trojan and you have a weak root password on the ubuntu machine, you could have problems.

---

