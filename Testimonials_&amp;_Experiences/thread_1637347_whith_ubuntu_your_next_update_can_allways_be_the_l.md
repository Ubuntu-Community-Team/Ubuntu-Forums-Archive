---
title: "whith ubuntu your next update can allways be the last one"
date: 2010-12-04
forum: Testimonials &amp; Experiences
---

### Post by petex on 2010-12-04
when everything works. This is probably one of the most anoying things about ubuntu. Just updateted my system and last time SD card reader stoped working this time it lost my USB mouse

I use it beacuse i really belive in it but there's allways so much fixing that I start to doubt if it's worth the effort

---

### Post by NightwishFan on 2010-12-04
I think only a kernel update can cause that big of change. Though I have never had something "give up on me" just with normal updates. I try not to doubt it happens though I have no idea how such bugs come about so often. Updates are tested quite heavily. Are you running PPAs or unsupported/pre-released updates?

Also a good habit is to update every few weeks, and only update more often than that if you know you need a fix. (Such as msn will not connect fixed in update)

Was it a kernel update that did it? Try booting to the older kernel. If you do not see a grub menu, hold shift after the bios screen and you should see a list of kernels.

---

### Post by petex on 2010-12-04
PPA
the issue with SD card was on updating to ubuntu 10.10
but USB was just an update

---

### Post by NightwishFan on 2010-12-04
I see. Yes, generally if your machine running right for a long time is at all important to you, the best option is to run the LTS (Currently 10.04). As for upgrades, they generally go favourably for me, though it is always best to test a new release before you commit to the upgrade. (For example, 10.10 has pulseaudio issues on my laptop, which I can fix however I manage many of this same machine for others. If I blindly updated them I would have to fix it on all of them. ;)

Generally, if it "can work" it can be fixed. Why not post a thread about your issues? Insert an SD card and in the terminal type:
```
dmesg
```

Post the output of dmesg in the new thread, this will show your system activity to the helpful geeks that will fix the problem.

Do not give up on us, though if your work flow is interrupted there is no shame in using Windows. We will get there, trust me! :)

---

### Post by petex on 2010-12-04
thanks for reply
generally i don't even try to fix it anymore if it's not big issue. 

It's more of generall discussion and being frustarted a bit after another bug :( 

I just don't waste time on fixing things which are not cruciall anymore and wait till it's fixed by Ubuntu developers. My point is if you use ubuntu you often have to sacrifice your time for fixing things so it's still far from OS for everyone it's trying to be. I enjoy configuring systems etc. but most people will be much better of with Windows or OSX

---

### Post by NightwishFan on 2010-12-04
At the moment, most people might indeed be better off. Open source is a bit fragmented with many things being developed with different aims and goals, which means Canonical can not fix everything. Though our time will come, as open source is seeing real consumer adoption (not just behind the scenes). It is run on phones with android and on professional desktops in France. With more demand comes more support as well! :)

I will not run Windows, so at the moment I ensure any hardware I will buy is compatible. I understand not everyone has the ability or option to do so though.

I hope your luck changes my friend. :)

---

### Post by smo0th on 2010-12-04
whenever you find a bug you should follow the steps described at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

by doing this you help the community letting know the developers about the bug, sometimes it is already reported and the solution is posted there, so you should check out! =)

---

### Post by petex on 2010-12-04
I've been using ubuntu for ca. 3 years now so I'm gonna still do it it's just that somtimes it can really **** you off:) 
as for Android I really like it and try to write my apps. Although I need to get a better phone as my current is terrible (samsung Spica - super sluggish and overaly poor UX) but i belive on good phone UX should be very cool

---

### Post by smo0th on 2010-12-04
by sticking with LTS you dont get ****ed up that often =] but yeah, I got your point, even so, I find it better than any other out there =)

---

### Post by Spice Weasel on 2010-12-04
Stick with the LTS but use a separate /home partition and do a fresh install (besides /home, obviously) every two years.

---

### Post by Lancro on 2010-12-04
Im in the other side, ubuntu detects and configures my hardware better than windows, since windows vista logitech hasnt developed drivers for my keyboard, but in ubuntu all the multimedia keys works!!, and in 10.04 my microphone didnt work, I upgraded and it started to work, when natty comes out I will do the same as in maverick, test the hardware in a usb stick, and upgrade if it works.

---

### Post by Shining Arcanine on 2010-12-04
> **petex said:**
> when everything works. This is probably one of the most anoying things about ubuntu. Just updateted my system and last time SD card reader stoped working this time it lost my USB mouse

I use it beacuse i really belive in it but there's allways so much fixing that I start to doubt if it's worth the effort
Have you considered switching to RHEL 6? RedHat is supposed to have the best Linux support you can get sort of becoming an expert yourself.

---

### Post by madjr on 2010-12-04
am waiting for **btrfs** to become default and integrated into grub. Then i can do a system rollback before silly updates break my stuff.

---

