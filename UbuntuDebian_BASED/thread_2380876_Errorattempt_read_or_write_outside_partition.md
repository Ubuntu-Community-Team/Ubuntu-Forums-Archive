---
title: "Error:attempt read or write outside partition"
date: 2017-12-23
forum: Ubuntu/Debian BASED
---

### Post by pkpkpk123456 on 2017-12-23
Please fix error
grub rescue>...

---

### Post by pkpkpk123456 on 2017-12-23
Error: attempt read or write outside of partition


Please fix error, I can't login into my pc
 I think I made partition error while dual boot with Linux os

---

### Post by coffeecat on 2017-12-23
Threads merged. Please do not create duplicate threads about the same problem. It causes confusion and dilutes community effort.

For the forum community to be able to help you, you will need to provide more information.

To start with:

What is the setup on your machine? That is, how many operating systems do you have installed on it?
Which Linux operating systems do you have - name of distro and release?
Do you have any non-Linux operating systems installed?
What exactly were you doing that has caused this problem?
What hardware are you using?

You also need to post information that reveals the current partition layout. Boot up a live session of Ubuntu, or one of the flavours, open Gparted and take a screenshot. Alternatively, in the live session, open a terminal and post the output of this command:

```
sudo parted -l
```

---

### Post by pkpkpk123456 on 2017-12-23
I'm using dell Inspiron 3000 series of amd 64bit processor,I had installed two operating systems
I had Kali Linux 2017.3 and windows10 are installed in it
When I'm switch on my laptop it shows entering to grub
grub rescue >
Which tells an error :attempt read or write outside of partition 


That it cannot entering into any os systems

---

### Post by coffeecat on 2017-12-24
Kali is not Ubuntu.

*Thread moved to **Ubuntu/Debian BASED**.*

Without the information requested about your partition layout, members here will not be able to help you.

---

