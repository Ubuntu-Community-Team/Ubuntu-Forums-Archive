---
title: "Problems with 12.04 beta1"
date: 2012-03-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by oldtom on 2012-03-03
Have downloaded and burnt 12.04 to a CD. Then installed usb-creator and installed live CD to a 4Gig usb stick to gain persistence. Then rebooted.

However, when I make shortcuts on the desktop, their creation is a bit flaky. Sometimes I can only make one shortcut, other times two. If I say make a third as "new", all the details of the previous shortcut (the second), are already filled in. If I edit these dialog boxes, it overwrites my already created second shortcut and will not create a third one. Similar problems with edited the icon description. The changes won't stick.

Only once, when I made another shortcut did the fields present themselves as empty and allowed me to make a new one. But immediately after I tried to make another, I could not get a clean dialog box even though "new" was selected. Anyone else had this trouble or are these problems part of a beta distribution.  

Also, downloaded and burnt v11.10 to see if the previous version had these dramas, but when it boots from the CD it stops at a prompt and won't go into a desktop. Anyone know how to fix this.

---

### Post by Elfy on 2012-03-03
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

Please post support requests for dev versions here and not in general support forums.

---

### Post by bennachie on 2012-03-03
Sounds as if you have been using a LiveCD at all times (that is, you haven't actually installed Ubuntu 12.04 to your USB stick in the same sense that you might have installed it to one or more hard disk partitions, just made a LiveUSB with persistence generated through USB Disk Creator). Your problem with short-cuts sounds like some kind of "lack of persistence" issue. Certainly the problem doesn't arise with a hard disk installation, and I'm finding 12.04 Beta 1 to be admirably stable.

I can't say that I have used Disk Creator much in recent times. Now that we have hybrid ISOs, it's much simpler just to use "dd" to clone the ISO to a USB stick and forget about the, not always entirely reliable, persistence.

I don't know why you would have experienced a problem launching an 11.10 LiveCD session, although I seem to recall a similar issue having arisen occasionally during the testing process.

---

### Post by VinDSL on 2012-03-03
> **oldtom said:**
> Have downloaded and burnt 12.04 to a CD. Then installed usb-creator and installed live CD to a 4Gig usb stick to gain persistence. Then rebooted.[...]
> **bennachie said:**
> Sounds as if you have been using a LiveCD at all times [...]
I've been running various OSs on USB sticks, for quite some time.

I've used various methods:
[LIST]
[*]dd (Live-CD clone with no persistence)
[*]Startup Disk Creator (Live-CD clone with limited persistence)
[*]Fully partitioned install (separate /home & /swap with full persistence, EXT4 format)
[/LIST]

I can (just about) guarantee you that you cannot do a fully functional Ubu 12.04 install on a 4GB USB stick.  

Personally, I wouldn't even attempt to run a "slim" release, like Lubuntu or Peppermint Two on 4GB.

Here's what I would recommend:
[LIST]
[*]Clone an Ubu 12.04 Live-CD iso to your 4GB USB stick.
[*]Buy a 16GB USB stick.
[*]Run GParted against the 16GB stick.
[*]Make a 5GB root partition, a 10GB /home, and a 1GB /swap.
[*]Then, do a full Ubu 12.04 install on the 16GB stick, using the 4GB Live-CD clone as your source.
[/LIST]

This will give you the best chance of a successful install, IMO. ;)

---

