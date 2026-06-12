---
title: "connection failure"
date: 2005-11-19
forum: Repositories &amp; Backports
---

### Post by Manuka on 2005-11-19
Hi all,

I am struggling with my package downloads.
I have already copied a source list from the forum (thanks by the way), I have checked the ping command and it worked (thanks also for the tip), BUT... I still receive this sort of message:

[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-i386/Packages.gz:) 407 Proxy Authentication Required

Here I need to say that I am connected on a university network and that we need to enter login/password everytime we want to browse the internet. I set the synaptic network properties with the uni IP address.

So.. why does it work with the ping command, and not with synaptic??
or is it something else

Thanks a lot!

manu(ka)

---

### Post by marco-zero on 2005-11-25
Include your login name and password besides your proxy host name on the network settings of synaptic.  It worked for me.

Sources:  
   [http://www.aims.ac.za/pipermail/aims-tech/2005-August/000087.html](http://www.aims.ac.za/pipermail/aims-tech/2005-August/000087.html)
   [http://ubuntuforums.org/archive/index.php/t-1575.html](http://ubuntuforums.org/archive/index.php/t-1575.html)
   [http://ubuntuforums.org/archive/index.php/t-20310.html](http://ubuntuforums.org/archive/index.php/t-20310.html)

---

