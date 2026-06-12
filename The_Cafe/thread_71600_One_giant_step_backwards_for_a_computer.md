---
title: "One giant step backwards for a computer"
date: 2005-10-03
forum: The Cafe
---

### Post by Felipejane on 2005-10-03
I hate to confess this, but I've got to put Windows **back** on a computer. It's an old one onto which I've successfully loaded Ubuntu 5.04. It works, albeit slowly, and I'd hoped that would be good enough. 
But the person I'm giving this computer to is not adept with computers at all, and is only used to Windows. Furthermore, she's determined to use AOL as her ISP; I'm assuming that means that Linux is not an option as her operating system.
So here's the problem: even though I've set the BIOS to boot from the CD-ROM, when the Windows 98 CD (because that's what I have available to install) is in the drive and I reboot, I see that it's trying to boot from the CD, but very quickly GRUB starts the countdown to booting in Ubuntu. Is there any way I can slow down when GRUB starts, so that Windows has time to boot from the CD? 
Any suggestions, including ways to use AOL as her ISP under Linux (dial-up modem), are welcome.

---

### Post by mstlyevil on 2005-10-03
[QUOTE=Felipejane]I hate to confess this, but I've got to put Windows **back** on a computer. It's an old one onto which I've successfully loaded Ubuntu 5.04. It works, albeit slowly, and I'd hoped that would be good enough. 
But the person I'm giving this computer to is not adept with computers at all, and is only used to Windows. Furthermore, she's determined to use AOL as her ISP; I'm assuming that means that Linux is not an option as her operating system.
So here's the problem: even though I've set the BIOS to boot from the CD-ROM, when the Windows 98 CD (because that's what I have available to install) is in the drive and I reboot, I see that it's trying to boot from the CD, but very quickly GRUB starts the countdown to booting in Ubuntu. Is there any way I can slow down when GRUB starts, so that Windows has time to boot from the CD? 
Any suggestions, including ways to use AOL as her ISP under Linux (dial-up modem), are welcome.[/QUOTE]

  You need to enter the bios and chang the boot order to the cd rom before the HD. To do this usually you just press the delete key on startup and then you shoul get the bios menu.

---

### Post by poofyhairguy on 2005-10-03
Linux and AOL:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)

---

### Post by Felipejane on 2005-10-03
In answer to MstlyEvil: 

That's exactly what I did. And the machine displays a message that it's trying to boot from the CD. But before the CD is spinning up to speed, GRUB starts its countdown, and the CD never gets a chance to run.

In answer to PoofyHairyGuy:

This has potential; I'll have to look into it. Thanks.

---

### Post by codejunkie on 2005-10-03
someone correct me if im wrong but windows 98 isn't a bootable cd you have to use a windows 98 boot floppy to load the cd-rom driver, partition, and format the harddrive drive and then install windows unless it's an oem cd that the pc manufacture has customized.

---

### Post by Felipejane on 2005-10-03
[QUOTE=codejunkie]someone correct me if im wrong but windows 98 isn't a bootable cd you have to use a windows 98 boot floppy to load the cd-rom driver, partition, and format the harddrive drive and then install windows unless it's an oem cd that the pc manufacture has customized.[/QUOTE]
Hmm. I don't know if that's true or not. This is an upgrade CD, so it may have to have Win98 already on the hard disk in order to operate; that might be why it isn't working. That would explain this behavior, I guess. Thanks for that tip.

---

### Post by mike998 on 2005-10-03
Win 98 isn't bootable.
Do a google for "boot disk windows 98"
That's just the way that it is.

---

### Post by irish rebel on 2005-10-03
Firstly you cannot install win98 from a cd you need a boot floppy disk change the bios settings to boot from floppy drive then when you get the command prompt you type in fdisk [ god its been a long time] delete the non windows drives create a partition and then format , when format is complete type in D: PRESS ENTER then you should have D: type setup press enter and the joys of windows is yours my friend [ oh make sure cd is in drive]

---

### Post by codejunkie on 2005-10-03
[QUOTE=Felipejane]Hmm. I don't know if that's true or not. This is an upgrade CD, so it may have to have Win98 already on the hard disk in order to operate; that might be why it isn't working. That would explain this behavior, I guess. Thanks for that tip.[/QUOTE]
no one flame me here for using windows;)  but i have the windows 98SE upgrade cd and it's not a bootable cd-rom you have to use a floppy startup disk for all versions  of microsoft cd's even upgrades except for the newer versions of windows xp and customized oem cd's. but since you have the win98 upgrade you still have to have a copy of windows 3.1 or 95 that you have to insert for verification during the windows 98 setup. you can download a windows 98 bootfloppy from [www.bootdisk.com](www.bootdisk.com) hope this helps.

