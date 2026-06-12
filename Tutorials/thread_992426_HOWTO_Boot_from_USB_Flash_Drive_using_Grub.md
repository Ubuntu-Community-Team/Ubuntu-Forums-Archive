---
title: "HOWTO: Boot from USB Flash Drive using Grub"
date: 2008-11-24
forum: Tutorials
---

### Post by Jose Catre-Vandis on 2008-11-24
I have found a way to use grub to boot from usb (avoids all detection issues at boot). This howto works specifically for xubuntu 8.10, but you can apply the same process for Ubuntu and Kubuntu.

This is thanks to the USBCDX810.iso from [www.pendrivelinux.com](www.pendrivelinux.com), which is designed to create a bootable cd-rom when your PC cannot / will not boot directly from a usb flash drive. Here's how you do it. (Howto probably not for Newbies ;))

> Requirements: A PC with some kind of Linux installed with grub as the bootloader. If you have a Windows install and want to acheive the same thing, see TJCIB's post further down. I did this using my Xubuntu 8.10 hard drive installation, you may need to modify paths if your distro / grub puts things / requires things in a different place.

Download the USBCDX810.iso from here: [http://downloads.sourceforge.net/pendrivelinux/USBCDX810.iso](http://downloads.sourceforge.net/pendrivelinux/USBCDX810.iso) (only @ 10mb)

Using gmountiso or similar iso mounting program mount the iso

Create a new folder in your /boot directory, I used /boot/usb-boot
```
 sudo mkdir /boot/usb-boot
```

Copy the grub folder, vmlinuz and initrd.gz files across from the mounted iso to your new directory
```
cp -R /media/iso/boot/* /boot/usb-boot
```
where /media/iso is the location of your mounted iso

Next open up your grub menu.lst: 
```
sudo nano /boot/grub/menu.lst
```

Add the following to the bottom:

> title Run Xubuntu 8.10 from USB FLASH DRIVE
root (hd0,0)
kernel /boot/usb-boot/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent quiet splash
initrd /boot/usb-boot/initrd.gz
boot

This assumes your system is running on the first partition of the first hard drive. Substitute (hd0,0) for the correct path. You can edit out quiet and splash if you like to watch what is going on, and remove the persistent entry if you are not running a persistent flash drive.

Save out, unmount the iso and reboot, inserting your flash drive as you go.

You may want to edit your bios settings to stop your PC directly booting from the flash drive. (Yes, this sounds odd, mine does, but I wanted a way of doing this from grub, so I stopped the bios from doing it)

On reboot, press ESC if you need to show your grub menu, then select the Run "Xubuntu 8.10 from USB FLASH DRIVE" entry at the bottom, and with any luck, you should start booting up from your USB Flash Drive.

A bit more work, but a more elegant solution in my opinion.

pendrivelinux also has similar boot isos for Ubuntu and Kubuntu, and you can edit the menu.lst lines to your own preference.

Enjoy

See also [zasf]("http://ubuntuforums.org/showpost.php?p=7057077&postcount=29")'s post about the DIY approach for a boot CD

EDIT

Although the link for the boot cd is still up, pendrive linux have changed things a biyt and now tell you how to create a boot cd rather than providing one.

For xubuntu 8.10 go here: [http://www.pendrivelinux.com/usb-boot-cd-for-xubuntu-810/](http://www.pendrivelinux.com/usb-boot-cd-for-xubuntu-810/)

They don't appear to have moved up to 9.04 yet

---

### Post by TJCIB on 2009-01-30
LOL,

I just did the same thing logging my steps to make a howto.
I was using Ubuntu.  But got all the same steps as you except for the directory name which is personal preference.

Thanks for confirming what I did.

I also used 
[http://www.icpug.org.uk/national/linnwin/step00-linnwin.htm]("http://www.icpug.org.uk/national/linnwin/step00-linnwin.htm")
 as a resource

Fun mini-project!

---

### Post by TJCIB on 2009-01-30
In an attempt to be a little more original (since you did my idea a few months before me) I thought I would try to do it through windows.

I used the method from Win'N'Lin NewB combined with the files from pendrivelinux.com to hook into the Windows XP boot loader.

This means no messing with your MBR or anything, it is basically just adding a few files and editing a few text items.  

Thanks for the inspiration!

---

### Post by Jose Catre-Vandis on 2009-01-30
Why not list out the steps and the software/scripts/actions required to do it through windows?

---

### Post by TJCIB on 2009-02-01
I made a HOWTO for the method of hooking into the Windows Bootloaders instead of installing grub to the MBR.

Here is the link
[http://ubuntuforums.org/showthread.php?t=1056601]("http://ubuntuforums.org/showthread.php?t=1056601")

my credits are on that page, it wasn't a totally original idea =)

---

### Post by mbele3000 on 2009-02-16
You both need to clean this up and the original was HOW TO BOOT FROM GRUB BOT BIOS!!! STOP CONFUSING PEOPLE! Thats great you were able to do that but AGAIN IT IS TO MUCH INFO! And the info that is there is not that clear. So when you go into how to do this from WINDOWS is not only misleading it is misinformation! <snip>

   Confused and upset Newbie

---

### Post by bapoumba on 2009-02-17
@ mbele3000: not sure we understand what you mean..

---

### Post by mbele3000 on 2009-02-17
OK Grub and Dos are 2 different things and are for 2 different operating systems! The original guide is explaining how to boot a Ubuntu via Grub (even though the instructions are VERY UNCLEAR). Then TJCIB in the same thread confuses the matter by "explaining" how to do the same thing in Windows which has NOTHING to do with the original thread so it confuses things!
  I have a old IBM Netvista and the BIOS (DOS NOT GURB!) does not have a option to boot from USB. So I was searching to see if there was a way to do this through GRUB. I followed the instructions for doing the Grub thing and to no avail (very frustrating to say the least). 
  The reason I left that "addition" to the thread was to express my frustration as a new user of Ubuntu and to say Please clean it up and clarify the steps in the Grub explanation and Differentiate the explanation regarding the Windows explanation. 
  Than You All!

---

### Post by bapoumba on 2009-02-17
Okay, the other members in this thread will say if I'm correct (I do not have much experience in the field), but you won't be able to boot from a usb drive if your bios does not support it.
Grub is the default bootloader used by Ubuntu (there are others around) and not an OS (Operating System). The purpose of the thread is to delegate the usb boot to grub, and looks quite appropriate to me, although probably not what you are looking for.

---

### Post by Jose Catre-Vandis on 2009-02-17
As far as I understand it, my howto does not require a computer that can "Boot" from a USB drive, just a usb port with a bootable installation (e.g. pendrivelinux / Create a USB disk)

I know this works on three counts. 1. I disabled my USB bootability in the bios on one PC and the setup I described worked. 2. On a ancient laptop that has just one usb port and nothing in the bios about booting from it, I am able to boot from the USB drive. 3. On another newer laptop that is supposed to boot from USB, but refuses and dies when trying through the bios, will boot up when using my method.

To simplify things, I suggest that mbele3000 tries the pendrivelinux method to boot using the Boot CD with the usb drive in place. If this doesn't work, there must be something wrong with a) the usb installation, b) the CD, c) Instructions not followed quite right. Can mbele3000 try the usb drive and the CD on another PC for testing?. If this does work, then move to the next stage and follow my howto. The CD and the USB versions have to match - 8.10 to 8.10 in my example.

Can't take credit for TJCIB's effort, haven't tried myself, but understand what has been done. To my mind this thread is about creating a bootable environment of a USB installation of 8.10, and although my howto was about doing it through grub, the thread became (hard drive) OS agnostic as we seek to boot Ubuntu from USB. If I want to boot Ubuntu from a USB stick, I beleive it is useful to know how to do this either through grub or dos, then end result is the same, Ubuntu booting up on a PC.

I will edit the howto to include the need for grub to be installed on the hard drive of the computer, within a bootable environment, in my case, Linux. I guess TJCIB's effort is the same but requires a Windows installation. I try to make no assumptions about other users abilities and skill level when writing howtos, but still being a newbie (3 years in!) myself, it may be I will miss a step here and there. I wrote it as I did it. (If I go on any longer I'll have to start grovelling, and I am not quite sure why I should) Bring back "OMG Pink POnies" :)

---

### Post by mbele3000 on 2009-02-17
Thank You VERY MUCH! That really clears things up! Again apologize for any inappropriate comments. 
      
    Sincerely Mbele

---

### Post by Jose Catre-Vandis on 2009-02-17
Let us know how you get on, and post back with any further problems, we'll see what we can do to help :)

---

### Post by KaPoPa on 2009-03-29
This seems to the right thread for me, I am fairly new to use Linux. So, I have:

- 2003 Packard Bell (it had XP) little boosted
- now only Ubuntu 8.10 on hard disk
- installed now 8.10 on USB stick, 8 Gb. I used "Create a USB startup disk"

I wish to boot from the stick, but the answer is in english "automatic startup program not available" or similar. I have not yet tried other computers.

Could you help me?

---

### Post by Jose Catre-Vandis on 2009-03-29
Hi KaPoPa

Does your Pc bios have an option for USB boot?
If so, is "automatic startup program not available" thge message you get when trying to boot from your USb stick.

If not (that is does not boot from usb) have you tried following my howto on page 1, ot simply using the pendrive boot cd?

Tell us what you have done and what you have tried.

More info please,  so more help can be given.

---

### Post by tturrisi on 2009-03-29
> **mbele3000 said:**
> OK Grub and Dos are 2 different things and are for 2 different operating systems! The original guide is explaining how to boot a Ubuntu via Grub (even though the instructions are VERY UNCLEAR). Then TJCIB in the same thread confuses the matter by "explaining" how to do the same thing in Windows which has NOTHING to do with the original thread so it confuses things!
  I have a old IBM Netvista and the BIOS (DOS NOT GURB!) does not have a option to boot from USB. So I was searching to see if there was a way to do this through GRUB. I followed the instructions for doing the Grub thing and to no avail (very frustrating to say the least). 
  The reason I left that "addition" to the thread was to express my frustration as a new user of Ubuntu and to say Please clean it up and clarify the steps in the Grub explanation and Differentiate the explanation regarding the Windows explanation. 
  Than You All!

Just to clear up any misunderstandings you may have:

GRUB = Grand Unified Bootloader.  Grub is NOT Linux specific.  It's for ANY operating systems.

Windows does not use GRUB by default as Windows has its own bootloader, but Windows bootloader can be removed and replaced with GRUB.

BIOS = Basic Input Output System.  The BIOS is code that has been placed onto a EPROM chip, a programable memory chip.  The BIOS code is NOT DOS. DOS is an operating system.  GRUB can be used as the DOS bootloader as well.

The bootloader for Linux (GRUB) is usually installed in the MBR (Master Boot Record), the first several bites of the drive, but does not have to be installed there, it can be installed in a directory.  GRUB boot options are contained in the file /boot/grub/menu.lst.

The bootloader for Windows NT operating systems (including XP & 2003 server) is the file c:\NTLDR, and its configuration is contained in the file c:\boot.ini.  Vista bootloader is different.

---

### Post by KaPoPa on 2009-03-30
Thank you Jose Catre-Vandis

When I put the stick in a Media icon appears and clicking it a text opens "This medium contains software to be automatically started. Do you want to run it?"
When I click run, the answer is "Error autorunning software. Cannot find autorun program"
The icon opens also the File Browser with all? Ubuntu files and a bar "Open Autorun box" Clicking it starts the above "This medium... all over again.
I don´t know if my PC bios has a USB boot option.
Suppose I need to follow your instructions.

---

### Post by Jose Catre-Vandis on 2009-03-30
OK. Looks like you are trying to run your ubuntu stick from within Ubuntu. Won't work like that. Leave the stick in and reboot your PC. When the first messages start coming up on screen, you should see an instruction of how to get into your bios, "Press F2" or "press Delete". Do what is says and you should be presented with a dos type graphical menu. You need something like "Advanced Bios Options" where there is a listing of which device will boot first, which second, and so on. Select the first one, and try to change the device. If you have USB-Drive, or USB-FDD or USB-ZIP or similar choose this, and then save out and reboot. with any luck your PC will start booting from your USB stick.

If this doesn't work, try some of the other USB related selections in the BIOS. if it still doesn't work, then head over to [www.pendrivelinux.com](www.pendrivelinux.com), and download the Boot CD iso related to your specific install. Burn this ISO file to a CD/CDRW, and set your bios to boot from CDROM first. Keep the USB stick in place, and let the CD do the rest.

If this is what you want, you can then follow my howto to do things wihtout the CD :)

---

### Post by KaPoPa on 2009-04-04
So, I have downloaded "USBCDX810.iso and have it's icon on desktop, but cannot mount it. I have /boot/usb-boot, but the command "sudo nano..." does not find the iso. :confused

---

### Post by Jose Catre-Vandis on 2009-04-04
If you want to boot from it, you to burn it to a CD
```
 cdrecord -v speed=4 dev=/dev/cdrom USBCDX810.iso
``` or use Brasero

If you want to copy the contents across to your hard drive, have you installed gmountiso? if not use this command to mount the iso:
```
sudo mkdir /mnt/disk
sudo mount -o loop USBCDX810.iso /mnt/disk
```

---

### Post by KaPoPa on 2009-04-06
I have the "USBCDX810.iso" in the file browser and opening it I end up with following:

title Run Xubuntu 8.10 from USB DISK
root (cd)
kernel /boot/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent quiet splash
initrd /boot/initrd.gz
boot

Don't know how to continue. It seems also that I need to change the CD-drive(s) (I have two now) as I can't burn it. Can't copy it to hard disk either. But I don't intend to give up.;)

