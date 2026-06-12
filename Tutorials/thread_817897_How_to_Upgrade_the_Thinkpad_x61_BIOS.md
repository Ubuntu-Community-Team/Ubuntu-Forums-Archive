---
title: "How to Upgrade the Thinkpad x61 BIOS"
date: 2008-06-04
forum: Tutorials
---

### Post by mbsullivan on 2008-06-04
[CENTER]**[COLOR="#FF0000"][SIZE=5]NOTE: If attachments are missing - I would be inclined to look for a newer source than one 5 years old thread here[/SIZE][/COLOR]**[/CENTER]


This tutorial details how to upgrade the BIOS of a Thinkpad x61, x61s or x61s tablet notebook using a bootable USB stick. At the time of writing, the 2.20 BIOS and 1.03 firmware versions are the most current for the X61/X61s. Also, the most current BIOS and firmware versions for the ThinkPad X61 Tablet are 1.23 and 1.03, respectively.

*Disclaimer: While these steps worked for me while upgrading my X61 BIOS from 1.06 to 2.07, and later from 2.07 to 2.14 and 2.14 to 2.20, use them at your own discretion. BIOS upgrades always carry some associated risk, and I cannot be held liable for anything that goes wrong.*

**[SIZE="4"]Motivation[/SIZE]**

The Thinkpad x61 is an ultralight notebook offered by Lenovo. As any x61 owners should know, the internal optical drive present in most laptops was omitted from the x61 in order to minimize weight.

Regular BIOS upgrades have been offered by Lenovo for the x61, and are released without charge in two forms:

[INDENT]**X61/X61s:**
1. A [Win32-only  executable]("http://www-307.ibm.com/pc/support/site.wss/MIGR-67982.html")
2. A bootable [DOS CD-ROM disc]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-67983")[/INDENT] 


[INDENT]**X61 Tablet:**
1. A [Win32-only  executable]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-68005")
2. A bootable [DOS CD-ROM disc]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68006")[/INDENT] 

The bootable CD-ROM disc is the only option available for GNU/Linux users. Ridiculously enough, USB CD-ROM drivers are not included on the disk, such that external CD-ROM drives will **[COLOR="Red"]not[/COLOR]** work with the BIOS upgrade. Not even the Lenovo Thinkpad USB CD-ROM drive allows the user to upgrade the BIOS.

Officially, the supported method for an x61 upgrade on a non-Win32 platform is to use the CD-ROM drive in an ultrabase. Those of us who don't have one are left in the dark. In this tutorial, I will show how to upgrade the x61 BIOS from a bootable USB stick.

**[SIZE="4"]Why Upgrade the BIOS[/SIZE]**

Although the stock BIOS shipped with most x61 laptops may be fine for most users, the BIOS v2.07, which was released in January 2008, offers an improved fan speed controller. It also fixes USB interrupt bugs present in previous releases, which have manifested themselves as problems with the right-side USB ports (see [here]("http://ubuntuforums.org/showthread.php?t=658065&highlight=USB") and [here]("http://ubuntuforums.org/showthread.php?p=4083012&posted=1#post4083012")). Later BIOS revisions have dealt with other firmware bugs, such as WOL (Wake on LAN) errors, POST issues and CardBus and 1394 bugs. Some BIOS release between 2.14 and 2.20 (for the x61/x61s) fixes DSDT problems that have cropped up with recent kernels.

That being said, a BIOS upgrade not a necessity. There are workarounds for many of the problems it fixes (I provide a hack for the USB devices, for example, in the previous two hyperlinked posts). Of course, the newest BIOS and firmware versions are preferable, however, so without further ado...

**[SIZE="4"]How to Upgrade the Thinkpad x61 BIOS with a USB Thumb Drive[/SIZE]**

The rest of this tutorial shows how to upgrade the Thinkpad BIOS to the newest version without an internal CD-ROM drive. The basic steps involved are:

[INDENT]1. Format the USB stick to be a DOS boot device
2. Copy the bootable ISO BIOS files to the USB stick
3. Boot to the USB stick and follow instructions[/INDENT]

The instructions for Step 1 are given both using a Windows computer, as well as one running Linux. This issue is *not* unique to Linux users, and also affects users of a 64-bit Windows operating system.

**[SIZE="4"]1. Format the USB stick to be a DOS boot device (Windows)[/SIZE]**

There are [multiple ways]("http://www.bootdisk.com/pendrive.htm") to do this step, I'm taking the easiest route I know: the HP USB Disk Storage Format Tool combined with Win98 DOS boot disc files.

First, connect a USB stick (<= 4GB) and backup any important files; we are going to format the device, which will erase any information you have on it.

Next, get the HP USB Disk Storage Format Tool (from [here]("http://www.bootdisk.com/plan30/hpflash1.zip") or HPUSBFW.zip attached to this tutorial). Run HPUSBFW.EXE and select the FAT (FAT16) filesystem and "Create a DOS Startup Disc". 

Under "using DOS system files located at", provide a directory containing a valid DOS boot disc. I have attached the appropriate files for a Win98 DOS boot disc to this tutorial, in win98boot.zip. They should also be available [here]("http://files.extremeoverclocking.com/file.php?f=196") .

Click "Start" to format the USB into a bootable DOS-wielding device. If this process worked, then skip to the section entitled "**2. Copy the bootable ISO BIOS files to the USB stick**".

**[SIZE="4"]1. Format the USB stick to be a DOS boot device (Linux)[/SIZE]**

I had previously posted instructions on how to properly format a USB stick under Linux. A rough copy of these instructions can be found [here]("http://ubuntuforums.org/showpost.php?p=5544555&postcount=26"). However, it soon became clear that the procedure was finicky at best, and did not work for all users. 

Since then, I have come to the conclusion that by far the simplest and least risky way to format a USB stick under Linux is to prescribe to the same method that was used under Windows, by formatting the USB stick as a (proprietary, but gratis) Windows 98 boot disk. Furthermore, the simplest way to do so is to copy an image of a bootable USB stick directly onto the USB device.

First, insert your USB stick and determine what device it is assigned to. This is fairly simple by looking at the output of:

```
sudo fdisk -l
```

For a device which is the same size as your USB stick and formatted (presumably) as Fat32 or Fat16. Normally the device will be in the form /dev/sdb or /dev/sdc, etc. 

***Note: It is critical that you get the name of your USB device correct, and always type it accurately. If you use the device name of another harddrive, you could very easily end up wiping other, unrelated disks. For that reason, I'm always going to use the identifier [USB device] for the device name of your specific USB drive. Use the name of the root device, and omit any partition numbers that may follow the device name.***

After you have discovered your USB stick device name, download the raw bootable USB stick image ("win98usb.tar") which is attached to this post. We will copy this image directly onto the USB device, which will thrash any existing file system. Therefore, remove *all* data before proceeding. 

Untar the bootable USB stick image into the current directory. The only reason that the image is tarred is in order to comply with the Ubuntu Forums filetype restrictions for uploads.

```
tar -xf ./win98usb.tar
```

Unmount the USB stick, either through Nautilus or with the following command:

```
umount -f [path to root folder of mounted USB stick]
```

Once the USB stick is unmounted, copy the image onto the device with the following command:

```
sudo dd if=win98usb.img of=[USB device] conv=notrunc
``` 

The dd command should not take long, and will produce output similar to the following:

```
$ sudo dd if=./win98usb.img of=/dev/sdc conv=notrunc
1214+0 records in
1214+0 records out
621568 bytes (622 kB) copied, 0.193487 s, 3.2 MB/s
```

This will prepare the USB stick as a bootable device ready for the remainder of the X61 BIOS installation procedure.

**[SIZE="4"]2. Copy the bootable ISO BIOS files to the USB stick[/SIZE]**

This step is very simple: just copy all of the files from the bootable BIOS CD provided by Lenovo onto the USB stick. The most recent ISO file can be found for the X61/X61s [here (regular)]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-67983"), and for the X61 Tablet [here (tablet)]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68006"). The link for the correct ISO file will be found corresponding to the file description "BIOS Update Bootable CD".

This can be done many different ways. In Windows, one must first mount the .iso file (which can be done using any of a number of different free [programs]("http://www.google.com/search?hl=en&client=firefox-a&channel=s&rls=com.ubuntu%3Aen-US%3Aofficial&hs=Gyr&q=windows+mount+iso&btnG=Search")) and then copy the files over. 

In Linux, the ISO may be trivially mounted and copied from the command line:

```
sudo mount -o loop [path to ISO file] [mount point]
sudo cp -af [mount point]/* [path to USB folder]
```