---

### Post by mstlyevil on 2005-10-03
I forgot about the boot floppy. I have been dealing with XP and Linux for so long I completely forgot about that. Dohhhhhhhhhhhhhhh

---

### Post by blastus on 2005-10-04
Even Windows 2000 Professional cannot be booted from the CD. You need 4 floppies and it can take a good 1/2 hour just to get to the installation menu. 

I've experienced the same thing with a friend's computer. I really wanted to put Linux on it but I can't get the printer to work because it's a newer printer and there are no Linux drivers. I literally spent an entire day installing Windows 2000 and installing hotfixes, updates, Zotob patch, stopping services, locking down IE, installing antivirus, antispyware, firewall, and a bunch of other stuff that generally comes with Linux etc.... The freaken Windows driver for my friend's printer was 34MB...that's not nice on dialup :mad:

---

### Post by codejunkie on 2005-10-04
[QUOTE=blastus]Even Windows 2000 Professional cannot be booted from the CD. You need 4 floppies and it can take a good 1/2 hour just to get to the installation menu. 

I've experienced the same thing with a friend's computer. I really wanted to put Linux on it but I can't get the printer to work because it's a newer printer and there are no Linux drivers. I literally spent an entire day installing Windows 2000 and installing hotfixes, updates, Zotob patch, stopping services, locking down IE, installing antivirus, antispyware, firewall, and a bunch of other stuff that generally comes with Linux etc.... The freaken Windows driver for my friend's printer was 34MB...that's not nice on dialup :mad:[/QUOTE]

I feel your pain i just had the joy of installing windowsME, ok now stop rolling around on the floor laughing at me;)  i know that a few years back linux on some hardware was a beast to get up and running, but that's changing quickly even though we don't get the driver support that microsoft does from hardware manufactures. this is the thing that gets to me i've noticed alot of these windows is easier, linux suck because it's so hard to get working, there's no mp3 support out of the box, threds showing up on the forums lately and it just make me wonder what in the heck these people are smoking because it took me almost five hours on a fast machine to get windows me installed updated virus protection etc, etc, etc. i can have a fully working and up to date ubuntu install with minimal effort in less than an hour with a few manual tweaks but i have to use that scary command line. ah enough ranting for each is own i guess i just thought id through my horror story in there.

---

### Post by Omnios on 2005-10-04
Im a pro at reformatting and reinstalling win98 Im getting pretty good at reinstalling win XP, Linux is another story that might take a couple years and lots of releases.

---

### Post by mstlyevil on 2005-10-04
Just when you think you have linux all figured out, then comes a new distro to make you look stoopid all again. (Yes I know stoopid is mispelled.

---

### Post by az on 2005-10-04
Firstly, win98 cd is bootable.  Your cdrom drive must be really realy old.  You need the floppy.  

Second, how old is this machine, and how much ram does it have?

Third, AOL:

Package: penggy (0.2.1-3) [universe]Allows you to connect to AOL via modem or TCP/IPThe project aims to be a full AOL client including all known access methods like DSL, cable, TCP/IP or modem (with the modem-emulation of linux via /dev/ttyI* ISDN, too). 

Currently, only TCP/IP and modem is supported.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=aol&searchon=all&subword=1&version=hoary&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=aol&searchon=all&subword=1&version=hoary&release=all)

---

