---
title: "[SOLVED] Samba Lockup"
date: 2008-09-07
forum: Server Platforms
---

### Post by Dusenberg on 2008-09-07
I connect to my home pc xp drives from my ubuntu (Gutsy) laptop using Samba. Works a treat except if someone switches off the PC. Then ubuntu completely locks up and the only way to get out of is to switch the laptop off. I've lost work like this, and it's not possible to guarantee the PC is not switched off.  Is there some way to get Samba to fail gracefully if the PC suddenly 'dies'?

Cheers

---

### Post by bobbob1016 on 2008-09-07
I'm not sure I can help much, but knowing if you put the smb share in your /etc/fstab might help someone else.

---

### Post by Sef on 2008-09-08
Moved to server platforms.

---

### Post by HermanAB on 2008-09-08
If you are using the deprecated smbfs, then rather use cifs - it should be better with hanging mounts.

---

### Post by Dusenberg on 2008-09-08
> **bobbob1016 said:**
> I'm not sure I can help much, but knowing if you put the smb share in your /etc/fstab might help someone else.

Thanks bobbob1016.

Yes they are all in fstab with following params:

smbfs	auto,credentials=/root/.credentials,uid=1000,mask=000,user	0	0

---

### Post by Dusenberg on 2008-09-08
> **HermanAB said:**
> If you are using the deprecated smbfs, then rather use cifs - it should be better with hanging mounts.

Thanks. 

As this is my first use of samba I have just googled 'deprecated smbfs' and 'cifs'.  I'm running 2.6.22-15 kernel and 3.0.26a samba which I thinks means its not depracated. Everything other than this hanging mount lock-up is fine with samba so I don't want to move to cifs if I can help it. I am looking for a fix - I would have thought Samba error handling would pick up a timeout on a mounted fs and hence could do something sensible rather than just hang the whole system...... Any ideas would be much appreciated.

---

### Post by bab1 on 2008-09-08
There is no need to hard mount other hosts shares.  See the attached jpg.  This is from the host malibu.

The host newport (XP) shares are visable from and bookmarked on the host malibu.  They not listed malibu's fstab (hard mount).  The local host malibu has shares that do have hard mounts in fstab.  Looking at it in smbtree you can't tell the difference between hard and soft mounts.

Don't hard mount others shares to the local host.  Browse to them and then bookmark them.

---

### Post by Dusenberg on 2008-09-11
> **bab1 said:**
> There is no need to hard mount other hosts shares.  See the attached jpg.  This is from the host malibu.

The host newport (XP) shares are visable from and bookmarked on the host malibu.  They not listed malibu's fstab (hard mount).  The local host malibu has shares that do have hard mounts in fstab.  Looking at it in smbtree you can't tell the difference between hard and soft mounts.

Don't hard mount others shares to the local host.  Browse to them and then bookmark them.

Thanks bab1 - changed things as you suggest and very happy. If PC goes away now, my laptop keeps going.  Solved.  Much appreciated. :)

---

