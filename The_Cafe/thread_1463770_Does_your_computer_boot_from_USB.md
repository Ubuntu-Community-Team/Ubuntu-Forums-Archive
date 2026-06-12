---
title: "Does your computer boot from USB?"
date: 2010-04-27
forum: The Cafe
---

### Post by aysiu on 2010-04-27
When I originally started my Ubuntu tutorials five years ago, downloading and burning CDs or DVDs was the way to go. It was all about optical drives. Every six months, I would burn at least one CD.

These days, I don't burn any CDs. I use UNetBootIn to "burn" .iso files to USB instead.

So right now my "burning" tutorial focuses mainly on burning CDs with a "burn" to USB as only a side note. Should it be the other way around (USB the main method and CD burning the side note)?

I'm really curious, for your computer (one you installed Ubuntu or some other Linux distro on), can you boot from USB or not? How common is the ability to boot from USB in BIOSes?

---

### Post by P4man on 2010-04-27
Id say its VERY common for the PC the be able to boot from USB. In fact, its rather exceptional to still find a PC unable to do this, I think it has been commonplace for 6-7 years now? (looking at a 7 year old laptop that boots happily from usb)

However, I think its slightly less common to find *people* able to boot their pc from usb, even if the pc can do it; ie, enter the bios and change boot settings. Often CD is set as primary boot device already as default settings, usb almost never.

---

### Post by aysiu on 2010-04-27
Well, if the computers can do it, it's just a matter of educating people on how to do it.

I'd really like to have the focus be on USB booting if people's computers can actually handle it, since it saves a blank CD, and USB 2.0 reads a lot faster than an optical drive. If you don't know what you're doing, you can get a lot of coasters trying to burn an .iso.

Also, keep in mind that at this point in time (and in the last five years at least), the vast majority of new Ubuntu users are either former Windows power users (which means they can figure out how to boot from USB) or the friends/family members of former Windows power users (which means they won't be reading my tutorials anyway).

My target audience are not total computer illiterates but people who are well-versed in Windows but new to Linux, and especially to Ubuntu.

---

### Post by switch10 on 2010-04-27
I never really messed with booting from a USB drive much until recently, when I decided to create a live USB with persistent storage.  Now all of my USB sticks have an OS on them it seems like....

---

### Post by CharlesA on 2010-04-27
All 5 of my machines can boot off of USB. Only one of them is not able to see my 16GB usb stick, but it boots fine off a 4GB one. *shrugs*

I don't really use CDs anymore.

---

### Post by SonicSteve on 2010-04-27
The only computers that can't boot from USB that I come across are usually 6+ yrs old. I have a bunch of s478 P4 machines with 533mhz FSB and they can't boot from USB, nor does ASUS provide any BIOS updates, really a BIOS update is the only thing preventing them. Which we know the manufacturers will never provide. 

Having said that they represent about 30% of my machines, the other 70% can boot from USB and I use it regularly to boot up Clonezilla to re-image them.

---

### Post by RiceMonster on 2010-04-27
Yes, both my laptop and desktop. However, I still use CDs out of habit.

---

### Post by aysiu on 2010-04-27
Only 15 responses so far, but it's looking good. If it's really true that only really old computers can't boot from USB, I think I'm going to change the focus a bit in my tutorials. I would like more responses, though.

---

### Post by gnomeuser on 2010-04-27
My netbook e.g. requires me to change the BIOS configuration everytime I want to boot from a USB drive. This is because it detects it as a harddrive and it partitions boot order into "harddrives" and the rest. Meaning you have to go in an prioritize the USB "hd" over the actual harddrive.

I don't actually remember what my Acer Aspire Revo r361 does but I am sure it suffers from pretty similar insanity.

This I think is the standard for most computers really, and it is a shame because I think there is a lot to be gained from having e.g. the ability to run Ubuntu entirely from the USB stick. Many users might want to try it out, take it around with them and still keep their existing system entirely safe. 

A LiveCD does this but it doesn't allow you to e.g. upgrade the system and actually use it.

I think if we can pull something like that off and make it basically a one click to create the USB stick for Windows users it will become much easier for them to try it and they will be more willing to do so since it is perfectly safe while allowing them a system that will grow and adapt to them.

---

### Post by MindSz on 2010-04-27
Both my laptop and work computer can boot from USB no problem. I still do it the CD way tho.

---

### Post by nmccrina on 2010-04-27
I just found out how easy it was to create a live usb stick. I followed the tutorials from [Fedora]("http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo") to put Fedora on my 2 GB usb drive, and it was very simple. If I had known that, I would have switch from CDs a long time ago (long time = ~1 year :D ).

---

### Post by 23dornot23d on 2010-04-27
I have one very old Acer Laptop ..... the Hard Drive is only 40 Gig ....
The CD drive broke on it a long time ago 
The USB connectors are the main reason that it is useable

I plug in a USB Optical Drive and a USB Terra Drive ...  which has a number of OS's
on it ....... I ticked USB only ..... but its also booting from CD ......

I have 3 computers though as I bought a newish Acer laptop to replace the old one 
and also have a desktop ....... 
but all have decent sized USB drives that they can all boot off ...... 

I usually set the OS's up from CD or DVD 
I keep the old versions handy too, as they were designed to run better on my old laptop ....

---

### Post by Doctor Mike on 2010-04-27
Funny I've just been wrestling with trying to get my hi-speed 8GB Lexar Firefly to boot from USB. Have even upgraded the bios, but now suspect that my main problem is with my ports being ver 1.1 and not 2.0. My hub and drive are 2.0 and I think backward compatibility for booting is not supported.

[off topic] Does anyone know if a USB 2.0 pci card would help... aside from obvious speed increase? [/off topic]

---

### Post by beetleman64 on 2010-04-27
I've never actually booted from USB, but I saw a part in my computer's instruction manual saying it can. So the answer to that is that it will boot from both.

---

### Post by koleoptero on 2010-04-27
> **gnomeuser said:**
> My netbook e.g. requires me to change the BIOS configuration everytime I want to boot from a USB drive. This is because it detects it as a harddrive and it partitions boot order into "harddrives" and the rest. Meaning you have to go in an prioritize the USB "hd" over the actual harddrive.

^ This.

Also it boots from external usb optical drive too. Quite good for a 5 yo laptop. I have been using a usb flash drive to check distros for about half a year now.

---

### Post by CharlesA on 2010-04-27
> **gnomeuser said:**
> My netbook e.g. requires me to change the BIOS configuration everytime I want to boot from a USB drive. This is because it detects it as a harddrive and it partitions boot order into "harddrives" and the rest. Meaning you have to go in an prioritize the USB "hd" over the actual harddrive.

I've got to do that on 3 of my 5 machines. Two with Gigabyte mobos and 1 with an Abit mobo. The Asus allows me to hit F8 to select a boot device, but the others don't.

Pain in the butt until I figured it out (and still a bit of a pain to have to set the boot order each time you want to boot off of usb).

---

### Post by P4man on 2010-04-27
Aysiu, 

one thing you may want to point out in any tutorials covering booting from usb, is that a lot of usb sticks come with U3 firmware:
[http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3)

I think all sandisk sticks come with this, and lots of others.

AFAIK, such a stick can not be made bootable for linux (I know I had problems with it) unless you [remove]("http://u3.com/support/default.aspx#CQ3") the U3 firmware with their own removal tool, and that is irreversible. There is a linux program for that floating on the web as well somewhere, but dont have a link at hand.

 U3 is really crap, but its rather wide spread, so take and make a note about it :)