### Post by wilee-nilee on 2010-12-04
Never have had any problems as described by the OP and this is on at least 20 different open source platforms.

---

### Post by holiday on 2010-12-04
> **Spice Weasel said:**
> Stick with the LTS but use a separate /home partition and do a fresh install (besides /home, obviously) every two years.

Second that! And don't upgrade to the next LTS until the adventurers are taking on the *.10.

And never upgrade until you feel like dealing with technical puzzles.

---

### Post by MooPi on 2010-12-04
> **wilee-nilee said:**
> Never have had any problems as described by the OP and this is on at least 20 different open source platforms.
Likewise, but I'm a devout Openbox platform user and it changes so little over time with less integration and complexity. I feel the pain of those with update problems though even though it leaves me confused as to how sometimes. I heard a very good statement years ago at a lug meeting. "Linux is very stable but if you like bleeding edge or change constantly you'll find a way to break it".

---

### Post by handy on 2010-12-04
I had problems back in the day. Both Breazy & Dapper worked fine on my No.2 box, then Edgy came along & there goes my PS2 keyboard, as in incredible lag when typing, & my mouse USB mouse would intermittently fail, to the point that a warm boot was required to fix it.

In the end I found that for some reason? Edgy & some but not all of the other distros I tried didn't like the onboard USB chip on my Gigabyte motherboard. These regressions can really irritate a user & cost a great deal of time to solve, if you can solve them.

I disabled the on board USB via the BIOS & installed a PCI USB card, which fixed the problem for me.

That was also about the time that I dumped Ubuntu. Sabayon worked perfectly on that machine with the onboard USB enabled & handled my graphics card from hell (that's another story), until after a couple of version upgrades Sabayon no longer liked my hardware - black screen of death early in the boot of the Sabayon LiveDVD. 

So then I took that machine to Arch (where No.1 box had happily been for sometime), after which there were no more problems.

Often when people are lucky enough to have never had a problem with hardware compatibility in the Linux world, they think that whoever is having the trouble is just a klutz with Linux & that their system is messed up by their own hand. Admittedly this can sometimes be true, but overall there are many genuine cases of hardware incompatibility, & unfortunately, the dreaded regression.

Due to the existence of just too many combinations of chips & versions of chips, from so many different manufacturers, I find it very hard to imagine that under these circumstances there will ever truly be a way to thoroughly test FOSS systems like the Linux distros against all this hardware. 

So if you use Linux, you are a tester whether you like it or not.

---

### Post by wilee-nilee on 2010-12-04
> **handy said:**
> I had problems back in the day. Both Breazy & Dapper worked fine on my No.2 box, then Edgy came along & there goes my PS2 keyboard, as in incredible lag when typing, & my mouse USB mouse would intermittently fail, to the point that a warm boot was required to fix it.

In the end I found that for some reason? Edgy & some but not all of the other distros I tried didn't like the onboard USB chip on my Gigabyte motherboard. These regressions can really irritate a user & cost a great deal of time to solve, if you can solve them.

I disabled the on board USB via the BIOS & installed a PCI USB card, which fixed the problem for me.

That was also about the time that I dumped Ubuntu. Sabayon worked perfectly on that machine with the onboard USB enabled & handled my graphics card from hell (that's another story), until after a couple of version upgrades Sabayon no longer liked my hardware - black screen of death early in the boot of the Sabayon LiveDVD. 

So then I took that machine to Arch (where No.1 box had happily been for sometime), after which there were no more problems.

Often when people are lucky enough to have never had a problem with hardware compatibility in the Linux world, they think that whoever is having the trouble is just a klutz with Linux & that their system is messed up by their own hand. Admittedly this can sometimes be true, but overall there are many genuine cases of hardware incompatibility, & unfortunately, the dreaded regression.

Due to the existence of just too many combinations of chips & versions of chips, from so many different manufacturers, I find it very hard to imagine that under these circumstances there will ever truly be a way to thoroughly test FOSS systems like the Linux distros against all this hardware. 

So if you use Linux, you are a tester whether you like it or not.

It is not the klutz clause bro it is make sure you have compatible hard ware and have everything backed up.

This ain't rocket science it is a box of transistors with no logic, the user needs to exercise the logic.

It isn't luck on my part but using a system of basically a Socratic approach, you eliminate the variables that work against the process.

---

### Post by handy on 2010-12-04
> **wilee-nilee said:**
> 
It is not the klutz clause bro it is make sure you have compatible hard ware and have everything backed up. 

That doesn't work for people who are new to Linux, they are involved in a learning curve so steep that it loops the loop. So many get a disk on a magazine, read the article associated with it, install & take it from there where they will. If good fortune is smiling upon them they won't have any hardware incompatibilities.

Be you inexperienced or a Linux guru, you still can't see a regression coming before it hits you. Unless you are watching a BB before you upgrade & you happen to have very common hardware (which stands a better chance of having been tested). It is great insurance if someone on the dev' team is using the same hardware as you are.

> **wilee-nilee said:**
> 
This ain't rocket science it is a box of transistors with no logic, the user needs to exercise the logic. 

Cars since 1986 have had more computer components in them than Apollo ll, & the landing module had in them when they landed on the moon. :)
 
Chips contain logic, & it is harder than rocket science if you happen to be developing parts of a system that interface with unknown hardware. There is a multitudinous variety of chips & versions of those chips & firmware that you are attempting to successfully interface with, mostly site unseen. Not my idea of fun.

Which is one of the benefits the hardware producers like Apple have, as they design both their hardware products & the systems that run on them.

> **wilee-nilee said:**
> 
It isn't luck on my part but using a system of basically a Socratic approach, you eliminate the variables that work against the process.

Good work; find a way to pass that on effectively to a Windows user that's going to have a go with the magazine disk; & to the dev teams with the insurmountable challenge of dealing with the incalculable number of assembly variations in low level hardware components that have been put together over the last >15 years.

I have tried to install Linux on a variety of old Pentium, PII & PIII boxes & they were incompatible, I attempted with more than one distro as well. Though I do have a PIII & an Athlon 700, which are both happy to be Linux firewalls. 

You just don't know until you try the hardware with the system. Or in the case of upgrades, until you have tried the new version with your hardware.

So like it or lump it, we are all testers.

---

### Post by wilee-nilee on 2010-12-04
> **handy said:**
> That doesn't work for people who are new to Linux, they are involved in a learning curve so steep that it loops the loop. So many get a disk on a magazine, read the article associated with it, install & take it from there where they will. If good fortune is smiling upon them they won't have any hardware incompatibilities.

Be you inexperienced or a Linux guru, you still can't see a regression coming before it hits you. Unless you are watching a BB before you upgrade & you happen to have very common hardware (which stands a better chance of having been tested). It is great insurance if someone on the dev' team is using the same hardware as you are.



Cars since 1986 have had more computer components in them than Apollo ll, & the landing module had in them when they landed on the moon. :)
 