PS: I can read an older CD with my files.

---

### Post by Jose Catre-Vandis on 2009-04-06
So I can help you, please answer these questions and give details of where you have got stuck for each question:

1. Do you want to boot from hard drive (as in the howto) or boot from CD then run USB Xubuntu?
2. Have you created a USB stick version of Xubuntu?
3. Have you tried editing the bios options on your PC to boot by USB?
4. I am pretty sure you have downloaded the USBCDX810.iso onto your computer (@ 10mb)?
5. Why can't you burn the iso to CD?
6. Why can't you mount the iso as a folder?

---

### Post by KaPoPa on 2009-04-09
1. What I wish to do is to boot from a USB stick, first to try the installed Ubuntu 8.10 in my machine. If it works, I go to other machines to try or install Ubuntu there, or I install other Linux (Xubuntu?) in my stick to try it in my computer.
2. Earlier I downloaded Ubuntu 8.04 but could not burn it. When I can I shall try ex. Xubuntu. I have now Ubuntu 8.10 CD.
3. I have gone with F2 to bios, with the stick in place and can find there the hard disk but nothing about the USB. 

Advanced CMOS Setup shows following:
Quik Boot      		        Enabled
1st Boot Device		        CDROM
2nd      "			IDE-1
3rd       "			IDE-2
Try Other Boot Devices	        Yes
S.M.A.R.T. for hard Disks	Enabled
BootUp Num-Lock		        On
System BIOS Cacheable	        Enabled
Initial Display Mode		Silent