---

### Post by aysiu on 2010-04-27
That's good to know. Thanks for the heads-up, P4man.

I have a Sansa Clip with no U3 (or perhaps I removed it and forget that I had?). Is it something specific to USB sticks, as opposed to MP3 players?

---

### Post by CharlesA on 2010-04-27
I think it's something that is specific to USB sticks. I removed it from all the USB sticks I have, since I find it quite useless.

---

### Post by aysiu on 2010-04-27
Odd that the UNetBootIn home page makes no mention of U3, even its FAQ.

---

### Post by P4man on 2010-04-27
Yeah, USB sticks only. It makes the stick act like both a tiny CD rom and a usb stick, the cdrom containing some autorunning soft/mal/bloatware specifically for windows. Would be no point doing that on a mp3 player. 

Thing is, its not just files on the stick you can delete,  or even a partition you can delete, its in the firmware.

---

### Post by gemmakaru on 2010-04-27
You have got me wondering now, my laptop has an sd slot, I wonder if I can boot off that?

---

### Post by aysiu on 2010-04-27
> **gemmakaru said:**
> You have got me wondering now, my laptop has an sd slot, I wonder if I can boot off that? Yes, you probably can. I can on my netbook, anyway.

---

### Post by P4man on 2010-04-27
> **aysiu said:**
> Odd that the UNetBootIn home page makes no mention of U3, even its FAQ.

Hmm.. I should drop them a line. If you google for unetbootin and u3 you will find plenty of people who suffered the same problem, like here:

*The Sandisk Cruzer USB stick apparently comes with a U3 application (it auto-runs a menu to give me options on what I want to do with the USB stick). I had to un-install the U3 application first before running unetbootin, as unetbootin does not automatically delete the U3 application. There is an uninstall.exe option when you explore the existing folders in the USB which allows you to remove the U3 application. Uninstalling the U3 application essentially turns the USB into a regular storage device. Afterwards, I was able to boot from the USB with no problems. Take away: Make sure your USB is completely clean before mounting the .iso. *
[http://wiki.geteasypeasy.com/Troubleshooting:_Installation](http://wiki.geteasypeasy.com/Troubleshooting:_Installation)

knoppix also mentions it:
[http://www.knoppix.net/wiki/Bootable_USB_Key](http://www.knoppix.net/wiki/Bootable_USB_Key)

here:
[http://ubuntuforums.org/showthread.php?t=971041](http://ubuntuforums.org/showthread.php?t=971041)

well, all over really.. :)

---

### Post by tuddy666 on 2010-04-27
I use a netbook, so no optical drive (excluding a USB optical drive, which actually counts as a USB boot, I suppose). Ergo, I voted "USB Only" because it's the most logical answer, imo.

---

### Post by Doctor Mike on 2010-04-27
> **P4man said:**
> Aysiu, 

one thing you may want to point out in any tutorials covering booting from usb, is that a lot of usb sticks come with U3 firmware:
[http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3)

I think all sandisk sticks come with this, and lots of others.

AFAIK, such a stick can not be made bootable for linux (I know I had problems with it) unless you [remove]("http://u3.com/support/default.aspx#CQ3") the U3 firmware with their own removal tool, and that is irreversible. There is a linux program for that floating on the web as well somewhere, but dont have a link at hand.

 U3 is really crap, but its rather wide spread, so take and make a note about it :)I don't believe Lexar hi-speed is on the list, but do you know if there is an issue trying to use a 1.1 ver port for booting. At this point it's my best guess for failure to boot on my system. My bios appears to have support and additional support after flashing...

For anyone interested after flashing my ami bios my usb is now seen as a rmd fdd instead of just usb fdd.

---

### Post by Paqman on 2010-04-27
Poll could do with being multi-choice. I have one machine that won't boot from USB, and a couple that will.

---

### Post by P4man on 2010-04-27
> **Doctor Mike said:**
> I don't believe Lexar hi-speed is on the list, but do you know if there is an issue trying to use a 1.1 ver port for booting. At this point it's my best guess for failure to boot on my system. My bios appears to have support and additional support after flashing...

Google tells me "Lexar highspeed" is not a USB key, but a SD card. If so, it wont have U3, and you have a different problem. As for USB 1.1. Im not sure, but I think it does support booting (assuming your bios does) But if it does, it will be painfully slow. USB 1.1 is 40x slower than 2.0.

---

### Post by speedwell68 on 2010-04-27
All 3 of my computers can boot from USB, the netbook has no option but to boot from USB.  The only time I use my CD/DVD drive these days is to watch a DVD or rip a CD for my MP3 player.  I do make an install disk for my Uncle every 6 months for his PC, he prefers to keep the install disk.  TBH he has quite a collection Ubuntu disks now, he has 7.10 to 9.10.  However IMHO disks for software installations are a thing of the past.

---

### Post by Irihapeti on 2010-04-27
I've got three computers. Two of them will boot off USB stick and SD card, but I have to choose to boot from them at the time. The other is a old Toshiba laptop that will read USBs but not boot from them.

---

### Post by PhilGil on 2010-04-27
Most newer computers will boot from a USB drive.  However, It's going to be complicated to instruct users on how to set up their computers to boot this way.  There are many different ways that the BIOS can implement USB boot functionality...

On my netbook, I hit <ESC> when the computer posts and I can select my boot device (HDD or USB drive) from a menu.

My home computer recognizes the USB device as a hard drive, so I have to go into the BIOS setup and reorder the hard drive boot priority.  In addition, the BIOS doesn't remember the setting from boot to boot (even with the USB drive inserted the whole time).

My office computer is too old to boot from a USB drive.

In addition, some computers are fussy about the type of USB drive they will boot from.

By contrast, booting from a CD "just works" on most existing machines, even elderly ones.

---

### Post by aysiu on 2010-04-27
> **PhilGil said:**
> Most newer computers will boot from a USB drive.  However, It's going to be complicated to instruct users on how to set up their computers to boot this way.  There are many different ways that the BIOS can implement USB boot functionality...

On my netbook, I hit <ESC> when the computer posts and I can select my boot device (HDD or USB drive) from a menu.

My home computer recognizes the USB device as a hard drive, so I have to go into the BIOS setup and reorder the hard drive boot priority.  In addition, the BIOS doesn't remember the setting from boot to boot (even with the USB drive inserted the whole time).

My office computer is too old to boot from a USB drive.

In addition, some computers are fussy about the type of USB drive they will boot from.

By contrast, booting from a CD "just works" on most existing machines, even elderly ones.
Well, I'm not going to leave out CD burning completely, but I may prioritize or push for USB booting.

Knowing about U3 is a big help.

To be honest, there have been computers I've had to explicitly tell to boot from CD also.

---

### Post by oldfred on 2010-04-27
Both my 3 year old desktop and 3 year old laptop boot from USB as well as CD. I did not understand in the beginning that all the BIOS selections for USB boot, foppy, CD, etc, did not include a USB hard drive. I had to select hard drive to boot from and there was a new choice to boot from my USB key.

I recently converted to just copying the ISOs to the USB and booting with grub2 from my 4GB key. I have several Ubuntu, gparted and system rescue all on one USB key.
MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)

My next USB project is a standard install with grub2 and partitions to a larger USB key.

---

### Post by Zimmer on 2010-04-27
[http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)

