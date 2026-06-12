---
title: "acer recovery disc not working"
date: 2008-01-07
forum: Windows
---

### Post by ncatbs on 2008-01-07
Be gentle, am a complete newbie.  I have an Acer laptop (Aspire 3623, 1.5 ghz Celeron, 1 gig ram).  Was running XP, decided to try Ubuntu.  Made back ups of  everything important and did a complete install of Ubuntu.  I now however would like to have XP and Ubuntu as I need XP for certain things.  My laptop did not come with a XP disc, I had to burn my own recovery discs ( four cds).  I have now tried to reinstall XP using the recovery discs with no luck, I get to a screen that informs me it will restore back to factory default, when I put the second cd in it tells me there is no device.  I have booted using the live cd, then used Gparted to make a partition which I then formatted to FAT32, same story, tried formatting to NTFS and same story again. I realise that I could have originally done a dual boot system but it is too late for that now.  Any suggestions as to how I should proceed?  If need be I can get hold of the XP discs from my old laptop which was a Fujitsu Siemens though not sure they would work as they are quite old ie only has SP1 and obviously are not from the same manufacturer

Edit: When I insert disc1 it tells me 'loading RAMDISK image', I then have the choice of language and then 'restore factory default system'.  It then asks for disc2, after inserting the disc I get 'device does not exist' and the only option is to click 'OK' after which a small window pops up 'Cannot find preload.tag for SetBootIni', again the only option is to click 'OK' at which point it asks for disc1 and the whole process repeats itself.  I have now used Gparted have unformatted a 45gig partition.

---

### Post by Jhongy on 2008-01-07
Perhaps your laptop had a "hidden" partition on it which stored the OS files, and your recovery CD is looking for that? 

First step would be to fire up GParted and see if that old partition still exists. If it does, some amount of fiddling may make things work. If not, then it looks like those WinXP discs from your other computer are your best option.


Alternatively, if there are any specific problems that you are facing in Linux, or specific software that you think you need Windows for, perhaps we can help you overcome that? :-)

---

### Post by ncatbs on 2008-01-07
Thanks for the reply.  Am pretty sure that there was a hidden partition, alas it is no more I fear.  

I do like Ubuntu, it works great at home but trying to get the wireless to work at my girlfriends place took a long time and browsing is very slow.  Will try and configure the network there again to see if it would solve the problem.  I have a creative mp3 player and also a creative webcam that I would like to use, admittedly I have not delved very deeply into this.  I am also not sure as to how Ubuntu will work with REW, software for acoustic measurements.

Ideally I want both XP and Ubuntu.  Here is a screenshot from Gparted.

edit: the partition was not hidden when I tried to use the recovery discs, I changed it to hidden to see if it would make a difference.

[ATTACH]55576[/ATTACH]

---

### Post by ncatbs on 2008-01-08
*bump*

Any ideas?  I have now contacted Acer to see what they suggest I do, though I would like to solve this problem myself.  I sold my previous laptop to my boss and gave him all the relevant documents and discs but he cannot find them and so I cannot yet try and install XP from the discs.

Will have to just wait and see.

---

### Post by caravel on 2008-01-08
It looks like you've wiped out the recovery partition when you installed Ubuntu.  You now have two primary partitions one of FAT32 and the other ext3 and one in the extended partition which is just swap space by the looks of it.  If the recovery discs rely on the recovery partition somehow then you're out of luck with those.  You'll need to use the licence key on the sticker on your case with an XP disc and reinstall. (note: XP Home and Professional keys are different).

---

### Post by ncatbs on 2008-01-08
Thanks for the reply, pretty much what I feared.  Hopefully will be able to get hold of a XP installation disc, tried everyone at work and most have computers but know less about them than I do.  May try the store where I bought the laptop to see if they will let me use a disc, no harm in trying I suppose!

---

### Post by caravel on 2008-01-08
The way I see it is if you have the licence sticker on your PC then you pretty much have the right to a Disc to get it reinstalled on your PC.  Borrow someones XP disc and make a "backup copy" if you must, you're not exactly breaking the law as the thing is licenced.  As I said before make sure that if your licence is for Home, that you get a home CD and not a Pro one, or vice versa.

---