4. Yes I have (10mb) and Gmount-iso as well, in which I select USBCDX810.iso as "Image File" and boot/usb-boot as "Mount point". After mounting I get "loop0 mounted on /boot/usb-boot". When I go to see it in Gnome Commander, there is under /boot/usb-boot/ "boot file" and "boot.catalog" and in "boot file" all the rest needed, I suppose.
5. I just don't know. I can play music and read files on both CD and CD/DVD players.
6. I have to try it.

---

### Post by Jose Catre-Vandis on 2009-04-09
Given everything you have said, all I can suggest is that you revisit Post #1 and follow the howto again very carefully. You need to copy files over from the boot cd to the /grub/usb-boot folder, not mount the iso there.

If you have Xubuntu installed on your flash drive you are good to go, if you have Ubuntu installed, you need to visit pendrivelinux.com and get or create the Boot Cd for Ubuntu.

As previously suggested, you might like to try booting up with the Boot CD to get the USB install working. If this is OK, then copy the required files across, edit your grub menu, then try to boot from the hard drive to get the USB install running.

---

### Post by zasf on 2009-04-10
I'm trying to boot my laptop with a usb stick altough my laptop doesn't support native usb boot support.

I followed the first post carefully, here is what I added to menu.lst
```
title USB FLASH DRIVE
root (hd0,6)
kernel /boot/usb-boot/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper noprompt cdrom-detect/try-usb=true persistent
initrd /boot/usb-boot/initrd.gz
boot 
```

