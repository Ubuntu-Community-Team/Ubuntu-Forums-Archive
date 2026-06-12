---
title: "Advice needed on system specs"
date: 2016-09-07
forum: Ubuntu, Linux and OS Chat
---

### Post by ghostu on 2016-09-07
I'm looking to buy either a laptop or possibly an Intel NUC to run a dual boot of Ubuntu and Windows 10 for my daughter in grade school.  She would like to use the system for homework (docs and web assignments), Netflix, learning Linux, and some basic gaming.  I think I would also put Minecraft on.  I would only install this as a dual boot just in case there is a need for Windows 10 due to other assignments she may get, but her primary OS would be Ubuntu or I'm thinking Ubermix.

So if anyone could offer advice on a suitable system setup it would be greatly appreciated.  Also, any reason why not to use Ubermix in this situation?  I'm not too deep in the Linux world, but can do installs and work my way around the command line.  Just trying to find the best solution in this case.

Thanks in advance!

---

### Post by sudodus on 2016-09-07
I have an Intel NUC and it is very friendly to both linux and dual booting. But when I think of my children, I have noticed, that they prefer a laptop. I usually buy refurbished professional class laptops. They are a few years old, and linux has caught up with the hardware in them.

If you buy a computer with Windows 10, you can expect to get it installed in UEFI mode.

There are several links, that might be useful for you via this link:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

Configure dual boot:

- Start installing Windows (if not installed already)

- Shrink the Windows partition with Windows tools (inside Windows). Do ***not*** let Windows create partitions.

- Boot from an Ubuntu [flavour] DVD/USB drive, start ***gparted*** and create partitions in the unallocated space.

- Create a partition for Ubuntu of at least 20 GB - for the root partition, with the ext4 file system.

- Create a swap partition. If you intend to hibernate, it should be at least the same size in GiB (base 2) as the RAM, for example 4 "GB" RAM --> 4.8 GB swap. Otherwise, if you do not intend to hibernate, it is probably enough with 1 GB swap.

- You may want a separate **data** partition (for documents, pictures, music, video clips etc), and you want it available from both linux and Windows. So put an NTFS file system there.

- Start the installer and select ***Something else*** in the partitioning window. That way you can select the partitions, that you created with gparted.

---

### Post by Bucky Ball on 2016-09-07
> **ghostu said:**
> Also, any reason why not to use Ubermix in this situation?

A big thing with Linux is support. A good reason for not using Ubermix is it is a fairly obscure spin and you probably won't get a lot of help with it if things go pear-shaped. ([HERE is their forum]("http://forums.ubermix.org/").) It is not officially supported by Canonical and we do not support it here, although you could look for support in the 'Other OS' section. Generally, the more 'boutique' the spin, the harder to get support as less people are using it.

The more 'boutique' spins and flavours are probably better served after a hearty and fulsome meal of regular Ubuntu. In other words, once you know your way around and have a better idea of how to fix something if it breaks. Good luck. :)

* Just had a look at Ubermix. Wouldn't bother. Any apps that are in that you can install in a regular Ubuntu. The desktop environment they are using, for instance, looks like xfce4, the one used in Xubuntu and the one I'm using right now. Ubermix is based on Ubuntu and would use the same software repositories (in other words, they've probably just done a Ubuntu minimal install, or perhaps an Xubuntu-core install, added the software they want from the software repos, created an ISO of the install and called that 'Ubermix' and there you go ... the only thing special about it is they've done the work for you, but only they know what they've done unless you are familiar enough with Ubuntu to figure out what that is). There is also [Edubuntu]("https://edubuntu.org/"), which is supported here, but basically, you could install a lightweight flavour like Xubuntu (supported) then customise that to whatever suits your daughter's needs. We're always here to help with that.

* Just one more thing about Edubuntu: it has 'bundles' for different age groups which you can install in any Ubuntu flavour. See 'Installation on existing Ubuntu' [down the page here]("https://edubuntu.org/download"). :)

---

### Post by mastablasta on 2016-09-07
> **sudodus said:**
>  I usually buy refurbished professional class laptops. They are a few years old, and linux has caught up with the hardware in them.


