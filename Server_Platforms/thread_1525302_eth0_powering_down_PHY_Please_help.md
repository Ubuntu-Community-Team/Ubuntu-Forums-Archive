---
title: "eth0: powering down PHY Please help"
date: 2010-07-06
forum: Server Platforms
---

### Post by phatdawg on 2010-07-06
Hi, Im having major issues. Everything was fine until just recently. I tried to transfer some files to my server and noticed that it was really slow. then i noticed the link light on my router going out every few seconds. So i did some research and found this info in my logs.
 
Jul 6 14:04:53 Web-Server kernel: [ 462.923970] b44: eth0: powering down PHY
Jul 6 14:04:53 Web-Server kernel: [ 463.000097] b44: eth0: Link is down.
Jul 6 14:04:56 Web-Server kernel: [ 466.000163] b44: eth0: Link is up at 100 Mbps, full duplex.
Jul 6 14:04:56 Web-Server kernel: [ 466.000168] b44: eth0: Flow control is off for TX and off for RX.
Jul 6 14:04:58 Web-Server kernel: [ 467.925946] b44: eth0: powering down PHY
Jul 6 14:04:58 Web-Server kernel: [ 468.000095] b44: eth0: Link is down.
Jul 6 14:05:01 Web-Server kernel: [ 471.000163] b44: eth0: Link is up at 100 Mbps, full duplex.
Jul 6 14:05:01 Web-Server kernel: [ 471.000167] b44: eth0: Flow control is off for TX and off for RX.
Jul 6 14:05:03 Web-Server kernel: [ 472.927942] b44: eth0: powering down PHY
Jul 6 14:05:03 Web-Server kernel: [ 473.000113] b44: eth0: Link is down.
Jul 6 14:05:06 Web-Server kernel: [ 476.000164] b44: eth0: Link is up at 100 Mbps, full duplex.
Jul 6 14:05:06 Web-Server kernel: [ 476.000169] b44: eth0: Flow control is off for TX and off for RX
 
 
 
I tried very hard to find a solution. I guess this is a known issues with the broadcom b44 drivers, but i cant seem to find a fix. I think this may have started after a update, but im not sure. 
 
Im runnung Ubuntu 10.04 server
 
Please if anyone can help...

---

### Post by arrrghhh on 2010-07-06
Looks like your best option would be to downgrade to Hardy.  Lucid isn't exactly "production-quality" yet...  8.04 is still going to be supported on the server until 2013 I think...

