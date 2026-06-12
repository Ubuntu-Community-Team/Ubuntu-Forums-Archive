---
title: "Howto: Create LiveUSBs from Windows using a GUI (UNetbootin)"
date: 2008-05-29
forum: Tutorials
---

### Post by tuxcantfly on 2008-05-29
_**Purpose/Overview**_

This guide creates a [color="blue"]_[LiveUSB](http://en.wikipedia.org/wiki/Live_USB)_[/color] out of your standard 1 GB (or larger) USB flash drive entirely from within Windows, using a nice graphical application (no command lines), [COLOR="Blue"]_[UNetbootin](http://unetbootin.sourceforge.net)_[/COLOR]. The generated Ubuntu (or, optionally, another Linux distribution) LiveUSB functions identically to a standard Ubuntu LiveCD, so you can use it for Ubuntu installs or system recovery as you would a LiveCD, the only caveat being that your computer will need to be fairly modern (built after roughly 2002) in order to be able to boot a USB drive.

_**Requirements**_

* Windows 2000, XP, 2003, Vista, 2008, or newer (though this guide can be done from Linux as well, see [color="blue"]_[site](http://unetbootin.sourceforge.net)_[/color]). I have personally tested this on Windows XP, Windows 2008 x64, Ubuntu 7.10 i386, and Ubuntu 8.04 amd64; the others were reported by users. Note that this will **NOT** work on Windows 95/98/ME.

* A USB drive, with slightly more free space than size of the ISO file you wish to use (roughly 700 MB for Ubuntu). Your USB drive will not be formatted, so your existing files *should* be safe, though backup important files just in case. (The USB drive should also be formatted as [FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table), though if you don't know what that is, don't worry; your USB drive is probably FAT32 unless you reformatted it yourself)

_**Instructions**_

**1.** [color="blue"]_[Download](http://unetbootin.sourceforge.net/unetbootin-windows-latest.exe)_[/color] the latest version of [COLOR="Blue"]_[UNetbootin](http://unetbootin.sourceforge.net)_[/COLOR] for Windows

**2.** [color="blue"]_[Download](http://www.ubuntu.com/products/GetUbuntu/download)_[/color] an ISO file for Ubuntu (any of its derivatives such as [color="blue"]_[Kubuntu](http://kubuntu.org/download.php)_[/color] or [color="blue"]_[Xubuntu](http://xubuntu.org/)_[/color] will also work).

**3.** Run the UNetbootin executable. The dialog shown in the screenshot below should appear (Note that the screenshots show PCLinuxOS, but the same procedure works for Ubuntu and most other distros). Select the *Disk Image* radio button, and use the file selector on the far right to select your ISO file. Select *USB Drive* as the installation type, and select your USB drive under "Drive". Note that memory cards will also be displayed, since Windows detects both as "Removable Drives", so ensure that it's really your USB drive that you're selecting. If your USB drive is not displayed, you may need to unplug and reinsert it, restart UNetbootin, restart Windows, and/or reformat the USB drive (To reformat your USB drive, go to "My Computer", right-click the *USB Drive -> Format*; note that this **will** wipe out all data on it, and should be unnecessary).

[img]http://sourceforge.net/dbimage.php?id=173795[/img]

**4.** Press OK to begin installing to your USB drive. As shown in the screenshot below, the installation occurs in 3 stages (downloading, extracting, and installing the bootloader), but since you've already pre-downloaded the ISO file, the first stage will be skipped. Since filesystem.squashfs is the largest file (over 650 MB), the progressbar will hang once it gets to this file as it is extracted and copied to the USB drive; this is only momentary, though; wait patiently, and do not close the application.

[img]http://sourceforge.net/dbimage.php?id=173797[/img]

**5.** Finally, after UNetbootin installs the bootloader onto your USB drive, you will be prompted to reboot, as shown below. Reboot. You should now be able to boot and install Ubuntu from your liveUSB drive, though you may first need to specify the USB drive in the boot order of your BIOS, which can usually be accessed by pressing *Esc*, *F1*, *F2*, *F12*, *Del*, or another key combination which is usually displayed as *Boot Devices* or *BIOS Setup* as your computer starts up.

[img]http://sourceforge.net/dbimage.php?id=173851[/img]

_**Undoing Changes**_

If all you wish to do is remove the Ubuntu liveUSB installation from your flash drive in order to free up space, you can simply delete the files and folders that were created by UNetbootin, which will be listed in the files "ubnfilel.txt" and "ubnpathl.txt" on the top directory of your USB drive. However, should you wish to wipe the last traces of the bootloader and liveUSB system out entirely, you can use the format tool included in Windows (note that this **will** wipe out all data on your USB drive); simply open *Windows Explorer*, navigate to *My Computer*, right-click the drive letter of your USB drive, and select the *Format* option from the drop-down menu. Accept the default options (though you may want to check the "Quick Format" option if you're impatient), and your USB drive will be wiped clean and reformatted.

_**Notes/Credits/Misc**_

[COLOR="Blue"]_[UNetbootin](http://unetbootin.sourceforge.net)_[/COLOR] was created by me (Geza Kovacs). This is a simplified version of the guide I previously posted on the [color="blue"]_[PCLinuxOS forum](http://www.pclinuxos.com/index.php?option=com_smf&Itemid=58&topic=46097.0)_[/color], with instructions/information that shouldn't be required for Ubuntu (altering USB drive partitioning schemes) removed. This same procedure should also work for creating LiveUSB drives out of various other isolinux-based ISO files (used by most mainstream Linux distributions, such as Fedora, PCLinuxOS, etc), though it won't work for Windows CDs or the like. If you think you've found a bug [color="blue"]_[file a bug report](https://bugs.launchpad.net/unetbootin)_[/color], or post the issue you're experiencing.

---

### Post by dubref on 2008-05-29
Simply great utility!

It worked flawlessly. I did reformat the Flash drive to FAT32. Drive in question is a 2GB PNY model.

Before that, I had followed instructions from Ubuntu at: [http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/](http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/) and it was not recognizing the boot sector apparently and was at my wits end till I saw your post.

Thank you so much. :)

---

### Post by AndyCee on 2008-05-30
Very smooth, very cool.

Is there any way to make it persistent?

---

### Post by tuxcantfly on 2008-06-01
***_EDIT:_* This apparently doesn't work anymore on 8.04 (I last tested this on 7.10), see [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) for instructions instead**

> **AndyCee said:**
> Very smooth, very cool.

Is there any way to make it persistent?

Go to [http://unetbootin.sourceforge.net/diskimg/](http://unetbootin.sourceforge.net/diskimg/) and download one of the files (128mb.zip, 256mb.zip, or 512mb.zip) corresponding to the amount of persistent space you want (make sure the size of the persistent disk image is smaller than the free space you have on your USB drive).

Now extract the file "casper.rw" from the zip file to your USB drive.

Now edit D:\syslinux.cfg (assuming D:\ is where your USB drive is) and add in "persistent" at the end of the line that begins with "append", and save the file, so your syslinux.cfg should look something like this:

```

default unetbootin
label unetbootin
	kernel /ubnkern
	append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --

```

For more info see [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Hopefully I'll get this automated in the next version or so.

---

### Post by geetarista on 2008-06-11
I'm trying to install Hardy Server (from iso), but I keep running into a couple of problems.  The first issue I have is with the CD-ROM detection.  No matter what I do, it can't install drivers or detect a CD-ROM since it doesn't exist.  That's the whole point of my trying this out.  I'm assuming this then causes an issue with debconf since it's looking in /cdrom/preseed/ubuntu-server.seed and cdrom doesn't exist.

Any ideas?

It looks like this bug report is probably related to my issue: [https://bugs.launchpad.net/unetbootin/+bug/237867](https://bugs.launchpad.net/unetbootin/+bug/237867)

---

### Post by tuxcantfly on 2008-06-11
> **geetarista said:**
> I'm trying to install Hardy Server (from iso), but I keep running into a couple of problems.  The first issue I have is with the CD-ROM detection.  No matter what I do, it can't install drivers or detect a CD-ROM since it doesn't exist.  That's the whole point of my trying this out.  I'm assuming this then causes an issue with debconf since it's looking in /cdrom/preseed/ubuntu-server.seed and cdrom doesn't exist.

Any ideas?

It looks like this bug report is probably related to my issue: [https://bugs.launchpad.net/unetbootin/+bug/237867](https://bugs.launchpad.net/unetbootin/+bug/237867)

I haven't tested using any of the alternate/install Ubuntu isos, but I presume they apparently don't have the necessary filesystem drivers or the like built in into the default initrd, so it probably won't work.

You could either simply install using the standard desktop/liveCD version, remove the GNOME stuff and install the various server-specific packages.

Alternatively, should you happen to have internet access on the machines, you can use the "Netinstall" version of Ubuntu (listed under the version selection box), and from there you can select the option to download and install the server-specific packages once you've rebooted and have started the installer.

Alternatively, you could also manually give it the "hd-media" kernel and initrd files, available from the Ubuntu FTP archives, and that should be able to detect your predownloaded and extracted ISO file and install from it.

---

### Post by geetarista on 2008-06-12
Thank you for your response.  I tried both the netinstall and using a regular iso, but now I'm having the same issue as people in this thread: [http://ubuntuforums.org/showthread.php?t=824576](http://ubuntuforums.org/showthread.php?t=824576).  I'll post a follow-up once I figure something out.

---

### Post by tuxcantfly on 2008-06-12
> **geetarista said:**
> Thank you for your response.  I tried both the netinstall and using a regular iso, but now I'm having the same issue as people in this thread: [http://ubuntuforums.org/showthread.php?t=824576](http://ubuntuforums.org/showthread.php?t=824576).  I'll post a follow-up once I figure something out.

Since the updated initrd is already in hardy-proposed, I suppose this'll be fixed upstream soon, but until then, you can download the latest kernel (linux) and initrd (initrd.gz) files from [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/installer-i386/current/images/netboot/ubuntu-installer/i386/) and supply them to UNetbootin under the "Manual" option as the kernel and initrd files.

Also, what was the issue you encountered with the regular iso (I presume you tried installing using the standard, full Ubuntu desktop/liveCD as I suggested)?

---

### Post by geetarista on 2008-06-13
Yeah, I tried all of the options and still doesn't work.  One time I got this error: "No boot filename received. DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER."  I did some searching and I guess it's trying to boot from the network, which obviously doesn't work.  I don't know if grub wasn't installed correctly or if it's something else.  My BIOS boot settings are also correct.  I don't know if this is a hardware issue or just this whole process.

I really need to have a static solution because my client wants to pay for the USB so they can re-use it to install on other servers with my instructions.  So it would be best if I could use an ISO install of Ubuntu Server to make things a lot easier for them and myself.  What do you suggest?

I also just tried downloading the kernel and initrd files using the manual option like you suggested and I now get the original problem where it can't find a cd-rom.

---

### Post by Kpu4 on 2008-06-15
Used Unetbootin(Win) on 2 distros. After succesive write on "Flash-card" One freezes at OS load screen, second doesn`t even want to boot(freezes when trying to read data from card and shows "couldn`t find kernel" error). The distros are:

"mandriva-linux-one-2008-spring-KDE-int-cdrom-i586"

"ubuntu-8.04-desktop-amd64"

Tryed both on 2 PCs, one is my laptop, second is desktop, errors are the same. The errors about "couldn`t find/Mount" directories or files in both cases. Could it be because I use micro SD card instead of "normal" USB-Flash Drive? Any tip on solving this?

Tryed it on USB-HDD, same errors.

Could it be what Unetbootin works "better" under linux OS? )

The photo of screen with errors is [here]("http://img150.imageshack.us/img150/5646/mandrivascreenbv5.jpg").
Sorry for bad angles, don`t have a tripod.

---

### Post by terry_gardener on 2008-06-16
when ever i try this on my 8gb usb drive 

it seems to do it ok but when trying to boot using usb it just seems to ignore it and loasd the default os already on the system. 

I have changed the boot order for the usb memory to boot first but still the same. 

any ideas 

i have tried the pendrivelinux and unetbootin same results for both 

Thanks

---

### Post by tuxcantfly on 2008-06-26
> **terry_gardener said:**
> when ever i try this on my 8gb usb drive 

it seems to do it ok but when trying to boot using usb it just seems to ignore it and loasd the default os already on the system. 

I have changed the boot order for the usb memory to boot first but still the same. 

any ideas 

i have tried the pendrivelinux and unetbootin same results for both 

Thanks

If you've used both pendrivelinux and unetbootin, and your computer isn't booting from USB for either, it's most likely your BIOS settings. Consult your motherboard's manual, they usually have instructions for booting from various media, are you completely sure you set it up correctly? Maybe you'll have to update your BIOS if it's an older computer. If you're certain you configured it correctly, try booting the USB drive on another computer which you have confirmed is able to boot from USB, does it boot then, or does it also ignore the USB drive (if it's the former, then it's an issue with your BIOS)? Perhaps check the contents of the USB drive, can you confirm that the hidden file ldlinux.sys and syslinux.cfg exist (they should)?

@Kpu4: that's most likely because you're using a micro-SD card, and some card readers aren't supported by Linux; try again with a proper USB drive or maybe try the Hard Disk installation mode, or perhaps try installing a different distro (PCLinuxOS tends to work well).

---

### Post by nothingspecial on 2008-06-26
I`m trying to install Ubuntu 7.10 on a laptop with a broken cd drive. I get the error "couldn`t find kernel /ubnkern" or something similar.
 The laptop is currently running Ubuntu 8.04 but it`s messed up (my fault I just love to tweak).
 It will boot from usb because I tried some manual instructions (copying the content`s of a cd onto the pendrive, putting syslinux on it, editing the syslinux.config files etc) and it nearly worked.
 Should I be selecting Hard Disk on the bottom left dropdown where it says type? (I want a clean Gutsy install over the whole laptop).
 The instructions at the top of this thread are for windows. Should I be doing something different from Ubuntu?
 Thanks.

---

### Post by tuxcantfly on 2008-06-27
> **nothingspecial said:**
> I`m trying to install Ubuntu 7.10 on a laptop with a broken cd drive. I get the error "couldn`t find kernel /ubnkern" or something similar.
 The laptop is currently running Ubuntu 8.04 but it`s messed up (my fault I just love to tweak).
 It will boot from usb because I tried some manual instructions (copying the content`s of a cd onto the pendrive, putting syslinux on it, editing the syslinux.config files etc) and it nearly worked.
 Should I be selecting Hard Disk on the bottom left dropdown where it says type? (I want a clean Gutsy install over the whole laptop).
 The instructions at the top of this thread are for windows. Should I be doing something different from Ubuntu?
 Thanks.

Since you used custom instructions, did you also remember to copy the kernel file at (paths relative to the ISO/USB drive contents) /casper/vmlinuz to /ubnkern, and the initrd file at /casper/initrd.gz to /ubninit, since that's where UNetbootin expects those files to be? It seems like syslinux, which has been configured to go by UNetbootin's default paths, is not finding them. Otherwise, try changing the syslinux.cfg to this:

```
default unetbootin
label unetbootin
	kernel /casper/vmlinuz
	append initrd=/casper/initrd.gz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
```

---

### Post by efrenefren on 2008-06-28
in UNetbootin 235 Damn Small Linux 4.4 Live (The only option) does not work.

---

### Post by efrenefren on 2008-06-28
> **efrenefren said:**
> in UNetbootin 235 Damn Small Linux 4.4 Live (The only option) does not work.

does not work meaning it does not download the ISO file.

---

### Post by tuxcantfly on 2008-06-28
> **efrenefren said:**
> in UNetbootin 235 Damn Small Linux 4.4 Live (The only option) does not work.

Oh darn, seems like the URL changed. For the time being, just download the ISO file from [ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-4.4.2-initrd.iso](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-4.4.2-initrd.iso) and specify it using the ISO diskimage option.

---

### Post by efrenefren on 2008-06-28
Why not use this link instead?
[ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/current.iso](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/current.iso)

so that you will always sure you will get the current. :D

---

### Post by tuxcantfly on 2008-06-28
> **efrenefren said:**
> Why not use this link instead?
[ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/current.iso](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/current.iso)

so that you will always sure you will get the current. :D

That one points to the standard ISO ( [ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-4.4.2.iso](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-4.4.2.iso) ) which doesn't work as reliably as the -initrd.iso one since it has to locate the external file titled "KNOPPIX" on boot, rather than having everything be loaded via the initrd by the bootloader at once. I'll probably just use a few regexps to filter out the latest url to the -initrd.iso file to avoid having to update the urls.

---

### Post by SAKeeler on 2008-06-29
im having some issues with getting the drive to boot, maybe someone has some ideas.

Windows xp SP3 is the working OS for creation of the drive.  I'm using a 20 GB toshiba HD in an external enclosure.

creation of the target from an ISO of the latest ubuntu seems to go fine. but when i boot to the usb drive i get:

Remove Disks or other media.
Press any key to restart.

unetbootin-windows-235.exe is being used

thoughts are welcome on what to try.
if you require more details on anything just ask.

i have tried creating the usb drive with the linux installer as well through the ubuntu live cd
the results are the same

---

### Post by tuxcantfly on 2008-07-03
> **SAKeeler said:**
> im having some issues with getting the drive to boot, maybe someone has some ideas.

Windows xp SP3 is the working OS for creation of the drive.  I'm using a 20 GB toshiba HD in an external enclosure.

creation of the target from an ISO of the latest ubuntu seems to go fine. but when i boot to the usb drive i get:

Remove Disks or other media.
Press any key to restart.

unetbootin-windows-235.exe is being used

thoughts are welcome on what to try.
if you require more details on anything just ask.

i have tried creating the usb drive with the linux installer as well through the ubuntu live cd
the results are the same

Try booting the USB drive on another computer that you know can boot from USB; are you getting the same error? Did you also check the contents of the drive you installed to after UNetbootin installed; were the contents of the Ubuntu ISO file, and the files syslinux.cfg, ubnkern, ubninit, and ldlinux.sys (you may need to use "show hidden files" to see them) in the top directory of the drive?

---

### Post by animetal on 2008-07-05
Just to confirm with you tuxcantfly, does persistent mode work with Linux Mint 5r1?

---

### Post by JR Tyner on 2008-07-13
A few questions before I try this:

1. My USB MicroDrive has a 9GB FAT32 partition and a 3GB Swap Partition. If I install Xubuntu on the FAT32 partition will it recognize and use the 3GB Swap Partition also on the MicroDrive?

2. I have 6GB worth of Windows programs that I need to do my job and they have no Linux versions. Can I install them on the drive with WINE?

3. Will I be able to put this drive in my computer at work and run Xubuntu by bringing up the boot menu with F12?

4. Will I be able to upgrade Xubuntu, or will I need to reinstall it using a new iso file?

5. Any other comments, suggestions, hints for a first time user?

---

### Post by animetal on 2008-07-13
JR Tyner, I think you can do a normal install to your USB stick. See [here]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/") for more information.

So far, I've only converted my USB stick into a LiveUSB distro using unetbootin and it works like a charm.

---

### Post by mattisking on 2008-07-17
tuxcantfly, Thanks a LOT for this utility. I picked a very bad time to attempt a fresh install (not primary machine so it's not the end of the world or anything) of Intrepid Alpha 2 because apparently my CD drive is dying. I downloaded the Alternate Installer (no Live CD yet - I wish you'd suppport, if possible, the Alternate Installer) and verified the MD5 of the ISO but every time I'd to an integrity check it would fail. Ultimately the CD's were fine though (tested on another machine)... the CD drive was dying. Later tests proved this out when the install puked after nuking my old partitions. Anyway, since unetbootin doesn't support the alternate installer image, I let it download and create based on the Hardy refresh. I read on the wiki that certain changes would be required but that turned out not to be the case for me. It worked perfectly! Thanks a lot!

---

### Post by stangdaman on 2008-08-01
I had a question about this. I used this software to setup the live usb stick. I went into the bios and set it to boot from the usb drive and it does. It brings up the little ubuntu loading graphic but once that finishes it just goes to a blank screen. I'm not quite sure why or how to tell what's going on. It did work with the iso on a dvd. I just need it for another PC though that I'm not able to use the cd drive on.

---

### Post by stangdaman on 2008-08-01
So, it would appear that the problem that I was having was related to the specific PC I was trying it on. I don't know why the iso on a dvd would work and not on a flash drive but it is working on other PCs and working for the one I wanted it to in the first place anyway. I just had another question though. Is there a way to make the live usb drive persistent while you're using it. Or would you only be able to do it from outside in windows or linux? I saw the instructions about making it persistent but I'm not sure if I can edit those things while it's running. 

Also, if I can would it be the one labeled as "file system" that I want to extract the casper.rw to?

---

### Post by tzepu on 2008-08-17
well 
i tried UNetbootin and it works like a charm
but
i need to make a multiboot pendrive (i need several distros and recovery iso's), all i want is put the pendrive into the usb port, start the computer, and choose which iso image to load
UNetbootin does that but uses just one iso at the time
is there possible to make it to put on the pendrive several iso's at once?
and to be able to choose which one to boot?
i tried to create multiboot iso(it is ok this way too) with magiciso,ultraiso,easyboot(this one is much too complicated for me,it might work if someone can explain me how to create a multiboot isowith it)
but al of them makes my pendrive getting stuck after booting at the main menu, where i have only 'default' option, and no other, and nothing works, the timer continue to run from 10 seconds to 0 again and again
when i put on just one iso, everything runs ok(i can get into livecd, install it, etc)

---

### Post by sandos on 2008-08-21
Persistance is higly needed or fedore will crush ubuntu using [https://fedorahosted.org/liveusb-creator](https://fedorahosted.org/liveusb-creator)

:)

I know there is a liveusb project in launchpad, but thats not for windows, which is an important demographic for getting new users.

---

### Post by moycano on 2008-08-21
when I try with the *Ubuntu 8.04.1, during the boot I get several "Buffer I/O error on device fd0 logical block 0" warnings and the system fail to start.

Could be a distro stuff? I've successfully start many LiveUSB --> LiveUSB before (including *Ubuntu 8.04) but only with this version get this errors.

Following the pendrivelinux's tutorials, I also have the messages but the system actually start after a long wait.

:confused:

SALUDOS/REGARDS.

---

### Post by minhmeoke on 2008-09-10
@JR Tyner:
Check the AppDB on WineHQ [http://appdb.winehq.org/](http://appdb.winehq.org/) to find if your windows programs work in wine. Also note that UNetbootin will create a LiveUSB, so you will need to create another partition on your flash drive if you want to save changes. One last comment: using the flash drive for swap will decrease its lifespan.

@stangdaman, sandos:
A black screen after splash usually means that X.org or your graphical environment failed to start. If you are interested in persistent usb, then see [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

@tzepu:
Multi-boot USB is possible, see this: [https://answers.launchpad.net/unetbootin/+question/24298](https://answers.launchpad.net/unetbootin/+question/24298)

@moycano:
What filesystem is the usb formatted as? You can check with "sudo fdisk -l"; it should be FAT32, and NTFS will not work. Also, there may have been some kind of problem mounting the usb device, since fd0 usually refers to floppies. You could check if the usb is mounted correctly with "lsusb", and also see the error log with "dmesg" command. You could also try reformatting the drive, or checking if it has errors.

---

### Post by Pyro_Killer on 2008-10-02
Dear makers of the Unetbootin software, I have used your method to install ubuntu 7.10 on my eee pc, which I am very satisfied with. the eeeubuntu sucks, so thank you for that. 

What I find dissapointing, is that the mandriva installer has absolutely NO real function, it can't install the download way, nor the ISO way.

Please fix this little, bug, beacause ther are many people out there that really needs this feature without getting all scripty

---

### Post by quizwedge on 2008-10-03
I noticed that the docs say that you can use UNetbootin to create a dual-boot system, but I can't find the option to do that.  I've got a 2GB USB key that I'm trying to put BackTrack and Ophcrack on.  Parted Magic too if I have the room.  What option(s) do I need to select so that it makes it a dual-boot system instead of just overwriting the files that are the same?

---

### Post by Natanael_L on 2008-10-22
Yeah, I want built-in support for this.
 
I think that there should be a dual boot checkbox that makes two buttons appear when the user have set their options for the first OS - "Next OS" and "Done".
 
If the user click on "Next OS" then it should keep the settings in memory until the user click on "Done".
If the user click on "Done" before setting up a second OS, then it will work like a single boot system.
If the user click on "Done" after setting up more than one OS, then all will be installed, but instead of just installing them all one by one, the OS:es and the (one and only (no need for one per OS)) boot loader (GRUB?) will be configured so that all OS:es will be listed in a single boot loader at boot.

---

### Post by vjones777 on 2008-11-01
> **Natanael_L said:**
> I think that there should be a dual boot checkbox that makes two buttons appear when the user have set their options for the first OS - "Next OS" and "Done".
... boot loader (GRUB?) will be configured so that all OS:es will be listed in a single boot loader at boot.

Agreed - that would be nice.  It would also be nice to be able to specify how much space to allocate to a swap partition - a FAT32 partition to be able to swap files with windoze PCs would be nice.  (I'm assuming here that Unetbootin creates an extX partition as if it created a FAT partition then windoze isnt able to recognise a 2nd FAT partition on a USB stick from what I understand).

Apparently it is possible for UNetbootin to support multiple OSes, but you have to manually do that.  [Have a look]("https://answers.launchpad.net/unetbootin/+question/24298").

---

### Post by pumpin on 2008-11-02
hi
i also have a problem with this.
after installing and reboot
i boot from the usb and there's no problem.
but after i select start *ubuntu without change ...
it loads and stops after loading the vmlinuz, and initrd.gz

it looks some sort of this

vmlinuz.....................................ready
initrd.gz...................................ready

and after that it doesn't go on so where's the problem?

---

### Post by karlmp on 2008-11-04
hi,
after installing, rebooting and changing the boot priority order in the BIOS i just get a black screen with the cursor blinking in the upper-left corner

(i have dual boot: Ubuntu 8.04.1 (messed up (i love to tweak)) and windows xp)

i just want to edit the Ubuntu and windows partitions to give more space to Ubuntu and less space to windows and then format Ubuntu to do a fresh install of intrepid ibex

---

### Post by C.S.Cameron on 2008-11-04
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent", (this must be done at every boot that you want persistence.
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

This only works with 8.10 as 8.04 has a flaw in casper.

I'm wondering what to modify so that I don't need to hit Tab, then type "(space)persistent" at boot?

Oops missed the thing about editing syslinux.cfg in post 4.
Tried this and now I don't have to type persistent at each boot.

I sort of like home and casper on separate partitions so I can update the kernel with out loosing all my stuff.

---

### Post by HereSkip on 2008-11-10
Hi,

I've just tried to install the 8.10 x64 on my usb device and when I boot up it says

"Could not find kernel image: linux"

I have done an MD5 check on the iso and it is not corrupted.

Any ideas?

Thanks

---

### Post by Timber_Wolf on 2008-11-15
I have a few questions, as I have never done something this complicated before:

1. If I make my USB into a LiveUSB, can I then use that same USB to run the Ubuntu 8.10? (I'm new to Linux so I don't know exactly what a LiveUSB is... as in, is it just an installation function, or a full-blown OS)
2. I heard that 8.10 already has a USB creator with some sort of a persistency function.  Will this work if I make a LiveUSB with this method? 

I guess what I really want to know is if I can use the LiveUSB like I would a LiveCD to do this:  [http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

By that I mean using the LiveUSB to put Ubuntu 8.10 on the SAME USB.

Thank you in advance for any help you can give me

---

### Post by OBnascar on 2008-11-16
Of course I know this is not the correct place to be posting this, but I can not find the correct place. 

I was looking for a Linux Unetbootin USB install tutorial. I can not get my installs persistent and want to find out why, pretty much useless if they are not persistent.

Could some one please point me in the right direction ?

thanks,
obnascar

---

### Post by minhmeoke on 2008-11-22
@people getting black screens: could you post your syslinux.cfg here? Also, can you enable debugging by removing the "quiet splash" options in the append: line in syslinux.cfg? If UNetbootin does not work for you, then you can try Pendrivelinux [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) or the built-in USB creator in Ubuntu 8.10. If none of these work, then there may be something wrong with your motherboard's BIOS settings that prevents you from booting from USB.

@Timber_Wolf: LiveUSB is a usb-drive that boots a full operating system in RAM, but does not save your changes when you shut down. Persistent USB install saves your changes, but it also causes the USB drive to wear out faster due to more write cycles.

@OBnascar: Ubuntu 8.10 includes a tool to create live and persistent USBs, but if you want to use UNetbootin you can follow the instructions in [http://ubuntuforums.org/showpost.php?p=6106470&postcount=38](http://ubuntuforums.org/showpost.php?p=6106470&postcount=38) . You should also add the "persistent" option to the "append" line in syslinux.cfg as described in [http://ubuntuforums.org/showpost.php?p=5089854&postcount=4](http://ubuntuforums.org/showpost.php?p=5089854&postcount=4)

---

### Post by martinveasey on 2008-11-23
Hi - thanks for the great utility. Really easy to use.

Hope you don't mind but I have a question on the subsequent installation that is bugging me. I have a new PC which I want to set up as a server. It has no CD-ROM installed (in the event, I think I'll buy a cheap SATA internal and use it just for the installation or use a USB external).

Anyway, I've used UNetbootin to prep up an external hard disk (USB) to mirror the ISO files and it boots up fine to the first 8.10 server menu. I select install server and the first two stages (language and keyboard selection) work fine. The third stage of the install enables the selection of the source CDROM. This isn't autodetected and the installer defaults to allowing you to select modules and devices to continue.

It ought to be easy - no module required and simply select the relevant /dev/sdb1 in my case, but the attach doesn't work. Dropping to one of the simple text terminals indicates that the mount simply doesn't work - mount -t msdos /dev/sdb1 /cdrom.

Is anyone aware of a troubleshooting guide that I can read through?

Cheers,

Martin

---

### Post by Philip390 on 2008-11-27
> **tuxcantfly said:**
> ***_EDIT:_* This apparently doesn't work anymore on 8.04 (I last tested this on 7.10), see [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) for instructions instead**



Go to [http://unetbootin.sourceforge.net/diskimg/](http://unetbootin.sourceforge.net/diskimg/) and download one of the files (128mb.zip, 256mb.zip, or 512mb.zip) corresponding to the amount of persistent space you want (make sure the size of the persistent disk image is smaller than the free space you have on your USB drive).

Now extract the file "casper.rw" from the zip file to your USB drive.

Now edit D:\syslinux.cfg (assuming D:\ is where your USB drive is) and add in "persistent" at the end of the line that begins with "append", and save the file, so your syslinux.cfg should look something like this:

```

default unetbootin
label unetbootin
	kernel /ubnkern
	append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --

```

For more info see [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Hopefully I'll get this automated in the next version or so.
Are there any files for making a larger casper-rw file? Very useful btw

---

### Post by thisisasignin on 2008-11-30
> **HereSkip said:**
> Hi,

I've just tried to install the 8.10 x64 on my usb device and when I boot up it says

"Could not find kernel image: linux"

I have done an MD5 check on the iso and it is not corrupted.

Any ideas?

Thanks

Hello. I get this error as well.

I have tried Ubuntu (Hardy & Intrepid) as well as Puppy and Mint.
They all work when booting from my 8GB USB drive in a *laptop*.
However, when trying to use the same 8GB USB drive in a *desktop*, I get the kernel image error.

I do not understand why I would get the error on one machine, but not another.
Any insight would be appreciated and thank you in advance.

---

### Post by minhmeoke on 2008-12-05
@ martinveasey: What is the error message you get when you try to mount? If the system just hangs, then maybe the device is very large and mounting it takes a long time.
1) Can the system see the USB device at all, check with "lsusb".
2) Are you sure that the location that the system assigns the drive is sdb1, check "dmesg | tail" after plugging in the usb drive.
3) is /cdrom already being occupied by another device(check "mount"), or is its fstab entry somehow conflicting?
4) try creating a new mount node using "mknod", try mounting there.
Edit: there's a guide here: [http://ubuntuforums.org/showthread.php?t=48126](http://ubuntuforums.org/showthread.php?t=48126)

@ Philip390: As far as I can tell, casper.rw is just a standard ext3 filesystem labelled as casper-rw, so you should be able to create it yourself with the partition editor as described here: [http://ubuntuforums.org/showthread.php?p=6192609](http://ubuntuforums.org/showthread.php?p=6192609)

@ thisisasignin: That is strange, there could be a resource conflict or some other hardware-specific problem. Could you post logs, if available? I'll notify tuxcantfly, the UNetbootin developer.

---

### Post by mhh91 on 2008-12-05
i've used unetbootin before,but now it doesn't install the bootloader,why?


when i boot using the USB option,it ignores it and boots from my hard disk,what did i do wrong??

---

### Post by shane wiley on 2008-12-06
I installed ubuntu from a memory disk using unetbootin (the cd drive is not working too well).
Seemed fine, but after install the USB ports will not properly mount a memory stick (have tried a number of different sticks that work fine on my other computers with ubuntu). The screen will display the name of the memory stick, just not allow it to be opened.
The USB ports do 'talk to' a USB floppy drive, and do talk to printers.

---

### Post by thisisasignin on 2008-12-08
> **minhmeoke said:**
> 
@ thisisasignin: That is strange, there could be a resource conflict or some other hardware-specific problem. Could you post logs, if available? I'll notify tuxcantfly, the UNetbootin developer.

Hello, thank you for your reply.
If there is a log available, where/how would I be able to locate it?
As far as I can tell, nothing gets written to the USB drive. 
Would there be a log in the ram?

---

### Post by Indycent on 2008-12-12
Ok, I can get this to work perfectly with <8.10 desktop i386>, but whenever I try to install <server 8.04 i386> I get the following error.

> Loading /ubnkern................................
Loading /ubninit..........................................................................ready.
[    0.000000] initrd extends beyond end of memory (0x1f6864f8 > 0x1f686000)
[   26.074621] Kernel panic - not syncing:  VFS: Unable to mount root fs on unknown-block(104.1)

Anybody have a suggestion?  EDIT: I have tried formating in both FAT and FAT32... same error for both.

UPDATE:I DL'ed the <8.10 server i386> and I get the same error that martinveasey(@7 posts above) gets.  It says it cannot find the cdrom.  I have tried some of the suggestions of minhmeoke to no avail.
1. "lsusb" which is "not found", I assume it is not included in the limited built-in shell.
2. "dmesg | tail"  the message I get:
> 
[9.297697] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[9.297701] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[9.301040] sd 4:0:0:0: [sdb] 3915776 512-byte hardware sectors (2005 MB)
[9.301786] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[9.301802] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[9.302021] sdb: sdb1
[9.303636] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[9.304025] sd 4:0:0:0: Attached scsi generic sg1 type 0
[490.560762] Intel ISA PCIC probe: not found.
3. I see nothing about fstab or cdrom at all when I "mount".
4. No clue about usage of mknod.(I used to use UNIX/AIX a lot, but I am no admin)

P.S.  I am using a mini-pc that has no CD/DVD... hell if it had more than one SATA port I would use the CD instead of the USB.

---

### Post by klausthorn on 2008-12-15
@thisisasignin: after the error message "Could not find kernel image: linux" in my case appeared a prompt "boot:".

After this prompt I could enter a kernel file name and options. in my case worked:

ubnkern initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper

ubnkern is the kernel filename relative to the main directory of my usb stick. the same is true for ubninit, the filename of the inital ramdisk filesystem image.

The other options I got from reading syslinux.cfg in the same directory.

---

### Post by thisisasignin on 2008-12-16
> **klausthorn said:**
> 
ubnkern initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper


Thank you.
I will give that a try.

---

### Post by dbbd8 on 2008-12-19
I created a bootable USB using unetbootin, and installed 
ebuntu 2.0 iso on it.

When I boot using the USB, I get the Unetbootin screen. It has
"Default, Help & oem entries, and it counts down to automatic boot. When the count down hits 0, then refreshes the same screen and starts to count down again (same happens when I hit enter).

Any way to see a log? errors? debug it?

(Might be relevant - I first burned a CD with the same distro, when I boot it, I get the splash screen, but when I hit install, the cd spins, but nothing happens. The live cd won't start either)

Thanks,
Dan

---

### Post by thisisasignin on 2008-12-21
> **klausthorn said:**
> 
ubnkern initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper


After trying that command at the boot: prompt, I get
> Could not find kernel image: ubkern
:confused:

---

### Post by Slym.fr on 2008-12-21
I've made a software to make a LiveUSB very easily.

You can try it out at [http://usbuntu.slym.fr]("http://usbuntu.slym.fr")

It's only working with Ubuntu 8.10, Kubuntu 8.10 and Xubuntu 8.10.

Don't be afraid, the webpage is in french but the software is multilanguage (French/English) 

It's really easy to use and if you are lucky you will be able to boot directly your usb key in windows through the integrated Portable VirtualBox.

 :popcorn: I hope you will enjoy it. :popcorn:

I also opened a dedicated thread there : [http://ubuntuforums.org/showthread.php?t=1011152]("http://ubuntuforums.org/showthread.php?t=1011152")

---

### Post by bradsmith on 2009-01-01
Hi,

I'm trying to get a bootable/runnable openSUSE distro onto a USB stick that will persist data.

I got it installed and booting from my USB stick using the Windows UNetbootin utility, but step 3 on the website ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) says "After rebooting, select the UNetbootin entry from the menu list as the system boots up", however there doesn't seem to be any option like this. The only options are:

1. Default
2. openSUSE_Live_(KDE)
3. Failsafe_Settings
4. mediacheck
5. memtest

Choosing ANY of the options runs through the usual text boot echos, but it hangs at the following:

------->Waiting for CD/DVD devices to appear...
------->Mounting live boot drive.....
------->Couldnt find live image configuration file
------->rebootexception: error consoles at Alt-F3/F4
------->rebootexception: reboot in 120 sec....

Ive tried this with 2 USB sticks, one was a 2GB Sony, the other a 4GB LG
I used the live cd distro: "openSUSE-11.1-KDE4-LiveCD-i686.iso". Is this the right one to use?

Any help for a noob would be greatly appreciated.

---

### Post by le12 on 2009-01-03
> **dbbd8 said:**
> I created a bootable USB using unetbootin, and installed 
ebuntu 2.0 iso on it.

When I boot using the USB, I get the Unetbootin screen. It has
"Default, Help & oem entries, and it counts down to automatic boot. When the count down hits 0, then refreshes the same screen and starts to count down again (same happens when I hit enter).

Any way to see a log? errors? debug it?

(Might be relevant - I first burned a CD with the same distro, when I boot it, I get the splash screen, but when I hit install, the cd spins, but nothing happens. The live cd won't start either)

Thanks,
Dan

I also have the same problem using liveusb. Can someone help please?

---

### Post by le12 on 2009-01-04
I found the solution for my problem. The file was corrupted. Download Ubuntu again and it works. You should download it again dbbd8.

---

### Post by Patrick Snyder on 2009-01-09
Is there any difference in the outcome between these two?  Is the USB stick the same in the end?
[LIST=1]
[*]"Create a USB Startup Disk" in Ubuntu 8.10 
[*]Installing Ubuntu 8.10 on a USB with Unetbootin
[/LIST]

---

### Post by oomingmak on 2009-01-11
> **mhh91 said:**
> i've used unetbootin before,but now it doesn't install the bootloader,why?

when i boot using the USB option,it ignores it and boots from my hard disk,what did i do wrong??
I get the exact same problem.

All files are copied across correctly, but when I switch boot device in the BIOS (so that the system boots from the USB stick) nothing happens, and it ends up booting from my default hard disk instead.

UnetBootin DID work for me when I let it install files to my c:\ drive, but obviously that is not a preferred method. I don't want to be scattering stuff all over my system drive, even if only temporary.

I tried various different ISO distros, but same problem occurred every time I tried to use USB.

Plus, I have 3 USB sticks in and only the two that I DON'T want to use are shown in the UnetBootin drop list. I have to check "show all drives" to show the USB key that I wnat to use. I don't know why it only shows the other two USB devices.

---

### Post by drinkmocha on 2009-01-11
My netbook (S10) is stuck on black screen after rebooting after a fresh install of Ubuntu using a liveUSB. Please help. I tried going to the boot order and BIOS but nothing happens. I hear the harddrive make a sound after 3 seconds and that's it.

Now I don't know what to do without being able to access even BIOS. Help please. :(

---

### Post by borlosky on 2009-01-14
> **drinkmocha said:**
> My netbook (S10) is stuck on black screen after rebooting after a fresh install of Ubuntu using a liveUSB. Please help. I tried going to the boot order and BIOS but nothing happens. I hear the harddrive make a sound after 3 seconds and that's it.

Now I don't know what to do without being able to access even BIOS. Help please. :(

sounds more like a hardware/pc issue, but try to format/reinstall see if you get any change. if no change, i'd start trouble shooting your hardware. not being able to get into your pc's bios shouldn't have anything to do with an ubuntu install.

---

### Post by dmanchipman on 2009-01-27
Humm...

So I want to try something, but I'm not sure how safe it would be, and I wanted to check first.

I want to use UNetbootin to create a partition on my Zune and use a portion of its harddrive to work as a LiveUSB.

How plausible is this and will it work? What risks do I face by doing this?

---

### Post by danmarycap on 2009-02-15
> **tuxcantfly said:**
> Did you also check the contents of the drive you installed to after UNetbootin installed; were the contents of the Ubuntu ISO file, and the files syslinux.cfg, ubnkern, ubninit, and ldlinux.sys (you may need to use "show hidden files" to see them) in the top directory of the drive?

downloaded the ubuntu-8.10-alternate-i386.iso and used UNetbootin to create a Live USB bootable drive.  When I try to boot my Dell Mini9 from the USB (so I can install Ubuntu 8.10), I get (on a DOS-like black screen with white text):

Intel UNDI, PXE-2.1 (build 082)
Copyright (C) 1997-2000 Intel Corporation

For Realtek RTL8101E/8102E PCI-E Ethernet Controller v1.08 (080408)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.
Error loading operating system 
(and it stops there with a blinking cursor)

or, sometimes, instead of "error loading OS", I get:

Disk error
Press any key to restart


I checked the USB drive (on my WinXP machine) and the ldlinux.sys file you mentioned is not on the USB drive anywhere.

Any thoughts?

---

### Post by D_one on 2009-02-15
I have looked at a few other places for some help here but I will try here.  

I used remastersys to create a custom iso image of my ubuntu install then used unetbootin to put it on an sd card and make it bootable, works great, (the second time for me unfortunately) It is a great combo of tools to create a bootable restore of your system on an sd card.  

So here is where I made my mistake:  The first time around My sdb1 (sd card) was coming up under sda2 (wha t I thought was my sd card, but was actually some other file system, possibly related to windows).  

Now I have a custom install of my original system (eeebuntu filesystem was originally on sda6, and is still there) and the boot loader installed with unetbootin replaced my old one that let me choose between windows and eeebuntu.  Now I cant boot into either.  Lucky for me, my backup version works almost as well as the original:) and I sucessfully made the bootable sd card the second time around.  

Has anyone else encountered this?

So my questions:

Idealy I just want it back the way it was. 
1.Can I install another boot loader that will recognize my windows (hopefull it still works since I dont have a cd drive)?

2. I cant seem to find my origina menu.lst in my original file system, is it gone? I dont see such a file in the unetbootin version, Where does it choose it's boot options?  Can I edit that to my old configurations?

3.  Is there any other changes that I would have to do in order to get my other two systems to be bootable?

Asus eee 900ha, 

$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92e4538c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3188    25607578+   7  HPFS/NTFS (windows)
/dev/sda2           18432       19452     8201182+   b  W95 FAT32 (where I accidentally used unetbootin to install the iso image)
/dev/sda3           19453       19457       40162+  ef  EFI (FAT-12/16/32) (?not sure here)
/dev/sda4            3189       18431   122439397+   f  W95 Ext'd (LBA) (?not sure here)
/dev/sda5            3189        3218      240943+   7  HPFS/NTFS
/dev/sda6            3219        6405    25599546   83  Linux 
(my original eeebuntu install)
/dev/sda7            6406       17808    91594566    b  W95 FAT32
/dev/sda8           17809       18431     5004216   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8199 MB, 8199864320 bytes
255 heads, 63 sectors/track, 996 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000888c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         996     8000338+   b  W95 FAT32


Help:)
Thanks in advance!

---

### Post by D_one on 2009-02-16
OK, so I was easily able to boot back into windows by using partition editor to change the boot flag.  However, after trying to change the boot flag to all the other partitions, I think that I erased the partition that had my boot list on it.  Thus I still have only 3 options, boot into windows, boot into a live version on sd card (by holding esc) or boot to the copy of my system on sda2.  So, my question is really the same, how do I either get my old menu.lst back, or edit the existing one that was installed with unetbootin to work with my system (allow for options to boot into my original system or windows).

Help, anyone?

---

### Post by D_one on 2009-02-16
And, before a reply I solved it;)

I downloaded and installed supergrubdisk and it basically found my old grub and re-installed it on the original partiition that my system was on!

I am amazingly impressed with these tools.  It seems that whatever I want to do, someone has thought of and done it (except found a way for me to print on my lexmark printer which is really the only reason that I would keep xp on).  

So: for all those other eee users out there or anyone without an optical drive (the netbooks are coming....) 

**Remastersys**: a tool to create a bootable iso of your system as is now, combined with;
**Unetbootin**: to put that .iso on your sd card is more or less a must have.  Do not choose to "show all drives" here if you sd card doesnt come up, just reformat your sd card and it should come up just fine (that was my mistake).  If you do by accident replace your working os with the unetbootin version, get 
**supergrubdisk**: put it on another sd card (or the same one if you dont need to boot into the card) and choose the install of linux that you want grub to be in.  

I am now more or less completely worry free with my eee since I can always boot from the sd card into my exact system with all my tools to fix ..... almost' anything, or so it seems.  

:popcorn::popcorn:my computers back baby!

Im no longer sure if these posts are relevant here, feel free to move them somewhere else if needed.

---

### Post by gwon on 2009-02-17
When I attempt to boot from my usb stick, I select it from the boot menu and then get the error message

ntldr is missing

any ideas?

---

### Post by Flying caveman on 2009-02-18
This worked great for what I needed it for.  My 2gopc came with a flaky install of Edubuntu.  I used Unetbootin to put a regular Ubuntu 8.04 on it and now it works great.  

Does this mean my CD/DVD burner will go the way of the floppy drive?  

Thanks TuxCantFly for this wonderful and powerful tool.

---

### Post by DougM1 on 2009-02-21
I have a Dell Mini 9 (aka Inspiron 910) running Ubuntu. I wanted to upgrade so I purchased a Runcore 32G SSD.

I cloned my original 4G SSD to the 32G SSD, using "sudo dd if=//dev/sda1 of=/dev/sdb2". When it was complete both drives had the same data on them - good start. So I swapped out the drives and attempted to boot up. The computer froze up at a black screen that said "GRUB" in the top left corner. I swapped the drives back and everything booted fine.

I had probably mistakenly assumed that if you cloned a hard drive that the new hard drive would be a mirror of the old one, only with more capacity. Wrong answer!!!!!

I did some more research on line and found that I needed to make a  Live USB stick (as there is no optical drive), so I did that, making a Live USB of Ubuntu 8.04, using UNetbootin. I was to then be able to boot off the stick so that I could fix the "GRUB"

I again swapped out my drives, edited my BIOS to boot off of the USB stick as directed, and attempted to boot up. A UNetbootin screen came up that said it would boot in 10 seconds, it counted down the 10 seconds, and then came back with the message that it would boot in 10 seconds, repeat, repeat, etc. There was also a line that said "Press [Tab] to edit options". When I do that I get a line of code: /ubnkern initrd=/ubninit _ 

What do I do now?

---

### Post by A340 on 2009-02-22
Hello to all, this is my first post, and need some assistance with starting ubuntu 8.10 from my USB Disk.

My Laptop BIOS does not support booting from a USB device. So I followed this information and I am stuck.

[http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/]("http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/")

Then I did this:

[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/]("http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-810/")

All went well, however, when I boot from the ISO image I made, I get **grub>_**

I typed **boot**, but got the ***kernel has to be loaded first***.

I am brand new to ubuntu, so any help I can get would be appreciated.

Thanks

---

### Post by A340 on 2009-02-22
Here is an update from my last post:

I did over the **iso** instructions in the **second link**. This time I booted ubuntu from the LiveCD and ran firefox. I copied and pasted all the terminal instructions. Put the new iso image on a CD,and attempted to boot with the USB stick, and CD.

Got **"Run Ubuntu using a USB Disk"** hit enter, some text scroll by and finally at the end got this:

[I]Bios EDD Facility v0.16-2004-Jun-25, o devices found
EDD information not available
input: At Translation set 2 keyboard a /devices/platform/i8041/serio0/input/input1
VFS: cannot open root device "<NULL>" or unknown_block (8,1)
Please append a correct "root" boot option; here are  the available le partations.
Kernel panic not syncing. VFS:unable to mount root fs on known block (8,1)[/I]

I tried the CD and the USB Disk on my desktop, same information I got. I decided to go into the BIOS of the desktop set it to boot from a USB device and use the USB stick alone. The USB stick booted ubuntu fine. 

However I need this to work on my Laptop for when traveling. Hence why I need to get this the USB Boot CD going.

---

### Post by jimmypk on 2009-02-25
I wan to install Mandriva 2009 and I use UNetbootin.
Mandriva's boot screen appears and error.
--------------------------------------------
Uniform Multi-Platform E-IDE driver
SCSI subsystem initializied
Driver 'sr' needs updating - please use bus-type methods
init started: BusyBox v1.6.1 (2008-05-16 12:38:44 UTC) multi-call binary
Cannot run '/etc/init.d/rcS': No such file or directory

Please press Enter to activate this console
--------------------------------------------
I tried it on Laptop and Desktop, also error.

---

### Post by DougM1 on 2009-02-28
This method worked great for Intrepid 8.10. I have a Dell Mini9, so now I just have to figure out how to get the sound to work and be able  to scroll within input screens, such as Thunderbird Address cards. Anyone have any suggestions?

---

### Post by volneilo on 2009-03-11
Hi all!
I've tried to run Arch Linux and Elive in LiveUSB mode, but got the same error: "Failed to mount squashfs filesystem" message, and then "Can't access tty; job control turned off" . After this, i'm dropped to "(initramfs _ )" and that's all... Any help on that?

---

### Post by jrybon on 2009-03-13
Is boot loader in Unetbootin linux specific?  It works just fine with the distros provided.  But when I try to make a windows liveusb (like a Bart disc), then the startup screen offers no option at all.

---

### Post by xflyboy on 2009-03-17
> **danmarycap said:**
> downloaded the ubuntu-8.10-alternate-i386.iso and used UNetbootin to create a Live USB bootable drive.  When I try to boot my Dell Mini9 from the USB (so I can install Ubuntu 8.10), I get (on a DOS-like black screen with white text):
Disk error
Press any key to restart

I checked the USB drive (on my WinXP machine) and the ldlinux.sys file you mentioned is not on the USB drive anywhere.

Any thoughts?

Same "Disk Error" error here.
Kingston 1Gb + ubuntu-8.10-desktop-i386.iso + unetbootin-windows-319.exe + WinXP Pro. Drive wasn't formated before instalation.
ldlinux.sys is on the drive.

PD: Old files still on the Drive. Formated it and will try again. will report later.

---

### Post by Ark_74 on 2009-05-02
Does anybody had experience with build a certain usb image with a custom kernel?

Changing the default one (kernel) from the *.iso file
I've had checked the UNetbootin documentation and no luck.

Thanks in advance

---

### Post by sundar_ima on 2009-05-26
is it possible to create multiple live linux on a pendrive using unetbootin? tried [this]("http://people.ofset.org/~ckhung/p/mk-boot-usb/") link but it is not user friendly for newbie like me.

---

### Post by hesapotman on 2009-05-26
Little Windows GUI app designed specifically for creating Live USBs for Ubuntu (and variants). "Ubuntu Live USB Imager" can be found at ...

[http://phatwares.dyndns.org:8080/contentUU.html]("http://phatwares.dyndns.org:8080/contentUU.html")

[IMG]http://i174.photobucket.com/albums/w85/phantomsea2005/UU.png[/IMG]

Hope you all get some use out of this! :p

---

### Post by stkrzysiak on 2009-05-26
Hey all, 
I have read most of this thread and do not recall seeing any mention of this, so here it goes.

    I have been playing around with Unetbootin for my Asus EEE 701.  At the same time, I am also [trying to get Ubuntu NR to get going]("https://answers.launchpad.net/netbook-remix/+question/71747") on that EEE.  
    After wrestling with Unetbootin since late last week, I realized today that it does indeed create a live USB drive for me, I just never get prompted to boot into it.  I have to manually hit escape during the POST to select the PCs boot source.  Regardless what distro I use with Unetbootin(Ubuntu 8.04, 8.10, 9.04, BT 3).  I know it is not the BIOS setup on my laptops(also testing with a sys76 laptop) because when I create a live USB with the previously mentioned Ubuntu NR, it boots up just fine.

Sorry if I lost anyone, but my basic question is this:  Why does the Ubuntu Netbook Remix usb stick boot up properly, yet when I use Unetbootin, I have to manually select the boot source?


Thanks all, 
Steve

---

### Post by Eric B on 2009-05-27
Does anyone have any tips on setting it up like its own install and not a copy of the live CD?

---

### Post by Eric B on 2009-05-27
found my answer. remastersys.

---

### Post by ckm1956 on 2009-07-15
I'm trying to
create a live USB using UNetbootin and a 64bit version of Jaunty. The creation goes fine. But when I boot, I get:

loading /ubnkern
loading /ubninit
initrd extends beyond the end of memory
disabling initrd
1.224254 kernel panic. not syncing VFS : unable to mount root FS, unknown block

Any ideas??

---

### Post by timur_ba on 2009-07-20
> **sundar_ima said:**
> is it possible to create multiple live linux on a pendrive using unetbootin? tried [this]("http://people.ofset.org/~ckhung/p/mk-boot-usb/") link but it is not user friendly for newbie like me.

Here is a manual procedure.
[http://tazbuntu.blogspot.com/2009/05/multibootin-with-unetbootin.html](http://tazbuntu.blogspot.com/2009/05/multibootin-with-unetbootin.html)

There are two major features missing in Unetbootin, multiboot being one. 
The other one is an option not to extract ISO, unless it's necessary. For example, I'd like to have Windows XP installation ISO, can I have it without extraction?

---

### Post by woodbrick on 2009-07-21
> **tuxcantfly said:**
> ***_EDIT:_* This apparently doesn't work anymore on 8.04 (I last tested this on 7.10), see [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) for instructions instead**



Go to [http://unetbootin.sourceforge.net/diskimg/](http://unetbootin.sourceforge.net/diskimg/) and download one of the files (128mb.zip, 256mb.zip, or 512mb.zip) corresponding to the amount of persistent space you want (make sure the size of the persistent disk image is smaller than the free space you have on your USB drive).

Now extract the file "casper.rw" from the zip file to your USB drive.

Now edit D:\syslinux.cfg (assuming D:\ is where your USB drive is) and add in "persistent" at the end of the line that begins with "append", and save the file, so your syslinux.cfg should look something like this:

```

default unetbootin
label unetbootin
	kernel /ubnkern
	append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --

```

For more info see [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Hopefully I'll get this automated in the next version or so.

I made a hardy heron startup disk no problem, but when I try to get persistent mode working (as per above instructions) I get a disk I/O error in FD0 and I drop back to a shell prompt. Any ideas?

*EDIT:Sorry I didn't notice the line at the top. It doesn't work with Hardy. I have now tried Jaunty. Same result. *

---

### Post by woodbrick on 2009-07-23
Ok I have just about run out of options, and I'm thinking maybe there is something wrong with my hardware (??) when it comes to running a persistent live Jaunty USB.

I have tried everything suggested in this thread, and I have also gone through these:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) and
[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

All yield very similar results. I can always get the kernel loaded and the first splash screen displayed. With Ubetootin, I can actually boot up in non-persistent mode. 

With all the other options, or with Unetbootin after editing the syslinux.cfg file, I still get the splash screen, but after the line goes back and across the screen about 50 times, I get a black screen and an error message that says something about an I/O error at FD0.

I do know that 'fd' means floppy drive, but I don't have one, and I don't have any floppy marked as a boot device in BIOS. 

Has anybody got any suggestions as to how I can get a working (peristent) live USB???

---

### Post by karlmp on 2009-08-07
doesn't work with tiny core 2.2:(

---

### Post by karlmp on 2009-08-13
doesn't work with slitaz stable:(

i haven't tried the cooking version

---

### Post by doctorphibes on 2009-11-09
In spite of all the posts about Unetbootin (I'm a newb to Linux but I know a nice piece of work when I see it, well done), I'm still having some difficulty. I used a cruzer 2G used the box to get Linux Mint but I can't get my machine (2005 model) to boot to the usb. I can pull up the drive letter, see all the files and ISO but how do I get it to work as an OS? Net BIOS won't give me the option to boot to USB. I would appreciate any help anyone can give me on how to proceed from this point. Thanks in advance.
doctorphibes :popcorn:?

---

### Post by doctorphibes on 2009-11-09
In spite of all the posts about Unetbootin (I'm a newb to Linux but I know a nice piece of work when I see it, well done), I'm still having some difficulty. I used a cruzer 2G used the box to get Linux Mint but I can't get my machine (2005 model) to boot to the usb. I can pull up the drive letter, see all the files and ISO but how do I get it to work as an OS? I have 9.04 running on my laptop just fine from a live cd. Net BIOS won't give me the option to boot to USB. I would appreciate any help anyone can give me on how to proceed from this point and get a persistent drive. Thanks in advance.
doctorphibes :popcorn:?

---

### Post by pedor on 2009-11-30
Add support for fedora 12 please!

---

### Post by 999terry on 2009-12-21
Hi to the creator of UNetbootin. Could you please state on the webpage for unetbootin download that it can only be used for machines post 2002 - and this will save people like me a lot of unnecessary time trying to achieve the impossible. Do you know of a reasonably simple alternative to unetbootin that can install Xubuntu 9.10 on a year model 1999 NEC Versa Lite FX laptop? Would appreciate any links you could suggest.
Thanks - Terry

---

### Post by Brinstar on 2010-01-24
note to devs, please read the following (short) thread:

[http://ubuntuforums.org/showthread.php?t=1389480](http://ubuntuforums.org/showthread.php?t=1389480)

---

### Post by valnar on 2010-01-26
deleted

---

### Post by pwebster25 on 2010-01-30
I am looking to do just the opposite as this.  I run Ubuntu 9.10 as my only OS.  I need to setup a bunch of netbooks with XP Pro SP3.  I have a legitimate install CD and real license codes.  I just can't successfully turn my cd into a bootable usb.
I did the following in ubuntu:
[LIST=1]right clicked on the cd and did copy.  Chose .iso as the format
I installed unetbootin from the ppa on launchpad in Ubuntu.
I formatted my USB stick (tried fat 32 and fat 16)
I ran unetbootin and chose the .iso from the windows install cd
I boot from the stick and it comes up with a prompt that says boot:
[/LIST]

What do I put here?  Nothing seems to work. I have tried the tab and don't know enough to edit it.

---

### Post by Sadpanda on 2010-02-07
I am sorry I am not interested in Linux anyhow and I do not really have direct question to this topic. This is the first topic I found a link to in some "how to do" guide in UNetbootin.
 
My whole computer crashed. Actually my dad manage to do so somehow. I got an information that he was "moving something from cd to usb" (the day before and when he woke up next morning the computer did not want to start) and after few more questions i got the answer it was something with lunix. I had to reinstal my system (windows XP - yes I know you probably dont like them) and many of the data on disc were damaged or lost. From what I know it seems like something happened to fat. The disc itself wasnt anyhow damaged but most of the data are lost.
I was searching trought the rest that left undamaged and I found an download folder which contains few reparation programs and drives from today and an unebootin-windows-356.exe file. From the date it is it must be the thing my dad was using. From what i can understand this program is ment to do an bootable linux copy from cd image on USB flash disk. My dad said he was doing just some simple operation "just a copy" and its not his fault at all. I am not here to blame him but I would like to ask you what is this program for, how does it work and is it like...how to say it - well is it some soft running program or is it like some program that may or could anyhow cause a system damage. Is it even possible it can cause an system/dics damage if used wrong ? 
I hope you will understand my problem (I gey you for it) and possibly help me a bit at least to understand what happened. Thank you all in advance
 
Martin

---

### Post by SteveF48 on 2010-02-24
I've been trying to create a USB boot device for Ubuntu 9.10. My first attempts used a 1gb USB pen drive and failed with various errors.
I then discover3ed unetbootin, this also failed. In desperation I used a 4gb sdhc card, with card reader and I've made some progress:
The laptop boots from the card and displays Unetbootin screen with 3 options.
I did nothing, which let it use the 'default'
Display showed loading ubnkern... loading ubninit... ...ready.
Should I wait, if so how long? Should I press a key? If so which key?
Pressing return displays a blank screen, however I can type on it. Should I type something, if so what?
What else can I do?
BTW I'm trying to install on a Toshiba Satellite A30, with a busted CD-ROM drive.

I tried selecting help from the UNetbootin menu, that gave a different result:
the ubnkern and ubninit messages were followed by lots of displays, which end with:
[ 2.792664] EDD information not avaiable
[ 2.8193971] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4

---

### Post by boosted on 2010-02-27
I too am having the same issue as you.  I get the same result on the screen and have no idea what I should do.  I am trying to install without a cd/dvd drive installed in the desktop.  If anyone has any info about this please respond.  Thanks

---

### Post by omelette on 2010-03-07
Real excitement on discovering this turns to real disappointment.  Using the 'Distribution' option, everything seems to work perfectly, at least with the 3 mini-downloads; 'FreeDOS', 'Super Boot Manager' & 'Damn Small Linux', that I tried.  The 'Diskimage' option on the other-hand, seems to be completely useless - 3 ISO's that run perfectly from virtual drives fail to boot completely.  Even the Ubuntu 9.10 ISO I downloaded fails...

---

### Post by omelette on 2010-03-10
I finally managed to find something that works with ISO's - Winsetup.  I have just spent 10min searching for a link to the site where it is being developed so people may download the latest version, and failed - but note that version most sites link to does NOT work!  The exact version I downloaded that works is;

***WinSetup-1-0-beta6.7z***

---

### Post by littlebigman on 2010-04-19
Hello

After reading [this article]("http://www.megaleecher.net/Get_Linux_On_USB"), I downloaded UNetBootIn to transfer the [Kaspersky Rescue CD ISO image]("http://devbuilds.kaspersky-labs.com/devbuilds/RescueDisk10/") onto a USB key.

After rebooting, after a few seconds, I'm stuck with the following error message:
> 
Determining root device: Could not find the root block device in .


Does someone know if something needs to be done when burning the image using UNetBootIn, or do I need to pass some switch to the command line when booting up the kernel?

Thank you for any hint.

---

### Post by Nisal on 2010-04-19
really nice utility thanks alot for this )

---

### Post by dadepfan on 2010-05-10
Hello all!

I may have misunderstood what a live USB is and what UNetbootin is used for...

First, I have an Acer Aspire EasyStore H340 home server (with two 1TB drives), that came with Windows Home Server, and I wanted to convert it to run Ubuntu Server.  I spent several days just trying to get this headless device to use a monitor and let me into the bios (involved changing jumpers on the MB!).

Having finally done that, I downloaded ubuntu-10.04-server-amd64.iso to my desktop PC and used UNetbootin to create a LiveUSB on my 4GB USB flash stick.  My intent was to have something I could boot to and use to install Ubunto server onto the Acer Aspire.  I wanted to replace everything on the server with Ubuntu, and have the server boot into Ubuntu when turned on.  I did not want or intend the USB stick to be required for the server to boot.

The installation seemed to go OK, but took a very long time and downloaded MANY files.  I assume that is standard.  During installation, I choose my 1TB SATA hard drive as the location of the installation.  Towards the end of the installation, a question about an existing OS (Vista) being detected and setting up a boot menu appeared.  There did not seem to be any way to just eliminate Vista from the boot process, so I selected 'Continue'.

So now, the server will not boot unless the USB stick is plugged in AND it has to be 1st in the boot order in the bios setup (this seems to be the case with this computer & bios no matter what is booting).  I believe that Ubuntu is actually installed on the 1st SATA drive, but the system will not boot from there,

So, how can I make the 1st SATA drive the actual boot device (with the USB stick not present and not in the boot list)??  I am fairly new to Linux, and do not have a working knowledge of the file system and all the utilities, so please respond with "take me by the hand dear Lord" language :redface:

Also, installation had me create a user name and password, but did not tell me how to log in as root.

Thanks,

Dave

---

### Post by djmerk on 2010-07-22
> **omelette said:**
> I finally managed to find something that works with ISO's - Winsetup.  I have just spent 10min searching for a link to the site where it is being developed so people may download the latest version, and failed - but note that version most sites link to does NOT work!  The exact version I downloaded that works is;

***WinSetup-1-0-beta6.7z***

AVG scan in XP turned up 5 spyware.

Careful in Windows folks.

---

### Post by mailman1175 on 2010-08-17
This is a little out there, but since this thread is linked as a "support forum" directly from Unetbootin's sourceforge page, I'll give it a shot: What font does Unetbootin use?

Here's the deal: I'm trying to install Unetbootin on OS X via Wine. It's been reported to work. When I run Unetbootin.exe, though, the dialog box has no lettering at all. The only reference I've found to this is someone suggesting that the font used by Unetbootin isn't recognized by Wine, and must be installed. They didn't say which font it is, though, and I've been unsuccessful thus far in my googling.

Any help?

---

### Post by tuxcantfly on 2010-08-17
> **mailman1175 said:**
> This is a little out there, but since this thread is linked as a "support forum" directly from Unetbootin's sourceforge page, I'll give it a shot: What font does Unetbootin use?

Here's the deal: I'm trying to install Unetbootin on OS X via Wine. It's been reported to work. When I run Unetbootin.exe, though, the dialog box has no lettering at all. The only reference I've found to this is someone suggesting that the font used by Unetbootin isn't recognized by Wine, and must be installed. They didn't say which font it is, though, and I've been unsuccessful thus far in my googling.

Any help?

Firstly, I am almost certain that UNetbootin would not work on Mac OS X via Wine - Mac OS X and Windows have different bootloaders, and I don't think syslinux works via Wine.

That said, UNetbootin doesn't request any specific font to be used; your system default is used. Thus, if you have the Microsoft Truetype Core Fonts installed, which you can get for non-Windows OSes at [http://corefonts.sourceforge.net/](http://corefonts.sourceforge.net/) (fink, macports, or whatever package manager you used to install Wine should probably have installed them), then you should have whatever system font Wine defaults to.

If you're not getting text displayed, it's probably a Wine rendering issue, not an issue with missing fonts.

---

### Post by mailman1175 on 2010-08-17
> **tuxcantfly said:**
> Firstly, I am almost certain that UNetbootin would not work on Mac OS X via Wine - Mac OS X and Windows have different bootloaders, and I don't think syslinux works via Wine.

That said, UNetbootin doesn't request any specific font to be used; your system default is used. Thus, if you have the Microsoft Truetype Core Fonts installed, which you can get for non-Windows OSes at [http://corefonts.sourceforge.net/](http://corefonts.sourceforge.net/) (fink, macports, or whatever package manager you used to install Wine should probably have installed them), then you should have whatever system font Wine defaults to.

If you're not getting text displayed, it's probably a Wine rendering issue, not an issue with missing fonts.

Hm. I actually used an install script (osxwinebuilder) to build from source. Fink had a missing dependency that couldn't be filled (arts-shlibs).

I've seen several reports that Unetbootin/Wine works on OS X. I may hit up an OS X forum or two and see if I can figure out how they got it working.

---

### Post by cnymike on 2010-08-21
I am late to the party and not very smart either so please have mercy.

Just acquired an Acer Aspire-One netbook. I have just read [Mark Gibb's column in networkworld]("http://www.networkworld.com/columnists/2010/080910-gearhead.html?source=nww_rss") about installing Ubuntu 10.04 Netbook Edition using Universal USB Installer onto a USB flash drive. So I bought an 8GB PNY flash drive and installed Ubuntu 10.04. Every thing was fine. I was able to boot into Ubuntu on my ACER no problem. Loved the interface, seems fast, etc etc.

During installation I specified  4GB persistence

Problems arose when I attempted to Update Files on the USB drive. First error that appeared was the Grub-pc cannot find a device for /, /boot and /boot/grub

I continued and towards the end of updating, which took several hours by the way, I got the error "sorry the package "linux-image-2.6.32-24-generic 2.6.32-24.41 failed to install or ugrade. There was some other info such as, "E: linux-image-2.6.32-24-generic: subprocess insstalled post-nstallation script returned error exit status2, E; linux-image-generic: dependency problems-leaving unconfigured, and E: linux-generic: dependency problems-leaving unconfigured.

I guess my question is what did I do wrong? 
What can I do to allow the USB flash drive to be updated successfully?
Can a LiveCD (USB drive) be updated using the Ubuntu update feature or is the USB drive only to be used for evaluation and not updated until Ubuntu is installed on the HD of the machine?
 Am I too stupid to be attempting to do this at all?

Michael

---

### Post by pwebster25 on 2011-01-29
CNYMIKE-
Ubuntu 10.04 NBE should work great on your Acer Aspire One. That is what I am typing on right now.  I think we will need to understand a few things:

[LIST]
[*]Did you install Ubuntu on the Acer hard drive using the flash USB drive or did you just run the Live CD?  It sounds like you might have been just running the live cd from USB.
[*]Was it still running from USB when you did update?
[*]How big is your hard-drive?
[/LIST]

You can run some updates while using the live cd (USB) and you can even install some new software but this is really only installed in RAM and goes away when you reboot.  The live CD is really for trying it out.
If I understand that you were just trying it out with the live cd then what you need to do it really install ubuntu on the Hard-Drive.

You will need to choose this option when it boots from your USB.  You can also choose install Ubuntu while you are actually running it from the live cd.  I'm not sure but I think it might be in favorites.

The install process is quite straightforward.  You will need to choose whether to use the whole hard drive or whether to install Ubuntu next to whatever else is on there (Windows?).  This would dual boot the machine.

It sound like your live USB device may be a bit gummed up now.  I would suggest you delete the partition on that and then remake your live USB stick before doing your install again.

Have a good time.  I have had a great experience with 10.04 on my AAO netbook (10").

---

### Post by seaoffecundity on 2011-02-25
sorry i don't know where else to turn with this.  trying to set-up again with limited resources and a windows system found an infected file.  maybe it's most relevant to all yous here.. 

  when i just went to get unetbootin for windows there were two download sites, sourceforge and launchpad.  now understand i trust launchpad over sourceforge, no particular reason, just sticking by a community i guess, so i would have gone right ahead, but avg quarantined it.  the launchpad file is unetbootin-windows-502.exe (4.5mb) and the sourceforge file is unetbootin-windows-494.exe (4.3mb).  the sourceforge 494 file is not suspected but it's older and i guess i just want to know which ones other users and the developers stand by. 

  are the sourceforge and launchpad files maintained by the same team?  where should viruses be reported?  sorry if the exclamation icon was inappropriate but i believe it is a virus alert.

---

### Post by thisisasignin on 2011-02-27
> **seaoffecundity said:**
> sorry i don't know where else to turn with this.  trying to set-up again with limited resources and a windows system found an infected file.  maybe it's most relevant to all yous here.. 

  when i just went to get unetbootin for windows there were two download sites, sourceforge and launchpad.  now understand i trust launchpad over sourceforge, no particular reason, just sticking by a community i guess, so i would have gone right ahead, but avg quarantined it.  the launchpad file is unetbootin-windows-502.exe (4.5mb) and the sourceforge file is unetbootin-windows-494.exe (4.3mb).  the sourceforge 494 file is not suspected but it's older and i guess i just want to know which ones other users and the developers stand by. 

  are the sourceforge and launchpad files maintained by the same team?  where should viruses be reported?  sorry if the exclamation icon was inappropriate but i believe it is a virus alert.

I would think files from sourceforge are the most recent. After all the UNetbootin homepage is hosted on [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

In any case, AVG could be reporting a false positive. Make sure AVG is up to date. If it is still reporting your file, add it to the exclude list so AVG will not quarantine it. This is of course if you are certain it is a file you trust.

---

### Post by Metungkp on 2011-03-27
I get this error when I try to run UNetbootin


Archive:  /media/PSSSTSTORAG/unetbootin-windows-527.exe
[/media/PSSSTSTORAG/unetbootin-windows-527.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/PSSSTSTORAG/unetbootin-windows-527.exe or
          /media/PSSSTSTORAG/unetbootin-windows-527.exe.zip, and cannot find /media/PSSSTSTORAG/unetbootin-windows-527.exe.ZIP, period.

---

### Post by Double Trouble on 2011-04-22
Sorry if this has already been asked in this thread but I just didn't have time to read all the pages. But I have the problem that unetbootin doesn't find my USB hard drive which I have formatted to fat32 and it has the size of 10 Gb.

I have tried both normal and quick format. The actual hard drive is 120 Gb but I have only one partition on is which is the above mentioned one.

Unetbootin only shows one USB drive which is K: and that's the drive for SM-cards!

---

### Post by johny why on 2012-07-01
hello, i'm running netbootin win on puppy linux wine. 

during the extract phase, my root dir gets so overloaded that my OS hangs, and i have to restore my OS from backup. 

is there a way to force netbootin to extract to a different hard-disk, instead of my OS disk?

thanks

---

### Post by Sorapak on 2012-09-09
hello,I did all those steps as described. but doesn't do anything.
tried all three boot sequences

[LIST]
[*]USB-FDD ignores usb,enters windows normally

[*]USB-ZIP boot error

[*]USB-CD rom ignores usb,enters windows normally

[/LIST]
Used Windows XP SP3.


Any ideas anyone?


Any help is appreciated.

---

### Post by spb37 on 2012-10-11
Can anyone help with this unanswered q
What I would like is to be able to boot from the USB flash drive, but then be able to remove it from the computer once the desktop has loaded.

[http://askubuntu.com/questions/194501/instruct-ubuntu-to-boot-toram-from-flash-drive-using-unetbootin](http://askubuntu.com/questions/194501/instruct-ubuntu-to-boot-toram-from-flash-drive-using-unetbootin)

---

### Post by g.allen on 2013-05-03
Thank you!!! It worked superbly on my netbook (no CD drive), even for a Linux novice like me.
I actually installed from an SD card, and no problems whatsoever.

Pity that Ubuntu runs so slowly as to be unusable... :-(

---

### Post by CrackedP0t on 2013-05-12
I find Universal USB Installer to work well too.

---

### Post by mel2000 on 2014-02-23
I just used Unetbootin to create a bootable Backtrack distro on an 8GB FAT32 USB, which worked just fine. However, when I later tried to add a Puppy Linux ISO to the menu, I was prompted to overwrite two existing files, which I declined. Is there a safe way to add another distro onto an already existing one with Unetbootin?

---

### Post by C.S.Cameron on 2014-02-24
I have not heard of a way to do it with UNetbootin, try MultiBootUSB.

---

### Post by mel2000 on 2014-02-25
OK, I'll try MultiBootUSB. I'm surprised the well-known Unetbootin is so limited. Thanks for your reply.

---

### Post by mel2000 on 2014-02-25
Thanks again C.S.Cameron, MultiBootUSB worked fine after I removed a dupe '/' from a CONFIG line in the menu/unlisted.cfg file.



CONFIG /multiboot/BT5R3-KDE-64/isolinux/isolinux.cfg

CONFIG /multiboot/lupu-528.005//isolinux.cfg



The BT5R3-KDE-64 line was OK as is, but the lupu-528.005 line needed fixing. There was no isolinux subdirectory for lupu-528.005.

---

### Post by andrew103 on 2014-03-17
sandisk 8 gb, had it formated NTFS but thanks to dubref managed to fix by formatting to fat32

---

### Post by Sleepy-zz-John on 2014-04-18
Last year I started burning flashdrives instead of CDs from new Ubuntu .iso downloads.  I used standard Ubuntu software,  not Unetbootin,   to burn two of them and they booted and worked fine for me until I tried to reformat them in preparation for burning a new .iso on to them.    At that point they both failed to reformat and became unusable despite my trying many different tools to get them working again.   One was an 8GB Kingston Data Traveller and when I contacted Kingston about possible boot sector repair software for their device,  they told me their product doesn't support using it in bootable mode at all.  

So my question now is which flashdrive brands support being used as bootable and are then subsequently still capable of being reformatted ready for a new .iso,  and which brands aren't?  I must admit surprise that a major brand like Kingston doesn't support bootable useage.  Someone suggested Sandisk Cruzer and HP can be made bootable and can later be subsequently reformatted OK,  but having destroyed two flashdrives this way I'm not keen to risk burning any more without some reassurance that they're going to survive.  

If I understand correctly,  different brands use different boot sectors so some have greater resilience to being made bootable than others. 

Or could it be that if burned with UNerbootin instead of standard Ubuntu software,  even Kingstons can be recycled over and over again?

---

### Post by C.S.Cameron on 2014-04-20
I Have had good luck with Kingston DataTraveler. I'm still using several that I have had since this thread was new.
Bad luck with Kingston 32GB DataTraveler 100G2, formatting multiple partitions, seems to have killed it.
And real good luck with Sandisk Cruzer Fit. These seem quite fast for USB2 to me.
I am convinced that trying to format a multi partition flash drive in Windows is not a good thing.

With both Startup Disk Creator and UNetbootin, there is no need to format the drive if it is already FAT32, and no need to format between Ubuntu persistent installations, just manually delete the previous installation and run the installer again.

---

### Post by Sleepy-zz-John on 2014-04-21
> **C.S.Cameron said:**
> I Have had good luck with Kingston DataTraveler. I'm still using several that I have had since this thread was new. Hmm.. Thanks,  but just to be sure,  please could you confirm you had previously burned and used these Kingstons as live and bootable before you recycled them with new .isos ? >  Bad luck with Kingston 32GB DataTraveler 100G2, formatting multiple partitions, seems to have killed it.  Yes,  I can imagine that trying multiple partitions would be pushing one's luck a bit too far.   If I understand correctly, the process of burning anything live and bootable necessarily causes some changes to be automatically made in the boot sector,  and I'm not clear myself whether  Startup Disk Creator and UNetbootin handle this part differently.  I mean could Startup Disk Creator be blamed for the subsequent troubles I've had at the recycling stage,  and could using UNetbootin   instead possibly have avoided them? >  And real good luck with Sandisk Cruzer Fit. These seem quite fast for USB2 to me.
I am convinced that trying to format a multi partition flash drive in Windows is not a good thing. Well yes,  any operation in Windows seems to imply hazards and should be avoided if at all possible.   Only this last weekend a Kingston 32GB (in this case I hadn't made it bootable) has mysteriously become completely write-protected and unresponsive to any formatting after I'd used it in a Windows programme to transfer data.   I'm begiinning to wonder if my Windows (which I only use rarely), could possinly be harbouring a virus that somehow attacks flashdrive boot sectors?   This wasn't the only flashdrive that's mysteriously gone write-protected on me ;(  >  With both Startup Disk Creator and UNetbootin, there is no need to format the drive if it is already FAT32, and no need to format between Ubuntu persistent installations, just manually delete the previous installation and run the installer again.  Yes,  OK,  thanks for that.  When I've tried to recycle my live flashdrives with new .isos in the past,  I've only resorted to trying reformatting when Startup Disk Creator failed.

I'm still trying to figure out what exactly it is that's been causing my flashdrives to become unusable.  It's got to more than simple bad luck!   Anyway,  today I've bought a Sandisk Cruzer as one replacement,  and I'm going to try burning it with UNetbootin and see if this brings better luck.

Thanks again  :-)

---

### Post by C.S.Cameron on 2014-04-21
I have two DataTraveler 8GB and four 4GB left.

The 8GB's usually have a portion as Ubuntu Persistent or Full install, one has gone missing and the other is being used daily for data. Both have been used with multiple partitions, FAT32, ext3, ext2 and swap partitions.

One 4GB runs XP, I used this to run my entertainment center, that only had S-video accessible, and would not work with Ubuntu.
One 4GB is a grub2 boot drive, it doubles as an install disk and emergency disk. I have just added the 14.04 iso's.
One 4GB had a Full install that I upgraded every release until a full install would no longer fit on a 4GB. Now I us it for data and testing new releases.
The last 4GB has been used for Full installs, Persistent installs, DSL, Puppy, gparted, etc, etc, and data and has been formatted many times using gparted.

One Sandisk Fit has 12GB / and 8GB swap, I have been using this for the entertainment center.
The other Fit Has 4GB NTFS, 5GB / and 7GB /home. The NTFS partition is for transferring data on a Windows computer. I used this to play movies on my work laptop.

---