```
$ ls -R /boot/
/boot/:
abi-2.6.27-11-generic         System.map-2.6.27-11-generic
config-2.6.27-11-generic      usb-boot
grub                          vmcoreinfo-2.6.27-11-generic
initrd.img-2.6.27-11-generic  vmlinuz-2.6.27-11-generic
memtest86+.bin

/boot/grub:
default        fat_stage1_5       jfs_stage1_5  menu.lst.backup    stage1
device.map     images             menu.lst      minix_stage1_5     stage2
e2fs_stage1_5  installed-version  menu.lst~     reiserfs_stage1_5  xfs_stage1_5

/boot/grub/images:
infinity-grub-fullcolor.xpm.gz

/boot/usb-boot:
grub  initrd.gz  vmlinuz

/boot/usb-boot/grub:
menu.lst  menu.lst~  stage2_eltorito

```

When I choose "usb flash drive" at grub menu, the system starts but it is not able to load anything from the usb drive, after 20/30 messagese like:

```
[    8.399945] kjournald starting.  Commit interval 5 seconds
[    8.400026] EXT3-fs: mounted filesystem with ordered data mode.

```

leaves me with a sad prompt.

What's wrong? It seems that it is not able to mount the usb drive. At the prompt, using mount, I'm able to mount the drive and see its contents (full dmesg attached).

---

### Post by Jose Catre-Vandis on 2009-04-10
A few things to try, as it seems you have done everything right so far!

1. Make a physical Boot CD and see if it works that way?
2. Check your versions of Xubuntu & USBCDX810
3. Check you are trying this with a matching "CD" and install
4. test your USB install on a USB booting PC to ensure that works OK

---

### Post by zasf on 2009-04-10
> **Jose Catre-Vandis said:**
> A few things to try, as it seems you have done everything right so far!

1. Make a physical Boot CD and see if it works that way?
what do you mean? put usb-boot folder and all that it needs in a cd?
> 
2. Check your versions of Xubuntu & USBCDX810
3. Check you are trying this with a matching "CD" and install
I'm using Ubuntu 8.10 and USBCD810.. this should be right
> 
4. test your USB install on a USB booting PC to ensure that works OK

hum.. this is a good idea. I made my usb booting stick with Ubuntu 8.10 utility but 9.4 beta image (jaunty), since I need to test jaunty on my system but I have problems with my cdrom.

I'll do this test first and report back here, thanks for your quick reply.

---

### Post by Jose Catre-Vandis on 2009-04-10
> **zasf said:**
> what do you mean? put usb-boot folder and all that it needs in a cd?

I mean burn the USBCD810.iso to a CD and boot up your PC from that, it should then make the USB flash drive boot. This will prove if your flash drive install works, and works with the contents of the boot cd.

---

### Post by zasf on 2009-04-11
> 
4. test your USB install on a USB booting PC to ensure that works OK

I tested it on another computer and it works great

> **Jose Catre-Vandis said:**
> 1. Make a physical Boot CD and see if it works that way?

It doesn't work, leaving the same busybox prompt..

---

### Post by zasf on 2009-04-12
I finally managed to boot via usb by rebuilding initrd, following the istructions on this [wiki page]("https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD").

I both tested the new initrd with cdrom and usb-boot directory in my root system.

You may want to link the wiki page from your first post, I'd like to update it also with instructions on how to use the initrd image with the grub hard disk.

Thanks for your help

---

### Post by ahoq on 2009-04-18
yes, it may come those problems, 

but as the technologies become more and more mature, seldom encounters these problems.

you canfind answers here.
[http://www.onthesource.com/computer-peripheral/flash-memory-drives/](http://www.onthesource.com/computer-peripheral/flash-memory-drives/)

---

### Post by mysterious_beans on 2009-05-17
Thanks for the thread.

I'm stuck at this point: confirming that GRUB can access the bootable flash drive (not really a step in the OP's recipe, but more of a sub-step).

I start GRUB (from boot), and go to console ('c'), with a bootable live Ubuntu 8.10 on a flash drive, plugged in.