Chips contain logic, & it is harder than rocket science, if you happen to be developing parts of a system that interface with hardware. As you can not know about all of the varieties of chips & firmware that the system you are working on can interface with. 

Which is one of the benefits the hardware producers like Apple have, as they design both their hardware products & the systems that run on them.


[B]
Good work; find a way to pass that on effectively[/B] to a Windows user that's going to have a go with the magazine disk; & to the dev teams with the insurmountable challenge of dealing with the incalculable number of assembly variations in low level hardware components that have been put together over the last >15 years.

I have tried to install Linux on a variety of old Pentium, PII & PIII boxes & they were incompatible, I attempted with more than one distro as well. Though I do have a PIII & an Athlon 700, which are both happy to be Linux firewalls. 

You just don't know until you try the hardware with the system. Or in the case of upgrades, until you have tried the new version with your hardware.

So like it or lump it, we are all testers.

If you look through my posts all I do, mostly is support work helping the Windows users, and others, and I work very hard at it.

I rarely post in other then the support part of the forum.

---

### Post by handy on 2010-12-04
> **wilee-nilee said:**
> If you look through my posts all I do, mostly is support work helping the Windows users, and others, and I work very hard at it.

I rarely post in other then the support part of the forum.

Oh good, the problem is fixed then. :p

---

### Post by wilee-nilee on 2010-12-04
Yep easy fix just use the forum tools take it easy.

---

### Post by Vorian on 2010-12-05
"with ubuntu your next update can always be the last one"  (fixed your spelling mistakes)

Did you ever consider the next time you get in a car, it could be your last?

---

### Post by petex on 2010-12-05
tht's my dmsg for SD card