### Post by oldtom on 2012-03-03
> **bennachie said:**
> Sounds as if you have been using a LiveCD at all times (that is, you haven't actually installed Ubuntu 12.04 to your USB stick in the same sense that you might have installed it to one or more hard disk partitions, just made a LiveUSB with persistence generated through USB Disk Creator). Your problem with short-cuts sounds like some kind of "lack of persistence" issue. Certainly the problem doesn't arise with a hard disk installation, and I'm finding 12.04 Beta 1 to be admirably stable.

I can't say that I have used Disk Creator much in recent times. Now that we have hybrid ISOs, it's much simpler just to use "dd" to clone the ISO to a USB stick and forget about the, not always entirely reliable, persistence.

I don't know why you would have experienced a problem launching an 11.10 LiveCD session, although I seem to recall a similar issue having arisen occasionally during the testing process.


Thanks for all the replies.

Just love lubuntu 12.04. :D It has everything I need, is simple, straightforward and has a great menu.

I have used usb-creator, usb pendrive and unetbootin considerably both in Win and Linux with persistence. Never encountered this problem with other Ubuntu variants or other Linux's.

Also have used both 4G and 8G sticks exclusively and with rare exceptions have been able to install many heavy programs, with space to spare. (usually 2-3G). Mint 12 took up 5G so I had to use an 8g stick but for all the others, 4G was plenty. So I don't think a 4G stick is too light for Lubuntu. But I will try with an 8G usb and see if that is the problem.

Indeed, Lubuntu feels snappier running from the live CD compared to the usb stick, but that may be just my imagination. Perhaps when I installed usb-creator with Synaptic, I installed the wrong one. There is a gnome and a gtk version and I picked the gnome one. Advice please on this!

The dd method of which I am unfamiliar, is no good without persistence as I need to use wireless and whilst I can get this going on the live CD with a bit of effort (one of my pet hates with all these linux versions), the computer needs to be restarted to put the changes in to effect and any changes are then lost. A classic chicken and egg scenario.

As well, I usually install my other favourite programs to test. I don't want to install to hard drive as I already multiboot and my disk is pretty much full anyway. Just love having a portable USB system to demonstrate to others. I just think lubuntu may have a slight bug here. 
 
I would use unetbootin exclusively but it does not have persistence where usb-creator does. Also do you know what method overcame the reluctance of 11.10 to fully boot. Thanks!

---

### Post by oldtom on 2012-03-03
> **VinDSL said:**
> I've been running various OSs on USB sticks, for quite some time.

I've used various methods:
[LIST]
[*]dd (Live-CD clone with no persistence)
[*]Startup Disk Creator (Live-CD clone with limited persistence)
[*]Fully partitioned install (separate /home & /swap with full persistence, EXT4 format)
[/LIST]

I can (just about) guarantee you that you cannot do a fully functional Ubu 12.04 install on a 4GB USB stick.  

Personally, I wouldn't even attempt to run a "slim" release, like Lubuntu or Peppermint Two on 4GB.

Here's what I would recommend:
[LIST]
[*]Clone an Ubu 12.04 Live-CD iso to your 4GB USB stick.
[*]Buy a 16GB USB stick.
[*]Run GParted against the 16GB stick.
[*]Make a 5GB root partition, a 10GB /home, and a 1GB /swap.
[*]Then, do a full Ubu 12.04 install on the 16GB stick, using the 4GB Live-CD clone as your source.
[/LIST]

This will give you the best chance of a successful install, IMO. ;)


Thanks,
I'll try the 8G option first, as I want to have a portable usb stick able to run on other machines. See my other comments. Cheers!

---

### Post by VinDSL on 2012-03-03
> **oldtom said:**
>  Cheers!
You're welcome!

Just a thought...

A USB stick without persistence can't be beat for security, e.g. for online banking, and so forth.  So, they do have their place...  ;)

---

### Post by oldtom on 2012-03-03
Just a follow up.

Installed Lubuntu 12.04 to an 8Gb stick using usb-creator on another machine. Installed lots of software, Firefox, Googleearth, shotwell etc and all OK. Still have over 3G space left on the stick. But still some bugs.

Making a shortcut to a file on the desktop still overwrites the previous made shortcut and creating a new one does not open a new set up box. It merely contains the input of the previously created one. However, with a bit of stuffing around, I did manage to created 3 new ones, as this bug is not consistently repeatable. Also the desktop sort option does not work. And an icon created from my own picture and stored in my pictures folder and used for a desktop shortcut disappeared on reboot, but the icons selected from Lubuntu's own library stuck. Seems these bugs are all related to the shortcut problem. 

Also updated the system from the menu option and the updater crashed with many errors shown in the dialog box. And this after updating gdebi to 8.5 beforehand. Additionally, the network manager icon keeps disappearing and mysteriously reappearing. All other changes to the desktop are retained.

Pity these bugs are there, as this version is really great otherwise, with pin sharp display and good choices of programs. A little slow to boot from the stick but shutdown is a 2 second affair.

---

### Post by cariboo on 2012-03-03
I think it was suggested you do an install to your flash drive, just like you would to a hard drive, not just creating a Live version.

I have Lubuntu install on an 8GiB SD card, and it works just like as if it was installed on a hard drive.

---

### Post by oldtom on 2012-03-04
> **cariboo907 said:**
> I think it was suggested you do an install to your flash drive, just like you would to a hard drive, not just creating a Live version.

