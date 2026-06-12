---
title: "battery cmos broken (e2fsck)"
date: 2011-09-28
forum: Server Platforms
---

### Post by ilSaul on 2011-09-28
Hi,
i search in many place and find many forum talk about my problem but never one give me a solution.

I replace the cmos battery but this lose the power too, then i arrive to think that i don't want the control on the start of the system on the date and time on the inode.

i found a setting that i can put in the e2fsck.conf on this thread [http://forums.debian.net/viewtopic.php?f=10&t=45797](http://forums.debian.net/viewtopic.php?f=10&t=45797)

but in ubuntu don't exist that file, then i create it but nothing change.

Someone know how to disable inode time and date check?
someone know which script start the e2fsck on the start?

My is a server without keybord monitor then i can't every time connect all for solve the problem ad i have ntp installed for solve it.

thx
Saul

---

### Post by volkswagner on 2011-09-28
I don't understand.

Are you avoiding replacing a CMOS battery?

If the issue is you don't want to shutdown the server, I'm pretty sure you can safely replace the CMOS with the server running.

There are other settings in the BIOS which you may loose from a bad batt, such as keyboard warnings, boot priority, etc.

---

### Post by ilSaul on 2011-09-28
I replace one time battery after some month have the same problem.
then my motherboard maybe don't charge the battery, or less use of the server destroy the battery.
it's not use replace battery.

In any case my server is off every night and on every morning. when my computer is on i don't have any problem.


Someone know how to disable inode time and date check?
someone know which script start the e2fsck on the startup?

Some information:
SO: Ubuntu 10.04 Lucid (updated)
Location: Italy
MB and CPU: Via
HD: 80 GB
Use: Home Automation

---

### Post by trundlenut on 2011-09-28
Do you physically unplug the server overnight?

Surely if it is still plugged in then it should be receiving power from the mains and so not fall back on the bios battery.

If it is plugged in could you have a fault with the motherboard.

---

### Post by ilSaul on 2011-09-28
I unplug it ... and all my network system.

---

### Post by trundlenut on 2011-09-28
leave it plugged in.

---

### Post by volkswagner on 2011-09-28
Generally the CMOS battery does not get charged (they are not rechargeable cells).  I have seen rechargeable CMOS battery packs on Laptops only.

Either you got a defective battery or a hardware failure with the mobo.  I'd try another CMOS batt and verify the voltage prior to installing it.

---

### Post by ilSaul on 2011-09-29
thx for the suggestion, ... but i want to solve it with modify the boot.

in my think is normal for a server, remember that a server became old machine, have this kind of problem. Then if i have 10 y.o. server with this problem what i can do?

i have install ntp then after start the server i don't have any problem with the date.
Then, pls., someone that know what/which script start the e2fsck can tell me?
then i edit the script for solve my problem.

pls watch the link in my fist post is very close to my problem.

thx
Saul

---

