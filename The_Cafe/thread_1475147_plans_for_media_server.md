---
title: "plans for media server"
date: 2010-05-06
forum: The Cafe
---

### Post by djyoung4 on 2010-05-06
So this summer i plan on building a media server type box.  I want it to be able to act as a dvr for my tv and store all my movies and music.  I would probably use something like xbmc for the media player but was wondering what would be the best distro to use.  mythbuntu seems kind of promising but would that work well for my media storage.  I also would like to make it a server so I could access any of the media from other laptops in my house.  sorry if its kind of confusing but any suggestions as to where to start or any other ideas are greatly appreciated.

edit: im going to update this whenever i find parts for what im building.  any input or known problems that anybody would like to share would really help.
Case: Antec 600 $69.95 + 9.99 shipping.  got it.  ordered 3 extra fans at 9.99 too.
PSU: Corsair 650TX 650W $89.99
Motherboard: MSi 870A-G54 109.99
TV Tuner Card: Hauppauge WinTV HVR-1600 $99.99
CD/DVD Drive: Sony Optiarc 24X $26.99
CPU: AMD Phenom II x4 945 Quad Core 139.99
RAM: 1 (possibly 2) Corsair XMS3 Xtreme Performance 2X2 GB $129.99 a piece
Graphics card: ZOTAC ZT-20201-10L GeForce GT 220 $78.99
TV: Vizio 37" LCD HDTV (already got it)
Hard Drives: Western Digital Caviar Black 2 TB 64MB cache $212.64 got it
Total is $968.51
did i forget anything
also i dont want to use hardware RAID(maybe software) because I don't think its really necessary but I do want to have at least 5 TB of storage

---

### Post by teet on 2010-05-06
> **djyoung4 said:**
> So this summer i plan on building a media server type box.  I want it to be able to act as a dvr for my tv and store all my movies and music.  I would probably use something like xbmc for the media player but was wondering what would be the best distro to use.  mythbuntu seems kind of promising but would that work well for my media storage.  I also would like to make it a server so I could access any of the media from other laptops in my house.  sorry if its kind of confusing but any suggestions as to where to start or any other ideas are greatly appreciated.

I would just use regular old ubuntu and install things from there.  I prefer gnome to xfce and many benchmarks have shown that using xfce doesn't really save any memory.  For configuring the samba server (to share with windows pcs or other linux boxes) I would suggest installing system-config-samba via synaptic.  It makes things much easier.

For the program you could use mythtv, xbmc, or boxee.  There are several others but those three are great choices.  MythTV doesn't have as slick an interface as the others but it will get the job done, plus it's the only one that will let you record TV too.

-teet

Edit:  I just reread your post and if you want to record TV then you are pretty much "stuck" using mythtv.  There is also Freevo but it has never been as popular and seems much harder to install and configure.

---

### Post by jbrown96 on 2010-05-06
Make sure to get an Nvidia card. I built a HTPC a couple years ago, and the AMD's FGLRX drivers are terrible. XBMC works much, much better with Nvidia.
VDPAU rocks. Check out the feature sets of cards [http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo). Try to get something with feature set C like a GeForce 205/210. They are cheap and rock.

---

### Post by djyoung4 on 2010-05-07
thanks guys. I found [this.]("http://havetheknowhow.com/default.htm")  should help me a bit but will be posting problems and editing with pictures and updates accordingly.
on a side note.  most sites that I did find all came to the question of windows vs linux and most of them said that linux is more labor intensive while windows is set it and forget it.  just an interesting little thing

---

### Post by PartisanEntity on 2010-05-07
I have set up a media server on my spare Ubuntu laptop. I store all my multimedia files on their, it acts as a media server for my TV and it also serves music to my iTunes on my MacBook. In addition it even serves as a Time Capsule for the Mac.