### Post by WildTangent on 2005-10-04
[QUOTE=blastus]Even Windows 2000 Professional cannot be booted from the CD. You need 4 floppies and it can take a good 1/2 hour just to get to the installation menu.[/QUOTE]

im sorry...but thats just not correct. i install windows 2000 quite often, and it does in fact boot from CD. as does windows 98 SE.

-Wild

---

### Post by blastus on 2005-10-04
[QUOTE=WildTangent]im sorry...but thats just not correct. i install windows 2000 quite often, and it does in fact boot from CD. as does windows 98 SE.

-Wild[/QUOTE]

MY Windows 2000 Professional CD is NOT bootable, neither is MY Windows 98 original edition CD. And it's not my CD drives; I've tried them on several drives and THREE different computers all with either CD burners or CD-ROM drives manufactured within the last couple of years (2003) and one just recently manufactured in May 2005. These computers support booting from a CD and MY Windows XP CD (along with different Linux distribution CDs such as FC, Mepis, Ubuntu, Helix) boots on all of them. 

So perhaps not all Windows 2000 Professional CDs are created equal, mine is NOT bootable and that is a fact.

---

### Post by ygarl on 2005-10-04
You gotta love an operating system which doesn't let you install it unless you boot off another media! LOL

---

### Post by joker on 2005-10-04
FYI:

My win 2000 cd is bootable, but my win 98SE cd is not, It requires a boot disk.

Since you have a 98 upgrade you will either need to have a copy of win 95 or 3.1 installed.... OR... the upgrade cd only looks for the existance of one file (unfortunately I don't remember which one, google is your friend), so if you have access to an old machine or a backup from an old machine, copy the magic file to the machine which is in need of the install and viola! the upgrade cd thinks it is upgraging an existing install. The upgrade cd is actually a full install cd with that little file check added for product differenciation.

As a baseline, I have win2k on a 400 mhz celeron (256 mb ram) and it does ok, DSL (damn small linux) flies on it, but isn't exactly new user friendly, and a little limiting for your purpose.  Ubuntu was slow on this machine with the default install, but after installing XFCE it was quite useable, it provided good speed without being too limiting.

And AOL is the DEVIL!!!

---

### Post by az on 2005-10-04
Okay, it is obvious that not all Windows CDs are the same.  Some are bootable some are not.  Whatever.  Use the SBM floppy.

[QUOTE=joker]And AOL is the DEVIL!!![/QUOTE]

Why do you say that?

---

### Post by kayas80 on 2005-10-04
[QUOTE=mike998]Win 98 isn't bootable.
Do a google for "boot disk windows 98"
That's just the way that it is.[/QUOTE]

Mike 998 is correct. The Win 98 CD is not bootable!

---

### Post by mike998 on 2005-10-04
Windows 98 SE *MAY* be bootable - I don't believe I have ever tried it.

Windows 2000 is normally bootable, however as mentioned here before, sometimes you have to use four boot floppies as some drivers are required that aren't on the CD.

You have to love the fact that a pretty hard-core Linux forum will try to help a user install windows.

---

### Post by joker on 2005-10-04
[QUOTE=azz]
Quote:
Originally Posted by joker
And AOL is the DEVIL!!! 

Why do you say that?[/QUOTE]



Pet Peeves really,

I used it back in the days when you could not always dial through to their servers (busy signals), and the first thing they would present you with when you finally got through was an advertisement to sell you an autodialer for only $19.95 so you wouldn't have to continuously try to dial up to their overloaded network.  This really pissed me off.

Any provider where you have to click "no I don't want to buy xyz product" on every log on gets a black mark in my book, and as of a year ago this was still the case.

Not following web standards for rendering webpages and not allowing many to be rendered at all (mostly fixed now I underdstand)

Expensive for basic web service, and I did not think their community offered me anything I couldn't find elsewhere. ;) 

Their interface takes the computer illiterate a step backwards IMO.

No linux support (I'm taking the origional posters word for this one)

No show stoppers, and I admit my statement may have been a little strong, I just think there are much better options, and I was kinda making a joke, ever seen "The Waterboy"

---

