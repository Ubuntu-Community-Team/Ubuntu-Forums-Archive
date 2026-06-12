---
title: "vmware-server not going away in update manager"
date: 2007-11-07
forum: Virtualisation
---

### Post by twistedtwig on 2007-11-07
Hi all,

I have had vmware-server in the update manager and each time I install it, it does not go away.  It says it all installs properly but I seems to fail miserably somewhere along the line coz it is not going away!!

can some one enlighten me please?

---

### Post by Feirefis on 2007-11-07
No help perhaps but I am having the same today - updated vmware but it still shows as update available. I'm using kubuntu and called in this forum to see if anyone else was getting this. Installed version is now 1.0.3-1and candidate for upgrade is the same.

Having updated vmware it is still working fine for me so it is not causing problems.

Feirefis

---

### Post by mattG on 2007-11-08
Glad to see that I am not the only one having this problem - I experience the exact same symptoms on Ubuntu 7.04...

---

### Post by timseal on 2007-11-08
I'll helpfully add that the same problem is happening on my machine also.

---

### Post by scorp123 on 2007-11-08
same here. :confused:

---

### Post by tbraun on 2007-11-08
Solved the problem...

I actually went and uninstalled vmware-server and then reinstalled. The pesky notification from the update manager went away.

Just a word of caution: Apparently you need to specify the 'purge' option when you do an 'apt-get remove' (if you installed via repos). I didn't do that, and promptly I could not install again out of the repositories. I ended up having to download vmware-server from the VMware web-site and do that install, which finally succeeded.

So, I hope that if you do the 'apt-get remove vmware-server --purge' you will not haver to go through that trouble.

Tom

---

### Post by timseal on 2007-11-08
That sounds more like another problem than a solution.

---

### Post by scorp123 on 2007-11-08
> **tbraun said:**
>  So, I hope that if you do the 'apt-get remove vmware-server --purge' you will not haver to go through that trouble.  Didn't help in my case .... the message about there being an "update" pops up right after I am finished installing again ..... No joy here. :(

---

### Post by LakeWind on 2007-11-10
I've got the same problem. The bug has been reported.

[https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/160683](https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/160683)

Hope it's resolved soon.

---

### Post by dshuck on 2007-11-10
Add me to the "Me too" list....

---

### Post by znemeth on 2007-12-03
I have the same problem on 7.10 with vmware-server version 1.0.4-1gutsy1

---

### Post by petervk on 2007-12-03
Another victim here. 2 different machines keep asking to update vmware-server.

---

### Post by yanks0616 on 2007-12-03
I have the same problem on 7.10 with vmware-server version 1.0.4-1gutsy1
$ uname -a
Linux workstation 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by twistedtwig on 2007-12-05
did an update today and it seems to be fixed (at least I am not being asked to do the update again)!!

---

### Post by znemeth on 2007-12-06
yeah, problem gone away for me also with an update to 1.0.4-gutsy2

---

### Post by znemeth on 2007-12-06
I mean 1.0.4-1gutsy2

---

