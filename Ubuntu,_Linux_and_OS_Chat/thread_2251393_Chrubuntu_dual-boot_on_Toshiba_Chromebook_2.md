---
title: "Chrubuntu dual-boot on Toshiba Chromebook 2"
date: 2014-11-04
forum: Ubuntu, Linux and OS Chat
---

### Post by iclethian-p on 2014-11-04
I am trying to install ubuntu alongside chromeos on my Toshiba Chromebook 2 IPS model. From what I've read, it has an Intel Celeron Processor, and I believe it can use legacy boot.

I have attempted to follow a number of guides in order get this installed, each time wiping my drive before attempting again. Every time Ubuntu installs, it tells me to hit ctrl+L to enter legacy boot, but it beeps loudly twice, and does nothing. 
The installation did seem to have an few errors, and it never asked me for prompts like the guide said it would. Specifically, I never had to choose a location of GRUB, nor any of the other settings.

I have also attempted to set my firmware update mode to developer and boot from a live usb (ctrl+U), and the screen beeped and flashed briefly to black, and then did nothing.

Guides I have followed without success:
[http://www.makeuseof.com/tag/install-linux-chromebook/](http://www.makeuseof.com/tag/install-linux-chromebook/)
[http://chromeos-cr48.blogspot.com/2012/04/chrubuntu-1204-now-with-double-bits.html](http://chromeos-cr48.blogspot.com/2012/04/chrubuntu-1204-now-with-double-bits.html)
[http://chromeos-cr48.blogspot.com/2013/10/chrubuntu-for-new-chromebooks-now-with.html?m=1](http://chromeos-cr48.blogspot.com/2013/10/chrubuntu-for-new-chromebooks-now-with.html?m=1)

Can somebody please guide me along the right path? I cant find much information on the Toshiba Chromebook 2 because of how new it is. Thanks for the help

---

### Post by vivekR on 2014-11-04
Do you remember the errors while installing, possibly something with the GRUB Bootloader?

I am not sure if the firmware has some hardware write protection on in the BIOS?



chronos@localhost / $ sudo bash
localhost / # chromeos-firmwareupdate --mode=todev
Starting Swanky firmware updater v4 (todev)...
 - Updater package: [Google_Swanky.5216.238.5 / EC:swanky_v1.6.197-c5a86fe]
 - Current system:  [RO:Google_Swanky.5216.238.3 , ACT:Google_Swanky.5216.238.5 / EC:swanky_v1.6.197-c5a86fe]
** - Write protection: Hardware: ON, Software: Main=ON**
 
[B]  Booting any self-signed kernel from SSD/USB/SDCard slot is enabled.
  Insert bootable media into USB / SDCard slot and press Ctrl-U in developer
  screen to boot your own image.[/B]
  
Firmware update (todev) completed.
localhost / # sudo flashrom --wp-disable
flashrom v0.9.4  : cbaba9c : Sep 23 2014 06:28:52 UTC on Linux 3.10.18 (x86_64), built with libpci 3.1.10, GCC 4.8.x-google 20140307 (prerelease), little endian
Mapping BYT IBASE at 0xfed08000, unaligned size 0x200.
Mapping BYT SBASE at 0xfed01000, unaligned size 0x200.
w25q_disable_writeprotect(): error=1.
FAILED
localhost / #

---

### Post by iclethian-p on 2014-11-04
I dont remember any errors specific to grub, no, but it was installing fast, didnt have much time to read. I ran the firmware update and tried to boot from my live usb. Should I try to install it again?

---

### Post by vivekR on 2014-11-05
Ok, I managed to install chrubuntu (it put 14.10 with unity desktop by default). 

I was also unable to use any switches at boot time to choose the OS. However, the aliases do work, and using them, I am able to get into Ubuntu 

1. do sudo rootdev to find your root device name (e.g. /dev/mmcblk0) 

2. Use cgpt show or fdisk -l to see the partition number where ubuntu got installed (e.g. mine was 7)

3. Create an alias like 
alias ubuntu='sudo cgpt add -i 7 -P 0 -S 1 /dev/mmcblk0;sudo reboot'

([http://terrybritton.com/create-shortcuts-to-easily-switch-between-chrome-os-and-chrubuntu-1006/](http://terrybritton.com/create-shortcuts-to-easily-switch-between-chrome-os-and-chrubuntu-1006/) )

4. You can create a similar alias on ubuntu to go back. 

Note, my ubuntu appears to be crashing repeatedly, possibly due to the wireless driver.. not too sure.. :-(

---

### Post by vivekR on 2014-11-05
btw. LTS version 14.04 (trusty) was working fine under crouton on the same hardware. 

So trying that now, to rule out any bleeding edge unstablity from the newly released 14.10 .. (curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd default lts).

---

### Post by vivekR on 2014-11-05
OK, good news .. LTS 14.04 is a lot more stable.. 

however, it still has several issues. 
1. hangs on suspend (just a black screen with the cursor, if I close the laptop lid and reopen)
2. wouldnt unlock with the correct password (had to reboot and disable locking on inactivity)
3. No sound yet
4. havent figured out the keyboard mappings for brightness/volume controls either.

---

### Post by iclethian-p on 2014-11-06
So is crouton my only option for a stable environment? I definitely need to have sound o

---

### Post by mnms on 2014-11-25
Hi vivekR

thanks for posting, I am trying to do the same with a Chromebook 2 Toshiba. I have not had much luck, ideally I would like to have them dual boot. Has 14.04 Lts worked?
I am in the process of installing it. I had installed 14.10 same outcome as usualy, 2 beeps when I press ctrl-L

Please let me know how to use the cgpt show command
I've tried several times but still can not find the partition.

Any information would be appreciated.

thanks,

:guitar:

> **vivekR said:**
> Ok, I managed to install chrubuntu (it put 14.10 with unity desktop by default). 

I was also unable to use any switches at boot time to choose the OS. However, the aliases do work, and using them, I am able to get into Ubuntu 

1. do sudo rootdev to find your root device name (e.g. /dev/mmcblk0) 

2. Use cgpt show or fdisk -l to see the partition number where ubuntu got installed (e.g. mine was 7)

3. Create an alias like 
alias ubuntu='sudo cgpt add -i 7 -P 0 -S 1 /dev/mmcblk0;sudo reboot'

([http://terrybritton.com/create-shortcuts-to-easily-switch-between-chrome-os-and-chrubuntu-1006/](http://terrybritton.com/create-shortcuts-to-easily-switch-between-chrome-os-and-chrubuntu-1006/) )

4. You can create a similar alias on ubuntu to go back. 

Note, my ubuntu appears to be crashing repeatedly, possibly due to the wireless driver.. not too sure.. :-(

---

### Post by david331 on 2015-01-26
I'm on the verge of ordering one of these if it can boot a full Linux distribution (I'm not interested in chroot).

> **vivekR said:**
> OK, good news .. LTS 14.04 is a lot more stable.. 

however, it still has several issues. 
1. hangs on suspend (just a black screen with the cursor, if I close the laptop lid and reopen)
2. wouldnt unlock with the correct password (had to reboot and disable locking on inactivity)
3. No sound yet
4. havent figured out the keyboard mappings for brightness/volume controls either.

Has there been any progress with the above issues?  Is it using the  kernel and modules from ChromeOS or those supplied by Ubuntu?

Issue 2 sounds like a keyboard map problem.

---

### Post by pfp.meijers on 2015-02-01
Using Ubuntu trusty (14.04) is working fine via crouton on my Toshiba Chromebook 2.
But I was not successful in getting it booting directly. Same kind of problems as described above. Ctrl-L just gives two beeps. Also not able to boot directly from USB via Ctrl-U (even with the corresponding crossystem flags set). 

Is there anyone who got a Ubuntu boot working?

---

### Post by david331 on 2015-02-01
Did you try vivekR's suggestion in post #4?  It should change the boot priority to make Ubuntu the default.

---

### Post by connor-jolley1980 on 2015-02-02
THis guide worked flawlessly (once I figured out how to get into dev mode in Chrome OS) on my Toshiba 2

[http://www.linux.com/learn/tutorials/795730-how-to-easily-install-ubuntu-on-chromebook-with-crouton](http://www.linux.com/learn/tutorials/795730-how-to-easily-install-ubuntu-on-chromebook-with-crouton)

---

### Post by david331 on 2015-02-02
That guide is for installing Crouton which installs Ubuntu as a chroot under Chrome OS.  This thread is for the discussion of the installation of Chrubuntu which allows you to boot directly into Ubuntu, where Chrome OS is not running at all.

I found there is a Chrubuntu community on Google+:

[https://plus.google.com/communities/108883927831773328803](https://plus.google.com/communities/108883927831773328803)

It looks like vivekR has made some progress and has solved the suspend/resume issue.  He also suggests that porting [CRAS]("http://www.chromium.org/chromium-os/chromiumos-design-docs/cras-chromeos-audio-server") (Chromium OS Audio Server, also known as ADHD) to Ubuntu might be required to fix the audio.  

The CRAS source code can be found here:

[https://chromium.googlesource.com/chromiumos/third_party/adhd/](https://chromium.googlesource.com/chromiumos/third_party/adhd/)

I will see if I can find some time this week to set up an Ubuntu 14.04 build environment on my PC (running Debian here) and have a go at building CRAS for Ubuntu.  I'm also curious to find out how other Chromebooks are running audio under Chrubuntu without CRAS.

Anyone know where I can get a copy of the Toshiba Chromebook 2 Linux kernel source?  Or does it use a mainline kernel?

---

### Post by david331 on 2015-02-02
Here are a couple of things to try to fix the audio:

[https://wiki.archlinux.org/index.php/Chromebook#Fixing_Audio](https://wiki.archlinux.org/index.php/Chromebook#Fixing_Audio)

[https://wiki.debian.org/InstallingDebianOn/Samsung/ARMChromebook#Audio](https://wiki.debian.org/InstallingDebianOn/Samsung/ARMChromebook#Audio)

---

### Post by MACscr on 2015-03-04
Did any of you get dual boot to fully work on your Toshiba? As much as I would like to continue to just use ChromeOS, i need better web development options.

---

### Post by zoomy942 on 2015-05-13
I've been looking all over for this.

I have a CB2 and it's a very sexy device.  If I could get Ubuntu on it - via Chrubuntu- that would be perfect.  ChromeOS for normal use and Ubuntu for the versatility.

Sigh - from the looks of it that isn't going to happen.

---

### Post by david395 on 2015-06-02
Forgive me if this is naive, but has anyone considered installing to an SD card? From what I understand the main issue with the dual boot is that the Toshiba uses UHCI instead of the typical SATA ([http://www.reddit.com/r/chromeos/comments/2i1aqj/toshiba_chromebook_2_gnulinux_compatibility/](http://www.reddit.com/r/chromeos/comments/2i1aqj/toshiba_chromebook_2_gnulinux_compatibility/)). I am yet to purchase and test myself but I'm interested if this would be a potential workaround.

---

### Post by zoomy942 on 2015-06-02
> **david395 said:**
> Forgive me if this is naive, but has anyone considered installing to an SD card? From what I understand the main issue with the dual boot is that the Toshiba uses UHCI instead of the typical SATA ([http://www.reddit.com/r/chromeos/comments/2i1aqj/toshiba_chromebook_2_gnulinux_compatibility/](http://www.reddit.com/r/chromeos/comments/2i1aqj/toshiba_chromebook_2_gnulinux_compatibility/)). I am yet to purchase and test myself but I'm interested if this would be a potential workaround.

I should update.  

I don't have it dual booting but I have Xubuntu installed to an SD Card via Crouton and it works perfectly.  Not using up space on my CB2 drive and can fire up linux anytime I need it.

---

### Post by david395 on 2015-06-02
Perhaps you could save me some research. Is there a command to use when installing crouton that allows me to specify which drive to use? This is the guide I was planning on using: [http://grephaxs.com/chromebook-install-kali-with-crouton/](http://grephaxs.com/chromebook-install-kali-with-crouton/). Just bought the Toshiba with a 16gb SD and I'm ready to install, still geting familiar with the whole crouton approach.



> **zoomy942 said:**
> I should update.  

I don't have it dual booting but I have Xubuntu installed to an SD Card via Crouton and it works perfectly.  Not using up space on my CB2 drive and can fire up linux anytime I need it.

---

### Post by zoomy942 on 2015-06-03
> **david395 said:**
> Perhaps you could save me some research. Is there a command to use when installing crouton that allows me to specify which drive to use? This is the guide I was planning on using: [http://grephaxs.com/chromebook-install-kali-with-crouton/](http://grephaxs.com/chromebook-install-kali-with-crouton/). Just bought the Toshiba with a 16gb SD and I'm ready to install, still geting familiar with the whole crouton approach.

I'm happy to help.

I used these two pages to get it done.  I'm using XFCE right now, but I'll be damned if I can;t figure out how to add the Ubuntu print manager.  

Anyway, try these and if you have questions feel free to ask.  I battled a ton learning but have it down now.

[http://www.maketecheasier.com/map-crouton-installation-external-device-chromebook/]("http://www.maketecheasier.com/map-crouton-installation-external-device-chromebook/")

[https://docs.google.com/document/u/1/d/1JWLvbn4cy-LmQ-K3JeWMD-2yvT08V3lyMhrFilMClP8/pub]("https://docs.google.com/document/u/1/d/1JWLvbn4cy-LmQ-K3JeWMD-2yvT08V3lyMhrFilMClP8/pub")

---

### Post by david395 on 2015-06-03
Thanks alot zoomy942! Much appreciated!! I'm getting an error when I try to install crouton that says "/usr/local/chroots/*RELEASE_NAME* is not an ext file system"(tried Kali which is my desired release and the Trusty release in the instructions). I didn't have this issue with my previous attempts but it seems using the first guide you posted where you set the link it starts to occur. I have formatted(and reformatted) my SD card through another Ubuntu machine to ext4. Any suggestions?

NOTE: also tried kde and xfce environments

Additional note: I found some guides that use the -p parameter to set the location for the crouton install, any idea if this is a newer functionality? Or any reason why it is better to use a soft link?

---

### Post by zoomy942 on 2015-06-03
Morning!

I had a bit of trouble getting the ext4 working as well.  

Use this command in the terminal on a linux machine...

sudo mkfs.ext4 -L "NAME OF SD CARD HERE" /dev/sdb  ----- so mine looks like this  sudo mkfs.ext4 -L "SD" /dev/sdb

That made it into ext4 no problem.  If you get an error saying it's in use, unmount it and it should work.



And I used a variation of this command to get it installed and yes -p is what I used.  I didn't want a symbolic link because running it from the SD is easy enough and if I change Linux versions I dont have to shange a thing on the chromebook.  Just reformat the SD card and off I go.

sudo sh -e ~/Downloads/crouton -r trusty -t xfce -e -p /media/removable/SD

PZ

---

### Post by xmbwd on 2015-06-05
I also just got one of these and used crouton to install Ubuntu on an external card (Sandisk USB cruze) following the instructions linked above.  This approach works great for almost everything, as there is a lot of room to add apps.  

**But **the problem for me is that I want to have multiple "**user accounts**" in Ubuntu, and that does not appear to be possible when using crouton.  So, two questions:

1.  Has anyone been able to get the Toshiba Chromebook 2 to boot directly into Ubuntu?  This was the OP's original question.  If so please post how....

2.  Has anyone been able to get a crouton install of Ubuntu (or any distro) to use multiple user accounts?

Thanks so much.

---

### Post by david395 on 2015-06-08
xmbwd:
1) From what I understand USB boot is firmly disabled for out Toshiba CB2's (try ctrl + u at the OS verification screen, i think its u... cant check atm)
2) What are your intentions for having multiple users? Keep in mind the whole crouton system is lacking in security, would running multiple chroots be a solution for you?

ALL READERS:
I have had a huge amount of trouble with "Read only file system" errors during the crouton setup, this is very easily solved by installing "Keep Awake" from the app store, there seems to be issues with some chromebooks and external media when the screen turns off or the chromebook goes to sleep... I found this to be a good bandaid.

Currently I am having issues starting xfce after a seemingly successful install with Kali to an SD card. If i run "sudo sh /media/removable/SDCARD startxfce4" I dont get an error but it does not start. Does anyone have any suggestions? I had the same issue trying to run gnome/kali

---

### Post by Bucky Ball on 2015-06-08
*Thread moved to **Ubuntu, Linux and OS Chat**.*

This thread has devolved into a free-for-all which is now pretty much off-topic and the original poster has not taken part for quite sometime, so feel free to chat amongst yourselves here.

If anyone has a specific support request I suggest you post a new thread with a descriptive title rather than plonking it 25+ posts deep here on a thread with a title that may have little to do with your issue. Chrubuntu, Crouton and Kali are not part of the official Ubuntu family so not supported in the main support areas here anyhow. Good luck.

---

### Post by christopher35 on 2015-07-21
> **zoomy942 said:**
> I'm happy to help.

I used these two pages to get it done.  I'm using XFCE right now, but I'll be damned if I can;t figure out how to add the Ubuntu print manager.  

Anyway, try these and if you have questions feel free to ask.  I battled a ton learning but have it down now.

[http://www.maketecheasier.com/map-crouton-installation-external-device-chromebook/](http://www.maketecheasier.com/map-crouton-installation-external-device-chromebook/)

[https://docs.google.com/document/u/1/d/1JWLvbn4cy-LmQ-K3JeWMD-2yvT08V3lyMhrFilMClP8/pub](https://docs.google.com/document/u/1/d/1JWLvbn4cy-LmQ-K3JeWMD-2yvT08V3lyMhrFilMClP8/pub)

I'm new to chromebooks and to linux for that matter, I'm trying to follow the tutorials you posted specifically the "How to map" one, it seems to skip directions I was hoping you might be able to fill in. 
I finished this step "[COLOR=#C20CB9][FONT=monospace]**sudo**[/FONT][/COLOR][COLOR=#333333][FONT=monospace] [/FONT][/COLOR][COLOR=#C20CB9][FONT=monospace]**ln**[/FONT][/COLOR][COLOR=#333333][FONT=monospace] [/FONT][/COLOR][COLOR=#660033][FONT=monospace]-s[/FONT][/COLOR][COLOR=#333333][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#333333][FONT=monospace]media[/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#333333][FONT=monospace]removable[/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#333333][FONT=monospace]NAME-OF-SD-CARD-OR-FLASH-DRIVE[/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#333333][FONT=monospace]chroots[/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#333333][FONT=monospace] chroots" and when I go to install crouton, I get the download to 100% then /usr/local/chroots/trusty is not an ext filesystem

Any ideas as to where I went wrong? Also the screenshot posted for the installer where localhost is red isn't what my screen looks like, it's still the green chronos@localhost, maybe that has something to do with it?

Thanks in advanced, I love my chromebook for what it is, it does 99% of what I need, the only fault is trying to get my CAC card reader to work, which is why I'm trying to install linux to an sd card, so when I need to access my army stuff.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-07-21
> **Bucky Ball said:**
> 
This thread has devolved into a free-for-all which is now pretty much off-topic and the original poster has not taken part for quite sometime, so feel free to chat amongst yourselves here.

If anyone has a specific support request I suggest you post a new thread with a descriptive title rather than plonking it 25+ posts deep here on a thread with a title that may have little to do with your issue. Chrubuntu, Crouton and Kali are not part of the official Ubuntu family so not supported in the main support areas here anyhow. Good luck.

Welcome. Suggest you post a new thread with a title that describes your issue and post links to the tutorials and the other information you've given here (and anything else you can think of). You will greatly improve your chances of support (this is not a support area). Be aware that Chrubuntu would go in one of the other OS forum sections. Good luck. :)

---