### Post by ncatbs on 2008-01-08
Yes I have a licence sticker on the underside of my laptop, pretty sure it is legal to use someone elses disc as I have already paid for XP Home when purchasing the laptop.  Not too sure will everything work after installing as I will probably need drivers etc.  Did read somewhere that somebody had success using the XP installation disc and then using the recovery discs.  As I understand it the installation disc should format the hd and then the recovery discs should contain all the other stuff required.  Will cross that bridge though when I come to it.

For now I have time to get used to Ubuntu which is not a bad thing!  Need to spend some time getting acquainted with it and will definitely do a dual boot system paying a bit more attention when installing Ubuntu second time around.

---

### Post by caravel on 2008-01-08
> **ncatbs said:**
> As I understand it the installation disc should format the hd and then the recovery discs should contain all the other stuff required.  Will cross that bridge though when I come to it.

You will usually find that there's not much on the recovery disks except junk that didn't need to be installed in the first place.

:lolflag:

---

### Post by PriceChild on 2008-01-08
> **caravel said:**
> You will usually find that there's not much on the recovery disks except junk that didn't need to be installed in the first place.

:lolflag:Agreed whole-heartedly.

If you have a "genuine windows" sticker on your laptop, use that key to install a completely fresh version of the windows version it is intended for. (the sticker says home or premium)

You can find all the required drivers from global.acer.com and Windows Update.

You may need to re-activate windows over the phone, (at least what I had to do with vista in an identical acer incident) but things should go smoothly. Just be sure to tell the truth on the phone, ie "purchased laptop with windows, have now reinstalled".

Pricey

---

### Post by ncatbs on 2008-01-08
Thanks for the replies!  Just got off the phone with Acer's tech support.  I explained the situation as best I could and the woman told me that they will be able to send me installation discs, great I thought until she said that they will charge me 30 euros and take two weeks to receive them.  I then asked about the possibility of using a friends installation disc and using my product key, according to her the installation disc would have to be from the same model to work, which I found a bit strange.  I did explain to her that I am not trying to use an illegal copy, only want to reinstall XP Home which I have already paid for.  She then said that XP would install ok but I would be missing the hidden partition and my recovery discs would be useless, also mentioned that I would not get any of the 'free included' software, a loss that I can handle.

Assuming I get the installation discs how should I proceed?  Should probably download any drivers and utilities and burn them to a disc, then install XP?  Will do some searching but any pointers much appreciated.

---

### Post by erfahren on 2008-01-08
> **caravel said:**
> You will usually find that there's not much on the recovery disks except junk that didn't need to be installed in the first place.

that's true but there's also all the drivers needed for the laptop 

Acer support isn't great, especially if it's out of warrenty. 

