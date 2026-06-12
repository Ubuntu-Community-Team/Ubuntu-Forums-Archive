---
title: "No bootable medium found"
date: 2012-12-18
forum: Virtualisation
---

### Post by Bill Z on 2012-12-18
Complete virtualization newbie here.

I’m running an Acer Aspire One NetBook booting Ubuntu 12.4.1LTS  1.5Gib RAM  A 32 bit 1.6GHz Intel Atom CPU with a 7.5Gb SSD.  I added 128Gb SDHD chip for extra storage.  No DVD on this Netbook
I installed VirtualBox and saved several ISOs on the 128Gb SDHD chip.

All of this is a recently new build.  Everything is current.
Starting out easy, I wanted to build a 95, XP then 7 virtual OS to run one at a time.

However, when I try to build the virtual OS the progress bar doesn’t move and the system indicates 0% for an hour and a half.  Drilling down, I find an error on a terminal screen saying ‘FATAL: No bootable medium found!  System Halted.’

I tested this file by moving the SDHD chip to my desk top and burning a bootable DVD.  I do not know what VB is looking for.

I don’t want to get hung up on any particular ISO, I just want to build a few virtual machines.

What do I need to do to get this working?

Please help!!

---

### Post by Ms. Daisy on 2012-12-19
Your virtual machine needs a virtual hard drive. So you need to create one.

[ATTACH]228908[/ATTACH]

The image I uploaded shows the "Settings" menu.  Click on storage and if you don't have the icon with 3 plates (which is a virtual hard drive) then create one by clicking on the little "+" sign towards the bottom of the window. 

You should also put your .iso into the virtual machine's cd drive.  I'm doing that in the attached image- I highlighted the icon with one disc (the virtual cd drive). Again if you don't have one click on the +.  Then over on the right side you see the little disc with the arrow: click on that and you can point virtualbox to your iso, wherever it is on your computer. 

If you haven't seen the virtualbox manual, it's incredibly helpful.
[http://www.virtualbox.org/manual/](http://www.virtualbox.org/manual/)

---

