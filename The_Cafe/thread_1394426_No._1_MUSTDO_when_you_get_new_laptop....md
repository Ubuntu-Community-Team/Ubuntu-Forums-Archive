---
title: "No. 1 MUSTDO when you get new laptop..."
date: 2010-01-30
forum: The Cafe
---

### Post by PureRumble on 2010-01-30
[SIZE="4"]REMOVE THE WINDOWS-LOGO STICKER, ***PISS*** ON IT AND THEN ***BURN*** IT!
<(~_~)>[/SIZE]

Otherwise for those of you wondering, it's a...

[SIZE="3"]_ASUS K61IC-JX013V._[/SIZE]
[SIZE="2"]**Display**: 16" HD/LED
**CPU**: Intel Duo T6600 @ 2.2 GHz
**RAM**: 4GB DDR2
**GPU**: Geforce GT 220M, 1 GB GDDR3 (maybe GDDR2, dunno)
**HD**: 320 GiB
**Price**: approx 1000 USD (price in sweden).[/SIZE]

Kubuntu disc burned and good-to-go! Wish me luck with the install!

**[SIZE="5"]UPDATE ON INSTALLATION:[/SIZE]**

[SIZE="3"]_* Had to reshuffle partitions a bit._[/SIZE]

Didn't like the kubuntu cd's partition manager, so I burned and used gparted. But they mention a scary bug in the stable releases of gparted at [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php). I had to use a test version.... **TEST VERSION FOR PARTITIONING :-/**. Now that got me worried!

[SIZE="3"]_* Done partitioning!_[/SIZE]

Table looks as follows (320 GiB hd, all numbers approx):

  + 1 MB unallocated (first in drive... dunno, it was like that and I thought better to leave it).
  + 17 GiB recovery partition (no fan of it, but thought better leave than kill).
  + 60 GiB NTFS Windows 7 (shrunk from staggering 140 GiB).
  + 4 MB unallocated (annoying couldn't get rid of it... has to do something with ntfs).
  + 180 GiB NTFS for data storage.
  + 50 GiB EXT4 for kubuntu (under extended partition).
  + 1 GiB SWAP (extended too).

Some of you may say too much mem for ext4, but it's a pretty powerful notebook and so maybe I'll experiment with lots of apps, who knows ;-). Same goes for 60 GiB windows 7, maybe I won't be able to resist it and install ton of games :-).

[SIZE="3"]_* Kubuntu installed! :P_[/SIZE]

Only two problems that occured:

*I never got to explicitly choose what partition to use for swap* (couldn't make the choice in swap partition's property window, list was greyed out). Hope it worked out well anyway, but heck who needs swap with 4 gig ram :P

When I clicked restart button when install had finished, screen just went completely black (but still illuminated).... **REALLY SCARY!** I ejected CD and did a Alt+SysRq+RSEIUB that did the trick!

_[SIZE="3"]* GRUB up and running![/SIZE]_

I first checked if windows 7 works and so it does well! unfortunately I started doing recovery discs in windows (just in case) and it will take a while. So I haven't tested kubuntu... yet.

_[SIZE="3"]*** GAAAAH! STUPID WINDOWS!**[/SIZE]_

So I'm burning the recovery discs, right? The app hasn't even prepped the iso file to burn to the discs, and this small popup says **"waky waky clock is 3:00 am so it's time to download some windows updates and install them, and oh just so you know your system will reboot so you be sure save all data ok buddy?"**.

All of a sudden there's this race against time to find this 3:00-am-update setting and turn it off before it wastes the app that is creating the recovery discs.

_... What. Is. Wrong. With. Programmers. At. Microsoft?_

_[SIZE="3"]**:KS:KS* Kubuntu works, yay!:KS:KS**[/SIZE]_

No problems, except that I need nvidia driver v.190.53 (notebook has geforce 220m) and you can't install it via the package manager. Need to figure out how to do this.

_[SIZE="3"]* Nvidia driver's installed![/SIZE]_

nvidia driver 190 installed, yay! Just followed these instructions:
[http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html](http://www.webupd8.org/2009/08/how-to-install-nvidia-190xx-drivers-in.html)

_[SIZE="3"]* Pulseaudio was NOT installed![/SIZE]_

This is MOST weird, but can you believe that pulseaudio was not installed from start? No wonder I had no sound!

Soooo weird...

---

### Post by Psumi on 2010-01-30
How much was it?

What version of the K61IC was it?

---

### Post by hessiess on 2010-01-30
Nuke the hard drive.

---

### Post by Psumi on 2010-01-30
> **hessiess said:**
> Nuke the hard drive.

with DBAN?

---

### Post by SuperSonic4 on 2010-01-30
Hope you burnt the 64 bit Kubuntu to take advantage of that RAM :p

---

### Post by Psumi on 2010-01-30
> **SuperSonic4 said:**
> Hope you burnt the 64 bit Kubuntu to take advantage of that RAM :p

or 64 bit ubuntu, xubuntu, edubuntu, mint, crunchbang, etc.

---

### Post by Icehuck on 2010-01-30
> **PureRumble said:**
> REMOVE THE WINDOWS-LOGO STICKER, PISS ON IT AND THEN BURN IT! <(~_~)>

Otherwise for those of you wondering, it's a...

ASUS K61IC.
Display : 16" HD/LED
CPU: Intel Duo T6600 @ 2.2 GHz
RAM: 4GB DDR2
GPU: Geforce GT 220M, 1 GB GDDR3 (maybe GDDR2)

Kubuntu disc burned and good-to-go! Wish me luck with the install!

That's what you do to a sticker?  Outside is that way ----->

---

### Post by PureRumble on 2010-01-30
> **Psumi said:**
> How much was it?

What version of the K61IC was it?

Made an update to main post to include your questions.

---

### Post by 5dolla on 2010-01-30
order a ubuntu sticker!

---

### Post by PureRumble on 2010-01-30
> **hessiess said:**
> Nuke the hard drive.

Naaaaah, good to have windows around for those rare occasions when your options are limited...

... because software developers and hardware producers all around the world won't realize how superior linux is and etc, etc, etc, :-)

---

### Post by PureRumble on 2010-01-30
> **SuperSonic4 said:**
> Hope you burnt the 64 bit Kubuntu to take advantage of that RAM :p

Of course, of course! ;-)

---

### Post by PureRumble on 2010-01-30
> **5dolla said:**
> order a ubuntu sticker!

WOW! You can do that!?! Where? How!?

---

### Post by NoaHall on 2010-01-30
Right, that's it, I'm going to cry in a corner. BRB.

---

### Post by Zoot7 on 2010-01-30
Complete wipe the hard drive or replace the hard drive totally. Then re-install Windows free of crapware and add some flavour of Linux to the mix.

And surely the sticker is hardly worthy of flames and urination? :tongue:

---

### Post by Kai69 on 2010-01-30
Stickers [http://system76.com/article_info.php?articles_id=9](http://system76.com/article_info.php?articles_id=9)

---

### Post by SoFl W on 2010-01-30
The first thing I do with any new computer is before booting for the first time or doing anything I make an image file with Ghost or True Image.  *If* you end up selling it in a few years or have to return it the image file will return it to its "as new" status.

---

### Post by PureRumble on 2010-01-30
> **NoaHall said:**
> Right, that's it, I'm going to cry in a corner. BRB.

why you wanna cry? :-]

---

### Post by PureRumble on 2010-01-30
> **Zoot7 said:**
> Complete wipe the hard drive or replace the hard drive totally. Then re-install Windows free of crapware and add some flavour of Linux to the mix.

And surely the sticker is hardly worthy of flames and urination? :tongue:

didnt get a windows 7 installer disc :-[

---

### Post by dearingj on 2010-01-30
Here's what I do when I get a new computer:
First, check that it works using whatever software is included with it. Make sure that [nobody set up me the bomb]("http://en.wikipedia.org/wiki/Somebody_set_up_us_the_bomb").
Second, if it doesn't have some form of Linux on it, install Ubuntu as a dual-boot with whatever it did come with.
Third, remove the Windows sticker (assuming it came with Windows) and [BURNINATE]("http://www.urbandictionary.com/define.php?term=burninate") it!
Fourth, install [Unison]("apt:unison-gtk") and use it to retrieve my music collection from another computer.

---

### Post by PureRumble on 2010-01-30
> **Zoot7 said:**
> 
And surely the sticker is hardly worthy of flames and urination? :tongue:

Ha ha ha, fair point! :]

---

### Post by Zoot7 on 2010-01-30
> **PureRumble said:**
> didnt get a windows 7 installer disc :-[
Head over to <insert torrent/filehost site here> and download an ISO for an untouched version of the Windows 7 you have. Then use your OEM product key when re-installing it. I would imagine as long as you have the product key and if the version is truly untouced (nothing ripped out) it shouldn't matter.

---

### Post by Stan_1936 on 2010-01-30
> **PureRumble said:**
> No. 1 MUSTDO when you get new laptop..

1.  Smell it.
2.  Lick it.

#1 and #2 are interchangeable.

---

### Post by KiwiNZ on 2010-01-30
Turn it on , check hardware for warranty purposes. Begin installing own Apps etc .Keep installed OS until end of warranty period.

---

### Post by RiceMonster on 2010-01-30
1) Install Ubuntu
2) Get angry because your wireless doesn't work
3) Complain on Ubuntu forums
4) Go back to Windows.

---

### Post by Kai69 on 2010-01-30
OK buy a s/h lappy have fun digging around in the old HDD put fav linux distro on then wait for warranty to run out from other lappy NOT A CHANCE :lolflag:

---

### Post by Frak on 2010-01-30
Rip it apart, take out all the hardware I don't need, go buy a new heatsink for the CPU, and put it back together.

---

### Post by NoaHall on 2010-01-30
> **Frak said:**
> Rip it apart, take out all the hardware I don't need, go buy a new heatsink for the CPU, and put it back together.

Good idea, you'll get over 9000 battery-powered-hours then.

---

### Post by Frak on 2010-01-30
> **NoaHall said:**
> Good idea, you'll get over 9000 battery-powered-hours then.
I hear if I rip out the CPU I get even MOAR hours.

---

### Post by RiceMonster on 2010-01-30
The monitor tends to use a lot of power. I would recommend not using it while on battery power.

---

### Post by NoaHall on 2010-01-30
> **Frak said:**
> I hear if I rip out the CPU I get even MOAR hours.

Infinity, I heards. It's like there's no loss at all...

---

### Post by HomoGleek on 2010-01-30
> **RiceMonster said:**
> 1) Install Ubuntu
2) Get angry because your wireless doesn't work
3) Complain on Ubuntu forums
4) Go back to Windows.
1. Download the Ubuntu ISO
2. Send hatemail to RiceMonster
3. Burn your ISO
4. Dual boot and enjoy the best of both worlds.

---

### Post by Frak on 2010-01-30
> **DarrenTod said:**
> ...and enjoy the best of both worlds.

*ugh*

FIGHT THE URGE, FRAK, FIGHT IT!

---

### Post by SuperSonic4 on 2010-01-30
> **Psumi said:**
> or 64 bit ubuntu, xubuntu, edubuntu, mint, crunchbang, etc.

Indeed, the OP said they'd downloaded kubuntu :KS

---

### Post by PureRumble on 2010-01-30
> **Zoot7 said:**
> Head over to <insert torrent/filehost site here> and download an ISO for an untouched version of the Windows 7 you have. Then use your OEM product key when re-installing it. I would imagine as long as you have the product key and if the version is truly untouced (nothing ripped out) it shouldn't matter.

I think it does matter for them... those bastards will bite you wherever they can in the EULA. :-[

---

### Post by PureRumble on 2010-01-30
> **RiceMonster said:**
> 1) Install Ubuntu
2) Get angry because your wireless doesn't work
3) Complain on Ubuntu forums
4) Go back to Windows.

Noooo! Never! ;P

---

### Post by PureRumble on 2010-01-30
> **Frak said:**
> Rip it apart, take out all the hardware I don't need, go buy a new heatsink for the CPU, and put it back together.

Ha Ha Ha Ha.

Seriously you're joking right?

---

### Post by CharlesA on 2010-01-30
> **KiwiNZ said:**
> Turn it on , check hardware for warranty purposes. Begin installing own Apps etc .Keep installed OS until end of warranty period.

This.

> **RiceMonster said:**
> 1) Install Ubuntu
2) Get angry because your wireless doesn't work
3) Complain on Ubuntu forums
4) Go back to Windows.

That too. Makes me glad I was able to get my hands on an Alfa wireless b/g/n adapter and get it working after much fiddling.

The first thing I do with a new PC is image it with Clonezilla then proceed to clean all the garbage off it.

---

### Post by Frak on 2010-01-30
> **PureRumble said:**
> Ha Ha Ha Ha.

Seriously you're joking right?
Gem from the Arch Forums: [http://bbs.archlinux.org/viewtopic.php?pid=628732#p628732](http://bbs.archlinux.org/viewtopic.php?pid=628732#p628732)

---

### Post by squilookle on 2010-01-30
My 5 year old Toshiba laptop still has the "Designed for Microsoft Windows XP" sticker on it. 

Doesn't matter, I know what OS I have on there.

---

### Post by Kai69 on 2010-01-30
Windows users need the sticker on there so the know which version of viruses they are using:lolflag:

---

### Post by HomoGleek on 2010-01-30
wrong thread .. sorry ... delete?

---

### Post by PureRumble on 2010-01-30
> **kai69 said:**
> windows users need the sticker on there so the know which version of viruses they are using:lolflag:

lol!

---

### Post by PureRumble on 2010-01-30
> **Frak said:**
> Gem from the Arch Forums: [http://bbs.archlinux.org/viewtopic.php?pid=628732#p628732](http://bbs.archlinux.org/viewtopic.php?pid=628732#p628732)

No, no you're not kidding...

---

### Post by Frak on 2010-01-30
> **PureRumble said:**
> No, no you're not kidding...
Don't do everything you read off of the internet. It may cause you to void a very expensive warranty.

---

### Post by PureRumble on 2010-01-30
> **Frak said:**
> Don't do everything you read off of the internet. It may cause you to void a very expensive warranty.

Kidding now, arent ya? I barely dare to burn a gparted cd and reshuffle some partitions... need to gather all courage! :) So I would never open up my laptop!

---

### Post by dolphinaura on 2010-01-30
> **PureRumble said:**
> didnt get a windows 7 installer disc :-[

they dont give those out anymore.
instead, you have to make your own recovery dvds.... :(

---

### Post by Kai69 on 2010-01-30
If its a new lappy theres normaly a shortcut or something saying recovery centre or such click on it and it will ask you if you want to burn recovery dvds normaly 2 one for the os and one for the drivers. I brought a new lappy for the kids at xmas 1st thing i did...

---

### Post by dolphinaura on 2010-01-30
> **dearingj said:**
> Here's what I do when I get a new computer:
First, check that it works using whatever software is included with it. **Make sure that [nobody set up me the bomb]("http://en.wikipedia.org/wiki/Somebody_set_up_us_the_bomb").**
Second, if it doesn't have some form of Linux on it, install Ubuntu as a dual-boot with whatever it did come with.
Third, remove the Windows sticker (assuming it came with Windows) and [BURNINATE]("http://www.urbandictionary.com/define.php?term=burninate") it!
Fourth, install [Unison]("apt:unison-gtk") and use it to retrieve my music collection from another computer.

Ive had a dell laptop with that problem. mcafee was installed by default... and since windows 7/vista had indexing functions, mcafee scanned the indexing process again.... and again.... and in that process it used up all of the 4GB ram on my computer. Which instantly caused it to BSOD again... and again.... until I booted up in safe mode and wiped it off the hard drive.....

---

### Post by dolphinaura on 2010-01-30
> **Frak said:**
> Don't do everything you read off of the internet. It may cause you to void a very expensive warranty.

> **PureRumble said:**
> Kidding now, arent ya? I barely dare to burn a gparted cd and reshuffle some partitions... need to gather all courage! :) So I would never open up my laptop!

I did crack open my laptop.... and dell didnt care at all about it when i returned it for a new A/C adaptor socket even though I had replaced the graphics card.... :D

They didnt even care I had mac osx installed on it. (I forgot to remove it....)

and yes, although you shouldn't try it, the graphics card is replacable on some laptops if you know how to take apart laptops without destroying them.... + lots of soldering experience.,..

besides, i wasnt expecting much from the laptop anyways... it was my old pentium M that I thought had died... (no, it wasnt, the powercord blew a fuse, which i replaced)

---

### Post by PureRumble on 2010-01-30
> **dolphinaura said:**
> they dont give those out anymore.
instead, you have to make your own recovery dvds.... :(

I just did mine... dunno if they will be of any use, not that I trust them really. ;)

---

### Post by dolphinaura on 2010-01-30
> **PureRumble said:**
> I just did mine... dunno if they will be of any use, not that I trust them really. ;)

p.s. ive found these DVDs an annoyance sometimes.... because they HAVE TO take over your entire hard drive. you CANNOT select which partition to install it in, because it installs by deleting the partition tables, then repartitioning the whole disk.

which means... each time windows goes kaput.... and repair doesnt work.... i have to backup all my data on mac osx and ubuntu before using the dvd....

---

### Post by Kai69 on 2010-01-31
I know what you mean but the point of the recovery dvds is if you mess up the lappy or you have to return it for warranty you can at least put the lappy back to how it was when you first got it, So have fun ..

---

### Post by Roasted on 2010-01-31
> **PureRumble said:**
> Naaaaah, good to have windows around for those rare occasions when your options are limited...

... because software developers and hardware producers all around the world won't realize how superior linux is and etc, etc, etc, :-)

I have XP and Ubuntu 9.10 on my work laptop for that exact reason. Oddly enough, I work in a Windows environment, so you'd think I'd have to bounce to Windows quite often. But to put that precious little cherry on top, guess how long it's been since I booted to my XP partition?

April 2009.

Win.

> **Kai69 said:**
> I know what you mean but the point of the recovery dvds is if you mess up the lappy or you have to return it for warranty you can at least put the lappy back to how it was when you first got it, So have fun ..

I developed a habit. Every time I buy a new computer, just to avoid any BS if I have to take it back, I always use Clonezilla to take a snapshot of the install. I don't deal with recovery DVDs anymore or anything like that. I just make my own backup image and keep it stored on my file server or external hard drive somewhere.

---

### Post by RabbitWho on 2010-01-31
> **PureRumble said:**
> Naaaaah, good to have windows around for those rare occasions when your options are limited...

... because software developers and hardware producers all around the world won't realize how superior linux is and etc, etc, etc, :-)

Isn't it a little hypocritical to take the sticker off and violate it when you still admit you rely on and need windows for some things? 

You just want people to think you're cool.

---

### Post by PureRumble on 2010-01-31
> **dolphinaura said:**
> p.s. ive found these DVDs an annoyance sometimes.... because they HAVE TO take over your entire hard drive. you CANNOT select which partition to install it in, because it installs by deleting the partition tables, then repartitioning the whole disk.

which means... each time windows goes kaput.... and repair doesnt work.... i have to backup all my data on mac osx and ubuntu before using the dvd....

Hugha! Maybe my discs will do that too? If they also reset the data partition (ntfs) that was in the notebook per default, well then you loose pretty much everything :-/.

Thx for the heads up.

---

### Post by PureRumble on 2010-01-31
> **Roasted said:**
> I have XP and Ubuntu 9.10 on my work laptop for that exact reason. Oddly enough, I work in a Windows environment, so you'd think I'd have to bounce to Windows quite often. But to put that precious little cherry on top, guess how long it's been since I booted to my XP partition?

April 2009.

Win.



I developed a habit. Every time I buy a new computer, just to avoid any BS if I have to take it back, I always use Clonezilla to take a snapshot of the install. I don't deal with recovery DVDs anymore or anything like that. I just make my own backup image and keep it stored on my file server or external hard drive somewhere.

I hadn't started my windows for over six months too before new year.

But this job I wanna get, microsoft sql certificate is mandatory... and so I was forced to install the darn thing to dig through the book.

Another thing that sometimes comes up is checking how my webdevelopment efforts look in ie6-8 (for they dont properly follow css, xhtml, javascript...), and so I need to visit my windows partition on those rare occasions.

But yeah using windows is turning into a rare treat for me too. :-D

---

### Post by Kai69 on 2010-01-31
Your right there the disks are only for putting the pc back to how it was when brought, As for losing data I use an external HDD and do backups to the ext HDD. So if the lappy does go nutty I can do a full install and just use the backup to put the data back on .

---

### Post by MichealH on 2010-01-31
> **PureRumble said:**
> Kidding now, arent ya? I barely dare to burn a gparted cd and reshuffle some partitions... need to gather all courage! :) So I would never open up my laptop!

My Warrenty Ran out In October... RIP Out my Stupid SIS Card and Get Intel! Only... Im 12 I dont have the money and I dont have the skills :(

> **dolphinaura said:**
> I did crack open my laptop.... and dell didnt care at all about it when i returned it for a new A/C adaptor socket even though I had replaced the graphics card.... :D

They didnt even care I had mac osx installed on it. (I forgot to remove it....)

and yes, although you shouldn't try it, the graphics card is replacable on some laptops if you know how to take apart laptops without destroying them.... + lots of soldering experience.,..

besides, i wasnt expecting much from the laptop anyways... it was my old pentium M that I thought had died... (no, it wasnt, the powercord blew a fuse, which i replaced)

As I said Above My SiS Card Is a pain when I redo Ubuntu and Im stuck in the 9.04 xorg.conf days :D

> **Kai69 said:**
> Your right there the disks are only for putting the pc back to how it was when brought, As for losing data I use an external HDD and do backups to the ext HDD. So if the lappy does go nutty I can do a full install and just use the backup to put the data back on .

I would do backups just My dad (Cos im 12) tells me backups are a waste of time. [I will secretly backup and when he goes oh s*** I lost everything.... You can Guess ;)

---

### Post by Kai69 on 2010-01-31
Hi micheal when something goes wrong your dad will wish he did have a backup. I normaly do one once a month and every 2 months I delete the oldest backup saves space on my ext HDD :D

---

### Post by Roasted on 2010-01-31
> **MichealH said:**
> 

I would do backups just My dad (Cos im 12) tells me backups are a waste of time. [I will secretly backup and when he goes oh s*** I lost everything.... You can Guess ;)

Then I suppose it's a waste of time for your dad's bank to do backups of their data too, huh? I'm sure daddy wouldn't like to wake up one day to find out the bank lost any and all records of balances in his savings account, therefore leaving him with 0 dollars.

---

### Post by JDShu on 2010-01-31
I still have my Windows Vista sticker. Maybe I can sell it for a lot of money in the future.

---

### Post by PureRumble on 2010-01-31
> **MichealH said:**
> I would do backups just My dad (Cos im 12) tells me backups are a waste of time. [I will secretly backup and when he goes oh s*** I lost everything.... You can Guess ;)

Micheal now I want you to be a good kid and listen to your-- no scratch that I want you to teach your dad to listen to YOU! ;-)

---

### Post by dolphinaura on 2010-01-31
> **purerumble said:**
> micheal now i want you to be a good kid and listen to your-- no scratch that i want you to teach your dad to listen to you! ;-)

+1

---

### Post by Leppie on 2010-02-01
why would you want to insist on making backups for someone who doesn't want backups??? :lolflag:

---

### Post by Psumi on 2010-02-01
What I'd do?

make recovery disks. Because I plan to put linux on it. If it don't work, I need to put windows back on.

---

### Post by Leppie on 2010-02-01
> **Psumi said:**
> What I'd do?

make recovery disks. Because I plan to put linux on it. If it don't work, I need to put windows back on.
why would linux not work?

---

### Post by Psumi on 2010-02-01
> **Leppie said:**
> why would linux not work?

A> Wireless drivers not available.
B> Sound may be borked. (IE: speakers may work, but not headphones.)
C> ????
D> Video Card Doesn't do 3D on Linux, but does on windows (Not a deal-breaker. I had two video cards that had this issue, but I didn't care.)
E> Fn Key may not work.

---

### Post by Leppie on 2010-02-01
> **Psumi said:**
> A> Wireless drivers not available.
B> Sound may be borked. (IE: speakers may work, but not headphones.)
C> ????
D> Video Card Doesn't do 3D on Linux, but does on windows (Not a deal-breaker. I had two video cards that had this issue, but I didn't care.)
E> Fn Key may not work.
F> can't watch porn?

---

### Post by CharlesA on 2010-02-01
> **Leppie said:**
> F> can't watch porn?

Cuz Linux is for porn watching. Mmmk.

Easiest thing to do is the clone the drive before you do anything with it, that way, if you need to send it in for repair, you won't have to worry about losing any data or having them void yer warranty due to not having the original OS on it.

That and you know they will restore it to the factory image anyway.

---

### Post by MelDJ on 2010-02-01
1.reinstall windows to remove all the software which is preinstalled. 
2. Reinstall graphic card to play games
3. install ubuntu 
4. install ati driver for compiz
5. update ubuntu and install songbird

---

### Post by Leppie on 2010-02-01
> **CharlesA said:**
> Cuz Linux is for porn watching. Mmmk.
did i write that?

---

### Post by Giant Speck on 2010-02-01
1.  Reinstall Windows to get a clean, junkware-less installation.
2.  Install desired basic Windows software (Firefox, iTunes, Pidgin, etc.)
3.  Burn .iso of latest Ubuntu release and install as dual boot.

---

### Post by Kai69 on 2010-02-01
Giantspeck 

Your step no1 can you please change it to read Reinstall windows to put all the crapware back on that will need 2hours to get rid of again, To have a junkfree install  ;)

---

### Post by Giant Speck on 2010-02-01
> **Kai69 said:**
> Giantspeck 

Your step no1 can you please change it to read Reinstall windows to put all the crapware back on that will need 2hours to get rid of again, To have a junkfree install  ;)

No.

---

### Post by clanky on 2010-02-01
> **CharlesA said:**
> Cuz Linux is for porn watching. Mmmk.

Only if you like your porn without sound!

---

### Post by Leppie on 2010-02-01
> **clanky said:**
> Only if you like your porn without sound!
lol

---

### Post by Capt. Blackwood on 2010-02-01
> **clanky said:**
> Only if you like your porn without sound!


I watch with sound bro. 


UBU 9.10 KK PAE

---

### Post by PureRumble on 2010-02-01
> **Psumi said:**
> A> Wireless drivers not available.
B> Sound may be borked. (IE: speakers may work, but not headphones.)
C> ????
D> Video Card Doesn't do 3D on Linux, but does on windows (Not a deal-breaker. I had two video cards that had this issue, but I didn't care.)
E> Fn Key may not work.

In my experience I'm most familiar with C> ;-)

No seriously, you just like go "what the h*ll happened?" :-D

---

### Post by Frak on 2010-02-01
> **Kai69 said:**
> Giantspeck 

Your step no1 can you please change it to read Reinstall windows to put all the crapware back on that will need 2hours to get rid of again, To have a junkfree install  ;)

> **Giant Speck said:**
> No.

Agreed.

---

### Post by Kai69 on 2010-02-01
Frak you numbnut I know you like windows definition of crapware == norton antivirus 10 day trial , Web Cam app 5sec trial AOL FREE for (but we need card details ) etc etc etc...
I WAS NOT DISSING WINDOWS OK 
I have no problem with the OS its the CEO I have a problem with or are you his best mate as well.:lolflag:<<< That means JOKE .....

---

### Post by Frak on 2010-02-01
> **Kai69 said:**
> Frak you numbnut I know you like windows definition of crapware == norton antivirus 10 day trial , Web Cam app 5sec trial AOL FREE for (but we need card details ) etc etc etc...
I WAS NOT DISSING WINDOWS OK 
I have no problem with the OS its the CEO I have a problem with or are you his best mate as well.:lolflag:<<< That means JOKE .....

[IMG]http://i46.tinypic.com/2qaivxg.jpg[/IMG] <--- That means I REALLY DIDN'T SEE WHAT YOU DID THERE

---

### Post by NoaHall on 2010-02-01
> **Kai69 said:**
> Frak you numbnut I know you like windows definition of crapware == norton antivirus 10 day trial , Web Cam app 5sec trial AOL FREE for (but we need card details ) etc etc etc...
I WAS NOT DISSING WINDOWS OK 
I have no problem with the OS its the CEO I have a problem with or are you his best mate as well.:lolflag:<<< That means JOKE .....

Ughhhhhhhh..................... This might sound retro, but "take a chill pill man", as it were.

---

### Post by Kai69 on 2010-02-01
:lolflag:Well chilled man

---

### Post by MichealH on 2010-02-01
But you know He has a Server at work So I dont know how Backups are useless ! My Rule is:

[SIZE=4]No matter How little data you have still backup![/SIZE]

Simples :)

---

### Post by warfacegod on 2010-02-01
> **MichealH said:**
> But you know He has a Server at work So I dont know how Backups are useless ! My Rule is:

[SIZE=4]No matter How little data you have still backup![/SIZE]

Simples :)

What if it's only one file?

---

### Post by Kai69 on 2010-02-01
Simples[ATTACH]145666[/ATTACH]

---

### Post by MichealH on 2010-02-01
> **warfacegod said:**
> What if it's only one file?

One problem, You cant have Just 1 file unless you want a computer with no OS!!! (Quite Unusable)

---

### Post by warfacegod on 2010-02-01
> **MichealH said:**
> One problem, You cant have Just 1 file unless you want a computer with no OS!!! (Quite Unusable)

Utterly beside the point.:p

---

### Post by MichealH on 2010-02-01
> **warfacegod said:**
> Utterly beside the point.:p

But still I'm the only one in the house who has attempted Linux and stool with it and if you're like me and is talented at computers I would make sure I do the best for my son to get a good job but sometimes my dad tells me to get back onto windows and tries to wean me off Linux or atleast that's what I think!

Sorry if this never made any sence :lolflag:

---

### Post by Kai69 on 2010-02-01
Hi Michealh Have you got your own pc or are you using the family pc ??
If its a family pc I sugest you get an external HDD put linux on that and all your other stuff change the boot menu to boot from USB 1st HDD 2nd that way the windows os is the only thing on the pc until you need it just plug your hdd in boot your in linux .. 

Im looking at putting edubuntu on my lappy for my kids at the weekend...

---

### Post by Simon17 on 2010-02-01
> **RiceMonster said:**
> 1) Install Ubuntu
2) Get angry because your wireless doesn't work
3) Complain on Ubuntu forums
**3.5) Get told off, called a noob.**
4) Go back to Windows.

.

---

### Post by fromthehill on 2010-02-01
1. use ubuntu livecd to see if everything works
2. wipe windows
3. create a 100GB partition with a clean windows vista(the win7 bootpartition is a pain in the ***).
4. install arch linux.
5. create windows xp, vista, 7 and ubuntu virtualbox machines

---

### Post by warfacegod on 2010-02-01
> **MichealH said:**
> But still I'm the only one in the house who has attempted Linux and stool with it and if you're like me and is talented at computers I would make sure I do the best for my son to get a good job but sometimes my dad tells me to get back onto windows and tries to wean me off Linux or atleast that's what I think!

Sorry if this never made any sence :lolflag:

There is no Windows in my house. My kids use Ubuntu, I do (obviously) and I didn't give my wife a choice. I backed up her files and put Ubuntu 8.04 over Windows, on her desktop. My girls (5 & 7) use Windows XP in their schools "Computer Lab". They come home and tell me that they hate it because they only get 10 minutes to play on it because it takes so long to turn on and run the games.

---

### Post by chucky chuckaluck on 2010-02-01
> **PureRumble said:**
> [SIZE="4"]REMOVE THE WINDOWS-LOGO STICKER, ***PISS*** ON IT AND THEN ***BURN*** IT!
<(~_~)>[/SIZE]

i don't mean to be a killjoy, but won't peeing on it, first, make it hard to light?

---

### Post by warfacegod on 2010-02-01
PM me asking for ways to break it.

---

### Post by raymondh on 2010-02-01
LOL .... I, as well, remove the stickers first. From thereon ... whatever catches my fancy.

---

### Post by Kai69 on 2010-02-01
Been there not saying it...:lolflag:

---

### Post by CharlesA on 2010-02-01
> **MichealH said:**
> One problem, You cant have Just 1 file unless you want a computer with no OS!!! (Quite Unusable)

Usually you should only back up yer data, not the OS. That's what cloning software is for. ;)

---

### Post by MasterNetra on 2010-02-01
*Replying to post 1*

Just a thought, could of gotten a better laptop from system76 with Ubuntu (64-bit) Pre-installed for a lower price. ( [http://system76.com/product_info.php?cPath=28&products_id=76](http://system76.com/product_info.php?cPath=28&products_id=76) ). Perhaps next time. ;)

---

### Post by MichealH on 2010-02-02
Yes I have my own pc just it has a sis card upgraDed to karmic last night and i dual boot all the others in the house have a computer

---

### Post by Malakai on 2010-02-02
Wipe the default OS loaded with its trialware and crappy software and replace it with a clean windows 7 or Linux (or both) install.

I feel so sorry for people that take their lappys/desktops home from the store and think that cluttered bogged down junk OS is what computing is supposed to be like. When people use my machine, with either win or linux, its like wow how do you make it so fast! Especially when they hear its AMD and ask "but isnt amd a crappy knock off of intelz?"

---

### Post by toupeiro on 2010-02-02
Remove anything sticky, other than a serial number, and change the power setting mode in whatever OS I decide to run to stay running with the lid closed.

---