Might help you if you have not already seen this site...
:)
and for those really old machines
[http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

---

### Post by cariboo on 2010-04-27
Of the 8 working computers system I have 3 (Mac G3, old Compaq desktop and HP laptop) will not boot from usb while the other 5 have no problems. I've bought several Sandisk Cruizer's lately because they are inexpensive. The first thing i do is plug them in and go to Sandisk's web site and remove U3. Does anybody actually use U3?

---

### Post by PhilGil on 2010-04-27
> **aysiu said:**
> Well, I'm not going to leave out CD burning completely, but I may prioritize or push for USB booting.

Knowing about U3 is a big help.

To be honest, there have been computers I've had to explicitly tell to boot from CD also.
I think it's a good idea, just letting you know some of the "gotchas."  At least setting the device boot order works much the same way in most of the BIOSes I've encountered.

I actually boot from USB often, both for installs and for trial runs.

---

### Post by P4man on 2010-04-27
I just saw subcook posting a link in [this thread]("http://ubuntuforums.org/showthread.php?t=1463898") which might be relevant here too:
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

It apparently lets you boot usb (or cd/dvd) if you dont have bios support for it. Disclaimer: havent tried it. But looks useful!

---

### Post by aysiu on 2010-04-27
Yikes... that looks complicated! I will post that as a resource, though, in case people really don't have BIOS support for external media booting.

---

### Post by lisati on 2010-04-27
My old machine (10+ years old) won't boot from USB. It doesn't even reliably boot from CD, even though the BIOS supports it. The only CD I've managed to boot from is the Win98SE CD that came with the machine. I keep a floppy with [smart boot manager]("http://sourceforge.net/projects/btmgr/") installed around "just in case".

Haven't tried booting from SD cards on my laptop or main desktop/server yet, but both can happily boot from USB.

---

### Post by Muffinabus on 2010-04-27
My current computer can boot from USB when I thought it wouldn't be able to.  It's about 5-6 years old now, but it has an option to boot from USB HDD which will detect my flash drive and boot from it.

---

### Post by Irihapeti on 2010-04-27
I think that the old Toshiba laptop might boot from a USB stick if it was plugged into a PC card (presumably, something inserted into the Cardbus slot). However, I don't really feel motivated to spend $50-odd (NZ) to find out - at least, not right at the moment.

---

### Post by Eldera on 2010-04-27
My Computer originally booted from either an optical drive or a USB stick. I had an accident in which the computer fell about 18" from a footstool.:confused: 

The CD/DVD drive was damaged and the case was banged just enough out of alignment so that the drive could not be replaced nor could discs be inserted. 

I now use an external USB connected CD/DVD drive and the BIOS "sees" this separately from a USB stick and will boot from either, depending on how I set the boot order.

---

### Post by sudoer541 on 2010-04-27
How old does your PC have to be in order to boot from USB?

---

### Post by wilee-nilee on 2010-04-27
> **P4man said:**
> Aysiu, 

one thing you may want to point out in any tutorials covering booting from usb, is that a lot of usb sticks come with U3 firmware:
[http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3)

I think all sandisk sticks come with this, and lots of others.

AFAIK, such a stick can not be made bootable for linux (I know I had problems with it) unless you [remove]("http://u3.com/support/default.aspx#CQ3") the U3 firmware with their own removal tool, and that is irreversible. There is a linux program for that floating on the web as well somewhere, but dont have a link at hand.

 U3 is really crap, but its rather wide spread, so take and make a note about it :)

I agree with this, although I had no problems with a sandisk, if I deleted then formated the partition with gparted every time I loaded a distro. In the end I gave the USB to a friend who bought W7 with his OS loaded for a install backup, it was a hassle to use. I always delete a partition before installing on a USB thumb anyway.

I think if your computer will boot from a thumb or usb ssd device for installation it will install faster then a CD.

---

### Post by Roasted on 2010-04-28
It was recommended to me about an hour ago that instead of making LiveCDs for systems that can't boot USB, to make 1 LiveCD of "Plop" and utilize that with USB flash drives as I would on newer hardware that supports USB booting natively. Plop LiveCD basically forces the system to boot to USB. Just tested it - works VERY nicely. I doubt I'll be making LiveCD's ever again thanks to this...

---

### Post by Plumtreed on 2010-04-28
I use both USB & CD/DVD(re-writable) and find it a fairly strait forward process.

I always re-format my USBs in Windows. This may be 'unscientific' but solves the U3 problem and provides a clean USB.

I think the important issue is installing to the USB rather than creating a bootable ISO. It is also important to have things 'persistent'!

---

### Post by gnomeuser on 2010-04-28
as an aside, I recently talked my girlfriend into trying Ubuntu for some hardware testing. She didn't have a cdr lying around but she did have a 2GB USB stick.

The first problem. Even getting the ISO (we used Lucid Beta2) onto the USB stick from Windows. Windows Vista apparently doesn't just do this and the instructions were mildly put user unfriendly. I did find a somewhat easy to use application to put generic distributions on USB sticks. That worked around the issue but this definitely needs to be addressed.

Second problem. Booting to USB, her machine is 2 years old and there was no apparent way of doing this without changing the setting in the BIOS. Doing this took a lot of courage for her, it is in a different language (her primary language is Brazilian Portuguese), there is the chance of screwing something up badly. She is quite clever and if anything went wrong I could always call her and talk her through getting back on track. We will lose anyone below this level. There appears to be no good way of probing if you boot directly from a USB stick or forcing the machine to do so from the OS.

