---
title: "hardy boot slow"
date: 2008-04-24
forum: The Cafe
---

### Post by markp1989 on 2008-04-24
am i the only person who thinks that hardy boots alot slower then gusty did?

---

### Post by acelin on 2008-04-24
Must be. I know that the live cd for Hardy booted way faster than what my installed Gutsy did.

---

### Post by klange on 2008-04-24
I have to press a key at some point during the boot or init will stop about half way in, but other than that, Hardy's been faster for me than Gutsy since I first upgraded over a two months ago.

---

### Post by markp1989 on 2008-04-24
on gusty  boot chart was showing 19 or 20 sec, and hardy is showing 32 sec

---

### Post by phrostbyte on 2008-04-24
Check if you have unneeded services loaded at bootup. You may have disabled some when you run Gutsy.

---

### Post by Fixman on 2008-04-24
> **markp1989 said:**
> on gusty  boot chart was showing 19 or 20 sec, and hardy is showing 32 sec

Do you mean you have to ask a 32 sec countdown when booting? Thats because of GRUB, not of hardy. Just go to /boot/grub/menu.lst, and edit the "timeout" line.

---