```

[19612.837022] end_request: I/O error, dev mmcblk0, sector 130
[19612.839496] mmcblk0: error -84 transferring data, sector 131, nr 5, card status 0x900
[19612.839669] end_request: I/O error, dev mmcblk0, sector 131
[19612.842167] mmcblk0: error -84 transferring data, sector 132, nr 4, card status 0x900
[19612.842351] end_request: I/O error, dev mmcblk0, sector 132
[19612.844846] mmcblk0: error -84 transferring data, sector 133, nr 3, card status 0x900
[19612.845029] end_request: I/O error, dev mmcblk0, sector 133
[19612.847527] mmcblk0: error -84 transferring data, sector 134, nr 2, card status 0x900
[19612.847710] end_request: I/O error, dev mmcblk0, sector 134
[19612.850257] mmcblk0: error -84 transferring data, sector 135, nr 1, card status 0x900
[19612.850442] end_request: I/O error, dev mmcblk0, sector 135
[19612.855039] mmcblk0: retrying using single block read
[19612.857365] mmcblk0: error -84 transferring data, sector 16, nr 8, card status 0x900
[19612.857551] end_request: I/O error, dev mmcblk0, sector 16
[19612.860103] mmcblk0: error -84 transferring data, sector 17, nr 7, card status 0x900
[19612.860283] end_request: I/O error, dev mmcblk0, sector 17
[19612.862839] mmcblk0: error -84 transferring data, sector 18, nr 6, card status 0x900
[19612.863024] end_request: I/O error, dev mmcblk0, sector 18
[19612.865507] mmcblk0: error -84 transferring data, sector 19, nr 5, card status 0x900
[19612.865693] end_request: I/O error, dev mmcblk0, sector 19
[19612.868184] mmcblk0: error -84 transferring data, sector 20, nr 4, card status 0x900
[19612.868364] end_request: I/O error, dev mmcblk0, sector 20
[19612.870922] mmcblk0: error -84 transferring data, sector 21, nr 3, card status 0x900
[19612.871101] end_request: I/O error, dev mmcblk0, sector 21
[19612.873604] mmcblk0: error -84 transferring data, sector 22, nr 2, card status 0x900
[19612.873789] end_request: I/O error, dev mmcblk0, sector 22
[19612.876270] mmcblk0: error -84 transferring data, sector 23, nr 1, card status 0x900
[19612.876455] end_request: I/O error, dev mmcblk0, sector 23
[19612.881148] mmcblk0: retrying using single block read
[19612.883472] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19612.883651] end_request: I/O error, dev mmcblk0, sector 0
[19612.886131] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19612.886317] end_request: I/O error, dev mmcblk0, sector 1
[19612.888798] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19612.888976] end_request: I/O error, dev mmcblk0, sector 2
[19612.891525] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19612.891715] end_request: I/O error, dev mmcblk0, sector 3
[19612.894205] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19612.894391] end_request: I/O error, dev mmcblk0, sector 4
[19612.896873] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19612.897058] end_request: I/O error, dev mmcblk0, sector 5
[19612.899557] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19612.899748] end_request: I/O error, dev mmcblk0, sector 6
[19612.902238] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19612.902423] end_request: I/O error, dev mmcblk0, sector 7
[19612.907028] mmcblk0: retrying using single block read
[19612.909345] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19612.909537] end_request: I/O error, dev mmcblk0, sector 0
[19612.912069] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19612.912260] end_request: I/O error, dev mmcblk0, sector 1
[19612.914752] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19612.914945] end_request: I/O error, dev mmcblk0, sector 2
[19612.917433] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19612.917619] end_request: I/O error, dev mmcblk0, sector 3
[19612.920172] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19612.920370] end_request: I/O error, dev mmcblk0, sector 4
[19612.922863] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19612.923055] end_request: I/O error, dev mmcblk0, sector 5
[19612.925540] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19612.925719] end_request: I/O error, dev mmcblk0, sector 6
[19612.928280] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19612.928466] end_request: I/O error, dev mmcblk0, sector 7
[19612.933103] mmcblk0: retrying using single block read
[19612.935426] mmcblk0: error -84 transferring data, sector 8, nr 8, card status 0x900
[19612.935608] end_request: I/O error, dev mmcblk0, sector 8
[19612.938108] mmcblk0: error -84 transferring data, sector 9, nr 7, card status 0x900
[19612.938294] end_request: I/O error, dev mmcblk0, sector 9
[19612.940831] mmcblk0: error -84 transferring data, sector 10, nr 6, card status 0x900
[19612.941011] end_request: I/O error, dev mmcblk0, sector 10
[19612.943508] mmcblk0: error -84 transferring data, sector 11, nr 5, card status 0x900
[19612.943687] end_request: I/O error, dev mmcblk0, sector 11
[19612.946180] mmcblk0: error -84 transferring data, sector 12, nr 4, card status 0x900
[19612.946358] end_request: I/O error, dev mmcblk0, sector 12
[19612.948876] mmcblk0: error -84 transferring data, sector 13, nr 3, card status 0x900
[19612.949062] end_request: I/O error, dev mmcblk0, sector 13
[19612.951629] mmcblk0: error -84 transferring data, sector 14, nr 2, card status 0x900
[19612.951813] end_request: I/O error, dev mmcblk0, sector 14
[19612.954309] mmcblk0: error -84 transferring data, sector 15, nr 1, card status 0x900
[19612.954502] end_request: I/O error, dev mmcblk0, sector 15
[19612.959095] mmcblk0: retrying using single block read
[19612.961487] mmcblk0: error -84 transferring data, sector 16, nr 8, card status 0x900
[19612.961671] end_request: I/O error, dev mmcblk0, sector 16
[19612.964158] mmcblk0: error -84 transferring data, sector 17, nr 7, card status 0x900
[19612.964338] end_request: I/O error, dev mmcblk0, sector 17
[19612.966827] mmcblk0: error -84 transferring data, sector 18, nr 6, card status 0x900
[19612.967006] end_request: I/O error, dev mmcblk0, sector 18
[19612.969502] mmcblk0: error -84 transferring data, sector 19, nr 5, card status 0x900
[19612.969690] end_request: I/O error, dev mmcblk0, sector 19
[19612.972205] mmcblk0: error -84 transferring data, sector 20, nr 4, card status 0x900
[19612.972391] end_request: I/O error, dev mmcblk0, sector 20
[19612.974868] mmcblk0: error -84 transferring data, sector 21, nr 3, card status 0x900
[19612.975047] end_request: I/O error, dev mmcblk0, sector 21
[19612.977526] mmcblk0: error -84 transferring data, sector 22, nr 2, card status 0x900
[19612.977709] end_request: I/O error, dev mmcblk0, sector 22
[19612.980251] mmcblk0: error -84 transferring data, sector 23, nr 1, card status 0x900
[19612.980430] end_request: I/O error, dev mmcblk0, sector 23
[19612.985043] mmcblk0: retrying using single block read
[19612.987360] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19612.987546] end_request: I/O error, dev mmcblk0, sector 0
[19612.990082] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19612.994174] end_request: I/O error, dev mmcblk0, sector 1
[19612.996679] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19612.996859] end_request: I/O error, dev mmcblk0, sector 2
[19612.999347] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19612.999544] end_request: I/O error, dev mmcblk0, sector 3
[19613.001080] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19613.001273] end_request: I/O error, dev mmcblk0, sector 4
[19613.003772] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19613.003974] end_request: I/O error, dev mmcblk0, sector 5
[19613.006477] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19613.006663] end_request: I/O error, dev mmcblk0, sector 6
[19613.009157] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19613.009353] end_request: I/O error, dev mmcblk0, sector 7
[19613.013984] mmcblk0: retrying using single block read
[19613.016352] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19613.016544] end_request: I/O error, dev mmcblk0, sector 0
[19613.019035] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19613.019230] end_request: I/O error, dev mmcblk0, sector 1
[19613.021767] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19613.021958] end_request: I/O error, dev mmcblk0, sector 2
[19613.024456] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19613.024634] end_request: I/O error, dev mmcblk0, sector 3
[19613.027121] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19613.027307] end_request: I/O error, dev mmcblk0, sector 4
[19613.029807] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19613.029998] end_request: I/O error, dev mmcblk0, sector 5
[19613.032502] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19613.032701] end_request: I/O error, dev mmcblk0, sector 6
[19613.035240] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19613.035425] end_request: I/O error, dev mmcblk0, sector 7
[19613.040064] mmcblk0: retrying using single block read
[19613.042417] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19613.042603] end_request: I/O error, dev mmcblk0, sector 0
[19613.045136] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19613.045320] end_request: I/O error, dev mmcblk0, sector 1
[19613.047814] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19613.048007] end_request: I/O error, dev mmcblk0, sector 2
[19613.050540] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19613.050732] end_request: I/O error, dev mmcblk0, sector 3
[19613.053227] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19613.053421] end_request: I/O error, dev mmcblk0, sector 4
[19613.055918] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19613.056109] end_request: I/O error, dev mmcblk0, sector 5
[19613.058601] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19613.058779] end_request: I/O error, dev mmcblk0, sector 6
[19613.061311] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19613.061512] end_request: I/O error, dev mmcblk0, sector 7
[19613.066135] mmcblk0: retrying using single block read
[19613.068452] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19613.068632] end_request: I/O error, dev mmcblk0, sector 0
[19613.071175] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19613.071366] end_request: I/O error, dev mmcblk0, sector 1
[19613.073878] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19613.074065] end_request: I/O error, dev mmcblk0, sector 2
[19613.076551] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19613.076728] end_request: I/O error, dev mmcblk0, sector 3
[19613.079218] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19613.079414] end_request: I/O error, dev mmcblk0, sector 4
[19613.081971] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19613.082164] end_request: I/O error, dev mmcblk0, sector 5
[19613.084682] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19613.084868] end_request: I/O error, dev mmcblk0, sector 6
[19613.087352] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19613.087525] end_request: I/O error, dev mmcblk0, sector 7
[19613.092158] mmcblk0: retrying using single block read
[19613.094498] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19613.094687] end_request: I/O error, dev mmcblk0, sector 0
[19613.097169] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19613.097361] end_request: I/O error, dev mmcblk0, sector 1
[19613.099841] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19613.100032] end_request: I/O error, dev mmcblk0, sector 2
[19613.102544] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19613.102726] end_request: I/O error, dev mmcblk0, sector 3
[19613.105220] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19613.105399] end_request: I/O error, dev mmcblk0, sector 4
[19613.107887] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19613.108072] end_request: I/O error, dev mmcblk0, sector 5
[19613.110618] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19613.110814] end_request: I/O error, dev mmcblk0, sector 6
[19613.113332] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19613.113529] end_request: I/O error, dev mmcblk0, sector 7
[19613.118520] mmcblk0: retrying using single block read
[19613.120854] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19613.121053] end_request: I/O error, dev mmcblk0, sector 0
[19613.123586] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19613.123778] end_request: I/O error, dev mmcblk0, sector 1
[19613.126262] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19613.126448] end_request: I/O error, dev mmcblk0, sector 2
[19613.128929] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19613.129115] end_request: I/O error, dev mmcblk0, sector 3
[19613.131656] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19613.131853] end_request: I/O error, dev mmcblk0, sector 4
[19613.134356] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19613.134551] end_request: I/O error, dev mmcblk0, sector 5
[19613.137039] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19613.137224] end_request: I/O error, dev mmcblk0, sector 6
[19613.139712] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19613.139897] end_request: I/O error, dev mmcblk0, sector 7
[19613.144503] mmcblk0: retrying using single block read
[19613.146822] mmcblk0: error -84 transferring data, sector 8, nr 8, card status 0x900
[19613.147003] end_request: I/O error, dev mmcblk0, sector 8
[19613.149545] mmcblk0: error -84 transferring data, sector 9, nr 7, card status 0x900
[19613.149731] end_request: I/O error, dev mmcblk0, sector 9
[19613.152232] mmcblk0: error -84 transferring data, sector 10, nr 6, card status 0x900
[19613.152429] end_request: I/O error, dev mmcblk0, sector 10
[19613.154927] mmcblk0: error -84 transferring data, sector 11, nr 5, card status 0x900
[19613.155113] end_request: I/O error, dev mmcblk0, sector 11
[19613.157594] mmcblk0: error -84 transferring data, sector 12, nr 4, card status 0x900
[19613.157780] end_request: I/O error, dev mmcblk0, sector 12
[19613.160306] mmcblk0: error -84 transferring data, sector 13, nr 3, card status 0x900
[19613.160507] end_request: I/O error, dev mmcblk0, sector 13
[19613.163010] mmcblk0: error -84 transferring data, sector 14, nr 2, card status 0x900
[19613.163190] end_request: I/O error, dev mmcblk0, sector 14
[19613.165677] mmcblk0: error -84 transferring data, sector 15, nr 1, card status 0x900
[19613.165855] end_request: I/O error, dev mmcblk0, sector 15
[19613.170491] mmcblk0: retrying using single block read
[19613.172824] mmcblk0: error -84 transferring data, sector 128, nr 8, card status 0x900
[19613.173009] end_request: I/O error, dev mmcblk0, sector 128
[19613.175500] mmcblk0: error -84 transferring data, sector 129, nr 7, card status 0x900
[19613.175681] end_request: I/O error, dev mmcblk0, sector 129
[19613.178171] mmcblk0: error -84 transferring data, sector 130, nr 6, card status 0x900
[19613.178351] end_request: I/O error, dev mmcblk0, sector 130
[19613.180944] mmcblk0: error -84 transferring data, sector 131, nr 5, card status 0x900
[19613.181141] end_request: I/O error, dev mmcblk0, sector 131
[19613.183650] mmcblk0: error -84 transferring data, sector 132, nr 4, card status 0x900
[19613.183838] end_request: I/O error, dev mmcblk0, sector 132
[19613.186318] mmcblk0: error -84 transferring data, sector 133, nr 3, card status 0x900
[19613.190408] end_request: I/O error, dev mmcblk0, sector 133
[19613.192904] mmcblk0: error -84 transferring data, sector 134, nr 2, card status 0x900
[19613.193084] end_request: I/O error, dev mmcblk0, sector 134
[19613.195570] mmcblk0: error -84 transferring data, sector 135, nr 1, card status 0x900
[19613.195756] end_request: I/O error, dev mmcblk0, sector 135
[19613.200401] mmcblk0: retrying using single block read
[19613.202719] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19613.202901] end_request: I/O error, dev mmcblk0, sector 0
[19613.205478] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19613.205662] end_request: I/O error, dev mmcblk0, sector 1
[19613.208140] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19613.208325] end_request: I/O error, dev mmcblk0, sector 2
[19613.210881] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19613.211066] end_request: I/O error, dev mmcblk0, sector 3
[19613.213561] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19613.213740] end_request: I/O error, dev mmcblk0, sector 4
[19613.216222] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19613.216405] end_request: I/O error, dev mmcblk0, sector 5
[19613.218900] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19613.219092] end_request: I/O error, dev mmcblk0, sector 6
[19613.221637] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19613.221819] end_request: I/O error, dev mmcblk0, sector 7
[19613.226439] mmcblk0: retrying using single block read
[19613.228771] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19613.228950] end_request: I/O error, dev mmcblk0, sector 0
[19613.231464] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19613.231654] end_request: I/O error, dev mmcblk0, sector 1
[19613.234178] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19613.234363] end_request: I/O error, dev mmcblk0, sector 2
[19613.236882] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19613.237087] end_request: I/O error, dev mmcblk0, sector 3
[19613.239579] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19613.239761] end_request: I/O error, dev mmcblk0, sector 4
[19613.242248] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19613.242438] end_request: I/O error, dev mmcblk0, sector 5
[19613.244932] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19613.245118] end_request: I/O error, dev mmcblk0, sector 6
[19613.247607] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19613.247792] end_request: I/O error, dev mmcblk0, sector 7
[19613.252452] mmcblk0: retrying using single block read
[19613.254776] mmcblk0: error -84 transferring data, sector 4096, nr 8, card status 0x900
[19613.254954] end_request: I/O error, dev mmcblk0, sector 4096
[19613.257455] mmcblk0: error -84 transferring data, sector 4097, nr 7, card status 0x900
[19613.257633] end_request: I/O error, dev mmcblk0, sector 4097
[19613.260181] mmcblk0: error -84 transferring data, sector 4098, nr 6, card status 0x900
[19613.260361] end_request: I/O error, dev mmcblk0, sector 4098
[19613.262867] mmcblk0: error -84 transferring data, sector 4099, nr 5, card status 0x900
[19613.263064] end_request: I/O error, dev mmcblk0, sector 4099
[19613.265555] mmcblk0: error -84 transferring data, sector 4100, nr 4, card status 0x900
[19613.265738] end_request: I/O error, dev mmcblk0, sector 4100
[19613.268218] mmcblk0: error -84 transferring data, sector 4101, nr 3, card status 0x900
[19613.268397] end_request: I/O error, dev mmcblk0, sector 4101
[19613.270968] mmcblk0: error -84 transferring data, sector 4102, nr 2, card status 0x900
[19613.271159] end_request: I/O error, dev mmcblk0, sector 4102
[19613.273677] mmcblk0: error -84 transferring data, sector 4103, nr 1, card status 0x900
[19613.273874] end_request: I/O error, dev mmcblk0, sector 4103
[19619.100247] mmcblk0: retrying using single block read
[19619.102582] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19619.102586] end_request: I/O error, dev mmcblk0, sector 0
[19619.104915] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19619.104918] end_request: I/O error, dev mmcblk0, sector 1
[19619.107235] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19619.107237] end_request: I/O error, dev mmcblk0, sector 2
[19619.109598] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19619.109601] end_request: I/O error, dev mmcblk0, sector 3
[19619.112020] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19619.112023] end_request: I/O error, dev mmcblk0, sector 4
[19619.114353] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19619.114355] end_request: I/O error, dev mmcblk0, sector 5
[19619.116674] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19619.116676] end_request: I/O error, dev mmcblk0, sector 6
[19619.118990] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19619.118992] end_request: I/O error, dev mmcblk0, sector 7
[19619.118994] quiet_error: 93 callbacks suppressed
[19619.118996] Buffer I/O error on device mmcblk0, logical block 0
[19619.123459] mmcblk0: retrying using single block read
[19619.125774] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19619.125776] end_request: I/O error, dev mmcblk0, sector 0
[19619.128089] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19619.128091] end_request: I/O error, dev mmcblk0, sector 1
[19619.130487] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19619.130490] end_request: I/O error, dev mmcblk0, sector 2
[19619.132825] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19619.132828] end_request: I/O error, dev mmcblk0, sector 3
[19619.135143] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19619.135146] end_request: I/O error, dev mmcblk0, sector 4
[19619.137465] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19619.137467] end_request: I/O error, dev mmcblk0, sector 5
[19619.139781] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19619.139783] end_request: I/O error, dev mmcblk0, sector 6
[19619.142116] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19619.142119] end_request: I/O error, dev mmcblk0, sector 7
[19619.142122] Buffer I/O error on device mmcblk0, logical block 0
[19619.146596] mmcblk0: retrying using single block read
[19619.148913] mmcblk0: error -84 transferring data, sector 0, nr 8, card status 0x900
[19619.148916] end_request: I/O error, dev mmcblk0, sector 0
[19619.151255] mmcblk0: error -84 transferring data, sector 1, nr 7, card status 0x900
[19619.151257] end_request: I/O error, dev mmcblk0, sector 1
[19619.153598] mmcblk0: error -84 transferring data, sector 2, nr 6, card status 0x900
[19619.153600] end_request: I/O error, dev mmcblk0, sector 2
[19619.155992] mmcblk0: error -84 transferring data, sector 3, nr 5, card status 0x900
[19619.155994] end_request: I/O error, dev mmcblk0, sector 3
[19619.158308] mmcblk0: error -84 transferring data, sector 4, nr 4, card status 0x900
[19619.158310] end_request: I/O error, dev mmcblk0, sector 4
[19619.160651] mmcblk0: error -84 transferring data, sector 5, nr 3, card status 0x900
[19619.160653] end_request: I/O error, dev mmcblk0, sector 5
[19619.162990] mmcblk0: error -84 transferring data, sector 6, nr 2, card status 0x900
[19619.162992] end_request: I/O error, dev mmcblk0, sector 6
[19619.165310] mmcblk0: error -84 transferring data, sector 7, nr 1, card status 0x900
[19619.165312] end_request: I/O error, dev mmcblk0, sector 7
[19619.165314] Buffer I/O error on device mmcblk0, logical block 0
[19634.865203] r8169 0000:06:00.0: eth0: link down
[19634.865650] ADDRCONF(NETDEV_UP): eth0: link is not ready
[19635.014487] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19655.724379] wlan0: authenticate with 00:21:04:7b:7d:39 (try 1)
[19655.726456] wlan0: authenticated
[19655.726480] wlan0: associate with 00:21:04:7b:7d:39 (try 1)
[19655.729160] wlan0: RX AssocResp from 00:21:04:7b:7d:39 (capab=0x431 status=0 aid=7)
[19655.729163] wlan0: associated
[19655.729717] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[19655.729955] cfg80211: Ignoring bogus country IE
[19666.250020] wlan0: no IPv6 routers present
[19666.798408] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[19673.897862] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[19693.185159] lo: Disabled Privacy Extensions
```