i plan to do it as well (unless i can find a good deal on lower end desktop). the added benefit when going for professional class laptops is that often they are linux certified (particulary HP and Dell). meaning it iwll all work out of the box. especially with Intel GPU. AMD is a bit different story, but even there Radeon driver should be good enough. you can get a dock with them and add a bigger screen an dporpper keyboard (if needed).

i already have a screen, mouse and keyboard, which is why this sounds attractive to me. plus you can get a good (robust), powerfull laptop at a very low price (even one with a new battery). 

even if they come with old windows version they might still be able to upgrade for free (accroding to some articles) and if not well win 7 supported until 2019 and win 8.1 i think until 2022 or something like that. you do not need win 10 for office and school work. all apps they make now still have support for win 7 at least, if not older.

---

### Post by ghostu on 2016-09-07
Great information!  OK, looks like I'll be looking for a laptop then which is nice because she could always take her work with her.  Also, I'll skip Ubermix and probably just install Xubuntu.  I'd rather have the most basic setup and work my way up from there.  I have a Windows 10 license to use, so I'm good there.

As far as the laptop, is getting an i7 overkill?  I'm thinking an i5 should do.  What are your thoughts?

Thanks again for the tips!

---

### Post by sudodus on 2016-09-07
Yes, I think an i5 is good, and as mastablasta suggested, Intel graphics are [usually] linux friendly.

---

### Post by mastablasta on 2016-09-08
for your needs even a Pentium one should do. i3 is normally what you would use for that (e.g. office work). so if you have the money i5 will be a very good choice that should last (powerfull enough) for some time to come. Make sure it has at least 4 GB ram.

i use an i3-6100U (so a 6th gen) with 4GB ram for office work in Win10 and so far i don's see any slowdown. work is fluent even with multiple windows open and cvarious applications loaded (SAP ERP, Edge, Outlook, Excel, word, Skype for business, One drive for business, one drive, greenshot...) on two montiors (laptop and docked). i rarely play videos but when i do there is no hickups, occasionally i would record screencast (when ifind some good solution i prepare a "how to" and share it with colleagues), i even did some video encoding (no issues and seemed fast enough). once or twice a week we do video conference with USA (2 locations), Netherlands and Sweden on my laptop where i would host or view a presentation over Skype for Business (former Lync). also no issue there, appart from occasional lag from network. i'd say as far as power is concerned i am pleased with what they gave me although i wish i had an i5. but us at lower level get budget stuff. :P

---

### Post by Bucky Ball on 2016-09-08
I use an i3 lappy with 4Gb of RAM. Would do what you want to do fine, although I have no idea about the Minecraft stuff. What I do know is that my machine runs Virtualbox just fine with the host and client machines running faultlessly. :)

Whether that would be anywhere equivalent to the resources needed for Minecraft I wouldn't know. You might find [this chart]("http://minecraft.gamepedia.com/Hardware_requirements") helpful with that. It looks recent. 

My machine is a Toshiba Satellite Pro L510. About five years old now I'd say (probably a bit older). Only a 14" screen, though. :|

---

### Post by mastablasta on 2016-09-08
while i explored the options i also took into account minecraft and educational apps used/played by my son. 
currently we run older (less optimised) version of minecraft and run it on Celeron e3300 with old ATI Radeon 9600XT 256Mb. it runs well on medium setting. the card can otherwise run well older games to about 2005. 
on my other PC it ran on high settings with Athlon 3.2 Ghz single core and Radeon HD 3650 512MB (which died on me just recently). this PC didn't just run the game but acted as a minercaft LAN server at the same time.

from my research (web, articles, tests reviews) i concluded that Intel gen3 and newer with their built in intel GPU will run minecraft very well as well as plenty games that were arorund ot about 2008, 2010. at least on some medium settings if nothing else. 

which is why a gen3 i3 laptop coupled with AMD radeon with 512 MB or more (gen3 had non hybrid GPU =GPU chip runs separatelly from CPU) should run circles arround minecraft. Gen4 or 5 with intel GPU should be doing well also. i5 with it's built in intel GPU seems to usually perform about 20, 30% better than i3 in gaming, so if you get your hands on one of those it would be an even better experience.

new i3 and i5 (gen 6) as well as Pentium (from same gen) should run Minecraft well. they can cate up to 1GB of ram to the GPU and the processing power of these mobile built in GPU's is not as bad as it used to be in the old days.