Third problem. Beta 2 at least didn't have the option to boot into safe vesa mode and since her videocard wasn't properly detected (I am sadly not aware of the specific model currently and the machine is half a world away). This meant I had to instruct her to edit the boot parameters (and even finding the correct variable here took a good 10 mins of careful googling). This is another huge share of users we lose, we are really shotting ourselves in the foot here. I would propose adding some easily understandable options to the boot menu such as "Something went wrong, I experienced only a blank screen" which would remove the technobabble and get you into a workable X. From where the first order of business should be reporting the system as non-working. On a USB setup this can be fixed using upgrades if we do it right, LiveCDs are not so lucky.

Now consider that she would be very unlikely, on general assumption and her own admission, to have been able to even get to a working desktop, the amazement that her first words returning to Windows to report back on the hardware was "wow that was easy".

We really need to do better, much better. The documentation for putting Ubuntu on a USB stick needs to improve, there needs to be a one click little Windows app that downloads the required files and puts it on the correct device. We need to have a system in place to inform the user of possible errors such as the machine not actually booting from USB and how to work around them.

I also made a few observations on user confidence.

One. Assuring the user that doing this will in no way harm the existing OS and not pestering her up front about replacing it removes a lot of fear. We should always be sure to not just mention this but to rigorously ensure that we keep that promise. We might also want to allow users on a USB stick to expand their experience, show them the full power of Ubuntu. They will understand that something "sticking out of the machine" is going to be a bit slower. The focus needs to change from getting the user to install Ubuntu to getting the user to try Ubuntu by giving it a perm. home on the USB stick. 

Two. Screenshots of every step helps. This may sound simple but it built a lot of confidence in my test subject that she could follow along on the website and see what she should expect every step of the way as confirmation that she did it right. Handling errors with screenshots is also mandatory.

---

### Post by NightwishFan on 2010-04-28
Are their any bugs installing from a live usb? I have not encountered any yet.

Also, installing is very fast, especially with the noop scheduler. Probably under 10 minutes easy.

---

### Post by P4man on 2010-04-28
Gnomeuser, good points, and I agree with your assessment overall, yet a few comments:

> **gnomeuser said:**
> 
The first problem. Even getting the ISO (we used Lucid Beta2) onto the USB stick from Windows. Windows Vista apparently doesn't just do this and the instructions were mildly put user unfriendly. I did find a somewhat easy to use application to put generic distributions on USB sticks. That worked around the issue but this definitely needs to be addressed.

unetbootin makes it rather trivial to create the stick on windows (or linux), but of course that assumes one knows about unetbootin. 

> 
Second problem. Booting to USB, her machine is 2 years old and there was no apparent way of doing this without changing the setting in the BIOS. 

I fear this is something we cant solve. At best we can provide some instructions for common computers and bioses, but I dont see a good solution for this as every manufacturer has its own bios, with different keys to access it, different configuration screens. Some have a bios boot menu others dont, and even the ones that do use different keyboard shortcuts to access it. Its a pita, but outside of our control im afraid.

BTW, the issue isnt all that different with CD/DVDs.Not all machines are configured to boot from cd, so users face the same problem.

> 
Third problem. Beta 2 at least didn't have the option to boot into safe vesa mode and since her videocard wasn't properly detected 

There is, but in its infinite wisdom, canonical decided to hide the menu and only show it if the user has the same infinite wisdom and presses a key at the correct moment (before the language selection). Canonical assumes that the tiny icon at the bottom of the screen makes a user understand that.

There is a bug report about this here:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

But im not sure what the best way is to complain about this. But this is getting a bit off topic, so Ill stop here :)

---

### Post by amitabhishek on 2010-04-28
Is there any guide/software available to make USB bootable (with img/ISO) on a XP system?

---

### Post by P4man on 2010-04-28
Only mentioned it like 5x now :)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by WannabeFantasma on 2010-04-28
It's supposed to do so, but it just doesn't work... Set bios things and everything, tried 3 USB drives, guess I'll have to dig into it further and I hope it will work soon or later!

But, I just bought 100 CD-R so :D will be using them for my main desktop
(yeah kinda waste of plastic ETC since I have couple of DVD-RW's)

---

### Post by gnomeuser on 2010-04-28
> **P4man said:**
> 
unetbootin makes it rather trivial to create the stick on windows (or linux), but of course that assumes one knows about unetbootin.


I would actually make the default Ubuntu download some kind of really slimmed down unetbootin. A tiny .exe file and have that fetch the required files, detect the USB/CD and plop in on there.

in the words of her loveliness... ISO?

> 
I fear this is something we cant solve. At best we can provide some instructions for common computers and bioses, but I dont see a good solution for this as every manufacturer has its own bios, with different keys to access it, different configuration screens. Some have a bios boot menu others dont, and even the ones that do use different keyboard shortcuts to access it. Its a pita, but outside of our control im afraid.

BTW, the issue isnt all that different with CD/DVDs.Not all machines are configured to boot from cd, so users face the same problem.


I would at least have the information either in the USB stick converter app or easily available on the webpage. I know we can't do anything about it right now but that doesn't mean we should give up.

I think most machines today will boot from a CD, with the exception strangely of my netbook and my nettop I don't think I have owned a machine that didn't default to doing that for years. Naturally since those two don't have dvd drives, one would wrongly assume they just worked with USB or a USB DVD drive. Alas, human stupidity is so far infinite.

Stage 2 might be hunting down BIOS developers and hitting them on the head with halibuts till they agree on some kind of standard. 

> 
There is, but in its infinite wisdom, canonical decided to hide the menu and only show it if the user has the same infinite wisdom and presses a key at the correct moment (before the language selection). Canonical assumes that the tiny icon at the bottom of the screen makes a user understand that.

There is a bug report about this here:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/539172)