I have Lubuntu install on an 8GiB SD card, and it works just like as if it was installed on a hard drive.

Yes, I understand that and I thank the poster. But wouldn't this tie me to one machine, mine. I want a portable usb stick that I can plug into any computer. This way it can be used to demonstrate what a great OS it is without changing the user's equipment. Am I on the wrong track!

---

### Post by bennachie on 2012-03-04
The usual approach is to select the target 8GB or 16GB USB stick as the location for installing GRUB. The installer will default to your primary hard disk, but offer you the option of choosing exactly where you want to put GRUB. That way, assuming that, as is almost always the case, the BIOS of the host computer is either set up to favour removable media, or can be persuaded to do so, you simply insert the USB stick in your target machine and power up - just as if you were using a LiveCD or LiveUSB.

---

### Post by MG&amp;TL on 2012-03-04
> **oldtom said:**
> Yes, I understand that and I thank the poster. But wouldn't this tie me to one machine, mine. I want a portable usb stick that I can plug into any computer. This way it can be used to demonstrate what a great OS it is without changing the user's equipment. Am I on the wrong track!

Yes. ;)

You can treat your USB stick as hard disk space, just run the installer and point it to your memory stick instead of your hard drive.  It's just the same, but presumably faster and less buggy.

---

### Post by oldtom on 2012-03-04
Thank you bennachie and MG&TL. 

Just shows you CAN teach an old dog new tricks. I've been doing the live usb install for so long, without a problem, I just assumed this was the correct method and I'm anxious now to do it your way. 

I just don't want to change anything on my existing dual boot installation that will confuse me and cause me grief later on.

Thank you for your help.

---

### Post by VinDSL on 2012-03-04
> **oldtom said:**
> [...] wouldn't this tie me to one machine, mine. I want a portable usb stick that I can plug into any computer.[...]
Heh!  That's what I call my "Pocket PC".  :D

I haven't had any (major) problems running a full USB stick install on any of the machines I've tried.

The only caveat is the formatting.  EXT4 can be sort of dicey.

For instance, on some Dell desktop computers, the USB ports on the front panel won't recognize USB sticks formatted with EXT4... but, the USB ports on the rear of the case will.

All of my machines, here at the abode, will run a full USB install without issue... various homebrew desktop machines, Toshiba lappy, Asus netty, et cetera.

As long as you use a 32-bit distro, and EXT2/EXT3 or FAT32, it should boot up on any machine.  EXT4 is a crapshoot.

At least, that's been my experience...  ;)

---

### Post by oldtom on 2012-03-04
> **VinDSL said:**
> Heh!  That's what I call my "Pocket PC".  :D

I haven't had any (major) problems running a full USB stick install on any of the machines I've tried.

The only caveat is the formatting.  EXT4 can be sort of dicey.

For instance, on some Dell desktop computers, the USB ports on the front panel won't recognize USB sticks formatted with EXT4... but, the USB ports on the rear of the case will.

All of my machines, here at the abode, will run a full USB install without issue... various homebrew desktop machines, Toshiba lappy, Asus netty, et cetera.

As long as you use a 32-bit distro, and EXT2/EXT3 or FAT32, it should boot up on any machine.  EXT4 is a crapshoot.

At least, that's been my experience...  ;)

Thanks, I'm trying a usb install now.

---

### Post by oldtom on 2012-03-04
Hi vinDSL,
I'm installing from a CD burnt from a downloaded iso. This is how I've always done the live usb's.

But you mention doing a clone of the iso. Can you lead me thru this. i.e. If I clone an iso to a usb stick, do I just get the iso file copied, or is it expanded on the stick, enabling a boot from the stick and hence an install. I take it that a clone is different from just copying. Hope that's clear, as I'm a little confused.

---

### Post by VinDSL on 2012-03-04
> **oldtom said:**
> [...] you mention doing a clone of the iso. Can you lead me thru this [...]
I didn't mean "clone", in a strict sense. I simply meant...

Instead of burning a Live-CD or DVD from an .iso (which you can still do, if you wish), make a bootable USB stick, via Startup Disk Creator (or whichever app you prefer).

Boot from the USB stick.  

Then, install Ubuntu using the bootable USB stick you created, but direct the install to be made on a second USB stick (instead of a HD).

Sorry for the confusion...  :)

---

### Post by oldtom on 2012-03-04
OK! Now I understand! In the process now and using my live CD as the source. Fingers crossed! Thanks again.

---