I did come across this site awhile back which sells recovery CDs - the site itself really sucks (as far as the design) - but you could see what they charge and stuff. There might be others like it.
[http://www.gennersales.co.uk/recovery/acerlaptops.htm](http://www.gennersales.co.uk/recovery/acerlaptops.htm)

I agree that you should be able to use just any WinXP disk- but I'm not sure how that would work with the Windows Genuine Advantage - you'd probably have to set it up  manually to verify it for updates.

The drivers would be an issue as well. You should be able to get all the basic ones you need from the Acer site but your notebook would be barely functional untill you install them. You'd definitely need a mouse hooked up.

All that would be time consuming and a pain - if you ever had to reinstall Windows again you'd have to go through all of it again. (unless you created your own OEM disk, but that's something for [another forum](http://www.msfn.org/board/nLite-f89.html) !)


good luck!

---

### Post by PriceChild on 2008-01-08
You do *NOT* need windows xp cds "for your model". Any old xp install cd will work.

How do you connect to the internet? If by an ethernet connection then I'm willing to bet it will work and you can find the drivers much  more easily once xp is installed. If its by wireless you may want to find the drivers for the wireless card and transfer them to the machine via a usb key.

I don't know about you, but most of the stuff installed on windows from manufacturers is utter rubbish. Whenever I install things I'm always careful to install only the driver, and not the "helper applications" or "toolbars". Webcams being a prime example here - I want msn messenger to see the webcam, I don't need your software to take low quality photos or videos or add effects.

---

### Post by ncatbs on 2008-01-08
I use a wireless connection from a router/modem though it is no problem to turn the wireless function off and just connect the cable and use the ethernet connection.  Will wait till I get hold of a disc, hopefully somebody that I work with will find their discs!

---

### Post by kvonb on 2008-01-08
-

---

### Post by erfahren on 2008-01-08
I just checked that site that I linked to earlier and apparently Microsoft will no longer allow them to sell duplicates of recovery CDs (it figures!).

Anyway, I do agree with PriceChild (somewhat) but I usually had better luck with the drivers that are on the manufacturer's site than what Windows update offers.

I'd go about it this way: go to [acer's support site - drivers & downloads](http://www.acerpanam.com/flex/acerdrivers/bin/drivers.html?CFID=6250082&CFTOKEN=66469233) (that link is for the US - you may want to change that), get the following and burn to CD

(also install in order given - it's not *too* critical, but the Chipset should be first))
the chipset INF
the VGA driver
the Audio diver
the Touchpad driver
the LAN driver
the modem driver
the Wifi driver

if you've never went through installing drivers - some will take you through a setup and installation (just like a program), but some will just extract somewhere first.

for the second type - just extract them and use the Windows Device Manager to update the driver - just take the "manually locate the driver" (or however they put it) option in the Wizard and browse to where the driver was extracted. 

(This all brings back memories!) the other thing I just remembered is that Windows may not even initially recognize some of the hardware (the wifi card for instance), so a driver needs to be loaded for it for Windows to be able to even recognize it. - so it'll be a good idea to have the drivers ahead of time.
_

---

### Post by PriceChild on 2008-01-08
kvonb I think we are getting mixed up with whether we are referring to "backup cds" or windows cds.

Yes "backup cds" are designed to operate only on the laptop model they were made from. You should definitely not attempt to bypass this.

Fresh, genuine Windows XP cds however should always work with any pc and the serial on the sticker will also.

---

### Post by kvonb on 2008-01-08
-

---

### Post by caravel on 2008-01-08
It looks like they're sending you the backup CDs again, but I thought that you already had those and had established that they didn't work without the recovery partition???

If I were you I wouldn't pay or wait, I'd just get hold of an XP Home CD from somewhere and install it using the license sticker.  Here in the UK the activation is usually by way of pressing buttons on your phone, if that fails you get transferred to an operator as has been the case most of the times when I've done it and they give you another password (be careful it's long and sometimes they read it out too fast).  Just tell them you've got a PC that windows got corrupted on, have now reinstalled and need to reactivate.  It's usually trouble free.

The drivers are the only reason you'd want the restore CDs but you may be able to get those later.  It's a good idea to get all the drivers beforehand, expecially those for networking devices and burn them onto a disc.

---

### Post by bufsabre666 on 2008-01-08
> **caravel said:**
> It looks like they're sending you the backup CDs again, but I thought that you already had those and had established that they didn't work without the recovery partition???

If I were you I wouldn't pay or wait, I'd just get hold of an XP Home CD from somewhere and install it using the license sticker.  Here in the UK the activation is usually by way of pressing buttons on your phone, if that fails you get transferred to an operator as has been the case most of the times when I've done it and they give you another password (be careful it's long and sometimes they read it out too fast).  Just tell them you've got a PC that windows got corrupted on, have now reinstalled and need to reactivate.  It's usually trouble free.

The drivers are the only reason you'd want the restore CDs but you may be able to get those later.  It's a good idea to get all the drivers beforehand, expecially those for networking devices and burn them onto a disc.

+1

tends to be my windows solution constantly, although i can say i own 2 copies of windows that ive paid for ((one mce and one home)) i use neighter of these, i just use a pre activated pirated copy, but if i need to i have proof i own it so i wouldnt worry

cheers

---

### Post by ncatbs on 2008-01-08
Been at work hence have not been following this thread.

I have my own recovery discs which do not work as the hidden partition has been erased (my own fault).  I did tell the woman I spoke to that she must not send the recovery discs, I have no need for a second set that do not work. 

 I plan to do the following, download all the drivers I can find from Acer's site that are relevant to my machine, burn them to a disc.  Will get to check out the burning feature on Ubuntu at the same time. 

 I will then try and get hold of an XP installation disc and will proceed to install.  I realise that this will wipe the hd completely and thus remove Ubuntu, no fear as I have the live cd.  I will then attempt to install the drivers off the disc I burnt, also connect to the internet and download AVG and a few other programmes, also update the version of XP.  Once I have everything up and running and have verified my copy of XP will boot the live cd and hopefully using Gparted and following instructions closely will attempt to partition and resize the hd and then install Ubuntu.  

  Now I just need to get hold of an XP installation disc, hopefully someone will bring one to work for me tomorrow and I can get started.  Thank you to everyone for their assistance so far, am sure I will be needing more in the near future.  

Took a few screenshots of my recovery discs, absolutely meaningless to me, discs 2-4 look the same, the numbers on the 'images' just progress.

[ATTACH]55746[/ATTACH]

[ATTACH]55748[/ATTACH]

[ATTACH]55749[/ATTACH]

---

### Post by PriceChild on 2008-01-08
When booting... with the cds in, hold alt+F10 on the bios screen... just humor me... reasonably sure I remember reading somewhere that would work with the recovery discs some times.

---

### Post by ncatbs on 2008-01-09
Tried the ALT+F10 several times but no luck.  Have the BIOS setup to boot from cd, D2D-enabled etc.  Will wait to get hold of the installation discs and then proceed.  Thanks for the assistance!

---

### Post by caravel on 2008-01-09
> **ncatbs said:**
>  I will then try and get hold of an XP installation disc and will proceed to install.  I realise that this will wipe the hd completely and thus remove Ubuntu, no fear as I have the live cd.  I will then attempt to install the drivers off the disc I burnt, also connect to the internet and download AVG and a few other programmes, also update the version of XP.  Once I have everything up and running and have verified my copy of XP will boot the live cd and hopefully using Gparted and following instructions closely will attempt to partition and resize the hd and then install Ubuntu. 
If you're going to reinstall everything, you may as well remove all your partitions from Gparted before starting, then just run XP setup and create an NTFS partition big enough for XP and leave the rest unallocated ready for Ubuntu.  This will give you a clean sheet.

---

### Post by ncatbs on 2008-01-09
Will do that, thanks for the tip.  I only have a 60 gig hd, how much should I leave for XP and how much for Ubuntu.  I plan on using Ubuntu for photos and pics etc, XP will only be for a few small applications and will not be using it for storage.  

OT: Kind of off topic, but should I buy an external hd how should it be formatted, ie can I leave it in one format which will then be accessible by XP and Ubuntu or should it also be split into partitions.

---

### Post by erfahren on 2008-01-09
> **ncatbs said:**
> Will do that, thanks for the tip.  I only have a 60 gig hd, how much should I leave for XP and how much for Ubuntu.  I plan on using Ubuntu for photos and pics etc, XP will only be for a few small applications and will not be using it for storage.  

OT: Kind of off topic, but should I buy an external hd how should it be formatted, ie can I leave it in one format which will then be accessible by XP and Ubuntu or should it also be split into partitions.
you really could get by on about 10GB to 12GB for WinXP

- I have a desktop with a WinXP install, it doesn't have too many programs but has about 1GB of saved data  (I use free AVG anti-virus and ZoneAlarm for security) - it takes up about 7GB 


If you formatted an external drive to FAT32 you'd be able to read/write to it from both WinXP and Linux - there is software available for Gutsy that can provide support to read/write to NTFS, but I don't know if it's installed by default or not. - NTFS takes less maintenance 
- maybe someone can provide more information on that.

---

### Post by PriceChild on 2008-01-09
Gutsy will read/write to ntfs partitions by default.

---

### Post by ncatbs on 2008-01-09
Thank you yet again for the info.  I will probably leave around 15 gig for XP just in case I need t.o make a legal back up of a dvd (that I own, just to ake it clear that I will not be making any illegal copies) and Ubuntu is not able to.  Will be purchasing a 500 gig external hd and will format it to NTFS.

I was using AVG and Zonealarm in additon to various other programmes, Spybot, Adaware etc.

---

### Post by Vince4Amy on 2008-01-09
I've found that with the Acer recovery program, it will only work if I clear all the partitions on the drive. The use the discs to restore.

---

### Post by ncatbs on 2008-01-09
> **Vince4Amy said:**
> I've found that with the Acer recovery program, it will only work if I clear all the partitions on the drive. The use the discs to restore.

Not sure that I am understanding you!  I thought that the recovery discs require the 'hidden partition' on the hd to exist in order for them to be usable, clear the hd and the recovery discs have nothing to work with?

---