```
grub> boot (hd
 Possible disks are:  hd0 hd1

grub> boot (hd1,
```

On the first prompt line, I've pressed TAB to get the drive list; hd0 is my notebook's SATA HD, and hd1 is (presumably) the plugged-in flash drive.

When I press TAB on the second prompt line, to "drill down into" hd1, the light on the flash drive, formerly on, is extinguished, and GRUB freezes. Incidentally, when I yoink the drive, the notebook reboots/shuts down (depending on whether I've hit the soft power button while GRUB was frozen).

Can anyone suspect what's going off the rails here?

For reference, it's a Gateway MX-6961; I have a dual-boot of XP and an old/half-broken Kubuntu (7.x) which I'm trying to update (overwrite). The boot order in the BIOS settings is configured to support bootable USB drives ("Removable drives"), but I can override and force a boot from the notebook's SATA HD when I need to start GRUB (in order to use the OP's method); XP is on sda1, Kubuntu on sda5. There might be a BIOS update for my notebook, but I'd like to avoid that if possible; I need this PC working as much as possible for the near future; no "experiments" can be done at this time. ;-)

---

### Post by mysterious_beans on 2009-05-17
Late-breaking news: I've got it down to a "Error 25: Disk read error" after successfully doing a "rootnoverify (hd1,0)" (after which I try "chainloader +1").

I'm trying to use this as a rough guide: [https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD](https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD)

(the part about the GRUB console in particular)

Does "Error 25" == old BIOS code that just doesn't have good USB support or similar?

---

### Post by Jose Catre-Vandis on 2009-05-18
I'm not quite clear as to where you are in the process? Can't see why you are having to "start/edit" GRUB when you boot?

Have you created a working boot cd that will get your USB flash drive going? If not, you should get to that stage first, then you know that the process will work. Then copy over the required files to a directory on your hard drive and set up your hard drive grub manually as per the first post.

Also check using fdisk the names for all your drives (hd0, hd1 etc)

---

### Post by mysterious_beans on 2009-05-21
Ah, there's the rub. I don't currently have a burn of 8.10, and my 8.04 is mysteriously lost. And so here I am, hoping to avoid burning yet another CD. :-)

Anyway, as to the step in question, I was trying to adapt your method to a CD-less solution, fixing problems as I go, by learning enough about the process to hopefully understand the cause of the problem.

In any case, I've made it a bit further.

