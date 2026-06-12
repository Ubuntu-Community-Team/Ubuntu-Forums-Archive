---
title: "Server Upgrade Problem"
date: 2009-05-05
forum: Server Platforms
---

### Post by [pl]ice on 2009-05-05
Hi,

 Got VPS server with ubuntu, but recently i cannot upgrade the following packages. I can't find more info why this is happening:

 apt-get upgrade -V
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
   bind9-host (9.4.2-10ubuntu0.1 => 9.4.2.dfsg.P2-2ubuntu0.1)
   dnsutils (9.4.2-10ubuntu0.1 => 9.4.2.dfsg.P2-2ubuntu0.1)
   libbind9-30 (9.4.2-10ubuntu0.1 => 9.4.2.dfsg.P2-2ubuntu0.1)
   libdns35 (9.4.2-10ubuntu0.1 => 9.4.2.dfsg.P2-2ubuntu0.1)
   libisccc30 (9.4.2-10ubuntu0.1 => 9.4.2.dfsg.P2-2ubuntu0.1)
   libisccfg30 (9.4.2-10ubuntu0.1 => 9.4.2.dfsg.P2-2ubuntu0.1)
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.

The apt-get is pointing to my Host who is holding the ubuntu update tree. Maybe i should point it to ubuntu normal web ubuntu server?

thanks

---

### Post by ITAndrew on 2009-05-05
Im pretty sure that the packages that are being held back are distribution updates, and since you did not specify that you want to do a dist-upgrade it apt holds back the distribution updates. Try sudo apt-get dist-upgrade and this should install all packages and update you to a later release up ubuntu.

---

### Post by [pl]ice on 2009-05-06
ITAndrew,

  Why a dist update? Is the new version of ubuntu coming out? Or is this some how major update? I have never met this before :/
thanks

---

### Post by _sluimers_ on 2009-05-06
> ITAndrew,

Why a dist update? Is the new version of ubuntu coming out? Or is this some how major update? I have never met this before :/
thanks 

Jaunty came out some time ago if that's what you mean.

---

### Post by [pl]ice on 2009-05-06
OMG! I didn't know anything!

Thanks guys.

---

