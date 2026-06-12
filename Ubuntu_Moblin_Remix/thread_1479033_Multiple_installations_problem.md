---
title: "Multiple installations problem"
date: 2010-05-10
forum: Ubuntu Moblin Remix
---

### Post by kilinkis on 2010-05-10
hi!
what happened?
i was on karmic remix and upgrade it to lucid remix
it installed but failed and then it wouldnt boot
it reached the UBUNTU screen but stucked there.

so i decided to fresh install lucid remix from my USB thumb

i installed it succesfully and now it works like charm =)

so, whats the problem?
the problem is that somehow i didnt choose the correct option when asked about partitions and now i have two UBUNTUs installed

the previous non working karmic remix version (installed on sda5)
and my new shiny lucid remix perfectly working version (installed on sda7)

so i want to delete the older version and if possible, merge the partitions.

i cant figure out how to solve it

netbook: ACER Aspire One netbook

P.S.: i have windows XP on other partition

any help?
thx a lot guys!

kilinkis

---

### Post by cariboo on 2010-05-10
You can use gparted to manipulate the partitons, it isn't install by default. Gparted is in the repositories. Before doing anything backup you data on both XP and Lucid.

---

### Post by kilinkis on 2010-05-11
hi and thx 4 your answer!
ive installed gparted, but when i try to delete the partition on sda5, it asks to unmount logical units with numbers greater than 6.
im running lucid on sda7, so how can i unmount a partition im using?

kilinkis

---

### Post by cariboo on 2010-05-12
Gpaerted won't work with partitions mount, You can boot from a usb device, and use gparted from there.

---

### Post by kilinkis on 2010-05-14
ill give that a try ASAP!
thx!

kilinkis

---