What I've done so far:
- grabbed USBCDX810.iso
- extracted its relevant contents into '/boot/usb-boot/'
- edited my GRUB menu.lst to add a new entry pointing to '/boot/usb-boot/*' as appropriate
- rebooted (and here's where the "manual sub-steps" come in)
- chose a GRUB prompt ('c') instead of booting, and entered the steps one by one so I could see each one succeed/fail
- I had erred and selected '(hd0,0)' as my root (or until the flash drive problems '(hd1,0)', also wrong) when i should have chosen '(hd0,5)' where my actual root is; I fixed that in the manual steps, and then reached the 'boot' command, which worked, more or less, until I got the big blast of 'EXT3-fs: mounted filesystem with ordered data mode.'/'kjournald starting.  Commit interval 5 seconds'. Eventually, however, it emitted a few ACPI-related errors, and then reached the BusyBox prompt, where I was able to navigate around in 'the (initramfs)' file system.

Is my quest (to boot by hooking in at GRUB, and "redirecting" the boot to a flash drive with a "live" Ubuntu 8.10) headed in a dubious direction?

For now, I'm using the Xubuntu .iso (the one you provided a link for); would one be able to swap that for another bootable CD image, say the Ubuntu 8.10 desktop edition?

Thanks for your thoughts, and don't trouble yourself if you feel I'm diverting the focus of the thread; I'm not trying to cause trouble. :-)

---

### Post by Jose Catre-Vandis on 2009-05-21
As far as I understand. for this to work, you need a USB install of 8.10 with the gubbins of the grub requirements coming from the pendrive boot CD.

So I will assume the following:

1. You have correctly installed Xubuntu 8.10 to a usb stick, using the USB creator that comes with recent versions of Ubuntu.

1.a. You have tested this out on another machine that allows booting from USB drives? Just to validate that your USB install works?

2. You have correctly copied over the necessary files from the PenDrive 8.10 Boot iso to you preferred location, sounds like /boot/usb-boot/* ?

3. You have edited the menu.lst on your hard drive installation grub and made an entry to point at the files in /boot/usb-boot, ensuring that the root section says (hd0,0) ('cos that's where grub and /boot/usb-boot/ is!)


No, the boot iso you have probably won't work with other flavours or editions of ubuntu/xubuntu/kubuntu as I understand they are tailored to the particular setup of each version.

Keep at it, once you have all your ducks lined up, you'll get it working :)

---

### Post by mysterious_beans on 2009-05-24
Thanks for the response.

Regarding assumption 1, since I want to install Ubuntu, and have a working 8.10 machine, I used it to make the bootable flash drive, so I do have the "wrong flavor" for the bootable disk.

To account for the difference, I made the necessary changes to menu.lst (e.g. xubuntu.seed -> ubuntu.seed), etc.

I actually tried to find an equivalent CD image for Ubuntu at the site you linked (subbing that in might do the trick, combined with the Ubuntu "USB Startup Disk Creator"'s results), but I found navigation there a bit weird, and never could get to an index of files like USBCD*.iso, so I couldn't find what I was expecting ('USBCD810.iso').

However, while browsing there, I came across this, and it contains links to various CD images which might be of use:
[http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/#more-401](http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/#more-401)

I don't mean to derail/hijack your thread, so I will only post back if I come up with a workaround for your method which can be used completely without a CD. In the meantime, keep up the good work.

---

### Post by Jose Catre-Vandis on 2009-05-24
From what you say it looks like you are trying to run an ubuntu usb stick with the xubuntu Boot CD. AFAIK this won't work due to the inner working of the initrd,gz file.

The link you were looking for is
[http://downloads.sourceforge.net/pendrivelinux/USBCD810.iso](http://downloads.sourceforge.net/pendrivelinux/USBCD810.iso)
(just needed to remove the X :) )

---

### Post by mysterious_beans on 2009-05-25
> **Jose Catre-Vandis said:**
> From what you say it looks like you are trying to run an ubuntu usb stick with the xubuntu Boot CD. AFAIK this won't work due to the inner working of the initrd,gz file.

The link you were looking for is
[http://downloads.sourceforge.net/pendrivelinux/USBCD810.iso](http://downloads.sourceforge.net/pendrivelinux/USBCD810.iso)
(just needed to remove the X :) )

Oh, duh! I can't believe it hadn't occurred to me to try that, especially after I'd deduced the expected filename. I will try using the "correct" image, and post my results if successful. Cheers!

---

### Post by mysterious_beans on 2009-05-25
Okay, I'm writing this from Ubuntu 8.10 live desktop, booted from a flash drive via special GRUB entry.

So, here are my notes for success (for others trying variations):
* it's important to understand the layout of your partitions, and to be certain which partition number (in GRUB format) contains your '/boot' subdir-tree; that's where you'll place 'usb-boot' (from the tutorial) -- my '/boot' is on "(hd0,5)", so I put that in place of "(hd0,0)" in the tutorial; until I did, I got error 17 in GRUB.
* you can't really mix and match the ISO images from PenDriveLinux with the bootable startup disk ("Create a USB startup disk"); if you use Ubuntu startup disk, you need the Ubuntu version of the PenDriveLinux ISO; if you mix and match, you can get as far as BusyBox (possibly still useful), and maybe further (no attempts made beyond BusyBox).
* ...however, you can substitute different flavors of Ubuntu as long as you can matching startup disks to their related ISO at PenDriveLinux; if you can figure out how those ISOs are built, then you can probably even adapt the original technique to other Linux distros.
* experimentation/variation with this technique is reasonably safe and leads to a better understanding of the boot process in general (make sure to take the usual precautions, like making a backup copy of 'menu.lst' before editing it, etc).

Anyway, I solved my problem (replace old/broken Kubuntu install with fresh Ubuntu desktop install via flash-based boot, without disturbing existing OS installations) with help from your tutorial, so thanks again, Jose (a shout-out as well to the folks at PenDriveLinux). \\:D/

---

### Post by Jose Catre-Vandis on 2009-05-25
:) @ mysterious_beans

---

### Post by Messyhair42 on 2009-06-21
found my own errors

---

### Post by mikitz on 2009-11-01
Great thread! I am just verifying that this method does indeed work for a machine without usb boot support. This is probably more of a tutorial on how to use grub, as it can be applied to any o/s that uses the grub boot loader (I've used it with Puppy Linux also)

Thanks Jose!

---

### Post by darkod on 2009-11-06
Hello.

I am also new Ubuntu user although I have worked with different Linux version few years back. If I can please jump into this thread, with a direct question.

For my purposes I am creating a USB stick booted by Grub and I wish the following menu:
1. Install Windows 7
2. Boot from first hard drive
3. Command line
4. Reboot

I have done all of them except number 2. In Grub2 I think there is command localboot 0x80 but localboot does not exist in Grub.

Can someone please tell me the command (if any) that after booting from the USB grub will let you continue with the HDD botloader (whatever it is) on any computer, not just one particular. The idea is to have the option to continue with the HDD boot without restarting the PC and taking out the USB stick.

Hope that made sense. :p

EDIT: I was playing with the command line while booting up from the USB stick and came to the following conclusion:
The USB stick is marked as hd0 by grub
My first (and only) SATA hdd as hd1

According to the above, the group of commands:
rootnoverify (hd1,0)
makeactive
chainloader /bootmgr

did the trick and after starting with the USB stick grub the PC continued booting from the hard drive.
So, are the above commands the way to go? I was looking for a general command that would tell grub to boot the first hard drive regardless of how many drives you have and whether they are SATA or IDE.
Will my USB stick always be hd0 and the first hard drive hd1? Is that because grub is actually on the stick and not the drive?
Personally I was surprised. I expect the drive to be hd0 and the stick hd1, and in situation when grub is on the drive that might be true. Now it's on the stick and I guess it makes a difference.

On another subject, for anyone looking into installing grub on USB stick on Windows, download GRUB4DOS and utility called grubinst. Easily found in google, sorry don't have the exact links right now. The grubinst utility even has a GUI program called grubinst_gui.exe that you need to run as Administrator (if in Vista, otherwise it won't work), you need to select Disk option and which drive (careful not to select your hdd, you will destroy the MBR) and then you click on the Refresh button in Part List option and that will allow you to select in drop down list whether you want it on the MBR of the selected disk or on a particular partition from the disk. Of course, unless you created more partitions with Gparted in Linux, Windows will be able to see just one or the first partition on USB sticks.
After selecting MBR or partition, check the Don't search floppy box and click on Install. That's it, now you have GRUB4DOS on your USB stick.
After that you need the following: extract the downloaded GRUB4DOS zip file and copy grldr and menu.lst to the root of your USB stick. Change the entries in menu.lst to your liking and that is it.

I just used this procedure to make a bootable stick with installation files of Windows 7 when for whatever reason windows was not making the stick bootable properly. GRUB4DOS (as well as grub in general, it's the same thing) works perfectly.

---

### Post by MrUmunhum on 2010-07-29
> **mbele3000 said:**
> OK Grub and Dos are 2 different things and are for 2 different operating systems! The original guide is explaining how to boot a Ubuntu via Grub (even though the instructions are VERY UNCLEAR). Then TJCIB in the same thread confuses the matter by "explaining" how to do the same thing in Windows which has NOTHING to do with the original thread so it confuses things!
  I have a old IBM Netvista and the BIOS (DOS NOT GURB!) does not have a option to boot from USB. So I was searching to see if there was a way to do this through GRUB. I followed the instructions for doing the Grub thing and to no avail (very frustrating to say the least). 
  The reason I left that "addition" to the thread was to express my frustration as a new user of Ubuntu and to say Please clean it up and clarify the steps in the Grub explanation and Differentiate the explanation regarding the Windows explanation. 
  Than You All!

Hi, saw your post. I know this is an old post but! If you still have the problem of a machine that will not boot from USB, try this site: [http://64.124.13.3/hacks/USB_Boot_using_GRUB.html](http://64.124.13.3/hacks/USB_Boot_using_GRUB.html).
It is a write up I did several years ago that details how to boot from USB even on PCs that do not support it.

I tried to send a privtae message but this system would not let me.

---

### Post by rajeshgheware on 2010-07-31
Hi Jose,

I tried booting from usb (my laptop  BIOS does NOT support USB though) and Ubuntu 10.04 worked!  This is what I did:
1. Created USB startup disk on Ubuntu 9+
2. Added following to /boot/grub/menu.lst (you need to be root)
****
title Run Ubuntu 10.04 from USB FLASH DRIVE
root (hd0,4)
kernel  /boot/usb-boot/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper  noprompt cdrom-detect/try-usb=true persistent quiet splash  i915.modeset=1
initrd /boot/usb-boot/initrd.lz
boot
***
NOTE: hd0,4 is the location where vmlinuz & initrd.lz are kept (copied from USB startup disk location - /casper/*)
3. Restart laptop (I used Acer Travelmate 2005 edition with no USB boot support)
NOTE: Kernel para i915.modeset=1 is critical as Ubuntu 10.04 does not boot clean for old intel video card
4. You will boot into live Ubuntu 10.04.  Use install button on desktop and follow the install instructions. When done, restart laptop
5. While booting when multi-boot options shown, press 'e' to edit kernel param and do not forget to add i915.modeset=1 if your video card is intel & old
6. Enjoy the great new Ubuntu Desktop!

- Rajesh Gheware
[http://chessacademy.in](http://chessacademy.in)

---

### Post by leejosepho on 2010-09-21
Greetings to all!
 
I have read through this thread a couple of times, and I can see you folks here actually really know your stuff. I am a rookie multi-booter in need of some help ... and please just let me know if you would rather I delete this post and start a new thread.
 
As posted to me on another board where someone has at least *understood* what I am trying to do:
 
> If I am correct, you are wanting a boot loader that is independent of any OS, i.e. no specific OS has control over the initial boot loader or what appears on it. GRUB and GRUB 2 can use chainloading, allowing you to tell the boot loader the location of an OS' native boot loader. You could then have a boot loader for each OS (for linux you would install the boot loader on the partition not the boot sector). Then install the OS independent grub on a usb stick or floppy drive. The usb or floppy would hold the menu.conf file and boot loader and you would load that up when you wanted to boot an OS. This way the independent boot loader only holds the locations of the boot loader for each OS but not the actual information to boot the OS.
I presently have five (5) operating systems on three hard drives in my machine, and I plan to add some more ... and yes, in case anyone might ask: Part of the reason I am doing this is just to prove it can be done. But beyond that, I am a retired (disabled) industrial (mechanical) fabricator who now has to remain seated most of the time anyway.
 
Here is what I presently have:
 
sda > Win2K -- Win98 -- WinXP -- Win7 -- storage
sdb > cloned backups and more storage
sdc > swap partitions -- Mint 9 and room for more distros -- more storage
usb > prepared-and-almost-ready location for an OS-independent boot selector
 
Here is a fairly recent screen shot: [https://sites.google.com/site/alphamultibootscoop/](https://sites.google.com/site/alphamultibootscoop/)
 
On my first drive, the Windows systems are all MS-naturally chained together, of course, and I can presently get to them all in each of these three ways:
 
1) letting my machine boot "normally" from the first drive's boot sector;
2) manually using SuperGRUB from a bootable CD to get to Win7's BCD (and to Mint);
3) from a selection GRUB placed in Mint 9's boot loader during Mint's installation.
 
On my third drive, Mint 9's boot loader is installed on Mint's own "/boot" partition (logical and not "active"), and I can presently get to Mint only by using SuperGRUB from the bootable CD already mentioned.
(Note: I have read it is possible to add non-MS boot links within XP's "boot.ini".)
 
The USB stick listed above is permanently attached *inside* my machine, and that is where whatever I do here will be located ...
 
... and I have more-than-once already been through many disastrous trials and tribulations of "Just let GRUB do it all!"
 
Never again -- my OS installation disks are getting worn out.
 
My BIOS is now seeing my USB stick as a "USB-CDROM", but I have yet to learn/figure/find out how to place a boot sector there (assuming I need one).  Also, I have read somewhere that I need to flip some bit on that stick so it will not show as "removeable".
 
Once again, here is what I am needing/wanting/trying to do:
 
> ... a master boot loader on a USB stick and independent of any OS, allowing me tell [add or edit] the location of each OS' native boot loader.
 
I am not asking for anyone to "just make this happen" for me, but to help me learn how to get it done ...
 
... and I thank you!

---

### Post by leejosepho on 2010-09-21
This evening I burned a GRUB2 disc with hopes of trying its *experimental* USB capabilities, but that selection at startup only ended at a flashing cursor.  I had been hoping to place GRUB2 on my USB stick for some experiments of my own, but for now I can nevertheless use it to get to Windows while beginning to learn some of its commands ... and I can still get to Mint via SuperGRUB, of course.
 
Question: What might be the best Ubuntu "mini"?  I plan to eventually install the full version of Ubuntu, but for now I think some trials with one or two smaller versions would help me gain some good experiences with ISOs and USB devices.

---

### Post by Jose Catre-Vandis on 2010-09-25
@ leejosepho
Things have moved on a bit since I did this howto. You might be best off setting up your USB stick with a full distro on board (Use unetbootin for this), and then by booting from the USB stick you can edit grub in order to get the other Os's running. You'll need to read up on Grub/Grub2 on how best to access the HDD's correctly on your system. Personally, I prefer to set aside one HDD (the primary one) for all my OS installations, which makes setting up GRUB easier, but you have to get the installation order right for this: W98>Win2000>WinXP>Win7>Main Linux>Other Linuxes (and don't overwrite the MBR with these) Then you don't need the USB to boot from. (Grub will offer you a Windows 7 boot option which will hopefully then offer you the Windows boot loader for the other windows systems, but quite honestly, unless you have specific hardware/software requirements not really any need for W98/Win2000 or XP any more.)

For a "mini" Ubuntu, you can use the Alternate CD to install a command line only system and then build a desktop from openbox or xfce. Check out the Psychocats tutorial for this or find elsewhere on the forum. Or get something like Crunchbang or Lubuntu.

---

### Post by MrGreen on 2010-10-10
I am having a problem booting a usbstick on my acer 5315 laptop, all I get is boot error then nothing.

Considered trying to get grub that is installed on laptop to boot it, not sure if that would work.

Does these guides here still work?

MrG

---

### Post by Jose Catre-Vandis on 2010-10-11
> **MrGreen said:**
> I am having a problem booting a usbstick on my acer 5315 laptop, all I get is boot error then nothing.

Considered trying to get grub that is installed on laptop to boot it, not sure if that would work.

Does these guides here still work?

MrG

Need more info to help...

What is on your usb stick?
How did you make it?
Will it boot on any other PC?
Does you Acer laptop boot from USB?
Does your laptop boot from CD?
Are you running grub on the laptop anyway?

---

### Post by MrGreen on 2010-10-12
I solved the issue by using Plop...Laptop is now running 10.10

---

### Post by ramanrjn on 2011-11-14
suppose i have a boot cd installed in my usb (without anything u posted, just installed it using unetbootin) and i plug it into my laptop with grub loader.....will it boot?

---

### Post by sekoica on 2013-06-16
Hi, i'm interresting by this howto but my problem is the iso files USBCDX810.iso where can found this iso. Any member can send me this iso files or a link where i can download I'm not interesting by new method of pendrivelinux (this work only on a ubuntu . I have grub and ArchLinux Just tell me where is this iso files now Thanks you My computer don't boot on my usb stick key by the BIOS, my CD drive don't work

---

### Post by Cheesemill on 2013-06-16
The file you are after is from a 5 year old OS, I'm not sure if it's still available anywhere.

Instead you can get the same result by adding a grub entry for PLOP boot manager. Instructions can be found here...
[http://www.plop.at/en/bootmanager/plpbt.bin.html#rungrub2](http://www.plop.at/en/bootmanager/plpbt.bin.html#rungrub2)

---

### Post by Merrattic on 2013-06-22
Knew I had them somewhere:

USBCD810

[http://ul.to/11fqrqd3](http://ul.to/11fqrqd3)

USBCDX810

[http://ul.to/loyo8mvj](http://ul.to/loyo8mvj)

---

