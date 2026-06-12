---
title: "Occasional System Freeze and Wayland"
date: 2021-04-25
forum: Virtualisation
---

### Post by dddman on 2021-04-25
It happens a couple times a week.  I am currently an occasional user of ubuntu and suspect this problem will grow worse the more I use it.  This is ubuntu 20.04 as guest system in virtualbox.

I first suspected virtualbox as the problem, but my googleFu has led me to wayland.  Even though xorg is old and being replaced by wayland it seems wayland is not yet ready for main stream use and better to stick with xorg.

Does this community agree with reverting back to xorg or should I look elsewhere for a fix?

Also
My googling led me to install gnome-system-log, but I see no errors logged by the latest freeze on the 23 of this month.

---

### Post by deadflowr on 2021-04-25
*Thread moved to **Virtualization***

---

### Post by WB0HYQ on 2022-03-29
Once moved here, this thread seemed to die. However, I have this problem myself (Ubuntu 20.04 and then 21.10). The system "appears" to be frozen, but although the mouse moves and (sometimes) there is an app popup description when I hover over the taskbar, clicking on it will NOT start the app. Any windows already open fail to respond to clicking anywhere, including the close "X". In fact, nothing on the keyboard responds at all.

Using the latest version of VirtualBox (6.1.32r-149290) and have all the add-ons. I've tried increasing the size of RAM available, as well as adjusting swapfile size and the "swappiness" setting from within Ubuntu. No matter what, I can count on Ubuntu freezing like I've described at least once a session. This requires me to send the "reset" signal from VirtualBox (which kills Ubuntu in a bad way) and rebooting. I know the OS is NOT frozen because there is still disk activity, yet the UI is completely unresponsive. How do I check to see if I'm using Wayland or xorg?

Any help out there?


Bill

---

### Post by DuckHook on 2022-03-29
Kindly do not necropost.

Prior postings go unanswered for many reasons, not least the possibility that no one knows the answer. There is no basis for the conclusion you jump to.

The computing landscape changes dramatically in a year. Bringing threads back from the dead does no one any favours and only promotes zombie solutions that have a high chance of misleading others or being outdated from the outset. 

Please repost your query under in its own thread and title.

*Thread Closed*

---