But im not sure what the best way is to complain about this. But this is getting a bit off topic, so Ill stop here :)

So THAT is what the icon means, I thought it was just there to look strange. Thank you Canonical, I know you mean well but I think we aren't at the stage yet where we can jump straight to assuming we do the right thing on all hardware. Especially on a beta release. Also the path of recovery here is way to steep.

---

### Post by P4man on 2010-04-28
> **gnomeuser said:**
> I would actually make the default Ubuntu download some kind of really slimmed down unetbootin. A tiny .exe file and have that fetch the required files, detect the USB/CD and plop in on there.

in the words of her loveliness... ISO?

unetbootin actually is that already. You can just download and run it, and it will download the iso for you and make the usb stick. 
Or did you mean making a version that hides all the other distro's?

---

### Post by Nickedynick on 2010-04-28
My current desktop boots fine from USB and optical. However, I've got an old PC I use as a backup in case I run into problems (it's around 8 years old) that can only boot from optical. I froget where I found it, but I normally use a custom CD that starts the boot process and hands over to USB to complete if I need to reinstall.

---

### Post by gnomeuser on 2010-04-28
> **P4man said:**
> unetbootin actually is that already. You can just download and run it, and it will download the iso for you and make the usb stick. 
Or did you mean making a version that hides all the other distro's?

I meant a version with an even easier UI. Picture of USB stick, Picture of CD. Click either and it downloads your stuff, puts it on there and off the the reboot you go. No non-Ubuntu distro stuff, no selection of files just give me by default the latest stable (or even the latest LTS).

And of course we replace the Ubuntu ISO download with this tool.

---

### Post by Doctor Mike on 2010-04-28
> **P4man said:**
> Google tells me "Lexar highspeed" is not a USB key, but a SD card. If so, it wont have U3, and you have a different problem. As for USB 1.1. Im not sure, but I think it does support booting (assuming your bios does) But if it does, it will be painfully slow. USB 1.1 is 40x slower than 2.0.Lexar also makes thumb drives like the 8GB Firefly Jumpdrive which I have.

---

### Post by NCLI on 2010-04-28
> **gnomeuser said:**
> I meant a version with an even easier UI. Picture of USB stick, Picture of CD. Click either and it downloads your stuff, puts it on there and off the the reboot you go. No non-Ubuntu distro stuff, no selection of files just give me by default the latest stable (or even the latest LTS).

And of course we replace the Ubuntu ISO download with this tool.

I think this should be made into a brainstorm suggestion, or maybe posted on the Ayatana mailing-list. It could be a great way to make it much easier for new users to try Ubuntu without using Wubi.

---

### Post by gnomeuser on 2010-04-28
> **NCLI said:**
> I think this should be made into a brainstorm suggestion, or maybe posted on the Ayatana mailing-list. It could be a great way to make it much easier for new users to try Ubuntu without using Wubi.

I am actually writing a spec for this, I am rather sold on the idea of running a living Ubuntu system on a USB stick. 

There are many exciting areas to tackle, e.g. should such a system use full disk encryption since they are easily lost. How to deal with detection of a new system (say if the user takes the stick to a friends house). There is also the problem of eventually offering the user the option to migrate his USBuntu system to the harddrive rather than doing a new install.

I think such a tool might open Ubuntu up to a lot of new people and with such things as Tracker and FUSE we can even safely read  files from the existing system and automatically e.g. offer the user his full media library imported into Banshee. Likewise one could be sneaky and see if we could import email settings and such from the existing system. Ideally this would take the form of a safe first boot to create the user and analyse the system, then a second boot into the properly set up system.

---

### Post by dadgetboy on 2010-04-28
With Grub2, any computer can now boot from USB.

---

### Post by P4man on 2010-04-28
> **gnomeuser said:**
> I am actually writing a spec for this, I am rather sold on the idea of running a living Ubuntu system on a USB stick. 


Keep in mind a livecd is not the same as an installed copy. LiveCD uses a compressed and read only filesystem, as a result takes a long time to boot, cant be updated afaik (if it can, its certainly tricky), you cant use proprietary drivers etc. 

If you want to give people a stick they can actually *use*, it should probably have to be a full install on a stick, but then its 5+ GB, you can not use it to install on to a hdd (at least not afaik) and Im sure there are other stumbling blocks Im not thinking off right now. Like proprietary (video) drivers if you move from one machine to the next...