Where *[path to ISO file]* is the path to the CD ISO image, *[mount point]* is wherever you want to mount the CD image to (you can choose this, */cdrom/* works), and *[path to USB folder]* is the location of your mounted USB drive.

It should be noted that the default DOS command-line interpreter (COMMAND.COM), if present, **[COLOR="Red"]must[/COLOR]** be overwritten by the (much smaller) version provided by Lenovo in order for this to work. Under Windows, this may require you to disable the read-only flag on the file before overwriting it.

**[SIZE="4"]3. Boot to the USB stick and follow instructions[/SIZE]**

This step should pretty much be self-explanatory. Make sure to set the boot priority of the USB device to be higher than your internal hard drive, and then reboot! 

***Note: With BIOS revision v2.14 and after, after booting to the USB device, the system may query for the location of the "COMMAND.COM" file. Should this happen to you, entering 'command.com' (without quotes) will allow you to proceed to the BIOS upgrade.*** 

Follow the on-screen instructions, and your BIOS should be upgraded within 5 minutes. As always with BIOS upgrades, do **[COLOR="Red"]not[/COLOR]** under any circumstances turn the laptop off before installation is complete, or you could turn your laptop into a very expensive paperweight.

That's it! Please let me know if you have any questions.

Mike



**Revision History:**
[INDENT]1.0.0 - Original post (June 4th, 2008)
  1.0.1 - Updated for BIOS revision X61/61s 2.14, Added "1. Format the USB stick to be a DOS boot device (Linux)" (July 30th, 2008)
  1.0.2 - Added ISO links for the X61 Tablet (August 5th, 2008)
  1.0.3 - Removed the Linux instructions, due to troubles reported by users (August 9th, 2008)
  1.0.4 - Updated the links for the most recent BIOS updates (2.20/2.23)
  1.0.5 - Added new Linux instructions (May 27, 2009)
  1.0.6 - Minor update to Linux instructions
  1.0.7 - Updated the links to BIOSes 2.21/1.24 for the X61/X61s and the X61 tablet (June 8th, 2010)
  1.0.8 - Minor changes[/INDENT]

---

### Post by gil2008 on 2008-06-25
works perfekt.

for 2.14 bios, release date 2008/06/13 too.

many thx

---

### Post by mbsullivan on 2008-07-03
> works perfekt.

for 2.14 bios, release date 2008/06/13 too.

many thx

Thanks for the kind words, and I'm glad the instructions are clear enough to have worked for at least one person :)

If anybody else has any problems, I'm subscribed to the thread so that I should be able to field any concerns in the future. The BIOS upgrade improves the embedded fan speed controller and seems to make suspend-to-RAM more reliable, so I think it's a good idea for x61ers.

Mike

---

### Post by darkbeethoven on 2008-07-04
GREAT tutorial. You hit the nail on the head.

I just finished upgrading my X61s to the latest bios.

Thanks again!

---

### Post by StickyTape on 2008-07-04
Works fine, thanks. The best thing is seeing that other people have done so without problems as I was a little worried about frying the X61.

The first time I overwrote the Win98 command.com file with the Lenovo one, using a simple copy and paste in windows, the flash drive failed to boot. It didn't like the command.com file. I then copied the DOS files from the ISO image to a new folder and pointed the HP USB tool to that folder. After booting fine, I ran updtflsh.exe to upgrade. I imagine that the Ubuntu commands avoid this. But anyway, a tip for those who do not yet have Linux or similar installed.

---

### Post by mbsullivan on 2008-07-04
I'm glad to hear that we're at least 4/4 for not destroying our laptops upgrading the BIOS :)

> The first time I overwrote the Win98 command.com file with the Lenovo one, using a simple copy and paste in windows, the flash drive failed to boot. It didn't like the command.com file. I then copied the DOS files from the ISO image to a new folder and pointed the HP USB tool to that folder. After booting fine, I ran updtflsh.exe to upgrade. I imagine that the Ubuntu commands avoid this. But anyway, a tip for those who do not yet have Linux or similar installed.

I don't know why copying the files via Windows Explorer would make a difference, but thanks for the tip :) 

***NOTE: I tried the entire operation in Windows recently (to update to BIOS 2.14, and had no problem with Windows Explorer. I'm not sure what the issue StickyTape was experiencing, but if anybody else has the same one, he described a possible solution above.***

Mike

---

### Post by MadeTheSwitch on 2008-07-14
Excellent guide, works like a charm.

I want to make one note - when the HP utility finished running, the USB drive will appear empty. No matter if you try to unhide files or whatever, it will seem that way.

Do NOT attempt to copy over the system files from the win98 directory! that will cause a crash on boot from the USB stick.

What happens is that Windows is configured to "super-hide" the essential files, so while they are there, you can't see them. Just copy over the files from the ISO - accepting to overwrite of command.com (that's you indication that even though they don't show, essential files were copies) - and keep going.

---

### Post by StickyTape on 2008-07-25
Has anyone had any luck installing the HD firmware upgrade below? The file is FWSH20.iso.

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-63685](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-63685)

I mounted the image within Linux but could still not see any files, nor could I open them within Windows. The format of the image is such that it cannot be viewed, thus it cannot be copied to a USB stick with 'cp' command or otherwise.

Any ideas?

---

### Post by mbsullivan on 2008-07-25
***Note: To clarify, the following discussion pertains to a Lenovo Hard drive firmware update bootable ISO, **not** the BIOS bootable ISO.***

> I mounted the image within Linux but could still not see any files, nor could I open them within Windows. The format of the image is such that it cannot be viewed, thus it cannot be copied to a USB stick with 'cp' command or otherwise.

Interesting question... The files can't be viewed because the ISO is made with a different bootable technique ("hard disk emulation" instread of "floppy disk emulation"). See [here]("http://www.nongnu.org/lpi-manuals/lpi-201/html/ch04s04.html") for details.

I'll have to think about this one... My guess is that it's possible using dd somehow, though it may take some hacking.

Also, I just noticed that many other versions of the BIOS have been released (up to 2.14)! I'll take a crack at updating the tutorial over the next couple of days to reflect what has come to light, and make sure everything's on the level for the newest BIOS revision.

Mike

---

### Post by mbsullivan on 2008-07-25
> I'll take a crack at updating the tutorial over the next couple of days to reflect what has come to light, and make sure everything's on the level for the newest BIOS revision.

Hi All,

I just wanted to put a note at the bleeding edge of the conversation that the tutorial has been updated: version 2.14 is now incorporated, and instructions to update using Linux only (at long last) have been posted.

Let me know if anybody runs into any trouble with the process!
Mike

---

### Post by mbsullivan on 2008-07-25
> Has anyone had any luck installing the HD firmware upgrade below? The file is FWSH20.iso.

[http://www-307.ibm.com/pc/support/si...cid=MIGR-63685](http://www-307.ibm.com/pc/support/si...cid=MIGR-63685)

I mounted the image within Linux but could still not see any files, nor could I open them within Windows. The format of the image is such that it cannot be viewed, thus it cannot be copied to a USB stick with 'cp' command or otherwise.

Any ideas?

Okay... I looked into this / thought about it some more. I'm sure it's possible, but it may require parsing the CD-ROM binary data (which follows the [El Torito Specification]("http://www.phoenix.com/NR/rdonlyres/98D3219C-9CC9-4DF5-B496-A286D893E36A/0/specscdrom.pdf") and extracting the files manually. 

A software engineer named Michael Kennett seems to have written a program to do something like this, and talks about it on his blog [here]("http://laurasia.blogspot.com/2005/10/touring-el-torito-viewing-minix-3.html"). However, his webserver that held the program seems to be down, now. I've e-mailed him... we'll see if he responds.

It's not clear how much work it would take to make this work... Why (if you don't mind me asking) are you interested in the hard drive firmware update utility? What's it do? From the Lenovo page, it looks like it's mostly applicable for Vista users... 

Mike

---

### Post by StickyTape on 2008-07-26
> **mbsullivan said:**
> 

It's not clear how much work it would take to make this work... Why (if you don't mind me asking) are you interested in the hard drive firmware update utility? What's it do? From the Lenovo page, it looks like it's mostly applicable for Vista users... 

Mike

In my particular case the HDD on my X61 is not listed as those included (HTS542516K9SA00), though similar models are. I was going to run it just in case due to a common freeze problem while on battery, running Vista x64 Business. This seems to be corrected with an updated turbo mem driver from Intel, not repackaged from Lenovo. Some people have reported better performance in Vista and XP after the firmware upgrade, but then they do that all the time! It is made to correct errors on these OS.

My question, then, is more out of curiosity than out of necessity and is open-ended. I see noone else talking about it so I would not waste time on it unless it affects your own laptop.

That said, opening the ISO with 7Zip shows a [BOOT] folder containing "Bootable_HardDisk.img". It is 512 bytes while the ISO is 30MB. No luck finding the rest of the contents.

---

### Post by evergreen on 2008-07-26
hi I'm trying to download BIOS (2.07) & BIOS (2.14) from lenovo.com uk support downloads & drivers

I keep getting a "504 Gateway Time-out"

I've trying your link & going to the site & using wget I can't seem to get those files.

Does anyone have them? Could someone send me them?

[email]bios@TempEMail.net[/email]

Thanks

---

### Post by mbsullivan on 2008-07-26
> hi I'm trying to download BIOS (2.07) & BIOS (2.14) from lenovo.com uk support downloads & drivers

I keep getting a "504 Gateway Time-out"

I've trying your link & going to the site & using wget I can't seem to get those files.

Does anyone have them? Could someone send me them?

[email]bios@TempEMail.net[/email]

Thanks

Right you are... Lenovo's support site (hosted on IBM servers) appears to be down right now. I've still got the 2.14 ISO on my machine, I'll send it your way.

Mike

PS: I've bzip2'ed it in a tarball, such that the proper way to extract it is:

```
tar -xjf 7nuj14uc.iso.tar.bz
```

---

### Post by mbsullivan on 2008-07-26
> 
That said, opening the ISO with 7Zip shows a [BOOT] folder containing "Bootable_HardDisk.img". It is 512 bytes while the ISO is 30MB. No luck finding the rest of the contents.

I'm not positive, but I think it's extracting the boot image. A Perl app named [geltorito]("http://freshmeat.net/projects/geteltorito/") gave me the same thing, as I recall.

I won't have much time to work on this right now, but I'll keep it in the back of my mind. We may figure a way to make it work.

Mike

PS: Michael Kennett, who wrote the rip3 program I mentioned earlier, got back to me by e-mail. He's looking for the source code (which is a couple of years old). Maybe we can hack his project to work for our purposes.

---

### Post by evergreen on 2008-07-26
Cheers for the reply mbsullivan I've sent you a private message with my gmail email could you send the file to me there. Temp mail doesn't seem to be working.

Thanks again

wow just checked my mail the file is already there many thanks :)

---

### Post by mbsullivan on 2008-07-27
> 
Cheers for the reply mbsullivan I've sent you a private message with my gmail email could you send the file to me there. Temp mail doesn't seem to be working.

Thanks again

wow just checked my mail the file is already there many thanks 

Let me know if everything goes well. Are you doing the Windows way, or through Linux only?

Mike

---

### Post by evergreen on 2008-07-27
All went well upgrading from bios 1.06 to 2.14 I used my mums windows computer to make the bootable usb. 

The first few attempts didn't work I was using a SanDisk 4gb usb stick with U3 software on it. I would boot in to a black screen.

I went home and got my ocz 1gb usb, it doesn't have any u3 software on it. I follow the windows parts of you tutorial and all went very smoothly. 

Once again great tutorial and thanks for the fast reply yesterday in sending me the bios update, It was very nice of you.

---

### Post by mbsullivan on 2008-07-27
> 
The first few attempts didn't work I was using a SanDisk 4gb usb stick with U3 software on it. I would boot in to a black screen.

Hmmm... Interesting! That's good to know.

> Once again great tutorial and thanks for the fast reply yesterday in sending me the bios update, It was very nice of you. 

Thanks for the kind words. I'm glad the upgrade worked for you!

Mike

---

### Post by millerl on 2008-08-01
Thanks for the guide!
Exactly what I was looking for!

Didn't have a single problem and am now running 2.14
:)

---

### Post by mbsullivan on 2008-08-01
> Thanks for the guide!
Exactly what I was looking for!

Didn't have a single problem and am now running 2.14


Glad to hear it! 

Did you use the Windows or Linux instructions? I want to make sure the Linux ones are understandable and have no bugs (they're fairly new).

Mike

---

### Post by speedkreature on 2008-08-03
Thank you so much.  With very little modification, I was able to use this to upgrade the BIOS on a SuperMicro server board.  Thanks to the result of this little how-to, you've helped put an end to 9 days of torment.  I can finally go home.  Thank you.

I more or less followed your instructions to a tee however, instead of the X61 BIOS ISO, I created an ISO from the SuperMicro Drivers using ISO Master (in the repos), copied those files, then repeated the copy process with a Windows98SE boot disk ISO I got from [http://www.allbootdisks.com/download/iso.html](http://www.allbootdisks.com/download/iso.html).

Best.  How-to.  Ever.


Ciao!

---

### Post by schmolch on 2008-08-04
I tried to update the BIOS of my Thinkpad X60T but it failed.

I booted the USB-Stick and got into the Setup.
When i chose to update the BIOS i got this message that says "this will take a minute, dont turn off your computer blablabla..." and about 10 seconds later my whole screen was flashing with "invalid opcode blablabla, DIE DIE DIE...",
Needless to say that i was scared shitless since this tablet-pc is really important to me because i do all my stuff for university on it.

Anyways, its still working.
Not sure if i want to investigate this, im still scared.

I still want to thank you though because i tried several of these "how to update your bios without windows" guides and never got this far.

---

### Post by millerl on 2008-08-04
> **mbsullivan said:**
> Glad to hear it! 

Did you use the Windows or Linux instructions? I want to make sure the Linux ones are understandable and have no bugs (they're fairly new).

Mike

Unfortunately, laziness prevailed and I used the running windows box in the next room...

---

### Post by mbsullivan on 2008-08-05
> Thank you so much. With very little modification, I was able to use this to upgrade the BIOS on a SuperMicro server board. Thanks to the result of this little how-to, you've helped put an end to 9 days of torment. I can finally go home. Thank you.

I'm glad to hear it worked for you! It seems that booting to a USB key should be so simple, but it's a bit more involved than it perhaps should be. It's good to hear that the instructions work for other ISOs, too.

> 
I booted the USB-Stick and got into the Setup.
When i chose to update the BIOS i got this message that says "this will take a minute, dont turn off your computer blablabla..." and about 10 seconds later my whole screen was flashing with "invalid opcode blablabla, DIE DIE DIE...",
Needless to say that i was scared shitless since this tablet-pc is really important to me because i do all my stuff for university on it.


Wow, that is indeed frightening! I would probably mess myself if that happened to me. I'm happy to hear that your tablet was not destroyed... lucky! 

As for the problem, did you perhaps use the X61 ISO instead of the tablet one? There is a special ISO for the X61 tablet, which is still at a much earlier version (1.17, 2008/06/13). It is available [here]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68006"). 

My guess is that the Tablet BIOS CD should work fine... that being said, nobody's tried it yet. If this is, in fact, what you were experiencing, then I should really add a warning to the tutorial.  Thanks for the input!

**EDIT*: I just read the tutorial again, and I see that I say it will work for the X series tablet in the first sentence, but then never give a link to the tablet ISO. I'm very sorry about that. I have revised the tutorial.*

Mike

---

### Post by tarlipe on 2008-08-07
> **mbsullivan said:**
> This tutorial details how to upgrade the BIOS of a Thinkpad x61, x61s or x61s tablet notebook using a bootable USB stick. At the time of writing, the 2.14 BIOS and 1.03 firmware versions are the most current for the X61/X61s. Also, the most current BIOS and firmware versions for the ThinkPad X61 Tablet are 1.17 and 1.02, respectively.

*Disclaimer: While these steps worked for me while upgrading my X61 BIOS from 1.06 to 2.07, and later from 2.07 to 2.14, use them at your own discretion. BIOS upgrades always carry some associated risk, and I cannot be held liable for anything that goes wrong.*

**[SIZE="4"]Motivation[/SIZE]**

The Thinkpad x61 is an ultralight notebook offered by Lenovo. As any x61 owners should know, the internal optical drive present in most laptops was omitted from the x61 in order to minimize weight.

Regular BIOS upgrades have been offered by Lenovo for the x61, and are released without charge in two forms:

[INDENT]**X61/X61s:**
1. A [Win32-only  executable]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-67982")
2. A bootable [DOS CD-ROM disc]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-67983")[/INDENT] 


[INDENT]**X61 Tablet:**
1. A [Win32-only  executable]("http://www-307.ibm.com/pc/support/site.wss/MIGR-68005.html")
2. A bootable [DOS CD-ROM disc]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68006")[/INDENT] 

The bootable CD-ROM disc is the only option available for GNU/Linux users. Ridiculously enough, USB CD-ROM drivers are not included on the disk, such that external CD-ROM drives will **[COLOR="Red"]not[/COLOR]** work with the BIOS upgrade. Not even the Lenovo Thinkpad USB CD-ROM drive allows the user to upgrade the BIOS.

Officially, the supported method for an x61 upgrade on a non-Win32 platform is to use the CD-ROM drive in an ultrabase. Those of us who don't have one are left in the dark. In this tutorial, I will show how to upgrade the x61 BIOS from a bootable USB stick.

**[SIZE="4"]Why Upgrade the BIOS[/SIZE]**

Although the stock BIOS shipped with most x61 laptops may be fine for most users, the newest BIOS (2.07), which was released in January, offers an improved fan speed controller. It also fixes USB interrupt bugs present in previous releases, which have manifested themselves as problems with the right-side USB ports (see [here]("http://ubuntuforums.org/showthread.php?t=658065&highlight=USB") and [here]("http://ubuntuforums.org/showthread.php?p=4083012&posted=1#post4083012")). Later BIOS revisions have dealt with other firmware bugs, such as WOL (Wake on LAN) errors, POST issues and CardBus and 1394 bugs. 

That being said, a BIOS upgrade not a necessity. There are workarounds for the problems it fixes (I provide a hack for the USB devices, for example, in the previous two hyperlinked posts). Of course, the newest BIOS and firmware versions are preferable, however, so without further ado...

**[SIZE="4"]How to Upgrade the Thinkpad x61 BIOS with a USB Thumb Drive[/SIZE]**

The rest of this tutorial shows how to upgrade the Thinkpad BIOS to the newest version under Linux or Windows without an internal CD-ROM drive. The basic steps involved are:

[INDENT]1. Format the USB stick to be a DOS boot device
2. Copy the bootable ISO BIOS files to the USB stick
3. Boot to the USB stick and follow instructions[/INDENT]

Instructions for Step 1 are given for upgrading under Windows as well as Linux. Although it may be distasteful to an Ubuntu user, [COLOR="Red"]the instructions for upgrading on a Windows machine are simpler and carry less risk[/COLOR]. However, should one be unable or unwilling to use a Windows machine, they may jump to the section entitled "**Format the USB stick to be a DOS boot device (Linux)**".

**[SIZE="4"]1. Format the USB stick to be a DOS boot device (Windows)[/SIZE]**

There are [multiple ways]("http://www.bootdisk.com/pendrive.htm") to do this step, I'm taking the easiest route I know: the HP USB Disk Storage Format Tool combined with Win98 DOS boot disc files.

First, connect a USB stick and backup any important files: we are going to format the device, which will lose any information you have on it.

Next, get the HP USB Disk Storage Format Tool (from [here]("http://www.bootdisk.com/plan30/hpflash1.zip") or HPUSBFW.zip attached to this tutorial). Run HPUSBFW.EXE and select the FAT (FAT16) filesystem and "Create a DOS Startup Disc". 

Under "using DOS system files located at", provide a directory containing a valid DOS boot disc. I have attached the appropriate files for a Win98 DOS boot disc to this tutorial, in win98boot.zip. They should also be available [here]("http://files.extremeoverclocking.com/file.php?f=196") .

Click "Start" to format the USB into a bootable DOS-wielding device. If this process worked, then skip to the section entitled "**2. Copy the bootable ISO BIOS files to the USB stick**".

**[SIZE="4"]1. Format the USB stick to be a DOS boot device (Linux)[/SIZE]**

First, insert your USB stick and determine what device it is assigned to. This is fairly simple by looking at the output of:

```
sudo fdisk -l
```

For a device which is the same size as your USB stick and formatted (presumably) as Fat32 or Fat16. Normally the device will be in the form /dev/sdb or /dev/sdc, etc.

*Note: It is critical that you get the name of your usb device correct, and always type it accurately. If you use the device name of another harddrive, you could very easily end up wiping other, unrelated disks. For that reason, I'm always going to use the identifier [USB device] for the device name of your specific USB drive.*

After you have discovered your USB stick device name, set up a bootable Fat16 partition on the USB stick. There are multiple ways to do this (users familiar with parted/gparted may want to go that route). The simplest way, IMHO, is to enter the following command into a terminal window:

```
sudo cfdisk [USB device]
```

Then, set up a "New" "Primary" partition filling the whole disc, make it "Bootable", and set the type to "0E" [W95 FAT16 (LBA)]. The "Write" the partition table to the USB drive.

Next, format the newly created partition as a FAT16 drive. To do this, run the following in a terminal window:

```
sudo mkdosfs -F 16 -vc [USB device]1
```

This may take a couple of minutes, unless your USB stick is on the smaller side.

Now we are going to set the drive to be bootable, using FreeDOS system files. In order to make the USB drive bootable, we are going to use **makebootfat**. Because it is not (yet) in the Ubuntu repositories, you must compile and install it yourself, from source code. Alternatively, as described below, you may use a .deb file that I created.

**Using a precompiled package for makebootfat:**

Compiling makebootfat requires various packages that are required to build C programs from source. For lazy users or those who cannot or will not install the necessary requirements, I have attached a debian package (.deb) to this post (entitled "makebootfat_1.4-1ubuntu0_i386.deb
"). I accept no liability for your use of this package. However, should you want to, it is installable through the following command:

```
sudo dpkg -i makebootfat_1.4-1ubuntu0_i386.deb
```

If you have installed makebootfat through the attached .deb file, you may jump to the section entitled "**Create the Bootable USB Device**".

**Building makebootfat from source:**

In order to compile and build makebootfat yourself, get the project source code (labelled "makebootfat-1.4.tar.gz (0.1 MB)") [here]("http://advancemame.sourceforge.net/boot-download.html"). I am also attaching the source code to this forum post, for reasons explained below.

*Note: This tutorial is written using makebootfat 1.4, which is protected under the GPL. On the off chance that future versions of the program stop working for our purposes, the source code for v1.4 is attached at the bottom of this post.*

The process for installing makebootfat is the same as most projects that must be built from source:

```
[in directory containing makebootfat-1.4.tar.gz]
tar -xzf makebootfat-1.4.tar.gz 
cd makebootfat-1.4
./configure
make
sudo make install
```

This should install the project binary (makebootfat) to /usr/bin/makebootfat.

**Create the Bootable USB Device**

Now, we use makebootfat to create a bootable DOS USB stick. These instructions use draw files from the [FreeDOS]("http://www.freedos.org/") and [SYSLINUX]("http://syslinux.zytor.com/wiki/index.php/The_SYSLINUX_Project") projects. In order to simplify everything, I have attached a tarball (linboot.tar.gz) that contains the files you need in order to upgrade the x61 BIOS. To get a better feel for where these files come from (and why) read [this article]("http://ben.franske.com/blogs/2007/08/21/booting_dos_from_a_usb_flash_drive").

Download the essential configuration and system files, extract them, and go to that folder:

```
tar -xzf linboot.tar.gz
cd linboot
```

Now, make the USB drive bootable with the provided master boot record settings (mbr.bin), and the boot sector images (fat*.bin). Also, provide the FreeDOS system files:

```
sudo makebootfat -o usb -E 255 -1 fat12.bin -2 fat16.bin -3 fat32lba.bin -m mbr.bin freedos
```

This will prepare the USB stick as a bootable device ready for the remainder of the X61 BIOS installation procedure.

**[SIZE="4"]2. Copy the bootable ISO BIOS files to the USB stick[/SIZE]**

This step is very simple: just copy all of the files from the bootable BIOS CD provided by Lenovo onto the USB stick. The ISO file can be found for the X61/X61s [here]("http://www-307.ibm.com/pc/support/site.wss/license.do?filename=mobiles/7nuj10uc.iso"), and for the X61 Tablet [here]("ftp://ftp.software.ibm.com/pc/pccbbs/mobiles/7suj11uc.iso").  

This can be done many different ways. In Windows, one must first mount the .iso file (which can be done using any of a number of different free [programs]("http://www.google.com/search?hl=en&client=firefox-a&channel=s&rls=com.ubuntu%3Aen-US%3Aofficial&hs=Gyr&q=windows+mount+iso&btnG=Search")) and then copy the files over. 

In Linux, the ISO may be trivially mounted and copied from the command line:

```
sudo mount -o loop [path to ISO file] [mount point]
sudo cp -f [mount point]/* [path to USB folder]
```

It should be noted that the default DOS command-line interpreter (COMMAND.COM), if present, **[COLOR="Red"]should[/COLOR]** be overwritten by the (much smaller) version provided by Lenovo.

**[SIZE="4"]3. Boot to the USB stick and follow instructions[/SIZE]**

This step should pretty much be self-explanatory. Make sure to set the boot priority of the USB device to be higher than your internal hard drive, and then reboot! 

***Note: With BIOS revision 2.14, after booting to the USB device, the system may query for the location of the "COMMAND.COM" file. Should this happen to you, entering 'command.com' (without quotes) will allow you to proceed to the BIOS upgrade.*** 

Follow the on-screen instructions, and your BIOS should be upgraded within 5 minutes. As always with BIOS upgrades, do **[COLOR="Red"]not[/COLOR]** under any circumstances turn the laptop off before installation is complete, or you could turn your laptop into a very expensive paperweight.

That's it! Please let me know if you have any questions.

Mike



**Revision History:**
[INDENT]1.0.0 - Original post (June 4th, 2008)
  1.0.1 - Updated for BIOS revision X61/61s 2.14, Added "1. Format the USB stick to be a DOS boot device (Linux)" (July 30th, 2008)
  1.0.2 - Added ISO links for the X61 Tablet (August 5th, 2008)[/INDENT]
Hello guys,

I've tried to upgrade my X61 BIOS from version 2.07 to 2.14 and get the following output while trying to write the update:

"Invalid Opcode at 3A29....
Invalid Opcode at 3A29....
Invalid Opcode at 3A29....
Invalid Opcode at 3A29....
" in an endless loop until I pressed and hold the power button.

Thanks a lot in advance for any clue.

Tarlipe

---

### Post by mbsullivan on 2008-08-08
> **tarlipe said:**
> Hello guys,

I've tried to upgrade my X61 BIOS from version 2.07 to 2.14 and get the following output while trying to write the update:

"Invalid Opcode at 3A29....
Invalid Opcode at 3A29....
Invalid Opcode at 3A29....
Invalid Opcode at 3A29....
" in an endless loop until I pressed and hold the power button.

Thanks a lot in advance for any clue.

Tarlipe

Hi Tarlipe,

Are you using a Tablet or a regular X61? Also, did you use the Windows or Linux version for step #1?

Mike

---

### Post by schmolch on 2008-08-08
> **mbsullivan said:**
> 
As for the problem, did you perhaps use the X61 ISO instead of the tablet one? There is a special ISO for the X61 tablet, which is still at a much earlier version (1.17, 2008/06/13). It is available [here]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68006"). 


I used the correct iso. I have the product-number of my x60t memorized (6363-a7g) and just enter that on the support & download section which brings me to the x60t page from where i pick the bios-iso.

Common sense would ask to simply repeat the whole procedure but i don't really need a bios-update and don't want to take the risk.

---

### Post by tarlipe on 2008-08-08
> **mbsullivan said:**
> Hi Tarlipe,

Are you using a Tablet or a regular X61? Also, did you use the Windows or Linux version for step #1?

Mike
I did the Linux version for step#1. Should I try on windows?

thanks for your answer

---

### Post by tarlipe on 2008-08-08
With the windows version for step#1, it worked like a charm!
It just need to type command.com and everything went right.

Thank you.

---

### Post by mbsullivan on 2008-08-09
> **tarlipe said:**
> With the windows version for step#1, it worked like a charm!
It just need to type command.com and everything went right.

Thank you.

... That is both good and bad news (for me, anyway). This means the Linux upgrade instructions are flawed, somehow. 

They worked for me (upgrade from 2.07 to 2.14 on an X61), but there must be some problem. I will try to investigate.

Mike

---

### Post by mbsullivan on 2008-08-09
Hi all,

While I was not able to reproduce the errors found by schmolch and tarlipe exactly (since I already have BIOS 2.14 running), I did poke around with downgrading to a previous BIOS version, following the Linux instructions exactly. 

There is some problem with the Linux portion of the instructions. Until I figure it out, I've removed those instructions from the tutorial.

Mike

---

### Post by pengo_au on 2008-09-01
Updated a Thinkpad x61 bios successfully from version 1.11 to 2.16. Many thanks.

Might be worth noting, however, after step 1 that you should **NOT** copy up the remaining files from win98boot.zip -- the 3 system files that are copied up by the formatter are all you need in step 1.

I (stupidly) copied up *all* the files from win98boot.zip (and then the files from the CD) and got stuck in an endless win98 boot screen. I tried again and only copied up files form the CD and it worked fine.

Pengo.

---

### Post by openmoho on 2008-11-04
it didn't work for me here. i got a blank screen with a blinking cursor, when i tried to type command.com grub appeared and booted into ubuntu. any help?

---

### Post by beneficity on 2009-02-02
Thank you

---

### Post by spreeendaz on 2009-05-13
Do you know if I can also rollback/downgrade that way ? The new Embedded Controller is blocking my non-IBM battery (new battery "management" I guess) and I'd like to be able to use my battery once again.

---

### Post by mbsullivan on 2009-05-14
> **spreeendaz said:**
> Do you know if I can also rollback/downgrade that way ? The new Embedded Controller is blocking my non-IBM battery (new battery "management" I guess) and I'd like to be able to use my battery once again.

I can't promise you anything, but my guess is that it will work. In the past, I repeatedly flashed between two versions in order to test different methods (definitely *not* recommended, but I was curious).

If you try it, let me know!
Mike

---

### Post by spreeendaz on 2009-05-18
> **mbsullivan said:**
> I can't promise you anything, but my guess is that it will work. In the past, I repeatedly flashed between two versions in order to test different methods (definitely *not* recommended, but I was curious).

If you try it, let me know!
Mike

I should add the following information to my previous interrogation:

"Notes
If you update to the BIOS version 2.06-1.03 or later, you are not able to get back to the older BIOS versions."

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-67982](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-67982)

Do you still think it's doable even if I have version 1.11 ?

---

### Post by mbsullivan on 2009-05-27
> I should add the following information to my previous interrogation:

"Notes
If you update to the BIOS version 2.06-1.03 or later, you are not able to get back to the older BIOS versions."

[http://www-307.ibm.com/pc/support/si...cid=MIGR-67982](http://www-307.ibm.com/pc/support/si...cid=MIGR-67982)

Do you still think it's doable even if I have version 1.11 ?

That might change things... thanks for bringing it to my attention. But I don't think so. I assume you have an x61/x61s, you have a BIOS installed which is after 2.06/1.03, and you want to roll back to 1.11/1.02?

The way I interpret their message, I'm guessing that will be impossible. I'm *not* sure what would happen if you tried... It could be anything. Given the new developments, I guess I would err on the side of caution if I were you.

The only BIOSes I went back and forth between were 2.14 and 2.07. I never went as far back as 1.11, though, so I can't lend any personal experience.

Mike

---

### Post by mbsullivan on 2009-05-27
****UPDATE****

I just updated the tutorial with information from the most recent BIOS, and included a new method which works without a Windows machine.

I used the new procedure to successfully flash from 2.14 to 2.20 on an x61. 

The update fixed an issue that had crept up with recent kernels, where bootup would freeze after the message:

```
ACPI: Checking initramfs for custom DSDT
```

With the new firmware, I no longer need my previous workaround of the noapic and nolapic kernel options.

I would appreciate feedback from anybody who flashes to a new BIOS, especially if you try the new Linux-based procedure.

Let me know if you have any questions!
Mike

---

### Post by spreeendaz on 2009-05-31
> **mbsullivan said:**
> That might change things... thanks for bringing it to my attention. But I don't think so. I assume you have an x61/x61s, you have a BIOS installed which is after 2.06/1.03, and you want to roll back to 1.11/1.02?

The way I interpret their message, I'm guessing that will be impossible. I'm *not* sure what would happen if you tried... It could be anything. Given the new developments, I guess I would err on the side of caution if I were you.

The only BIOSes I went back and forth between were 2.14 and 2.07. I never went as far back as 1.11, though, so I can't lend any personal experience.

Mike

I am a bit confused with the notation here. I have the 1.11 version, which is higher than 1.03. Does it mean I can't rollback ? Does the 1.xx updates notation apply to the first version of the BIOS and 2.xx to the second edition ? So the 1.11 version has nothing to do with being lower than 2.06, since they are in two different series, but is higher than 1.03, so I can't rollback ?

---

### Post by mbsullivan on 2009-06-01
> 
I am a bit confused with the notation here. I have the 1.11 version, which is higher than 1.03. 

There are two numbers associated with every BIOS release. The first is the BIOS version number (current version: 2.20), and the second is the embedded controller version (current version: 1.03). When I put a slash between versions (like "2.20/1.03"), I'm referring to a BIOS/embedded controller pair. See the table at the bottom of [this page]("http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-67983") for the version history.

> Does it mean I can't rollback?

If I'm understanding it correctly, then "no, you can't rollback". It is my guess that because you have 1.11/1.02, then upgrading to any BIOS revision associated with the 1.03 embedded controller will prevent you from downgrading to one with an earlier version of the embedded controller. Therefore, upgrading to *any* newer version will prevent you from going back to any BIOS earlier than 2.06/1.03.

Hope this helps!
Mike

PS: You said the following previously:

> The new Embedded Controller is blocking my non-IBM battery (new battery "management" I guess) and I'd like to be able to use my battery once again.

How do you know that the embedded controller is the one causing problems with your battery? If you have 1.11/1.02 installed right now, then:

1. You don't have the newest embedded controller. Upgrading might fix your problem.
2. There's no public BIOS release with an *older* embedded controller. Every release other than the very first BIOS has v1.02 or newer... So I don't see how you could ever downgrade to something earlier.

I guess I don't understand your problem -- if your battery is already broken by 1.11/1.02, then I don't see why you'd have to worry about rolling back to it.

---

### Post by PetePhillips on 2009-06-06
Hi

First of all, i used the tutorial to upgrade my X61s from 1.06-2.20 and it has worked perfectly as far as i can tell. The BIOS reports 2.20. Excellent stuff.

One thing I didn't understand - when the USB stick boots, there is a menu with 3 options. 0 was cancel (i think), so I selected option 1, expecting to be go back to the menu. However, after a VERY loud beep (after the first minute or so) it then says it will take another minute, then you get another beep (quite disconcerting!), and then it asks you to remove the CD and select the reboot option (or whatever term it uses).

I did this and it then clearly goes through some internal checks, then rebooted OK.  

My question is what is the third option (option 2) which I *think* refers to updating the model number ? Is it necessary to rerun the procedure and select the 2nd option ?

Pete

---

### Post by mbsullivan on 2009-06-08
> My question is what is the third option (option 2) which I *think* refers to updating the model number ? Is it necessary to rerun the procedure and select the 2nd option ?

No, this option is unnecessary. It's most likely for corporate users. 

It sounds like you selected the right option, and successfully upgraded your BIOS. Congrats!!!

Mike

PS: Which method did you use, the Windows or Linux version?

---

### Post by PetePhillips on 2009-06-08
> **mbsullivan said:**
> 

PS: Which method did you use, the Windows or Linux version?

The Linux version (of course!).

Pete

---

### Post by mbsullivan on 2009-06-08
> 
The Linux version (of course!).

Pete

Excellent! You're the first one to have tried it (and told me), apart from myself. I'm glad it worked!

Just out of curiosity, how big was the thumb drive that you loaded the image onto?

Mike

---

### Post by PetePhillips on 2009-06-10
2Gb

(hadn't realised i was being a trail blazer! <gulp>)

Pete

---

### Post by nswilliams on 2009-06-16
Linux only instructions worked fine for me. I did find these instructions a little ambiguous at first though:
sudo mount -o loop [path to ISO file] [mount point]
sudo cp -af [mount point]/* [path to USB folder]

---

### Post by mbsullivan on 2009-06-16
> **nswilliams said:**
> Linux only instructions worked fine for me. I did find these instructions a little ambiguous at first though:
sudo mount -o loop [path to ISO file] [mount point]
sudo cp -af [mount point]/* [path to USB folder]

I'm glad it worked! Thanks for the feedback... 

I added the following sentence after the code snippet. Do you think it helps?

> Where *[path to ISO file]* is the path to the CD ISO image, *[mount point]* is wherever you want to mount the CD image to (you can choose this, */cdrom/* works), and *[path to USB folder]* is the location of your mounted USB drive.

Mike

---

### Post by cprov on 2009-07-31
Excellent! It worked perfectly. Thanks a lot.

---

### Post by drear on 2009-11-03
Good instructions, thank you.  Flashed my x60s and everything worked out fine.

---

### Post by sunny_s on 2010-02-09
Excellent! I have flashed my x61 tablet from 1.23 to 1.24 and it is working perfectly. Thanks a lot.
(Linux method)

---

### Post by SaintDanBert on 2010-02-09
For those who are interested, there is a fresh, Thinkpad X61 and X61-tablet BIOS update available in January 2010. Visit [ http://www.lenovo.com ]( http://www.lenovo.com ) for download.

Cheers,
~~~ 0;-Dan

---

### Post by mbsullivan on 2010-06-08
> 
For those who are interested, there is a fresh, Thinkpad X61 and X61-tablet BIOS update available in January 2010. Visit [http://www.lenovo.com](http://www.lenovo.com) for download.

Cheers,
~~~ 0;-Dan

Hi Dan,

Thanks for the update! I didn't find any BIOSes from January 2010, though. The newest I could find were (2.21, 11/4/2009) for the X61/X61s and (1.24, 11/9/2009) for the X61 tablet.

I updated the links for those BIOSes, though. Could you post the exact links for the BIOS updates you were referring to?

Mike

---

### Post by guybrand on 2010-07-29
Thank you for these instructions, they worked for me to upgrade my Lenovo ThinkPad X61s using the Linux way to upgrade from BIOS revision 1.02 to revision 2.21:

Jul 29 10:56:22 kernel: thinkpad_acpi: ThinkPad BIOS 7NET21WW (1.02 )
...
Jul 29 11:44:45 kernel: thinkpad_acpi: ThinkPad BIOS 7NETC1WW (2.21 )

I used a 1 GB USB key and copied the win98usb.img with dd without problem (getting this image from this forum was the step that took the longest time!).

---

### Post by mbsullivan on 2010-08-01
> 
Thank you for these instructions, they worked for me to upgrade my Lenovo ThinkPad X61s using the Linux way to upgrade from BIOS revision 1.02 to revision 2.21:

Jul 29 10:56:22 kernel: thinkpad_acpi: ThinkPad BIOS 7NET21WW (1.02 )
...
Jul 29 11:44:45 kernel: thinkpad_acpi: ThinkPad BIOS 7NETC1WW (2.21 )



Wow, that's quite a jump... I'm glad it worked for you!

> 
I used a 1 GB USB key and copied the win98usb.img with dd without problem 

Thanks for the info!

Mike

---

### Post by rocksockdoc on 2010-08-14
Hi Mike,  

Can someone help me debug why this procedure failed for me?  

I'm very experienced with computers but this is my first of everything here (my first experience with the X61 tablet PC, Ubuntu 10.04, & flashing its BIOS) and even my first post to this forum (which I found by googling for how to update the BIOS).  I read EVERY post in this thread; and I followed the Windows installation instructions (logged below). (I have flashed BIOS's before but never had this problem and never from a USB stick and never with anything other than Windows.)

The problem is when I tried to boot to the USB flash drive on my Lenovo X61 (model number 7762B6U), I got a black screen with a flashing dash prompt at the top left corner, which, even after an hour, remained unchanged.   

Twice this black-screen-flashing-dash-prompt happened and I had to pull the plug both times (a scary thing given the warnings here about interrupting the BIOS upgrade).   

Can you help me debug? Here is a log file of what I did so far following your instructions whenever I could (deviations are noted when/where they occur; I suggest we improve the instructions even further for the items noted below so others don't have this problem).  

Thanks!

============================================================================
How I tried to flash my Lenovo X61 tablet (model number 7762-B6U) BIOS:
============================================================================
Summary:
- I followed instructions and had a couple of minor problems following them, 
  but overall didn't deviate much; but the end result was a black screen with
  a dash prompt which didn't go away. Tried twice and failed both times.
----------------------------------------------------------------------------
Environment:
- WinXP PC: Newly re-installed Windows XP (service pack 2) Dell laptop
- Linux PC: Lenovo X61, Model 7762 B6U, BIOS/EC 1.04/1.02, Ubuntu 10.04 Lucid
----------------------------------------------------------------------------
Problem Summary (major):
- Failed to boot from the USB drive to flash the BIOS. Nothing happened.
----------------------------------------------------------------------------
Problem Summary (minor):
  Note: Nowhere does the Lenovo X61 PC say it's a "tablet" but it has the pen 
  & swivel screen so I used the X61 tablet BIOS files (7suj18uc.iso).
  Note: I first tried an 8GB flash stick but the HPUSBFW tool reported:
        "Error: Volume is too big" 
  The final flash drive space used was 6.75 MB on my 4GB SanDisk flash drive.
  Note: The SanDisk flash drive had U3 removed long ago & has been formatted
        many times since.
  Note: The COMMAND.COM originally copied to the flash drive must have had
        the read-only bit set because the copy of the ISO contents didn't
        overwrite it even after I said "Yes" multiple times. I had to delete
        it and copy over the COMMAND.COM separately. The instructions aren't
        really clear on this point. They say you "should" overwrite the larger
        HP COMMAND.COM with the smaller Lenovo COMMAND.COM so I assumed I 
        "must" overwrite it; hence the need to delete it because the "Yes"
        (which should have worked), didn't work. :(
Note: A very minor problem is that the instructions are backwards when it comes
to the creation of the USB stick. The instructions are in the forward direction
in my notes below but that's only because I had to mentally switch the 
tasks midstream. They were explained well; just not in the order of 
occurrence. It's not a big deal; but it's worthy of note.
----------------------------------------------------------------------------
Loaded the USB drive from Windows XP SP2:
- Downloaded "Win98 DOS boot disc" files (win98boot.zip) to my XP hard drive;
- Extracted by clicking on "win98boot.zip" (which created win98boot); 
  [http://start.ubuntuforums.org/attachment.php?attachmentid=72888&d=1212559077](http://start.ubuntuforums.org/attachment.php?attachmentid=72888&d=1212559077)
- Made a note of the location of the resulting directory:
  (e.g., C:\tmp\win98boot)
- First plugged a blank 8GB SanDisk USB stick into the WinXP PC but that 
  failed in a step later so redid these steps with a 4 GB SanDisk USB stick;
- Downloaded "HP USB Disk Storage Format Tool" (HPUSBFW.zip) 
- Extracted the "HP USB Disk Storage Format Tool" (C:\tmp\HPUSBFW);
  [http://start.ubuntuforums.org/attachment.php?attachmentid=72887&d=1212559077](http://start.ubuntuforums.org/attachment.php?attachmentid=72887&d=1212559077)
- Doubleclicked on the C:\tmp\HPUSBFW\HPUSBFW.EXE executable to bring up the GUI;
- Selected FAT (FAT16) filesystem; & "Create a DOS Startup Disc";
- Under "using DOS system files located at", pointed to the "win98boot" folder;
- Clicked "Start" to format the USB into a bootable DOS-wielding device;
- Three files of 384KB total size resulted: 
  (command.com, io.sys, mosdos.sys);
  Note: The read-only permission of command.com caused problems later so
  in hindsight, I probably should have run "C:\> attrib -r E:\command.com".
- Downloaded the Lenovo "BIOS Update Bootable CD" files onto the WinXP PC;
  X61 tablet Make a note of the resulting location (e.g., C:\path\7suj18uc.iso):
   [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68006](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-68006)

  I assume (since the X61 has a pen and swivel monitor) it's an X61 tablet
  so that's why I did NOT use the X61/X61s files shown below:
  X61/X61s (7nuj21uc.iso);
   [http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-67983](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-67983)
- Created a directory to store the MS Virtual Control Panel files:
  (e.g., C:\tmp\winxpvirtualcdcontrolpanel)
- Downloaded a program to allow WinXP mounting of ISO images as a virtual CD:
  Microsoft Virtual CD-ROM Control Panel v2.0.1.1 
  [http://download.microsoft.com/download/7/b/6/7b6abd84-7841-4978-96f5-bd58df02efa2/winxpvirtualcdcontrolpanel_21.exe](http://download.microsoft.com/download/7/b/6/7b6abd84-7841-4978-96f5-bd58df02efa2/winxpvirtualcdcontrolpanel_21.exe)
- Doubleclicked on the winxpvirtualcdcontrolpanel_21.exe to unpack the 3 files;
  (readme.txt, VCdControlTool.exe, & VCdRom.sys)
- Copied VCdRom.sys to the WinXP SP2 %systemroot%\system32\drivers folder;
- Doubleclicked on the C:\path\VcdControlTool.exe to bring up the GUI;
- Pressed the "Driver control" button & then the "Install Driver" button;
- Pointed it to %systemroot%\system32\drivers\VCdRom.sys & pressed "Open";
- Pressed the "Start" and "OK" buttons;
- Pressed the "Add Drive" button which added a "Z:" drive;
- Selected that Z: drive and pressed the "Mount" button;
- Navigated to your Lenovo ISO image (c:\path\7suj18uc.iso) & pressed "Open";
- This mounted the ISO as a "CD Drive" named:
  7SET38WW (Z:) CD Drive
- Opened up a WinXP command window 
- Copied the mounted ISO files to the USB stick:
  Start -> Run -> cmd
  C:\> copy z:\*.* e:\
- You should see the message "32 file (s) copied";
- Note: At first, I got the write-permission error (even though I said "Yes"):
  ...
   z:\CHKBMP.EXE
   z:\COMMAND.COM
   Overwrite e:\COMMAND.COM? (Yes/No/All): y
   Access is denied.
   z:\FLASH2.EXE
   z:\lcreflsh.bat
   ...
       31 file(s) copied.
  ... 
- Note: I had to delete the old HP command.com because the instructions 
  aren't clear whether you want to overwrite the HP command.com with the 
  Lenovo command.com (they say "should" so I assumed it "must" be done).
  The resulting Lenovo E:\COMMAND.COM was 8 KB (not the 92 KB HP COMMAND.COM);
- The resulting amount of space used on the flash card was 6.75MB;
----------------------------------------------------------------------------
- I shut down the Lenovo X61 Ubuntu 10.04 Lucid machine;
- At first, I left the flash drive in place when I let it reboot but it hung
  with the black screen and permanent dash prompt; so I thought better of that
  the second time and REMOVED the flash drive and did a complete power down.
- Powered on the X61 
- Pressed the blue "Thinkvantage" button at the ThinkVantage/Lenovo/Intel screen;
- Pressed "F1" to enter the BIOS setup;
- Navigated to the BIOS "Startup" and then to the "Boot" screen;
  Note: I wasn't sure which of the three USB options is a flash drive:
  With the flash drive in, the available USB options were:
        - +USB HDD 
        - USB CD
        - USB FDD
  With the flash drive NOT in, the available USB options were:
        - -USB HDD 
        - USB CD
        - USB FDD
  I don't understand what the plus & minus means but I put the "-USB HDD"
  in the number one position (let me know if that's not the right thing to do).
- I wrote down the BIOS & Embedded Controller versions:
  BIOS 1.04 (7SET18WW) 2007-07-03
  Embedded Controller Version 1.02 
- I powered off the X61 (at first I just let it reboot but that failed with 
  the black-screen-left-corner-prompt, so this time I powered off the X61! 
- With the X61 powered off, I placed the USB drive in the #1 slot:
  Note: I am using a SanDisk 4GB with NO U3 software (U3 was deleted & 
  the USB stick has been formatted many times since U3 was deleted);
- I powered up the X61 in order to follow the on-screen instructions to 
  flash the BIOS.

Results:
- In both attempts, the screen was black with a blinking dash prompt at the 
  top left corner and remained this way for an hour the first time and for
  ten minutes the second time until I had to power it down and try again.

Potential problems:
- I'm asking if you have any idea WHERE the potential problems might be?
  (I will try the Linux method next but I don't want an X61 brick so that's
  why I'm asking first).

TIA
============================================================================
============================================================================

---

### Post by rocksockdoc on 2010-08-15
> **rocksockdoc said:**
> when I tried to boot to the USB flash drive on my Lenovo X61 (model number 7762B6U), I got a black screen with a flashing dash prompt

I waited for help on the Windoze side but it looks like it's not forthcoming so I tried flashing the wholly Ubuntu procedure Mike outlined. Since I'm new to Linux (not new to operating systems, just new to Linux), can someone help me here...

I'm stuck at the last step of creating the USB stick files:

rocksockdoc@ubuntu:~/tmp/flashbios$ sudo fdisk -l
...
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         490     3928032    e  W95 FAT16 (LBA)
...

rocksockdoc@ubuntu:~/tmp/flashbios$ sudo cp -af /cdrom/* /dev/sdb1
cp: target `/dev/sdb1' is not a directory


What am I doing wrong?

---

### Post by rocksockdoc on 2010-08-15
In order for you to better help me, here are the details regarding the plea for help above:

GOAL: Flash Lenovo X61 tablet PC using only Linux and a USB stick following
the Linux-only instructions at: [http://ubuntuforums.org/showthread.php?t=817897](http://ubuntuforums.org/showthread.php?t=817897)
---
Placed a Windoze formatted 4GB SanDisk USB stick in the X61 tablet PC
left-side USB slot. The USB icon showed up on the Ubuntu 10.04 desktop.
---
$ sudo fdisk -l
Reported:
/dev/sdb1 ...  W95 FAT16 (LBA)
---
Obtained win98usb.tar from:
[http://ubuntuforums.org/attachment.php?attachmentid=115376&d=1243462998](http://ubuntuforums.org/attachment.php?attachmentid=115376&d=1243462998)
---
$ tar -xf ./win98usb.tar
$ ls -a win98usb.img
Reported:
-rw-r--r-- 1 x x 621568 2009-05-27 14:14 win98usb.img
---
$ umount -f /dev/sdb1
This removed the USB stick icon from the desktop
---
$ sudo dd if=win98usb.img of=/dev/sdb1 conv=notrunc
Reported:
rocksockdoc@ubuntu:~/tmp/flashbios$ sudo dd if=win98usb.img of=/dev/sdb1 conv=notrunc1214+0 records in
1214+0 records out
621568 bytes (622 kB) copied, 0.88862 s, 699 kB/s
---
$ sudo mount -o loop `pwd`/7suj18uc.iso /cdrom/
$ ls /cdrom/
Reports:
  lots of files ...   COMMAND.COM   PREPARE.EXE   UTILINFO.EXE ... etc.
---
$ sudo cp -af /cdrom/* /dev/sdb1
Reported:
cp: target `/dev/sdb1' is not a directory
---
$ sudo cp -af /cdrom/* /dev/sdb1/
Reported:
cp: accessing `/dev/sdb1/': Not a directory
---
$ sudo cp -af /cdrom/* /dev/sdb1/*
Reported:
cp: accessing `/dev/sdb1/*': Not a directory
---
$ cp: accessing `/dev/sdb1/cdrom': Not a directory
---

I followed the instructions exactly (I think).
[http://ubuntuforums.org/showthread.php?t=817897](http://ubuntuforums.org/showthread.php?t=817897)

What am I doing wrong?

---

### Post by mbsullivan on 2010-08-16
Hi rocksockdoc,

That's quite a detailed description! So, going through:

> Note: Nowhere does the Lenovo X61 PC say it's a "tablet" but it has the pen & swivel screen so I used the X61 tablet BIOS files (7suj18uc.iso).

That sounds reasonable to me.

> Note: I first tried an 8GB flash stick but the HPUSBFW tool reported:
"Error: Volume is too big" 

Hmmm, that's probably because you're trying to format it as FAT16, which can only work on up to a 4GB logical partition. This is probably noteworthy in the tutorial.


> Note: The COMMAND.COM originally copied to the flash drive must have had the read-only bit set because the copy of the ISO contents didn't
overwrite it even after I said "Yes" multiple times. I had to delete
it and copy over the COMMAND.COM separately. The instructions aren't
really clear on this point. They say you "should" overwrite the larger
HP COMMAND.COM with the smaller Lenovo COMMAND.COM so I assumed I
"must" overwrite it; hence the need to delete it because the "Yes"
(which should have worked), didn't work. 

Yep, you "must" overwrite it. Otherwise, you'll get a command prompt (I believe). Definitely not the right thing, but it won't break anything.

So... getting to the meat of your question, I'm not sure what's going on with your Windows Thumbdrive. I do know why you can't get the Linux files on there, though, so let's go from there.

You need to have both your ISO AND your USB thumdrive mounted to a folder on your filesystem in order to copy files between the two. You only have the ISO mounted at this point. So, do an fdisk -l to find which device is the USB drive (you previously said /dev/sdb1), and then:

```
sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
sudo cp -af [ISO mount point]/* /mnt/usb/
```

I wouldn't worry about shutting down the computer when there's the blinking cursor in the upper left hand corner. You'll know when it starts to flash your BIOS, which is the risky part. At the very least, there's some user input required first, it doesn't just begin without you hitting any keys.

Mike

---

### Post by rocksockdoc on 2010-08-16
> **mbsullivan said:**
> 
```
sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
sudo cp -af [ISO mount point]/* /mnt/usb/
```

Hi Mike,
Thanks for taking the time to help me out. (I was worried you were on vacation or something more fun than helping me!) :)

I'm ready to reboot the Lenovo X61 tablet PC to flash... just had one (maybe minor?) glitch in the instructions where it asked me to specify the file system type (but I didn't do it 'cuz I didn't know what it wanted).

Here's what I did:

I placed the previously created 4GB USB flash drive in the Lenovo X61 left USB slot.

```

$ script /tmp/flashbios.log
$ sudo fdisk -l

```Reported:
... stuff about unrelated disks ...
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         490     3928032    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(488, 254, 63) logical=(489, 5, 27)

This merely proved that the USB stick was still in /dev/sdb1 so I then ran:

```

sudo mkdir /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
sudo cp -af /cdrom/* /mnt/usb/

```Reported:
*mount: you must specify the filesystem type*

Even with that warning?/error?, the command seemed to have mounted it nonetheless:
```

ls -l  /mnt/usb/COMMAND.COM

```Reported:
-r-xr-xr-x 1 root root 7376 2008-01-30 07:00 /mnt/usb/COMMAND.COM

So, I'll move forward from here and let you all know how it works out!
Thanks for caring about others!

---

### Post by rocksockdoc on 2010-08-16
Drat. 

Same result. A permanent blinking top-left-corner white cursor on a black screen. 
I tried multiple times from multiple USB ports (both left and right) on the Lenovo X61 tablet PC and with the "+USB HDD" listed first in the boot order in the BIOS.

I even changed the boot order in the BIOS to JUST the USB hard drive (i.e., +USB HDD).

I wonder what is going on. I noticed one other person in this thread had the same problem which doesn't seem to have been resolved but that was long ago so we won't know how he solved it.

I wonder if there is some "other" software, unbeknownst to me, running that somehow prevents a boot from the USB HDD flash drive???

Any suggestions? (one thing I'll try is the whole procedure all over again).

Here, by the way, is a listing of what's on the USB flash drive. 

```

sudo mount /dev/sdb1 /mnt/usb

```Reported:
 mount: you must specify the file system type
```

 ls -alsF /mnt/usb

```Reported the files are all there on the USB flash drive:

total 4768
   4 drwxr-xr-x 2 root root    4096 2010-08-16 17:28 ./
   4 drwxr-xr-x 3 root root    4096 2010-08-16 17:26 ../
2264 -r-xr-xr-x 1 root root 2317654 2009-10-13 02:46 $01B6200.FL1*
2056 -r-xr-xr-x 1 root root 2103350 2007-07-02 23:24 $01B6200.FL2*
   4 -r-xr-xr-x 1 root root     163 2006-10-24 22:19 06f1.hsh*
   4 -r-xr-xr-x 1 root root    4096 2008-01-30 07:00 06F1.PAT*
   4 -r-xr-xr-x 1 root root     163 2006-10-24 22:19 06f4.hsh*
   4 -r-xr-xr-x 1 root root    4096 2008-01-30 07:00 06F4.PAT*
   4 -r-xr-xr-x 1 root root     163 2006-10-24 22:19 06f5.hsh*
   4 -r-xr-xr-x 1 root root    4096 2008-01-30 07:00 06F5.PAT*
   4 -r-xr-xr-x 1 root root     163 2006-10-24 22:19 06f9.hsh*
   4 -r-xr-xr-x 1 root root    4096 2008-01-30 07:00 06F9.PAT*
   4 -r-xr-xr-x 1 root root     163 2007-04-02 01:06 06fa.hsh*
   4 -r-xr-xr-x 1 root root    4096 2008-01-30 07:00 06FA.PAT*
   4 -r-xr-xr-x 1 root root     163 2008-01-15 19:02 06fb.hsh*
   4 -r-xr-xr-x 1 root root    4096 2008-01-30 07:00 06FB.PAT*
   4 -r-xr-xr-x 1 root root     163 2008-01-15 19:02 06fd.hsh*
   4 -r-xr-xr-x 1 root root    4096 2008-01-30 07:00 06FD.PAT*
   4 -r-xr-xr-x 1 root root     163 2007-04-25 02:38 10661.hsh*
   4 -r-xr-xr-x 1 root root    4096 2008-01-30 07:00 10661.PAT*
   4 -r-xr-xr-x 1 root root     697 2008-01-30 07:00 CHKBMP.EXE*
   8 -r-xr-xr-x 1 root root    7376 2008-01-30 07:00 COMMAND.COM*
  28 -r-xr-xr-x 1 root root   26028 2008-01-30 07:00 FLASH2.EXE*
   4 -r-xr-xr-x 1 root root      26 2008-01-30 07:00 lcreflsh.bat*
   4 -r-xr-xr-x 1 root root     170 2008-01-30 07:00 LOGO.BAT*
   4 -r-xr-xr-x 1 root root     330 2008-01-30 07:00 LOGO.SCR*
 136 -r-xr-xr-x 1 root root  135275 2008-01-30 07:00 PHLASH16.EXE*
  92 -r-xr-xr-x 1 root root   91648 2008-01-30 07:00 PREPARE.EXE*
   8 -r-xr-xr-x 1 root root    7059 2008-01-30 07:00 README.TXT*
   8 -r-xr-xr-x 1 root root    4550 2008-01-30 07:00 TPCHKS.EXE*
  40 -r-xr-xr-x 1 root root   37836 2008-01-30 07:00 UPDTFLSH.EXE*
   8 -r-xr-xr-x 1 root root    7230 2008-01-30 07:00 UPDTMN.EXE*
  16 -r-xr-xr-x 1 root root   12501 2008-01-30 07:00 USERINT.EXE*
  16 -r-xr-xr-x 1 root root   15274 2008-01-30 07:00 UTILINFO.EXE*

BTW, when I switched the BIOS back to boot off the hard drive (only), I noticed that blinking cursor for a split second, and then ubuntu came up. So maybe it's a hardware thing? Maybe it doesn't like my flash drive. I don't have anything smaller than 4GB (even that was hard to find as all mine are way larger). I might go to the store and buy an el cheapo 32MB flash drive if they still sell 'em. 

I know this is a hard question w/o the Lenovo X61 tablet in front of you ... but ... may I ask ... 
Any suggestions as to what the next step of the debug procedure might be?

---

### Post by rocksockdoc on 2010-08-17
Googling I find that it appears to be extremely common to get a black screen with a blinking cursor when attempting to flash the IBM/Lenovo Thinkpad X61 BIOS ...

- 
- [Tablet PC Review (X61 blank screen with blinking cursor) ]("http://forum.tabletpcreview.com/lenovo-ibm/31448-can-x61-boot-some-external-device-no.html")
- [Lenovo Forums X61 black screen w/ flashing underscore cursor]("http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/X61-Can-t-get-sysprep-ed-image-to-boot-on-it/m-p/32715")
- [Checkpoint forums: fixboot for X61 Blank screen/blinking cursor]("https://forums.checkpoint.com/forums/message.jspa?messageID=25286")
etc.

Here is one explanation from the [Lenovo ThinkPad forums]("http://forum.thinkpads.com/viewtopic.php?f=2&t=57270&start=0"):
"*Flashing cursor in upper left corner indicates the drive does not have a  boot sector, or it is truncated.  Same thing happens when you use drive  cloning software such as Ghost and don’t set the switch to copy the  entire boot sector, not just the default size.  ThinkPads use a larger  boot sector.* "

I wonder why, if this is the case, others didn't report this in this thread (other than one other person)?

---

### Post by mbsullivan on 2010-08-18
> 
mount: you must specify the filesystem type


Oh, that's because it's FAT16. Try with -t vfat, like so:

```
sudo mount -t vfat /dev/sdb1 /mnt/usb
```

I think that it still should have done it right, it's just whining.

> Same result. A permanent blinking top-left-corner white cursor on a black screen. 

Yeah, that's a very common boot problem. 

I don't think the problem is because you're using a tablet... A quick scan through the previous responses shows 2-4 people who have successfully installed on a tablet, including ones who explicitly used the [windows method]("http://ubuntuforums.org/showpost.php?p=5549494&postcount=30") and [linux method]("http://ubuntuforums.org/showpost.php?p=8801688&postcount=52").

I don't know what could be up. I wish we could debug it more thoroughly, but it's kind of tough from here.

> 
Here is one explanation from the Lenovo ThinkPad forums:
"Flashing cursor in upper left corner indicates the drive does not have a boot sector, or it is truncated. Same thing happens when you use drive cloning software such as Ghost and don&#8217;t set the switch to copy the entire boot sector, not just the default size. ThinkPads use a larger boot sector. "

Hmmm... I'm familiar with how to move around the boot sector for Western Digital EARS drives, which are strange. If you can get more information about this (and it proves to be accurate) we MIGHT be able to work with it. Do you have a link to where you found it? I've never heard this before, though.

> 
BTW, when I switched the BIOS back to boot off the hard drive (only), I noticed that blinking cursor for a split second, and then ubuntu came up. So maybe it's a hardware thing? Maybe it doesn't like my flash drive. I don't have anything smaller than 4GB (even that was hard to find as all mine are way larger). I might go to the store and buy an el cheapo 32MB flash drive if they still sell 'em.

I know this is a hard question w/o the Lenovo X61 tablet in front of you ... but ... may I ask ...
Any suggestions as to what the next step of the debug procedure might be? 

I'm not sure if a different flash drive may help. If you find one, let me know?

Another thing you could try if you're feeling up to it is to try an alternative approach that doesn't require a flash drive. There are several, and the list has been [growing]("http://www.thinkwiki.org/wiki/BIOS_Upgrade/X_Series") since I've written this tutorial. They vary in complexity, and I haven't felt compelled to update or complicate the tutorial, since my aim was to make something that people could actually USE on both Windows and Linux.

One alternate [approach]("http://www.thinkwiki.org/wiki/BIOS_Upgrade/X_Series#Approach_10:_Booting_the_Lenovo_ISO_image_using_Grub_and_SysLinux") which would only work under Linux would be to mount the ISO directly on your harddrive as you boot up. We could always try this in your case, though I'm reluctant to put something like it in the tutorial since it doesn't work in the Windows case, and may also differ slightly depending on how the Lenovo ISOs were made bootable (CD mode or floppy emulation mode). If you want to try something like this, I could try and figure out the simplest way from A -> B... I haven't seen anybody actually say they've gotten it to work for an x61(s/T), but it's worked for other Thinkpads.

Mike

---

### Post by rocksockdoc on 2010-08-18
> Do you have a link to where you found it? I've never heard this before, though.

Hi Mike,
Thanks for the help. I know you don't have to volunteer to help others and I'll understand if you drop off before I get this resolved. As for that link, [here it is]("http://forum.thinkpads.com/viewtopic.php?f=2&t=57270&start=0") (the text is by "steves" on "Thu Feb 14, 2008 1:26 pm" and it's about midway down the page as they don't give me a link directly to just his post).

There is apparently a well known blinking cursor "hanging" that happens with Thinkpads due, apparently, to a hidden "IBM Predesktop Area" as explained in [this PDF]("http://pl887.pairlitesite.com/misc/config-stories/cloning_a_thinkpad.pdf") and in this[ IBM white paper]("http://pl887.pairlitesite.com/misc/config-stories/thinkpad-hidden-protected-area-whitepaper.pdf") (both referenced [here]("http://pl887.pairlitesite.com/misc/config-stories/thinkpad-x40-hard-drive-upgrade.html")).

BTW, I agree that it should be doable but that lots of people have problems with the blinking cursor trying to boot off of devices hanging on a Thinkpad. I'm reading this [Thinkpad boot wiki ]("http://www.thinkwiki.org/wiki/Installation_on_ThinkPads_without_CD-ROM_drive")to see if I can get a clue to the mystery.  Notice the section titled "Installation from USB drive" which says:

> 
Not all ThinkPads have a BIOS that [supports USB booting]("http://www.thinkwiki.org/wiki/Supported_Boot_Devices").
  This is probably the easiest approach: 
 
[LIST=1]
[*]Connect the USB drive[2]("http://www.thinkwiki.org/wiki/Installation_on_ThinkPads_without_CD-ROM_drive#footnotes") to the host and format it.
[*]Get a bootable system and all needed installation files onto  the USB drive, i.e. by copying the complete filesystem from your  installation CD-ROM to the USB drive. Of course if your USB drive is not  big enough for that you'll have to make more sophisticated choices  about what to copy and what to leave behind. Here are [some instructions]("http://wiki.debian.org/BootUsb") (and [instructions for ubuntu]("https://help.ubuntu.com/community/Installation/FromUSBStick"), [instructions for Debian 5.0 (Lenny)]("http://debian.org/releases/lenny/i386/ch04s03.html")) for converting a LiveCD ISO image onto a pen drive, and making it bootable.[3]("http://www.thinkwiki.org/wiki/Installation_on_ThinkPads_without_CD-ROM_drive#footnotes")
[/LIST]
 
[LIST=1]
[*]Insert the USB drive into the USB port of your ThinkPad.
[*]Power on the ThinkPad and press F12 to get to the boot menu.  For some models (X24 comes to mind) you need to go into the BIOS and  change the boot sequence before USB devices are shown in the boot menu.
[*]Select the USB drive as boot media and boot.
[*]Follow the normal installation process.
[/LIST]
 It seems some ThinkPad BIOSes don't use the code on the master boot  record (MBR), or at least skip it when it is blank.  These systems will  need an [Extended-IPL boot loader]("http://www.tsden.org/ryutaroh/extipl/"). Putting this Extended-IPL boot loader onto the disk (such as sda) goes something like this: 
 dd if=/dev/zero of=/dev/sda bs=1 count=446
dd if=/usr/lib/extipl/aldebaran.bin of=/dev/sda

However, if all this is true (that we need an extended IPL boot loader for example), then I wonder why I'm only running into this now. It can't be but I'll keep looking for the solution for this mystery.

> **rocksockdoc said:**
> I even changed the boot order in the BIOS to JUST the USB hard drive (i.e., +USB HDD).

I found a description of the [supported boot devices for all Thinkpads here]("http://www.thinkwiki.org/wiki/Supported_Boot_Devices"); unfortunately, the information on the X61 is sketchy at best in this reference. Specifically, it defines:

[LIST]
[*] USB HD = any hard drive/flash drive/pen drive connected via the USB port
[*] USB FDD = Diskette ("Floppy") drive connected via the USB port
[*] USB CD = CD/DVD(-R/-RW/-RAM) drive connected via the USB port
[/LIST]
So, it "should" have been correct when I set the "USB HDD" as the only boot device (although note the extra "D" in what I saw in my BIOS versus the reference above).

> Try with -t vfat, like so:

Thanks for the "-t" option. It didn't do any better but as you said, I think it's just whining so I don't think that's the problem either. 

```

$ sudo mount /dev/sdb1 /mnt/usb
Reported:
mount: you must specify the filesystem type

```

```

$ sudo mount -t vfat /dev/sdb1 /mnt/usb
Reported:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$ dmesg | tail
Reported:
[64645.081765] sd 6:0:0:0: [sdb] 7856127 512-byte logical blocks: (4.02 GB/3.74 GiB)
[64645.082213] sd 6:0:0:0: [sdb] Write Protect is off
[64645.082217] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[64645.082221] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[64645.086470] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[64645.086477]  sdb: sdb1
[64645.090713] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[64645.090719] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[64716.532120] FAT: invalid media value (0xb9)
[64716.532126] VFS: Can't find a valid FAT filesystem on dev sdb1.

```

>  try an alternative approach that doesn't require a flash drive.

Ah, I see you're looking at the same thinkwiki I referenced above (different pages though). I will investigate alternative approaches if I can't get the USB device to work after deleting the hidden boot stuff explained above and changing the USB drive itself. 

I like the way you work (writing a nice succinct tutorial and updating it as new information comes up) and I will try to report back what I find out so others can always benefit from both our efforts.

---

### Post by rocksockdoc on 2010-08-18
Hi Mike,
I tried it with a 256 MB flash drive with similar results (weirdly, instead of a flashing dash cursor (_), I repeatedly get a lower-case "j" with the flashing dash cursor (j_) with the smaller USB stick. I'm beginning to wonder if this Thinkpad X61 tablet BIOS is capable of booting off the USB memory stick.

This begs the obvious question whose answer should be of general interest to X61 tablet owners:
Q1: My Lenovo X61 BIOS (version 1.04 for the BIOS; version 1.02 for the Embedded Controller ) has "USB HDD" as an option but not "USB HD"; so is "USB HDD" the same as a USB stick (or is it only for a physical hard disk drive)?

In addition, a tactical question popped up because the dd seems to work whether or not I unmount the USB flash drive just before running dd ... so that begs the question:
Q2: Why do we unmount the USB flash drive before running "dd" to copy over the Win98 files?

The reason it might matter is that the USB sticks show up as disk drives in Ubuntu 10.04 until I perform that dd step; and then they no longer show up in the Ubuntu desktop after I perform the dd step (even after rebooting). Why do we unmount the USB drives before running dd?

I'll keep trying (and will post a log separately) but the answer to these two questions should be of general interest to all.

---

### Post by mbsullivan on 2010-08-19
> so is "USB HDD" the same as a USB stick (or is it only for a physical hard disk drive)?

I believe that "USB HDD" is the same as any USB device with a bootable filesystem. So it could be either.

> Why do we unmount the USB flash drive before running "dd" to copy over the Win98 files?

We unmount the USB drive, because "dd" is copying a new filesystem and files to the USB drive as a block device. It overwrites all previous contents, and doesn't interact with the mounted filesystem at all.

We keep the drive unmounted since we're about to thrash it, and having a mounted non-existent filesystem wouldn't turn out so well. Also, I'm not sure if this is a concern, but unmounting the drive avoids any write conflicts due to currently accessed files or file locks.

> 
Thanks for the "-t" option. It didn't do any better but as you said, I think it's just whining so I don't think that's the problem either

That's really strange. From your previous post, "fdisk -l" is obviously detecting it correctly as a Win95 Fat16 formatted partition (LBA = "logical block addressing", it should be fine).

> I'm beginning to wonder if this Thinkpad X61 tablet BIOS is capable of booting off the USB memory stick.

I'm not sure why yours wouldn't be... Other people have had success with it. You could always make a [Ubuntu LiveUSB]("https://help.ubuntu.com/community/Installation/FromUSBStick") and boot from that if you have a doubt.

The question is whether we want to keep trying to debug this, or try an alternate route.

Mike

---

### Post by rocksockdoc on 2010-08-21
> **mbsullivan said:**
> make a [Ubuntu LiveUSB]("https://help.ubuntu.com/community/Installation/FromUSBStick") and boot from that if you have a doubt.

Hi Mike,
Thanks for sticking with me. I think I found WHERE the problem lies (but I don't know enough about Linux to actually debug WHY the problem exists). 

If you look at the log below, notice that the win98 image does NOT seem to be copied onto either of the two USB flash drives. I think that's WHERE the problem lies. I'm not sure WHY that problem occurs as I followed your instructions exactly (I think). 

Can you suggest a debug sequence for me to understand WHY the win98 image did not transfer over to the USB sticks. The command to transfer it appears to have worked. But not the transfer itself???

I'm sure I made a mistake somewhere ... can someone help me spot the mistake or at least supply debugging hints at the appropriate point?

Thanks,
Rock
```

---
GOAL: Flash Lenovo X61 tablet PC using only Linux and a USB stick following
the Linux-only instructions at: http://ubuntuforums.org/showthread.php?t=817897
---
Placed a WinXP formatted 4GB SanDisk USB stick (FAT32) in the Lenovo X61 tablet
left-side USB slot and a WinXP formatted 250MB IBM USB stick (FAT16) in the
Lenovo X61 tablet right-side front USB slot.

The USB icon for each automatically showed up on the Ubuntu 10.04 desktop.
---
Confirm the two USB sticks are /dev/sdb1 and /dev/sdc1 respectively:

$ sudo fdisk -l
Reported:
 Disk /dev/sda: 120.0 GB, 120034123776 bytes
 (blah blah blah)

 Disk /dev/sdb: 4022 MB, 4022337024 bytes
 255 heads, 63 sectors/track, 489 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x0502fe69

 Device    Boot Start End Blocks  Id System
 /dev/sdb1 *    1     490 3928032 b  W95 FAT32
 Partition 1 has different physical/logical endings:
   phys=(488, 254, 63) logical=(489, 5, 27)

 Disk /dev/sdc: 255 MB, 255852544 bytes
 128 heads, 4 sectors/track, 976 cylinders
 Units = cylinders of 512 * 512 = 262144 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x04d704d6

 Device    Boot Start End Blocks Id System
 /dev/sdc1 *    1     976 249854 6  FAT16

QUESTION: What's /dev/sdb versus /dev/sdb1 & /dev/sdc versus /dev/sdc1?
---
Obtained win98usb.tar from:
http://ubuntuforums.org/attachment.php?attachmentid=115376&d=1243462998

$ tar -xf ./win98usb.tar
$ ls -a win98usb.img
Reported:
-rw-r--r-- 1 x x 621568 2009-05-27 14:14 win98usb.img
---
$ sudo umount -f /dev/sdb1
$ sudo umount -f /dev/sdc1

This removed the USB stick icons from the desktop
---
$ sudo dd if=win98usb.img of=/dev/sdb1 conv=notrunc
$ sudo dd if=win98usb.img of=/dev/sdc1 conv=notrunc
Reported:
1214+0 records in
1214+0 records out
621568 bytes (622 kB) copied, 0.858151 s, 724 kB/s

1214+0 records in
1214+0 records out
621568 bytes (622 kB) copied, 1.86486 s, 333 kB/s
---
$ sudo mkdir /mnt/usb1
$ sudo mkdir /mnt/usb2
---
$ sudo mount -t vfat /dev/sdb1 /mnt/usb1
$ sudo mount -t vfat /dev/sdc1 /mnt/usb2
Both reported:
  mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
  missing codepage or helper program, or other error
  In some cases useful info is found in syslog - try
  dmesg | tail  or so

$ dmesg | tail
Reported:
[190037.547196] FAT: invalid media value (0xb9)
[190037.547201] VFS: Can't find a valid FAT filesystem on dev sdb1.
[190163.630243] FAT: invalid media value (0xb9)
[190163.630249] VFS: Can't find a valid FAT filesystem on dev sdc1.
---
$ sudo mount /dev/sdb1 /mnt/usb1
$ sudo mount /dev/sdc1 /mnt/usb2
Reported in both commands:
 mount: you must specify the filesystem type

QUESTION: How can I prove whether this mounted properly or not?
---
$ ls -alsF /mnt/usb1
$ ls -alsF /mnt/usb2

Both reported:
total 8
4 drwxr-xr-x 2 root root 4096 2010-08-20 22:30 ./
4 drwxr-xr-x 4 root root 4096 2010-08-20 22:30 ../

QUESTION: Where did the files copied over by dd go?
---
$ mount -l | grep sd[b,c]1
Reported:
 Nothing

QUESTION: Why /dev/sdb1 & /dev/sdc1 not show up in the mount list command?
---
$ sudo mount -o loop `pwd`/7suj18uc.iso /cdrom/

$ ls /cdrom/
Reports:
$01B6200.FL1  06f5.hsh  06fb.hsh   CHKBMP.EXE    PHLASH16.EXE  USERINT.EXE
$01B6200.FL2  06F5.PAT  06FB.PAT   COMMAND.COM   PREPARE.EXE   UTILINFO.EXE
06f1.hsh      06f9.hsh  06fd.hsh   FLASH2.EXE    README.TXT
06F1.PAT      06F9.PAT  06FD.PAT   lcreflsh.bat  TPCHKS.EXE
06f4.hsh      06fa.hsh  10661.hsh  LOGO.BAT      UPDTFLSH.EXE
06F4.PAT      06FA.PAT  10661.PAT  LOGO.SCR      UPDTMN.EXE
---
$ sudo cp -af /cdrom/* /mnt/usb1/
$ sudo cp -af /cdrom/* /mnt/usb2/
[190037.547201] VFS: Can't find a valid FAT filesystem on dev sdb1.
[190163.630243] FAT: invalid media value (0xb9)
[190163.630249] VFS: Can't find a valid FAT filesystem on dev sdc1.
---
$ sudo mount /dev/sdb1 /mnt/usb1
$ sudo mount /dev/sdc1 /mnt/usb2
Reported in both commands:
 mount: you must specify the filesystem type

QUESTION: How can I prove whether this mounted properly or not?
---
$ ls -alsF /mnt/usb1
$ ls -alsF /mnt/usb2

Both reported:
total 8
4 drwxr-xr-x 2 root root 4096 2010-08-20 22:30 ./
4 drwxr-xr-x 4 root root 4096 2010-08-20 22:30 ../

QUESTION: Where did the files copied over by dd go?
---
$ mount -l | grep sd[b,c]1
Reported:
 Nothing

QUESTION: Why /dev/sdb1 & /dev/sdc1 not show up in the mount list command?
---
$ sudo mount -o loop `pwd`/7suj18uc.iso /cdrom/

$ ls /cdrom/
Reports:
$01B6200.FL1  06f5.hsh  06fb.hsh   CHKBMP.EXE    PHLASH16.EXE  USERINT.EXE
$01B6200.FL2  06F5.PAT  06FB.PAT   COMMAND.COM   PREPARE.EXE   UTILINFO.EXE
06f1.hsh      06f9.hsh  06fd.hsh   FLASH2.EXE    README.TXT
06F1.PAT      06F9.PAT  06FD.PAT   lcreflsh.bat  TPCHKS.EXE
06f4.hsh      06fa.hsh  10661.hsh  LOGO.BAT      UPDTFLSH.EXE
06F4.PAT      06FA.PAT  10661.PAT  LOGO.SCR      UPDTMN.EXE
---
$ sudo cp -af /cdrom/* /mnt/usb1/
$ sudo cp -af /cdrom/* /mnt/usb2/
[190037.547201] VFS: Can't find a valid FAT filesystem on dev sdb1.
[190163.630243] FAT: invalid media value (0xb9)
[190163.630249] VFS: Can't find a valid FAT filesystem on dev sdc1.
---
$ sudo mount /dev/sdb1 /mnt/usb1
$ sudo mount /dev/sdc1 /mnt/usb2
Reported in both commands:
 mount: you must specify the filesystem type

QUESTION: How can I prove whether this mounted properly or not?
---
$ ls -alsF /mnt/usb1
$ ls -alsF /mnt/usb2

Both reported:
total 8
4 drwxr-xr-x 2 root root 4096 2010-08-20 22:30 ./
4 drwxr-xr-x 4 root root 4096 2010-08-20 22:30 ../

QUESTION: Where did the files copied over by dd go?
---
$ mount -l | grep sd[b,c]1
Reported:
 Nothing

QUESTION: Why /dev/sdb1 & /dev/sdc1 not show up in the mount list command?
---
$ sudo mount -o loop `pwd`/7suj18uc.iso /cdrom/

$ ls /cdrom/
Reports:
$01B6200.FL1  06f5.hsh  06fb.hsh   CHKBMP.EXE    PHLASH16.EXE  USERINT.EXE
$01B6200.FL2  06F5.PAT  06FB.PAT   COMMAND.COM   PREPARE.EXE   UTILINFO.EXE
06f1.hsh      06f9.hsh  06fd.hsh   FLASH2.EXE    README.TXT
06F1.PAT      06F9.PAT  06FD.PAT   lcreflsh.bat  TPCHKS.EXE
06f4.hsh      06fa.hsh  10661.hsh  LOGO.BAT      UPDTFLSH.EXE
06F4.PAT      06FA.PAT  10661.PAT  LOGO.SCR      UPDTMN.EXE
---
$ sudo cp -af /cdrom/* /mnt/usb1/
$ sudo cp -af /cdrom/* /mnt/usb2/
[190037.547201] VFS: Can't find a valid FAT filesystem on dev sdb1.
[190163.630243] FAT: invalid media value (0xb9)
[190163.630249] VFS: Can't find a valid FAT filesystem on dev sdc1.
---
$ sudo mount /dev/sdb1 /mnt/usb1
$ sudo mount /dev/sdc1 /mnt/usb2
Reported in both commands:
 mount: you must specify the filesystem type

QUESTION: How can I prove whether this mounted properly or not?
---
$ ls -alsF /mnt/usb1
$ ls -alsF /mnt/usb2

Both reported:
total 8
4 drwxr-xr-x 2 root root 4096 2010-08-20 22:30 ./
4 drwxr-xr-x 4 root root 4096 2010-08-20 22:30 ../

QUESTION: Where did the files copied over by dd go?
---
$ mount -l | grep sd[b,c]1
Reported:
 Nothing

QUESTION: Why /dev/sdb1 & /dev/sdc1 not show up in the mount list command?
---
$ sudo mount -o loop `pwd`/7suj18uc.iso /cdrom/

$ ls /cdrom/
Reports:
$01B6200.FL1  06f5.hsh  06fb.hsh   CHKBMP.EXE    PHLASH16.EXE  USERINT.EXE
$01B6200.FL2  06F5.PAT  06FB.PAT   COMMAND.COM   PREPARE.EXE   UTILINFO.EXE
06f1.hsh      06f9.hsh  06fd.hsh   FLASH2.EXE    README.TXT
06F1.PAT      06F9.PAT  06FD.PAT   lcreflsh.bat  TPCHKS.EXE
06f4.hsh      06fa.hsh  10661.hsh  LOGO.BAT      UPDTFLSH.EXE
06F4.PAT      06FA.PAT  10661.PAT  LOGO.SCR      UPDTMN.EXE
---
$ sudo cp -af /cdrom/* /mnt/usb1/
$ sudo cp -af /cdrom/* /mnt/usb2/
$ ls -l  /mnt/usb[1,2]/COMMAND.COM

Reported:
-r-xr-xr-x 1 root root 7376 2008-01-30 07:00 /mnt/usb1/COMMAND.COM
-r-xr-xr-x 1 root root 7376 2008-01-30 07:00 /mnt/usb2/COMMAND.COM
---
---

```

---

### Post by mbsullivan on 2010-08-22
> Thanks for sticking with me.

You're welcome. :) 

> If you look at the log below, notice that the win98 image does NOT seem to be copied onto either of the two USB flash drives. I think that's WHERE the problem lies. I'm not sure WHY that problem occurs as I followed your instructions exactly (I think). 

Oh, okay! I think we can fix that problem.

> QUESTION: What's /dev/sdb versus /dev/sdb1 & /dev/sdc versus /dev/sdc1?

/dev/sdb is the identifier for the device (the whole drive), /dev/sdb1 is the identifier for the partition. In these cases, you happen to only have one partition to each drive, but you could have more, and then you'd have /dev/sdb2, /dev/sdb3, etc.

> $ sudo dd if=win98usb.img of=/dev/sdb1 conv=notrunc
$ sudo dd if=win98usb.img of=/dev/sdc1 conv=notrunc


These should be:

```
$ sudo dd if=win98usb.img **of=/dev/sdb** conv=notrunc
$ sudo dd if=win98usb.img **of=/dev/sdc** conv=notrunc
```

Because you're overwriting the ENTIRE drive, including the partition table, etc. You're not just affecting a single partition (/dev/sdb1, for instance).

If I'm not mistaken, that's your problem right there. A tiny thing, but it makes all the difference.

Lemme know if changing that fixes anything?
Mike

---

### Post by rocksockdoc on 2010-08-24
> **mbsullivan said:**
> If I'm not mistaken, that's your problem right there. A tiny thing, but it makes all the difference.

Hi Mike,
Again, thanks for sticking with me. I'm not new to computers but I'm wholly new to Linux operating systems. So I'm mostly following the commands like a recipe. The results were more predictable with that simple change of the [dd]("http://en.wikipedia.org/wiki/Dd_%28Unix%29") 'data description' command: 
```

FROM: $ sudo dd if=win98usb.img of=/dev/sdb1 conv=notrunc
TO: $ sudo dd if=win98usb.img of=/dev/sdb conv=notrunc

```Here is the results log showing we're ready to flash that bios!
(I'll let you know how it goes once I run a few more tests and back up some data.)

> 
---
GOAL: Flash Lenovo X61 tablet PC using only Linux and a USB stick following
the Linux-only instructions at: [http://ubuntuforums.org/showthread.php?t=817897](http://ubuntuforums.org/showthread.php?t=817897)
---
Placed a WinXP formatted 4GB SanDisk USB stick (FAT32) in the Lenovo X61 tablet
left-side USB slot and a WinXP formatted 250MB IBM USB stick (FAT16) in the 
Lenovo X61 tablet right-side front USB slot.

The USB icon for each automatically showed up on the Ubuntu 10.04 desktop.
---
Confirm the two USB sticks are /dev/sdb1 and /dev/sdc1 respectively:

$ sudo fdisk -l
Reported:
 Disk /dev/sda: 120.0 GB, 120034123776 bytes
 (blah blah blah) 

 Disk /dev/sdb: 4022 MB, 4022337024 bytes
 255 heads, 63 sectors/track, 489 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x0502fe69

 Device    Boot Start End Blocks  Id System
 /dev/sdb1 *    1     490 3928032 b  W95 FAT32
 Partition 1 has different physical/logical endings:
   phys=(488, 254, 63) logical=(489, 5, 27)

 Disk /dev/sdc: 255 MB, 255852544 bytes
 128 heads, 4 sectors/track, 976 cylinders
 Units = cylinders of 512 * 512 = 262144 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x04d704d6

 Device    Boot Start End Blocks Id System
 /dev/sdc1 *    1     976 249854 6  FAT16

QUESTION: What's /dev/sdb versus /dev/sdb1 & /dev/sdc versus /dev/sdc1?
ANSWER: /dev/sdb is the identifier for the device (the whole drive), while
        /dev/sdb1 is the identifier for the partition. We happen to have
        one partition on each drive, but we could have had more partitions.
        If we did have more partitions, we'd have /dev/sdb2, /dev/sdb3, etc.
---
Obtained win98usb.tar from:
[http://ubuntuforums.org/attachment.php?attachmentid=115376&d=1243462998](http://ubuntuforums.org/attachment.php?attachmentid=115376&d=1243462998)

$ tar -xf ./win98usb.tar
$ ls -a win98usb.img
Reported:
-rw-r--r-- 1 x x 621568 2009-05-27 14:14 win98usb.img
---
$ sudo umount -f /dev/sdb1
$ sudo umount -f /dev/sdc1

Note: This removed both USB stick icons from the Ubuntu desktop.
---
$ sudo dd if=win98usb.img of=/dev/sdb conv=notrunc
$ sudo dd if=win98usb.img of=/dev/sdc conv=notrunc
Reported:
1214+0 records in
1214+0 records out
621568 bytes (622 kB) copied, 0.858151 s, 724 kB/s

1214+0 records in
1214+0 records out
621568 bytes (622 kB) copied, 1.86486 s, 333 kB/s
---
$ sudo mkdir /mnt/usb1
$ sudo mkdir /mnt/usb2
---
$ sudo mount -t vfat /dev/sdb1 /mnt/usb1
$ sudo mount -t vfat /dev/sdc1 /mnt/usb2
Both no longer reported:
  mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
  missing codepage or helper program, or other error
  In some cases useful info is found in syslog - try
  dmesg | tail  or so

$ dmesg | tail
No longer reported:
[190037.547196] FAT: invalid media value (0xb9)
[190037.547201] VFS: Can't find a valid FAT filesystem on dev sdb1.
[190163.630243] FAT: invalid media value (0xb9)
[190163.630249] VFS: Can't find a valid FAT filesystem on dev sdc1.
---
$ ls -alsF /mnt/usb[1,2]
Now reported for both USB sticks:
total 356
 32 drwxr-xr-x 2 root root  16384 1969-12-31 16:00 ./
  4 drwxr-xr-x 4 root root   4096 2010-08-20 22:30 ../
 96 -r-xr-xr-x 1 root root  93880 1998-05-11 19:01 COMMAND.COM*
224 -r-xr-xr-x 1 root root 222390 1998-05-11 19:01 IO.SYS*
  0 -r-xr-xr-x 1 root root      0 1998-05-11 19:01 MSDOS.SYS*
---
$ mount -l | grep sd[b,c]1
No longer reported:
 Nothing
It now reported:
/dev/sdb1 on /mnt/usb1 type vfat (rw)
/dev/sdc1 on /mnt/usb2 type vfat (rw)

QUESTION: Why /dev/sdb1 & /dev/sdc1 not show up in the mount list command?
ANSWER: It does now that we fixed the dd command!
---
$ sudo mount -o loop `pwd`/7suj18uc.iso /cdrom/

$ ls /cdrom/
Reports:
$01B6200.FL1  06f5.hsh  06fb.hsh   CHKBMP.EXE    PHLASH16.EXE  USERINT.EXE
$01B6200.FL2  06F5.PAT  06FB.PAT   COMMAND.COM   PREPARE.EXE   UTILINFO.EXE
06f1.hsh      06f9.hsh  06fd.hsh   FLASH2.EXE    README.TXT
06F1.PAT      06F9.PAT  06FD.PAT   lcreflsh.bat  TPCHKS.EXE
06f4.hsh      06fa.hsh  10661.hsh  LOGO.BAT      UPDTFLSH.EXE
06F4.PAT      06FA.PAT  10661.PAT  LOGO.SCR      UPDTMN.EXE
---
$ sudo cp -af /cdrom/* /mnt/usb1/
$ sudo cp -af /cdrom/* /mnt/usb2/
$ ls -l  /mnt/usb[1,2]/COMMAND.COM

Reported:
-r-xr-xr-x 1 root root 7376 2008-01-30 07:00 /mnt/usb1/COMMAND.COM
-r-xr-xr-x 1 root root 7376 2008-01-30 07:00 /mnt/usb2/COMMAND.COM
---
We're now ready to flash that BIOS!
---                                       
I wonder which USB stick is booted from if I leave BOTH in the respective left and right USB slots?

---

### Post by rocksockdoc on 2010-08-24
> **rocksockdoc said:**
> 
I wonder which USB stick is booted from if I leave BOTH in the respective left and right USB slots?

Hi Mike,

I didn't want to risk both USB sticks being in at the same time so I turned the Lenovo X61 tablet off and stuck the smaller 250MB USB stick into the left USB slot and booted up the X61 (and did it again with the larger 4MB USB stick -- both worked fine to boot into the BIOS update program).

There was a bit of ambiguity since the word "BIOS" was never mentioned ... here's what happened when I powered the X61 tablet up with one USB stick in the left-side slot:
- First, the familar ThinkVantage screen popped up ... 
- Then a vaguely reminiscent  (from long ago) blue Win98 screen flashed momentarily
- Penultimately, a black screen asked me to "Type the name of the command interpreter" to which I responded with "command.com< enter >".
- Lastly the "Main Menu" came up asking me to "Select One", of the three options:
[B]1. Read this first
2. Update system program
3. Update model number[/B]

After reading the (nearly useless) information in option #1, I rebooted to Ubuntu and re-read all the posts in this thread and I realize that option #2 is probably the one that needs to be executed. (You might want to make it clearer which option to execute since NONE of them say anything whatsoever about the BIOS being updated.)

Anyway, I tried this both with the smaller 250MB USB stick and the larger 4GB USB stick with the same results. It failed, but not due to a fault of yours or mine. It seems that the "update system program" command noticed the totally dead battery (which has been dead for quite some time) and will not execute for fear that a power interruption will cause a problem.

Specifically, the system-program update stated:
*"ERROR: Your battery needs to be charged to avoid an accidental power-off during an update. Turn off the computer and connect the AC adapter to charge the battery".*

Of course, that won't work as the 14.4 volt 4300 Ah battery has been "charging" for months to no avail as I run off the 20 volt 4.5 amp AC adapter and the (dead) battery plugged in but useless; so I'm going to have to order a brand new battery to go any further. Thanks Mike for all your help. Sorry to be a pain. I hope other Linux newbies benefit from the specific steps I listed of your more general commands.

I'll update this thread after I order a new battery and try it again when it arrives and is charged up.

---

### Post by mbsullivan on 2010-08-24
> 

After reading the (nearly useless) information in option #1, I rebooted to Ubuntu and re-read all the posts in this thread and I realize that option #2 is probably the one that needs to be executed. (You might want to make it clearer which option to execute since NONE of them say anything whatsoever about the BIOS being updated.)

Oh, that's a good idea.

> Anyway, I tried this both with the smaller 250MB USB stick and the larger 4GB USB stick with the same results. It failed, but not due to a fault of yours or mine. It seems that the "update system program" command noticed the totally dead battery (which has been dead for quite some time) and will not execute for fear that a power interruption will cause a problem.

Specifically, the system-program update stated:
"ERROR: Your battery needs to be charged to avoid an accidental power-off during an update. Turn off the computer and connect the AC adapter to charge the battery".

Of course, that won't work as the 14.4 volt 4300 Ah battery has been "charging" for months to no avail as I run off the 20 volt 4.5 amp AC adapter and the (dead) battery plugged in but useless; so I'm going to have to order a brand new battery to go any further. Thanks Mike for all your help. Sorry to be a pain. I hope other Linux newbies benefit from the specific steps I listed of your more general commands.

I'll update this thread after I order a new battery and try it again when it arrives and is charged up.

What bad luck! I'm not sure of any easy way to hack around this (there MAY be, but I'd be reluctant to start changing the files they provide). Good luck when the new battery arrives!

Mike

---

### Post by evergreen on 2010-10-17
> I'm not sure of any easy way to hack around this (there MAY be, but I'd be reluctant to start changing the files they provide)

Hi, 

I'm in the same situation no working battery. Just wondering if anyone has found a way around this?

I know its a long shot but has anyone found a hack to get this working without a battery? Mines completely dead!

Great guide btw, Very well written. Thanks for keeping it updated you helped me back at post #16

---

### Post by StickyTape on 2010-10-18
Doesn't sound like something, even if were possible, you should be doing. If your battery will give you at least 5 min, then it will probably be ok. Otherwise, you will need a loan of one, or will have to purchase a new one. Long shot indeed!

---

### Post by evergreen on 2010-10-19
Do I need to buy a genuine Lenovo battery if upgrading the bios? 

Or can I just get one from Hong Kong?

I haven't got much money so would like to go for the cheapest option if It will work.

---

### Post by mbsullivan on 2010-11-16
> Do I need to buy a genuine Lenovo battery if upgrading the bios?

Or can I just get one from Hong Kong?

I haven't got much money so would like to go for the cheapest option if It will work.

I'm honestly not sure. Did you try it?

Mike

---

### Post by phaidros on 2011-02-01
worked like a charme! x61s now on bios 2.21.
thanx, great howto!

(tried with unetbootin before, but that didnt produce a bootable stick)

---

### Post by phaidros on 2011-02-02
trying on x60s now ...

..
<it may take about 1 minute>


..
..
[long time]
..
..

<< beeeeeeep >>

<it may take about 1 more minute>

..
..

<< beeeeeeep >>

DONE!!

thx, quite nice :)

now having 2.18 (7BETD7WW) aboard x60s
(get it here: [http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/7buj27uc.iso](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/7buj27uc.iso))


[SEO: thinkpad lenovo x60s x61s linux bios upgrade update usb stick flash drive]

---

### Post by fastness on 2011-02-16
Thanks for this interesting post. I just followed this instruction, tweaked it a little bit, and flashed the lenovo bios to a whitelist BIOS of the same version in my X61T 

After copying the lenovo BIOS image CD to a bootable pindrive, I replaced the lenovo Command.com with the original win98 DOS command.com.
Also I edit the lenovo batch command, lcreflsh.bat in the pin-drive, delete the second line "flash2.exe /u"
Download a white-list patched BIOS image file (*.rom ~4Mb) somewhere, and rename this bios.rom file to BIOS.WPH, save BIOS.WPH in this pin-drive
x61t-bios_SLIC_sata_1802_1804.rom  --> BIOS.WPH

Before rebooting my thinkpad, the following file are in the pin-drive:
win98 booting files, patched bios image file "BIOS.WPH" PHLASH16.EXE and other files form the lenovo CD image, command.com form the original win98 boot disk, and revised "lcreflsh.bat"

In this way, my thinkpad will boot to a regular DOS, instead of the crippled lenovo bios interface.

Under the regular DOS, knock in "PHLASH16.EXE", and run. PHLASH16.EXE will find the BIOS.WPH and flash the bios by itself. The laptop will reboot after the flashing. 

Here is my protocol.

1, HPUSBFW.exe + WIN98 boot disk to make a bootable pin-drive
2, download the BIOS cd image form lenovo.com, open the image file with 7-zip and copy them all to the pindrive.
3, 7-zip open the image of win98 boot disk again, replace the crippled lenovo command.com in pindrive with the original DOS command.com
4, google and download a patched ROM image, e.g. x61t-bios_SLIC_sata_1802_1804.rom , rename it to BIOS.WPH, save it to pindrive.
5, edit the lenovo batch command "lcreflsh.bat" in pindrive, edit the second line, delete "flash2.exe /u" or replace it with "PHLASH16.EXE" save the change.

after revision, lcreflsh.bat looks like
@echo off
PHLASH16.EXE

or 
@echo off

before this revision, lcreflsh.bat was like
@echo off
flash2.exe /u

6, up to now, before rebooting this thinkpad, the following files are in the pin-drive:
win98 booting files, 
patched BIOS image file "BIOS.WPH" from some amateur websites
PHLASH16.EXE and other misc. files form the lenovo CD image, 
command.com form the original win98 boot disk, 
revised "lcreflsh.bat"

7, check and charge the battery pack and check the power supply.
8, reboot the thinkpad with this customized pindrive. If you deleted "flash2.exe /u",you will be led into regular DOS
9, knock in PHLASH16.EXE, and run, PHLASH16.EXE will search for BIOS.WPH in the pindrive by itself. Once found it, it will flash bios automatically. While flashing, you thinkpad will make some noise and show the process on the screen. It took me around 3 minutes to flash my X61T. After flashing, the laptop rebooted by itself. 

10, If you replaced "flash2.exe /u" with "PHLASH16.EXE" in lcreflsh.bat. After rebooting, there is nothing you can do, but a cup of coffee. But I did it manually and listened to that monster's music.

Now my x61t is running Ubuntu happily with a salvaged wifi card in the left PCI-E slot.

---

### Post by mbsullivan on 2011-02-21
> Thanks for this interesting post. I just followed this instruction, tweaked it a little bit, and flashed the lenovo bios to a whitelist BIOS of the same version in my X61T 

Wow, that's ballsy. :) I'm glad it worked, though! Where'd you find your modified BIOS, for future reference?

Mike

---

### Post by fastness on 2011-02-23
[http://forum.notebookreview.com/lenovo-ibm/459591-t61-x61-sata-ii-1-5-gb-s-cap-willing-pay-solution-8.html#post6501443](http://forum.notebookreview.com/lenovo-ibm/459591-t61-x61-sata-ii-1-5-gb-s-cap-willing-pay-solution-8.html#post6501443)

---

### Post by mofoxer on 2011-03-01
Hey..
 
im glad that i found this tutorial!
 
i wonder, if it is possible to create a bootable .ISO file instead of creating directly a bootable usb stick?
 
my goal is to create a multi boot usb stick, with several bios versions..
 
x61, t61 and so on..
 
so that i will boot from the usb stick.. and it loads through syslinux or grub4dos the bootable image..
 
anyone of you got an idea?

---

### Post by martinlbb on 2011-07-21
I follow your tutorial to update BIOS from a USB key and it work perfectly (using Linux method).

I used it to update SATA to SATA2 Bios on a X61s.

I even update Bios Splashcreen :)

Many thanks :)

---

### Post by gbear14275 on 2011-09-10
This not longer seems to work...  I get:


$ sudo cp -af /tmp/bios/ /media/EED3-FFBD/
cp: failed to preserve ownership for `/media/EED3-FFBD/bios': Operation not permitted

Not sure what changed but any update would be great.

Also... you forget to mention that you should remount your USB between steps 1 and 2.

---

### Post by ipaid on 2011-12-08
Hi all

first of all thanks for this great how to! I managed to upgrade my BIOS yesterday. 

I prepared a USB stick on Windows. It took several attempts until it worked. The first attempt ended up in a blank (black) screen with a blinking cursor (several users reported the same issue in this thread). When i tried to prepare the USB stick on Linux, i noticed that the command

```
$ sudo dd if=./win98usb.img of=/dev/sdc conv=notrunc
```formatted my USB stick using FAT 32. 

So i tried the Windows path again but in step 1. Format the USB stick to be a DOS boot device (Windows), i chose FAT 32 instead of FAT 16.

This solved the problem (at least for me) with the blank screen and the blinking cursor.

Another helpful hint: After powering on your Lenovo, hit F12 -> A list of bootable devices will be displayed. Select your prepared USB stick to boot from that one.

Hope that helps.

---

### Post by love fingers on 2012-01-01
Just wanted to say a quick thank you for your detailed post.
Maybe it was the new years hangover but i didn't even think about using a usb stick.
And having the images attached to the post, made it a painless process.

So, thanks again mbsullivan.
~lf

---

### Post by billfeld on 2012-02-24
Thnks a lot. Works great for me.

You may be also interested in this:
[http://forum.notebookreview.com/lenovo-ibm/459591-t61-x61-sata-ii-1-5-gb-s-cap-willing-pay-solution-8.html#post6501443](http://forum.notebookreview.com/lenovo-ibm/459591-t61-x61-sata-ii-1-5-gb-s-cap-willing-pay-solution-8.html#post6501443)

It's a bios hack to enable SataII on many Lenovo Laptops... :popcorn:

---

### Post by Houmie on 2012-08-04
Hey,

Thanks a lot for this useful post.

I have a Lenovo X220 but also have the same problem of how to use the iso file to update the bios.

The iso file i need is this one here:

[http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8duj18uc.iso]("http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8duj18uc.iso")

I have followed your instructions up until here:
```

sudo mount -o loop [path to ISO file] [mount point]
```

But the iso seems empty, when I do a ls on the mount point. I can't proceed after that.

Any idea why this is happening?

Update:  I ended up burning the ISO on a CD and installing it from a CD. It worked fine. But how comes I couldn't mount and see the files inside the ISO? Its not ideal to burn each time a CD for a bios update :)

Many Thanks,
Houman

---

### Post by PPvG on 2012-08-27
> **Houmie said:**
> 
I have followed your instructions up until here:
```

sudo mount -o loop [path to ISO file] [mount point]
```

But the iso seems empty, when I do a ls on the mount point. I can't proceed after that.


I had the same problem (as did StickyTape, back on page 2). It turns out the iso is a boot image which contains a hard disk image. You can mount the hard disk image by setting the correct offset. For me, this worked:

```
sudo mount -o loop,offset=71680 [filename.iso] [mountpoint]
```

I have yet to try the bootable USB, but the files are all there.

The offset may be different for your iso. Unfortunately I have no idea how to find it. If you're interested, this is where I found this solution: [http://old.nabble.com/Re%3A-Bios-Splash-td33216538.html#a33270470](http://old.nabble.com/Re%3A-Bios-Splash-td33216538.html#a33270470)

---

### Post by bloblo blabla on 2012-11-06
> **mbsullivan said:**
> This tutorial details how to upgrade the BIOS of a Thinkpad x61, x61s or x61s tablet notebook using a bootable USB stick.

FWIW, I just used this procedure to upgrade the BIOS of my T61 to 2.30 (using the win98usb.tar disk image, and I had to type "command.com" at the prompt).  It went very smoothly, thank you very much.

---

### Post by Svagrad on 2013-04-14
Huge thanks! 
Worked like a charm updating Middleton's 2.29 BIOS on my T60/61 Frankenpad under Fedora 17

---

### Post by tomgobravo on 2013-09-14
I tried to use these instructions to upgrade the bios of a x201, which looked a lot easier than anything on [http://www.thinkwiki.org/wiki/BIOS_Upgrade/X_Series](http://www.thinkwiki.org/wiki/BIOS_Upgrade/X_Series)
Like some other people, I was trying to install from an iso in the 20MB range and needed to use an offset when mounting it, using [http://linux-thinkpad.10952.n7.nabble.com/Re-Bios-Splash-td20125.html](http://linux-thinkpad.10952.n7.nabble.com/Re-Bios-Splash-td20125.html) as a guide. To fix "cp: failed to preserve ownership for `/media/EED3-FFBD/TPCHKS.EXE': Operation not permitted" I used
```
sudo cp -dRfv --preserve=mode,timestamps /mnt/cdrom/* /media/EED3-FFBD/
```

The newest iso is 6quj19us.iso but when mounted I saw a bunch of corrupted file names /mnt/cdrom, so I tried the next newest, 6quj18uc.iso which looked much cleaner. After getting everything setup (and trying many times) I booted with the USB stick, typed "command.com" at the prompt and got the error "Incorrect DOS version" 

:sad:
[ATTACH=CONFIG]246239[/ATTACH]

To convince myself that everything else is working I tried the same procedure with X61 ISO 7nuj22uc.iso and I was able to start the upgrade program.

I tried the simple looking instructions in "[X220 BIOS UPDATE INSTRUCTIONS - USB]("http://forums.lenovo.com/t5/Linux-Discussion/SUPPORT-REQUEST-X220-BIOS-UPDATE-INSTRUCTIONS-USB/m-p/532077")" (using geteltorito.pl&#65279;) but got an "Missing operating system" error.

Hints welcome. Thank you.

---

### Post by tomgobravo on 2013-09-15
I gave up on trying to do the upgrade without modifying the target system and followed [http://www.thinkwiki.org/wiki/BIOS_Upgrade#GRUB2:_booting_CD_Image](http://www.thinkwiki.org/wiki/BIOS_Upgrade#GRUB2:_booting_CD_Image) which worked very well.

---