---

### Post by petex on 2010-12-13
> **Vorian said:**
> "with ubuntu your next update can always be the last one"  (fixed your spelling mistakes)

Did you ever consider the next time you get in a car, it could be your last?

yes but it does not happen almost each time i do some small fix /update  my car:)

---

### Post by CharlesA on 2010-12-13
Are you actually looking for support or just want to post yer opinion?

Also I/O errors mean the SD card is going out.

---

### Post by petex on 2010-12-13
to voice my opinion
however help would be also highly appreciated
what do you mean by "SD card is going out"? it works with my other PC

---

### Post by CharlesA on 2010-12-13
I/O errors mean it's having some sort of problem reading that device.

Since you've created a thread on the SD card issue, I'm bumping this over to T&E.

---

### Post by RiceMonster on 2010-12-13
> **Vorian said:**
> Did you ever consider the next time you get in a car, it could be your last?

Cars break down, therefore Ubuntu updates do not have to work. Cool.

---

### Post by Tristam Green on 2010-12-13
> **RiceMonster said:**
> Cars break down, therefore Ubuntu updates do not have to work. Cool.

Careful hoss. . .

---

### Post by ventrical on 2010-12-13
> **Vorian said:**
> "with ubuntu your next update can always be the last one"  (fixed your spelling mistakes)