If I understand correctly what you want to achieve, we'd need something inbetween a livcd and a regular install. I dont think thats undoable though. it just needs some tweaking, like making ubiquity run from an installed copy, autosensing of videocard and loading the correct driver (I actually wrote a little script for that some time back to boot my stick on PC with nvidia or ati cards and load either proprietary driver)

---

### Post by NCLI on 2010-04-28
> **gnomeuser said:**
> I am actually writing a spec for this, I am rather sold on the idea of running a living Ubuntu system on a USB stick. 

There are many exciting areas to tackle, e.g. should such a system use full disk encryption since they are easily lost. How to deal with detection of a new system (say if the user takes the stick to a friends house). There is also the problem of eventually offering the user the option to migrate his USBuntu system to the harddrive rather than doing a new install.

I think such a tool might open Ubuntu up to a lot of new people and with such things as Tracker and FUSE we can even safely read  files from the existing system and automatically e.g. offer the user his full media library imported into Banshee. Likewise one could be sneaky and see if we could import email settings and such from the existing system. Ideally this would take the form of a safe first boot to create the user and analyse the system, then a second boot into the properly set up system.
That sound great! I'm looking forward to see it happening.
> **dadgetboy said:**
> With Grub2, any computer can now boot from USB.
Not really a big help for a user migrating from Windows or Mac ;)

---

### Post by aysiu on 2010-04-28
> **P4man said:**
> 
If I understand correctly what you want to achieve, we'd need something inbetween a livcd and a regular install. I dont think thats undoable though. it just needs some tweaking, like making ubiquity run from an installed copy, autosensing of videocard and loading the correct driver (I actually wrote a little script for that some time back to boot my stick on PC with nvidia or ati cards and load either proprietary driver) It's doable. Puppy Linux has been doing this for years.

---

### Post by Objekt on 2010-04-28
My current box (specs in sig) can boot from USB, but I didn't know that until about a year ago.  Boy did I feel stupid when I realized I could have avoided burning all those boot CDs and DVDs!

The other wrinkle is this: USB only shows up as a boot option when you enter BIOS setup with a USB stick connected.  That's probably why I didn't notice sooner that I could have been installing Linuxes from a flash drive.

I also have an ancient Compaq notebook which can only boot from CD-ROM or over the network, despite having two USB ports.

I've been using computers long enough to remember when there was just no way to boot from an optical drive.  You had to first boot DOS from a floppy or the hard drive, in order to load the drivers, which would then allow use of the optical drive.  Bootable CDs were a huge advancement.

---

### Post by gnomeuser on 2010-04-28
> **P4man said:**
> Keep in mind a livecd is not the same as an installed copy. LiveCD uses a compressed and read only filesystem, as a result takes a long time to boot, cant be updated afaik (if it can, its certainly tricky), you cant use proprietary drivers etc. 


I am currently trying to figure out how to install a bog standard system onto a USB stick and leaving it bootable. It is as you say not entirely trivial but Fedora has been able to do this for a while as I recall so it doesn't sound impossible.

> 
If you want to give people a stick they can actually *use*, it should probably have to be a full install on a stick, but then its 5+ GB, you can not use it to install on to a hdd (at least not afaik) and Im sure there are other stumbling blocks Im not thinking off right now. Like proprietary (video) drivers if you move from one machine to the next...


I've been using a Zonbu box before and that only comes with 4GB flash storage. A full desktop with OpenOffice and Firefox, and this was even a couple of years ago. I am pretty sure that if we can't offer a system that is usable on a 4GB USB stick (and after all those are a couple of bucks these days, I know I got mine for about 10$ a while ago) then we are in deep trouble.

As for proprietary drivers I don't have a good answer, while I do use the nvidia module currently (since nouveau with 3D requires me to install the .34 kernel now and that overheats my CPU and GPU and because I get VDPAU support from the Fluendo codecs that way) it isn't a scenerio I am really that concerned with right now. In the time frame we can make this happen I am thinking the open drivers will be sufficient to run Compiz at least.

> 
If I understand correctly what you want to achieve, we'd need something inbetween a livcd and a regular install. I dont think thats undoable though. it just needs some tweaking, like making ubiquity run from an installed copy, autosensing of videocard and loading the correct driver (I actually wrote a little script for that some time back to boot my stick on PC with nvidia or ati cards and load either proprietary driver)

I think such code could be lifted from Fedora' rpmfusion packaging as well, I believe they have a check in their scripts to only load the driver if a supported card is present. As I said though, for a proof of concept I would be happy with open drivers only, baby steps.

And yes it is kinda like the in between of a livecd and a proper install. It gives the user the safety of being contained, but the freedom to actually use the system. Because let's be honest, the LiveCD isn't useful for actual work. This means a user either has to fall deeply in love with Ubuntu and install it at once or keep trying an inferior experience. A livecd doesn't have one of the absolute best features of Linux, being constantly updated for the whole system using one interface. It also doesn't really allow you to save and work on documents, set up your email and have it persist the next time you boot. You can't have your own user.

