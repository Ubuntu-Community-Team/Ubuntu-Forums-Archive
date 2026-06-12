---
title: "VirtualBox - Running XP in Ubuntu"
date: 2008-08-26
forum: Virtualisation
---

### Post by ljunggr1 on 2008-08-26
Hi,

I'm running Win XP on VirtualBox in Ubuntu (Hardy Heron), and I'm having problems with some installations in XP. The installation fails because of insufficient diskspace, yet there are over 6 GB available. This is a fixed-size image, not dynamically expanding, so I don't quite understand what the problem might be..

..And I really need the Nokia software updater! :)

Anyone?

---

### Post by ljunggr1 on 2008-08-27
Btw, no hassle with several other installations

---

### Post by kellemes on 2008-08-27
> **ljunggr1 said:**
> Hi,

I'm running Win XP on VirtualBox in Ubuntu (Hardy Heron), and I'm having problems with some installations in XP. The installation fails because of insufficient diskspace, yet there are over 6 GB available. This is a fixed-size image, not dynamically expanding, so I don't quite understand what the problem might be..

..And I really need the Nokia software updater! :)

Anyone?

Strange..
Maybe you should try defragmenting the (virtual) disk from Windows?
By the way.. you say 6 Gb available, does this mean there is 6 Gb free?

---

### Post by ljunggr1 on 2008-08-27
> **kellemes said:**
> Strange..
you say 6 Gb available, does this mean there is 6 Gb free?

6 GB free.. I'll try defragmenting. Thx :)

---

### Post by ljunggr1 on 2008-08-27
Well, it turned out to be a problem with the base memory. I found out that Windows didn't show the correct amount in System, so I tried to adjust it in the VirtalBox settings. Now it works! :) And also, Win shows the correct amount.

---

### Post by kellemes on 2008-08-27
> **ljunggr1 said:**
> Well, it turned out to be a problem with the base memory. I found out that Windows didn't show the correct amount in System, so I tried to adjust it in the VirtalBox settings. Now it works! :) And also, Win shows the correct amount.

Cool. :popcorn:

---

