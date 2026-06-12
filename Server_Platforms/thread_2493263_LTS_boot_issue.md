---
title: "LTS boot issue"
date: 2023-12-08
forum: Server Platforms
---

### Post by fenlasonb on 2023-12-08
Hey everyone. I had to move and my server was powered off for awhile. When I turned it on I had a warning that my cmos battery died. 


When trying to boot into ubuntu I am booting into emergency mode. Ive tried running fsck from a live cd on sda2 but this does not seem to be the issue. I couldn't get logs off the box so i tried taking picture of the fstab and the system journal 


Hopefully I can recover this. I have a  mdadm  raid array and worried im going to lose that data. trying to get access so i can back it up on my synology

 
[https://imgur.com/a/lVbBN4h](https://imgur.com/a/lVbBN4h)


thanks in advanced

---

### Post by guiverc on 2023-12-08
As already stated; you've provided few specifics.

Question also asked at [https://askubuntu.com/questions/1495434/ubuntu-lts-boot-issue](https://askubuntu.com/questions/1495434/ubuntu-lts-boot-issue)

---

### Post by MAFoElffen on 2023-12-08
I posted there a few minutes ago. If it is long and drawn out, it might be better to deal with that here.

Summary of what I said there. Replace the CMOS Battery. Reset the BIOS settings I noted there. Provide more information after that (noted there).

Decide where you want to deal with providing information and getting instructions. Should be just one place, so things are not duplicated between the two.

---

### Post by guiverc on 2023-12-09
I agree with what @MAFoElfenn has already stated.

You've provided few specifics as I see it, thus I'd be only guessing.

Yesterday was very windy in my local area, and power was *flaky* as a result, and kept going out at my place (*usually only seconds, but sometimes longer*). A server in my garage doesn't have good UPS batteries, and as a result died; I left it off until earlier today.

The CMOS message I saw earlier today related to a battery on a RAID controller (*within the machine*). My server  has numerous batteries in it (*not just on the motherboard itself*), but as I didn't have any glasses on, I went into another room to get them (*to read & record the messages, I'd failed to get it when I saw it last reboot maybe 5 months prior*), but it was gone & the system was booting normally before I returned with my spectacles. The message matters in my view, so you treat it appropriately & don't potentially make the issue worse.

In my case; I gather my RAID card was able to read the details of my three drive arrays (*from drives themselves*) & thus booted normally*. *I actually expect the same if it's a motherboard CMOS battery too, **though** every device is different in regards what keys/options it requires you to accept/decline (*my RAID controller can require me to confirm if it can't detect everything itself on occasion*).

The more details you provide (*software stack is a huge clue, but you've not yet stated what Ubuntu system; only LTS*) the better advice we can offer.

I'd go with what MAFoelfen suggested; you'll note too on askubuntu that advice wasn't from just one user too.

---

### Post by MAFoElffen on 2023-12-09
I would do those first, before even trying to boot from an Installer LiveUSB... Which would be the next logical diagnostic step after those steps.

*have noticed that you initially made posts at AskUbuntu, then hear, as if it was important to you and answers were not coming back fast enough... Then after that nothing... Many people answered you, but you never replied back from anywhere.*

Tip: If you can't keep up with answering in a timely manner, then it may be assumed that you may not be an active participant in resolving your own problems, and you may get overlooked for others that are. That is no dis on you, just how things happen.

---