I think the USB experience can be great, a bit slow but great. We can get there in small steps, e.g. we could in the Maverick cycle work on making it easy for a user to get from the webpage to having a USB stick with the Live image and persistent storage in hand.

Then for the next cycle a more specially crafted experience might be in order such as walking the user through an account creation on the first boot.

The aim could be to have this ready to ship early in the next LTS release cycle so that 2 years from now we could do this. 

I think it is important to take some extra time and make the experience really compelling and making it part of the Ubuntu family properly.

I am a huge fan of the evolutionary approach, I would rather get a bit better each time in useful ways than attempt to do it all at once.

---

### Post by LowSky on 2010-04-28
My desktop will boot from nearly any media.
My netbook will boot from the USB or a USB provided DVD-ROM

---

### Post by markp1989 on 2010-04-28
all of mine boot from usb, i do most of my installs from a sd card as a 1gb card can be had way cheap now

i only have 1 pc with a optical disk drive, and thats my htpc

---

### Post by WinterRain on 2010-04-28
I love USB installs now. Install time was cut in half for me. (4 minutes)

---

### Post by Plumtreed on 2010-04-28
I must be missing something! 

There is a 'USB Startup Disk Creator' ,since Ubuntu 9.04, that will 'create' a bootable USB drive painleesly????????????

---

### Post by P4man on 2010-04-28
> **gnomeuser said:**
> I am currently trying to figure out how to install a bog standard system onto a USB stick and leaving it bootable. 

?
Just install from a livecd (or usb stick) and install to a different usb stick instead of hdd. Its not any more difficult, or different. Just make sure in the last step of ubiquity you put grub on the stick and not on the hard drive. I got a stick like that, works like a charm.

> 
I've been using a Zonbu box before and that only comes with 4GB flash storage. A full desktop with OpenOffice and Firefox, and this was even a couple of years ago. I am pretty sure that if we can't offer a system that is usable on a 4GB USB stick (and after all those are a couple of bucks these days, I know I got mine for about 10$ a while ago) then we are in deep trouble.

Well actually, I have to admit I got it running on a 4GB stick and I think there just under 1 GB free space. But that is after I cleaned it up ( I think I even used remastersys but i dont recall)  and its still rather cramped. A usable system on a 4GB stick without compressed filesystem is doable, just not luxurious. 

Anyway, if I can help in anyway (other than something that really requires in depth ubuntu or programming skills :p) then id be happy to assist.

---

### Post by Doctor Mike on 2010-04-28
> **dadgetboy said:**
> With Grub2, any computer can now boot from USB.
Please explain???????????????

---

### Post by WinterRain on 2010-04-28
> **Plumtreed said:**
> I must be missing something! 

There is a 'USB Startup Disk Creator' ,since Ubuntu 9.04, that will 'create' a bootable USB drive painleesly????????????

Yes.

---

### Post by angry_johnnie on 2010-04-28
Mine can boot from usb thanks to a bios update.  It didn't do i before.  I guess I wasn't really interested in booting from usb until i came across one of those awesome [puppies]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm").

---

### Post by magmon on 2010-04-28
My answer requires a small amount of clarification. Although both of my computers can only boot from usb, they also do not have an optical drive. They boot just fine from an external CD drive, but I thought that fell within the realm of USB.

---

### Post by OpenSourceRules on 2010-04-28
Hardly got any USB drives YET.

---

### Post by magmon on 2010-04-28
> **OpenSourceRules said:**
> Hardly got any USB drives YET.

Speaking of which... What happened to those awesome ubuntu flash drives?? The canonical store doesn't show a trace of them.

---

### Post by NormanFLinux on 2010-04-29
My old HP laptop - a Pentium 4, does not boot USB from the BIOS. There is a tool called PLOP Linux that installs permanently to the hard drive which creates an entry that allows a bootable USB flash drive to be recognized as another hard drive. So now it is possible to boot from a USB  flash drive on a laptop that has no BIOS provision for a bootable USB device.

---

### Post by Plumtreed on 2010-04-29
> **WinterRain said:**
> Yes.

I wasn't @ you, WinterRain.

The OP was about the ability to boot from USB. Replies started to indicate that some people were looking for ways to create USB drives that could be used as a complete OS, that is, retain stuff, drivers etc. I felt the need to point out how easily this could be done, now, with Ubuntu without the need for Unetbootin, Pendrivelinux or creative code...:confused:

---

### Post by nerdtron on 2010-04-29
I installed 9.10 from USB flash drive. I think it looks cool when people see your PC boot from flash drive instead of CD. :p
I just press F11 and it shows up boot options: sata hdd, usb, cdrom, then press enter and that's it!
Btw the OP is the creator of the [www.psychocats.net](www.psychocats.net) blog. Thanks for the great tutorials! It really helped me deal with my new OS.

---

### Post by rolnics on 2010-04-29
> **NormanFLinux said:**
> There is a tool called PLOP Linux that installs permanently to the hard drive which creates an entry that allows a bootable USB flash drive to be recognized as another hard drive.

Another reason to read these forums! That's interesting, I'll have to look into that one, as all my PC's are P4 or older, so don't boot via USB.

---

