---
title: "Need opinion on possible failing HD / MB"
date: 2007-05-25
forum: The Cafe
---

### Post by ticopelp on 2007-05-25
I put this in the Community Cafe because it's a generalized hardware thing and not really related to Feisty as such. I would really appreciate any advice.

I have a machine with two HDs, a brand-new Western Digital 120 GB (less than a month old) and a six-month-old 250 GB, also Western Digital. I'm mainly running Ubuntu and haven't had to boot into Windows in about two weeks.

Over the past few days, the computer has started acting a bit funny. On reboots, it sometimes won't get past the CPU splash screen. It won't even get to the boot loader at all. On occasion, I will get "Grub error 21" and it will just sit there until I hit the reset button. At that point, 90% of the time, the machine boots and then runs perfectly. It's just started getting very erratic when I reboot it.

When I'm just using the machine, everything is fine. No performance issues, no slowdown. What does concern me is that maybe once every day or so, one of the HDs will make a single "click" sound that's out of the ordinary. It's not grinding or humming, just every once in a great while... "click." 

A friend of mine is convinced that the HD is failing, but I'm wondering if it might be the motherboard. I had a model of MB similar to this previously (I don't have a pre-built machine) and it exhibited the same behavior. The hard drive would occasionally "click," making me think it was going bad, but I replaced the MB and the problem went away and the drive was fine for years.

Just in case, I'm already beginning a full backup of all my data in case the HD really is failing -- but I wanted to get some expert opinions on this. Thanks for any feedback.

---

### Post by dca on 2007-05-25
Possible bad blocks on HDD.  From Windows run the 'chkdsk /f' utility...

---

### Post by insane_alien on 2007-05-25
first of all, run a backup of everything you can't afford/don't want to lose. then boot up from a live CD (preffereably a diagnostic orientated one such as [http://www.ghacks.net/2006/08/06/the-ultimate-diagnostic-boot-cd/](http://www.ghacks.net/2006/08/06/the-ultimate-diagnostic-boot-cd/)) then run every check that seems relevant.

if you get nothing then its probably a configuration error somewhere along the line.

---

### Post by FuturePilot on 2007-05-25
Sounds like you're hearing [the click of death]("http://en.wikipedia.org/wiki/Click_of_death") I'd start backing your stuff up now.

---

### Post by Lucifiel on 2007-05-25
Install smartmons.

then, run

sudo smartctl -d ata -a /dev/sda

where sda= your hdd

Also, clicking sound also could be:

floppy drive click of death and psu dying. If your psu is dying, it could play havoc with your motherboard and all your other devices.

---

### Post by ahaslam on 2007-05-25
From an overclockers point of view, it sounds like either your memory or psu. I'd run memtest86 for several passes and see what you get.

---

### Post by esaym on 2007-05-25
> **Lucifiel said:**
> Install smartmons.

then, run

sudo smartctl -d ata -a /dev/sda

where sda= your hdd

Also, clicking sound also could be:

floppy drive click of death and psu dying. If your psu is dying, it could play havoc with your motherboard and all your other devices.

yea smartmontools I think.

Check out the outputs.  Definitions are here:

[http://www.ariolic.com/activesmart/smart-attributes/](http://www.ariolic.com/activesmart/smart-attributes/)

---

### Post by ticopelp on 2007-05-25
Thanks for the replies. I ran some diagnostics and it looks, at this point, like it's the boot sector on the Windows HD that's bad. Everything on the MB seems to check out just fine. 

So I have to make my Linux drive bootable, which it isn't currently. Thanks for the help, the two posts about the diagnostic boot discs were tremendously handy.

---

### Post by mips on 2007-05-26
Go to the HD manufacturers website and download their diagnostic tools which checks the surface & SMART status. Should warn you of impending doom.

---