i haven't lookied into nvidia in the laptop area as it seems that older models had poor "optimus" (hybrid graphics) support. maybe somone else has more info on that. i also do not know how and if this situation improved recently.

Another thing i haven't looked into much is the AMD A series APU's. mainly since they do not sell many laptops with this config here (especially used ones are hard to get). however it a good and cheaper option for a mini PC. the CPU might be weaker than i3, but the GPU is a lot stronger (good for games and such). you would probably also have to build it yourself (unlike intel NUC). AMD A6 and upwards would be good for minecraft and some light gaming. i am not sure how well it performs in linux, but a user from local ubuntu support team is very happy with it.

---

### Post by ghostu on 2016-09-08
Thanks for the data!  I'm keeping my eye out for any good i5 deals out there.  Time is on my side, so I'm willing to wait til BF if needed.  I'd like to get about 8GB of RAM and an SSD in the config.

I used to always get Dells, but is there another manufacturer I should look into now?

---

### Post by sudodus on 2016-09-08
I'll repeat: refurbished professional class laptops. Brands: alongside Dell also HP, Lenovo and maybe Toshiba.

---

### Post by SagaciousKJB on 2016-09-09
Will the need for Windows have anything to do with accelerated graphics? If not then you might try just using Wine or a Virtual Machine. I very rarely have to use any Windows applications and can depend on them for virtually 100% of applications that don't require accelerated graphics.  Any kind of gaming though, it's got to be a dual boot. Wine will run SOME games, and SOME games well, but there's also a lot of user intervention needed and things break quickly as they're updated.

sudodus, what exactly is a professional class laptop? Curious, because I think I might be in the market for one sometime soon, and it's been a long time (2006) since I bought any kind of laptop/notebook/netboook/whatever and there's a lot of interesting stuff out now.

---

### Post by sudodus on 2016-09-09
Professional class laptops are built with higher grade mechanical as well as electronic components, and often sold to companies or professional individuals, for example HP Probook and Elitebook, Dell Latitude, Lenovo Thinkpad, Fujitsu Lifebook (usually with Intel i5 or i7). The focus is *not* on multimedia and gaming, and they are often dockable (convenient to connect to a company's wired network, and to separate monitor, keyboard and mouse).

---

### Post by SagaciousKJB on 2016-09-10
> **sudodus said:**
> Professional class laptops are built with higher grade mechanical as well as electronic components, and often sold to companies or professional individuals, for example HP Probook and Elitebook, Dell Latitude, Lenovo Thinkpad, Fujitsu Lifebook (usually with Intel i5 or i7). The focus is *not* on multimedia and gaming, and they are often dockable (convenient to connect to a company's wired network, and to separate monitor, keyboard and mouse).

Ahhh I see, is that why Lenovo Thinkpads are like, virtually identical in terms of appearance and form factor even though they keep coming out with new versions?

---

### Post by mastablasta on 2016-09-12
> **SagaciousKJB said:**
> Ahhh I see, is that why Lenovo Thinkpads are like, virtually identical in terms of appearance and form factor even though they keep coming out with new versions?

form factor is not important for companies. they need something more robust that can get the job done and that won't fall appart after 2 or 3 years. they also usually have a matt screen as people at work dont' care how well their PC looks on the stand in the shop. whoever came up with glare screens for laptops should be sent in front of firing squads anyway.

you also have what they call workstations if you need  more power under the hood. they are a bit bulkier but again they are aimed at professional power users. still you can get one that used to be sold for 4000 or 5000 EUR now for arround 500 or 600 EUR here. with powerfull GPU, 8 or 16 GB ram, quad core i7 2nd gen...

the thing is these laptops loose value fast and will seell at quite low price eventhough their specs are still quite good. so you can get a good PC (say core i5 second or 3rd gen), pumped with 8GB ram, sometimes with descrete GPU added, 15" matt screen and it will all cost you as much as one of the low cost laptops. here they sell then for 290 -350 EUR.

and if you look at the difference between the older gen core i CPU and the newer one there is not that big of a difference in power. mostly they went for better batter usage. but in power they do not have such a major difference.

---