[Here's](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279102) the official bug BTW.

I also saw this "Do other people notice the same interaction with Compiz that I reported? Notably, the problem stops when Compiz is turned off." - Uhm... You're not running Compiz on your server are you!?!  Or maybe on the other end...?

So perhaps you have an old kernel still in your GRUB, try the OLDEST kernel you can find in there.  I think it needs to be before .27, but I'm not sure.

---

### Post by phatdawg on 2010-07-06
> **arrrghhh said:**
> So perhaps you have an old kernel still in your GRUB, try the OLDEST kernel you can find in there. I think it needs to be before .27, but I'm not sure.
 
Im sure this is a real noob question but how do i do this?
 
Does anyone else know another work around?
 
Thanks for your quick reply

---

### Post by arrrghhh on 2010-07-06
Well you get a GRUB menu when you boot the server, yes?  There should be several selections, like Memtest and different kernels available for Ubuntu to boot from.  Just peruse that list, hopefully you'll have some old kernels in there.  If not, you're either in for a downgrade (NOT recommended) or a fresh install of 8.04.

---

### Post by y@w on 2010-07-07
According to the bug report, it looks like you could just disable Compiz to make it work again. Have you tried that yet?

---

### Post by phatdawg on 2010-07-07
yeah, compiz not installed.  but i think i found a solution.  I installed another network card...  problem doesnt seem to exist on the realtek card.  too bad there isnt a solution for the broadcom chipset.   Thanks for the help guys.

---

### Post by arrrghhh on 2010-07-07
I presented some solutions for your broadcom chipset, evidently they were ignored.  Pity, I would've been interested if there was a solution - obviously a different type of card without that chip would fix it.  Glad to hear it's working for you, hope no one else runs into this issue with this card...

IF anyone does, try my suggestion, post back with results!

---

### Post by phatdawg on 2010-07-07
> **arrrghhh said:**
> I presented some solutions for your broadcom chipset, evidently they were ignored. Pity, I would've been interested if there was a solution - obviously a different type of card without that chip would fix it. Glad to hear it's working for you, hope no one else runs into this issue with this card...
 
IF anyone does, try my suggestion, post back with results!
 
 
Sorry, your solutions were not ignored. just did not work. As this was a fairly new load, i did not have many older kernel to try, but i did try the ones that were there with no luck, and i verified that compiz is not installed.  I really did not want to re-load to 8.04 as everything else is working just fine, and from what i have been reading the problem has existed since 8.04 anyway.  I have been very frustrated with this issue and was trying to find the best way of getting my server to run better. But thanks for your time, if someone does find a solution to this problem i hope they will post, and hopefully they will release a kernel update that will fix this problem.
 
Thanks again

---

### Post by arrrghhh on 2010-07-07
Based on my reading, the issue cropped up around the Jaunty upgrade, maybe as early as Hardy... I'd just be curious to see if it makes any difference.

Glad you fixed it with a new NIC.  Hopefully if someone else runs into the problem they can drag this thread up and we can try to troubleshoot again.  Seems like it also may be a regression in the kernel, and hopefully with some kernel updates it will be fixed.

---

### Post by phatdawg on 2010-07-07
I hope so too, its been very frustrating. and have really found nothing after hours of searching that has even given me a clue on how to get this fixed... oh well

---

### Post by LupintheIst on 2010-10-21
Hello, 
   I seem to be having the same problem as phatdawg. I have been running Ubuntu 10.04 (not server) on my Dell Inspiron 9400 laptop. Every time there is some time of network load I get the following in dmesg:

[  632.998665] b44: eth0: powering down PHY
[  633.001131] b44: eth0: Link is down.
[  638.000288] b44: eth0: Link is up at 100 Mbps, full duplex.
[  638.000295] b44: eth0: Flow control is off for TX and off for RX.
[  947.548515] b44: eth0: powering down PHY
[  948.000145] b44: eth0: Link is down.
[  953.000230] b44: eth0: Link is up at 100 Mbps, full duplex.
[  953.000237] b44: eth0: Flow control is off for TX and off for RX.
[ 1018.577485] b44: eth0: powering down PHY
[ 1019.000170] b44: eth0: Link is down.
[ 1024.000205] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1024.000209] b44: eth0: Flow control is off for TX and off for RX.
[ 1074.280805] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 1087.360009] CE: hpet increasing min_delta_ns to 33750 nsec
[ 1087.360009] CE: hpet increasing min_delta_ns to 50624 nsec
[ 1094.767713] CE: hpet increasing min_delta_ns to 75936 nsec
[ 1134.478071] CE: hpet increasing min_delta_ns to 113904 nsec
[ 1134.478583] CE: hpet increasing min_delta_ns to 170856 nsec
[ 1153.574279] CE: hpet increasing min_delta_ns to 256284 nsec
[ 1153.575254] CE: hpet increasing min_delta_ns to 384426 nsec
[ 1154.669894] b44: eth0: powering down PHY
[ 1155.000132] b44: eth0: Link is down.
[ 1160.001506] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1160.001513] b44: eth0: Flow control is off for TX and off for RX.
[ 1236.578133] b44: eth0: powering down PHY
[ 1237.000105] b44: eth0: Link is down.
[ 1242.000232] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1242.000240] b44: eth0: Flow control is off for TX and off for RX.

Sometimes for a while it doesn't happen, other times it happens every single time I try to load a page in firefox. I tried most of the suggestions in the official bug thread. I havn't tried a downgrade of anykind though. I would be willing to try some troubleshooting if nothing else to try and shed more light on the problem. It is very annoying... 
     Is the problem really related to the broadcom nic driver? If so is there another driver that works?

---

