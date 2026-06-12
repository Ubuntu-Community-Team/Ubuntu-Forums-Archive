---
title: "*What* is wrong with my Serval?"
date: 2007-02-18
forum: System76 Support
---

### Post by unphased on 2007-02-18
I've been using my serval on a desktop for the last few weeks, and tonight came into work to set it up for a presentation i'm supposed to give tomorrow morning.

i seem to be stuck in the situation of either being completely unable to boot the machine (hangs at fsck, or sometimes with "soft lockup CPU#0" error), or having wireless not work at all.

these two states seems to be toggled by whether or not i've toggled wireless with the FN-F2 key combination.

how can i get this thing to boot, and to connect to wireless?

---

### Post by Amt0571 on 2007-02-19
I think you can't... I'm having the same issue, and so far the only solution I've found to boot is to physically remove the wireless card.

It seems a lot of people are experiencing this issue but nobody has a solution. I'm going to switch to Debian Etch as soon as I have some free time, since it seems the problem is also ocurring in Dapper and Feisty.

---

### Post by crichell on 2007-02-19
Make sure the wireless On/Off switch on the front of the machine is set to On prior to booting.

---

### Post by unphased on 2007-02-19
* thank you! *  it works!

---

### Post by Amt0571 on 2007-02-20
> **crichell said:**
> Make sure the wireless On/Off switch on the front of the machine is set to On prior to booting.

And what I'm supposed to do? my card is an internal PCI one and does not have a switch...

---

### Post by crichell on 2007-02-20
> And what I'm supposed to do? my card is an internal PCI one and does not have a switch...

Which system do you have?

---

### Post by Amt0571 on 2007-02-20
A PIV 2.8ghz with 512mb ram, nVidia MX440-8x, SB Live, and a Conceptronic C54Ri PCI Wireless card (with rt61 chip).

The same issue occurs with Ubuntu and Kubuntu, although I'm "running" Kubuntu now.

---

### Post by crichell on 2007-02-20
amt0571 - i'm not sure what to do in your case.  I'm not familiar with the wireless card.  You may want to switch to the Trendnet PCI wireless card we use.  It doesn't have this issue.  Model# TEW-443PI

---

### Post by Amt0571 on 2007-02-21
Thanks for your suggestion. Unfortunately I'm not willing to pay again for another card when I already one which is perfectly supported in other distributions, but somehow, it's support is not only broken in Ubuntu, but the driver provided by ralink does not work with this distro either (causing the mentioned error).

I'm starting to consider other distros like Fedora or Debian where people told me the card works trouble free.

Unfortunately I have seen this problem occurring lately with different wireless cards and systems, and I'm just starting to think Ubuntu is not reliable enough to use as a main OS, at least not in my system.

By the way, sorry for posting this in the System76 forum without having a System76 computer. I was just searching for a solution to this problem and had no success in other forums.

Thanks for you help again.

---