Did you ever consider the next time you get in a car, it could be your last?

Hello Ubuntu developer:)  I guess I can now heap some tons of praise on you people for doing such a great job with this great OS , (Maveric Ubuntu). I allow  ALL updates (have been since the BETA) and I'm still waiting for an update to be my last one. Some call me lucky. I just say that Ubuntu is dynamic. I am just so relieved that I can take my laptop harddiskdrive or pendrive and switch them to almost any PC. Usually, as I can understand it, it "appears" that when I swtich an hdd with a 10.10 install on it that any wrong detections of hardware are fixed or patched  in an hour or so or during the next reboot. Why ? I haven't got a clue. All I know is that 10.10 keeps getting better.

Perhaps the OP is right .. perhaps my next update may give me the black screen... but I'm still waiting :) and I'm not going to stop anytime soon using Ubuntu 10.10.:)

Just great work !!

---

### Post by arunb on 2010-12-14
I have never faced any problems with updates, but thats probably because I use LTS, its definitely more stable.

---

### Post by Tamlynmac on 2010-12-14
Perhaps, installing only the security updates instead of blindly  accepting all updates might be a beneficial option. There's  no mandate to install all updates. Especially, for those users that have  limited knowledge of the OS. One additional thought might be to backup one's system prior to updating. This may reduce the frustration of a failed update, by returning one's system to it's pre-update status. :idea:

I doubt, pointing out that updates work fine on other PCs improves the OP's perspective. IMHO, it only adds insult to injury. I guess that could be the intent (IDK)? :-k

To the OP - Good Luck

---

### Post by ventrical on 2010-12-14
> **Tamlynmac said:**
> Perhaps, installing only the security updates instead of blindly  accepting all updates might be a beneficial option. There's  no mandate to install all updates. Especially, for those users that have  limited knowledge of the OS. One additional thought might be to backup one's system prior to updating. This may reduce the frustration of a failed update, by returning one's system to it's pre-update status. :idea:

I doubt, pointing out that updates work fine on other PCs improves the OP's perspective. IMHO, it only adds insult to injury. I guess that could be the intent (IDK)? :-k

To the OP - Good Luck[http://ubuntuforums.org/showthread.php?p=10239181#post10239181](http://ubuntuforums.org/showthread.php?p=10239181#post10239181)

Hi Tamlynmac,

  I just started a thread here:

[http://ubuntuforums.org/showthread.php?p=10239181#post10239181](http://ubuntuforums.org/showthread.php?p=10239181#post10239181)

on the topic of how to do a back-up like you mentioned and the best software to use.

Perhaps you and others have some ideas??

thanks in advance.

---

### Post by overdrank on 2010-12-14
Thanks for sharing. Thread closed.

---

