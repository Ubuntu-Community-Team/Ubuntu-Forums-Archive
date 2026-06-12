---
title: "Just for giggles - ASRock Linux Support...or lack of!"
date: 2015-04-02
forum: Ubuntu, Linux and OS Chat
---

### Post by KillerKelvUK on 2015-04-02
Got an ASRock Z97 Extreme6 a few weeks back, dropped 14.10 on and use KVM for a few different bits and bobs.  I chose this board for the stated Vt-d capabilities as I wanted to attempt PCI device passthrough which I've successfully managed now with both a Nvidia GTX 650 card and a DVB-S2 card to different VM's.

However in the process of setting up the host I noticed that when I set 'intel_iommu=on' the HDMI audio on the host stops working and I can only use the analogue out.  I googled around, ended up raising a lauchpad bug report and found a few other posts suggesting it could be the vendors implementation of the EFI that was to blame.  Anyway I decided raise a support ticket with ASRock and shared with them my google results to see what would happen...

The first response was basically that ASRock don't officially support linux on there desktop boards but they'd refer the ticket onto their colleagues in Taiwan to see if they could help.  After a little chasing I got a reply where they had actually tested the problem but had obviously either not understood the scenario (host only) or the nuances had been lost in translation...they had attempted to install Windows 8.1 inside an ESXi host and pass through the boards HDMI audio controller...I got a nice little screen shot showing me their efforts :confused:.  So I kindly pointed out the very subtle differences of my problem vs. their testing and yesterday I got this email...

> 
[FONT=arial]Hello,[/FONT]



[FONT=arial]No luck I'm afraid. My colleague recommends using Windows instead. That is[/FONT]
[FONT=arial]Chinese for saying that we do not officially support Linux. With some issues[/FONT]
[FONT=arial]under Linux we can still help. But in this case it seems a bit too[/FONT]
[FONT=arial]complicated without enough Linux experience. So we cannot help you with[/FONT]
[FONT=arial]this. Sorry...[/FONT]



[FONT=arial]Kind regards,[/FONT]

[FONT=arial]ASRock Support[/FONT]


I personally wasn't surprised by the lack of support and I was actually a little shocked when they had attempted to replicate the scenario which shows some willing...does any hardware vendor offer end user linux support to desktop communities (i.e. non-enterprise customers)?

Anyway's, thought I'd share but will keep researching my audio problem, probably post elsewhere in the forums for some advice.

---

### Post by jclaeyssens on 2015-04-22
Hah, know the feeling! At least you got an answer out of them, they didn't even bother to answer mine... Luckily Amazon.co.uk customer service is top notch so now I have a brand new ASrock motherboard with fully functioning on-board audio. Bummer for you though...

---

### Post by Bucky Ball on 2015-04-22
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. ;)

---

### Post by user_of_gnomes on 2015-04-22
I don't understand why people buy Asrock. They used to make the most horrible low-grade mainboards in the late 90's and 00's that would constantly come up with bad caps or just have all sorts of other problems. I threw out I don't know how many Asrock mainboards and had to tell a lot of people that they were sold junk.

They seem to have given their reputation a complete overhaul because now they're suddenly being marketed as top-notch ... People have short memories.

---

### Post by Bucky Ball on 2015-04-22
I built my own desktop with an ASRock mb about twelve years ago. Not a peep. Still working faultlessly.

---

### Post by mastablasta on 2015-04-23
> **jclaeyssens said:**
> Hah, know the feeling! At least you got an answer out of them, they didn't even bother to answer mine... Luckily Amazon.co.uk customer service is top notch so now I have a brand new ASrock motherboard with fully functioning on-board audio. Bummer for you though...

I also didn't get any reply form them. just wanted to do NVidia upgrade to replace the old card. it didn't work in Linux. I am sure it would in windows. the other old card I tried from AMD worked, however it also crashed when running openGL. and that card had official BIOS support. 

as for their quality - I had one that worked about 9 months and then gave out. I had another one same model that still works after 10 years.

this a bit newer one I have doesn't really work well in Linux. but then again as they said they do not officially support Linux anyway. I think I will avoid them in the future. unless I read some good review about certain model. 

Gigabyte on the other hand works very well after 10 years. also fully compatible with Linux.

as for compatibility - we are asking manufacturers to maintain compatibility with myriad of distros. this one uses that kernel, that one uses the other... I find it a bit demanding since their funds are limited and Linux Desktop market is 1% or less. example my HP dm1 - fully compatible with 12.10, 13.04 some things stopped working. 13.10 some Fn keys stopped working, 14.04 - almost no Fn key I working. obviously the kernel changed so much they mess up the compatibility. why should the manufacturer keep up to date ? to Ubuntu, to Mint, to Debian, to Red Hat, to Fedora... each of them using different xserver, different kernel version, different libraries etc.

---