I wrote up a how to here in case you are interested:
[http://www.cognitivecombine.com/2009/12/diy-ubuntu-nas-with-afp-smb-dlna-and-itunes/](http://www.cognitivecombine.com/2009/12/diy-ubuntu-nas-with-afp-smb-dlna-and-itunes/)

---

### Post by 98cwitr on 2010-05-07
you know thats a 5400rpm drive you have picked out there, right :?

here's what Im looking to build. My recommendation for a tv tuner card is in this thread

[http://ubuntuforums.org/showthread.php?t=1465300](http://ubuntuforums.org/showthread.php?t=1465300)

---

### Post by JohnnyC35 on 2010-05-07
Hey I've built a media centre as well, I currently just have Ubuntu with xbmc on it but once my new hard drives come in I'll try Lubuntu with xbmc. Here's the specs on the case:

Apex MI-008 Mini ITX Black Case                                                            (60$)
Zotac IONITX-A-U Atom N330 1.6Ghz Dual-Core (195$)
            ---Includes motherboard, CPU, and built in PS
Corsair XMS2 2048MB PC6400 DDR2 800MHz     (55$) will get another once it's on sale again
Masscool 60mm (12$) will go in the gaping hole left by lack of Mini-ATX PS
StarTech 3.5 Universal Mounting HD Bracket       (7$)
Masscool 60mm ABS plastic foam fan filter         (6$)
3 WD Caviar Green 1.5T                                    (300$) will be in RAID5

This plays DVD and 720 Blue-Ray with no issue. but stutters on 1080 sadly but oh well. I don't have a TV tuner as the internet is my PVR device.

---

### Post by djyoung4 on 2010-05-07
updated thanks guys

---

### Post by teet on 2010-05-07
> **djyoung4 said:**
> most sites that I did find all came to the question of windows vs linux and most of them said that linux is more labor intensive while windows is set it and forget it.  just an interesting little thing

In my opinion, if you want to setup a linux media server/pvr you should think of it more as a hobby rather than a way to get a cheap appliance.  I've been messing with this stuff for several years now and now have a set up that has more features than any DVR available right now and has ended up being cheaper.  However, I have probably invested 100+ hours setting all of this up...but the thing is, I love spending time hacking around on my mythtv box.  

If you don't enjoy that sort of thing, it's much easier to just pay $10-15 a month extra to your cable/satellite provider and get their DVR.  If it breaks, they replace it.  For the media server side, you could probably just buy a big external harddrive and hook it up to one of those new fancy routers that come preinstalled with a linux os that let you access the hdd over your network.

-teet

---

### Post by andrewabc on 2010-05-07
You should briefly look into [nettops](http://en.wikipedia.org/wiki/Nettop).
[Zotac ZBOX HD-ID11 Review: Next Gen ION is Better & Worse than ION1](http://www.anandtech.com/show/3702/zotacs-zbox-hdid11-review-next-gen-ion-better-worse-than-ion1)

They're small, don't use much power etc, cost ~$300

But if you have $1000 to spend, then I wouldn't recommend them. I'm guessing you're looking for a powerful home server which nettops can not do yet.

---

### Post by jbrown96 on 2010-05-07
> **andrewabc said:**
> You should briefly look into [nettops](http://en.wikipedia.org/wiki/Nettop).
[Zotac ZBOX HD-ID11 Review: Next Gen ION is Better & Worse than ION1](http://www.anandtech.com/show/3702/zotacs-zbox-hdid11-review-next-gen-ion-better-worse-than-ion1)

They're small, don't use much power etc, cost ~$300

But if you have $1000 to spend, then I wouldn't recommend them. I'm guessing you're looking for a powerful home server which nettops can not do yet.

Ion is cool, but the problem is the Atom processor. The Nvidia graphics are great in them, but Atom is no good for stuff like Hulu since it's Flash. If you need Flash, then something with high speed is good. Additional cores won't really help, so a fast dual core would be sufficient.

---

### Post by djyoung4 on 2010-05-07
> **andrewabc said:**
> You should briefly look into [nettops](http://en.wikipedia.org/wiki/Nettop).
[Zotac ZBOX HD-ID11 Review: Next Gen ION is Better & Worse than ION1](http://www.anandtech.com/show/3702/zotacs-zbox-hdid11-review-next-gen-ion-better-worse-than-ion1)

They're small, don't use much power etc, cost ~$300

But if you have $1000 to spend, then I wouldn't recommend them. I'm guessing you're looking for a powerful home server which nettops can not do yet.

its not that i want to blow money.  i just want something that is gonna be able to handle anything I thrown at it.  I would rather it be too powerful then not powerful enough.  Also this is my first complete build so im really excited.

---

### Post by andrewabc on 2010-05-07
> **jbrown96 said:**
> Ion is cool, but the problem is the Atom processor. The Nvidia graphics are great in them, but Atom is no good for stuff like Hulu since it's Flash. If you need Flash, then something with high speed is good. Additional cores won't really help, so a fast dual core would be sufficient.

Ion is [capable of GPU decoding](http://www.pauljroberts.com/flash-10-1-beta-on-acer-revo-3610-testing-results) of flash (flash 10.1) since late 2009.
So 1080p flash is possible.

Although there are still bugs in the drivers etc. In the article I linked it showed that specific model can't play 1080p flawless. But that bug is supposed to be fixed in June. Original ion can play 1080p in most instances I think.

Nettops should be more popular by end of year when they fix bugs and prices drop. Great web browsing machines to replace old/big towers, or if you want to use specifically for HTPC. Default hard drives are crap, but that's why you would put in a SSD for OS/apps and 1tb HDD in external enclosure hooked up to esata.

Also would be better if they came out with a model with a better fan. Spend an extra $10 on good quality fan to keep noise low and heat low. Fan included just looks like generic cheap fan. And it is a problem with most nettops if the room were to get hot, or running lots of CPU/GPU intensive stuff constantly.

Also, wireless in most nettops is pretty bad. So if using for server I'd have hooked up to wire->router, as router should have better wireless.

---

### Post by djyoung4 on 2010-05-09
ok so i need to make a decision on a motherboard.  I have the money to start building this thing.  any suggestions.  i know i wanna go intel cpu.

---

### Post by djyoung4 on 2010-05-11
bump

---

### Post by FiveSidedPoly on 2010-05-11
A lot of people are giving you suggestions for HTPC/Media Players, not just for a Media Server.

Personally I would go with something in AMD's lineup of CPUs, they can offer the same performance, at a lot less of a cost.

I dropped an AMD Athlon II x2 240 in my media server, it's a 2.8ghz Dual Core, and ran me $54.  I got a good ASUS mobo for $69.

Going with something similar would save you over $200 on just those parts.

Since this is a "media server" and not a HTPC, the need for a interal CD/DVD drive is a personal choice, since typically a media server does not usually stream from a CD/DVD drive, nor do I know a lot of people who use it to install or burn anything on a regular basis.  But that would be up to what you want to use it for really.

I went an got a decent external CD/DVD drive to load Ubuntu Server and that was it, all my HTPCs in the house are drive-less too, so I do use it with them at times and for friends who have issues with Netbooks.

Also I would worry about your HTPC (media centers) having good graphics cards, not the server itself, I know mine doesn't have issues using the onboard ATI 4200 HD.  And I can stream to multiple computers throughout the house at any given time with XBMC.

If you plan on having the media server run all the time you might want to look into what actual power requirements it will need/may need in the future as you expand it.  450W can go pretty quick.  Also the WD Blacks, while being fast, do draw a decent amount of power.  You can use a Watt calculator, Antec, Thermaltake, Cooler Master and a few others have them on their websites.  Just search for power supply calculator.

My headless media server sits in a closet and doesn't see the light of day very often except for routine cleaning, runs like a champ, and I spent a lot less then you plan to right now.  I used the money I saved from price/part shopping to buy those extra HDs.

Come to think of it, I don't think I even spent $300 on any of my HTPCs, and I can do pretty much anything with them.

---

### Post by djyoung4 on 2010-05-12
> **FiveSidedPoly said:**
> A lot of people are giving you suggestions for HTPC/Media Players, not just for a Media Server.

Personally I would go with something in AMD's lineup of CPUs, they can offer the same performance, at a lot less of a cost.

I dropped an AMD Athlon II x2 240 in my media server, it's a 2.8ghz Dual Core, and ran me $54.  I got a good ASUS mobo for $69.

Going with something similar would save you over $200 on just those parts.

Since this is a "media server" and not a HTPC, the need for a interal CD/DVD drive is a personal choice, since typically a media server does not usually stream from a CD/DVD drive, nor do I know a lot of people who use it to install or burn anything on a regular basis.  But that would be up to what you want to use it for really.

I went an got a decent external CD/DVD drive to load Ubuntu Server and that was it, all my HTPCs in the house are drive-less too, so I do use it with them at times and for friends who have issues with Netbooks.

Also I would worry about your HTPC (media centers) having good graphics cards, not the server itself, I know mine doesn't have issues using the onboard ATI 4200 HD.  And I can stream to multiple computers throughout the house at any given time with XBMC.

If you plan on having the media server run all the time you might want to look into what actual power requirements it will need/may need in the future as you expand it.  450W can go pretty quick.  Also the WD Blacks, while being fast, do draw a decent amount of power.  You can use a Watt calculator, Antec, Thermaltake, Cooler Master and a few others have them on their websites.  Just search for power supply calculator.

My headless media server sits in a closet and doesn't see the light of day very often except for routine cleaning, runs like a champ, and I spent a lot less then you plan to right now.  I used the money I saved from price/part shopping to buy those extra HDs.

Come to think of it, I don't think I even spent $300 on any of my HTPCs, and I can do pretty much anything with them.
it is going to be and HTPC though.  sorry for the confusion.  Its going to be connected to the vizio tv I already have.  It will also be a server as well.  I dont know if I have confused anybody with that.  thanks for the info though.  I ordered my case the other day and need to order the motherboard soon.  If AMD is better then what would be a suggestion.  I want to be able to play 1080 hd so it has to have PCIe right?  also have at least 6 sata ports and have 4 to 8 gb of ram.  im pretty much clueless as to where to start.  thanks for any help

---

### Post by FiveSidedPoly on 2010-05-12
I see, your original post didn't seem to point in that direction.

Well you could use it for both an HTPC and a media server, have heard of people doing that, never tried myself.  

Two reasons why I don't think it is the greatest idea:

- if you shut it off for whatever reason or have an issue with it, then you can't stream or file share with other computers, and you lose an HTPC at the same time. 

- I assume performance would be reduced when combining all the services for both.   If you start doing a lot of media stuff on it, it could slow down the  serving functions.

If you plan on using it for both, I suggest a decent priced Quad Core, this would help balancing the load a little.  A good Dual Core might also do the trick.  I honestly don't know since I never combined the two functions.  If it will be running all the time or very often I suggest getting a low wattage CPU, 65W being very good, 95W being the highest I would go.  It can be tough though because it can limit you to Dual Cores and for the really good stuff at low wattage the price goes up a lot.

Something along the line of these might do it for you though:

[AMD Phenom II X2 555  Black Edition Callisto 3.2GHz Socket AM3 80W Dual-Core Desktop Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103846")
[AMD Athlon II X4 630  Propus 2.8GHz Socket AM3 95W Quad-Core ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103704")

Both of those are $99 on NewEgg right now.

[AMD Athlon II X2 250  Regor 3.0GHz Socket AM3 65W Dual-Core ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103681")is $65 right now.
[AMD Athlon II X2 255  Regor 3.1GHz Socket AM3 65W Dual-Core Desktop Processor Model  ADX255OCGQBOX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103844") is $69.

I have several different Athlon II X2s, running in anything from HTPCs, home/media servers, basic workstations.  I think they are tough, well priced, and reliable CPUs.

On another note, I can play 1080p with my onboard GPU.  You could look into something like the ASUS M4A785-M, they make another version with 128mbs of sideport memory but I can't remember the model number off the top of my head.  It will also cover your SATA and Ram specs you want.  A dedicated PCIe GPU would be important if you are wanting to combine both the HTPC and server functions.

---

### Post by 98cwitr on 2010-05-12
> **FiveSidedPoly said:**
> I see, your original post didn't seem to point in that direction.

Well you could use it for both an HTPC and a media server, have heard of people doing that, never tried myself.  

Two reasons why I don't think it is the greatest idea:

- if you shut it off for whatever reason or have an issue with it, then you can't stream or file share with other computers, and you lose an HTPC at the same time. 

- I assume performance would be reduced when combining all the services for both.   If you start doing a lot of media stuff on it, it could slow down the  serving functions.

If you plan on using it for both, I suggest a decent priced Quad Core, this would help balancing the load a little.  A good Dual Core might also do the trick.  I honestly don't know since I never combined the two functions.  If it will be running all the time or very often I suggest getting a low wattage CPU, 65W being very good, 95W being the highest I would go.  It can be tough though because it can limit you to Dual Cores and for the really good stuff at low wattage the price goes up a lot.

Something along the line of these might do it for you though:

[AMD Phenom II X2 555  Black Edition Callisto 3.2GHz Socket AM3 80W Dual-Core Desktop Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103846")
[AMD Athlon II X4 630  Propus 2.8GHz Socket AM3 95W Quad-Core ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103704")

Both of those are $99 on NewEgg right now.

[AMD Athlon II X2 250  Regor 3.0GHz Socket AM3 65W Dual-Core ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103681")is $65 right now.
[AMD Athlon II X2 255  Regor 3.1GHz Socket AM3 65W Dual-Core Desktop Processor Model  ADX255OCGQBOX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103844") is $69.

I have several different Athlon II X2s, running in anything from HTPCs, home/media servers, basic workstations.  I think they are tough, well priced, and reliable CPUs.

On another note, I can play 1080p with my onboard GPU.  You could look into something like the ASUS M4A785-M, they make another version with 128mbs of sideport memory but I can't remember the model number off the top of my head.  It will also cover your SATA and Ram specs you want.  A dedicated PCIe GPU would be important if you are wanting to combine both the HTPC and server functions.

even AMDs 2.8GHz 240 proc is on $52.99 on newegg, and it would work great for this role.

---

### Post by FiveSidedPoly on 2010-05-12
Very true.  I actually have four of them, but since they are wanting to have it as dual role HTPC/media server, I didn't want to suggest the 240 since you can get a 250 or 255 for a little bit more.

The Athlon II X2s are great little CPUs, but he might want the L3 cache of a Callisto or Propus chip.

---

### Post by djyoung4 on 2010-05-14
> **FiveSidedPoly said:**
> I see, your original post didn't seem to point in that direction.

Well you could use it for both an HTPC and a media server, have heard of people doing that, never tried myself.  

Two reasons why I don't think it is the greatest idea:

- if you shut it off for whatever reason or have an issue with it, then you can't stream or file share with other computers, and you lose an HTPC at the same time. 

- I assume performance would be reduced when combining all the services for both.   If you start doing a lot of media stuff on it, it could slow down the  serving functions.

If you plan on using it for both, I suggest a decent priced Quad Core, this would help balancing the load a little.  A good Dual Core might also do the trick.  I honestly don't know since I never combined the two functions.  If it will be running all the time or very often I suggest getting a low wattage CPU, 65W being very good, 95W being the highest I would go.  It can be tough though because it can limit you to Dual Cores and for the really good stuff at low wattage the price goes up a lot.

Something along the line of these might do it for you though:

[AMD Phenom II X2 555  Black Edition Callisto 3.2GHz Socket AM3 80W Dual-Core Desktop Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103846")
[AMD Athlon II X4 630  Propus 2.8GHz Socket AM3 95W Quad-Core ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103704")

Both of those are $99 on NewEgg right now.

[AMD Athlon II X2 250  Regor 3.0GHz Socket AM3 65W Dual-Core ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103681")is $65 right now.
[AMD Athlon II X2 255  Regor 3.1GHz Socket AM3 65W Dual-Core Desktop Processor Model  ADX255OCGQBOX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103844") is $69.

I have several different Athlon II X2s, running in anything from HTPCs, home/media servers, basic workstations.  I think they are tough, well priced, and reliable CPUs.

On another note, I can play 1080p with my onboard GPU.  You could look into something like the ASUS M4A785-M, they make another version with 128mbs of sideport memory but I can't remember the model number off the top of my head.  It will also cover your SATA and Ram specs you want.  A dedicated PCIe GPU would be important if you are wanting to combine both the HTPC and server functions.
i like that board.  seems it has all of the things I want.  Also does it support the tv tuner card and better graphics card that I want.

---

### Post by djyoung4 on 2010-05-15
bump

---

### Post by djyoung4 on 2010-05-17
I got it down to alot cheaper and have pretty much finalized everything.  If you know of any known problems with my setup that I updated on the first page let me know.  thanks in advance.

---

### Post by CharlesA on 2010-05-17
Looks good.

---

### Post by djyoung4 on 2010-05-22
So I ran into a little snag.  This htpc/dvr/media server will be running in arizona on cox digital cable.  my question is are there any tv tuner cards out there that will work with cox's hdtv channels.  Im pretty sure they are encrypted and have been trying to get into contact with cox to see what I can do but most of the customer support people I talk to have no idea.  any ideas.

---

### Post by CharlesA on 2010-05-22
Generally HD channels are encrypted, so good luck with that.

I was able to get SD channels with a TV tuner card, but just shelved the idea of getting HD, since there is no way to decrypt/view them without using a cablecard of some sort and that's a royal pain in the butt to get/find.

I've been just using their HD box hooked up to the tv and 5.1 speakers and that works fine, since there is a builtin programming guide among other things included.

Unfortunately no PDR.

---

### Post by djyoung4 on 2010-05-24
> **CharlesA said:**
> Generally HD channels are encrypted, so good luck with that.

I was able to get SD channels with a TV tuner card, but just shelved the idea of getting HD, since there is no way to decrypt/view them without using a cablecard of some sort and that's a royal pain in the butt to get/find.

I've been just using their HD box hooked up to the tv and 5.1 speakers and that works fine, since there is a builtin programming guide among other things included.

Unfortunately no PDR.

maybe some good news. I read on another forum that Cox rents out video cards that will decrypt the HD feed of all channels.  Haven't been able to ask cox yet though but hopefully they do.

---

### Post by cascade9 on 2010-05-24
I'd probably get a gigabyte 870 over the MSI, they are better boards IMO. 

also, if you only have 1 stick of RAM, you will only use single channel mode- a slight performance hit. Better off with 2 x 2GB or 2 x 4GB.

---

### Post by djyoung4 on 2010-05-24
> **cascade9 said:**
> I'd probably get a gigabyte 870 over the MSI, they are better boards IMO. 

also, if you only have 1 stick of RAM, you will only use single channel mode- a slight performance hit. Better off with 2 x 2GB or 2 x 4GB.

sorry it is 2 x 2 GB.  changed it.  and I checked out the gigabyte 870 but went with the MSI because it was cheaper at the time when I bought it and have roughly the same features.

---

### Post by jetsam on 2010-05-24
The case is the biggest issue.  I suggest a Roomba.

---

### Post by djyoung4 on 2010-05-25
> **jetsam said:**
> The case is the biggest issue.  I suggest a Roomba.

like the robot vacuum one?:confused:

---

