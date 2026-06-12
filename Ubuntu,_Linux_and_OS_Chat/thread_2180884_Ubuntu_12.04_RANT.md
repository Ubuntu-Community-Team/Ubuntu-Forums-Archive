---
title: "Ubuntu 12.04 RANT"
date: 2013-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by wlsemmens on 2013-10-15
I've been away from Linux for quite some time. I have just set up a PC for my wife who is bedridden but Windows would not allow me to adjust the size of certain objects, icons being the most annoying, so I thought, (now that's a dangerous concept) "Linux will fix this, I'll install Linux". Being the considerate husband that I am I decided to set it up on my media server first. Broke out my AMD64bit Karmic Koala cd and installed it like a dream, from there it has all been downhill! That version is too old to access the repositories, ok, I'll download the latest and greatest. TWO DAYS later I've finally managed to, at least get some semblance of an installer running, I'd have thought that by now support for nVidia chipsets would be endemic. After numerous "black screens" and so forth, I am currently in the process of finally partitioning a drive, (I hope, I seem to be waiting a long time for nothing to happen). It took me nearly 48 hours to get a fully working system using Windows 7 (including all updates and other software) on this same computer. If later versions of Ubuntu, and, I suspect, other perversions, are so "user unfriendly" I cannot see them becoming a viable alternative to the bits of fruit (Apple) and Windows. I'd have thought that by now, Linux would be a fairly mature OS with minimal issues to the novice. Heck, even Windows has managed to "get it right" (well sort of) ever since the days of DOS (remember those) some of the time. 


Now to some questions.

If I manage to download and install a Live CD/USB and, get it working with no black screen issues etc, do I still need separate variants for Intel and AMD processors?
Why is it that the installer only shows the absolute drive name (sda, sdb, etc) but does not seem to show the volume name which would make it much easier installing on a system with multiple drives?

---

### Post by mastablasta on 2013-10-15
> **wlsemmens said:**
> I've been away from Linux for quite some time. I have just set up a PC for my wife who is bedridden but Windoze would not allow me to adjust the size of certain objects, icons being the most annoying, so I thought, (now that's a dangerous concept) "Linux will fix this, I'll install Linux". Being the considerate husband that I am I decided to set it up on my media server first. Broke out my AMD64bit Karmic Koala cd and installed it like a dream, from there it has all been downhill! That version is too old to access the repositories, ok, I'll download the latest and greatest. TWO DAYS later I've finally managed to, at least get some semblance of an installer running, I'd have thought that by now support for nVidia chipsets would be endemic. After numerous "black screens" and so forth, I am currently in the process of finally partitioning a drive, (I hope, I seem to be waiting a long time for nothing to happen). It took me nearly 48 hours to get a fully working system using Windoze 7 (including all updates and other software) on this same computer. If later versions of Ubuntu, and, I suspect, other perversions, are so "user unfriendly" I cannot see them becoming a viable alternative to the bits of fruit (Apple) and Windoze. I'd have thought that by now, Linux would be a fairly mature OS with minimal issues to the novice. Heck, even Windoze has managed to "get it right" (well sort of) ever since the days of DOS (remember those) some of the time. 


i suspect nomodeset command would solve your issue: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

i have compatible hadrware and install took about 15 minutes (dual boot). not sure how you got 48 hours. and for what exactly...
edit: i have an even older mashicne and a slow one that took about 30 mins to install Chrunchbang which is perhaps only slightly more complicated to install.
> 
If I manage to download and install a Live CD/USB and, get it working with no black screen issues etc, do I still need separate variants for Intel and AMD processors?

x86 and AMD64 are brand names. x86 stands for 32 bit OS while AMD64 stands for 64 bit os. AMD64 works on 64 bit intel CPU as well. but because AMD was the first to make 64bit CPU this name stuck in image name. read more here: [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)
> 
Why is it that the installer only shows the absolute drive name (sda, sdb, etc) but does not seem to show the volume name which would make it much easier installing on a system with multiple drives?

because those labels are valid in DOS (they are DOS volume lables). why doesn't windows see linux file system and volume lables when you are installing windows as dual boot? in short it's a non issue if you are installing only linux OS. being able to do a dualboot with completely different OS is a bonus! other proprietary os will do everything in their power to actually stop you from booting anything else but their brand of OS (e.g. secure boot).

---

### Post by wlsemmens on 2013-10-15
Thanks for the quick reply, I used the nomodeset command which was less than satisfactory but it got me to the next bit, it did seem to install but I am now back at the black screen, yet again. I'm now going to have to break out my Old Linux disk just to modify, (I'm guessing here), GRUB to re-add nomodeset now that it is installed. Thanks for the bit of info about 64 and 32 bit variants, my info had been derived from earlier versions of Linux documentation which did not appear to be as clear as it should be.

My issue with drive labels, which I am happy enough referring to drive letters etc, has got nothing to do with OS dualbooting. As I said in my OP, that I was installing on my media server, which has 5 drives internally, and more external, mostly containing movies or software masters so no OS dualboot is involved or needed. My setup is such that I have one drive for an OS, One for Downloads, One as my documents repository which also contains backups of all software, one backup drive and the remaining drives contain movies and TV shows all have appropriate volume labels, which identify what they contain. Because I have so many drives installed, I forget into which SATA socket they are plugged. I know I could crack the case and work with one drive, but that defeats the purpose for the average noddy.

---

### Post by verymadpip on 2013-10-15
Hi there.
You could use GParted, or some such application, to examine your drives & see if you can tell which one is which (or whatever) by drive size & file system.
I think that's also possible from the command line with fdisk.
Of course, it won't help if all of your drives are the same size & file system.

Or perhaps the drives could be examined from the Live environment & then you can see what's on them.
Just a thought.

---

### Post by mastablasta on 2013-10-15
> **wlsemmens said:**
> Thanks for the quick reply, I used the nomodeset command which was less than satisfactory but it got me to the next bit, it did seem to install but I am now back at the black screen, yet again. I'm now going to have to break out my Old Linux disk just to modify, (I'm guessing here), GRUB to re-add nomodeset now that it is installed. Thanks for the bit of info about 64 and 32 bit variants, my info had been derived from earlier versions of Linux documentation which did not appear to be as clear as it should be.
.

hold left shift to get into grub and to boot again with nomodeset.

and then do this: [http://ubuntuforums.org/showthread.php?t=1675337&p=10396637#post10396637](http://ubuntuforums.org/showthread.php?t=1675337&p=10396637#post10396637)

to keep it. you didn't mention what GPU you use. perhaps you need to install additional drivers. i am not sure why this nomodeset appears now, i also didn't have this issue before but in some versions it's appearing. and drivers are opensource. i first came across it in OpenSUSE when i was trynig it out.

> 
My issue with drive labels, which I am happy enough referring to drive letters etc, has got nothing to do with OS dualbooting. As I said in my OP, that I was installing on my media server, which has 5 drives internally, and more external, mostly containing movies or software masters so no OS dualboot is involved or needed. My setup is such that I have one drive for an OS, One for Downloads, One as my documents repository which also contains backups of all software, one backup drive and the remaining drives contain movies and TV shows all have appropriate volume labels, which identify what they contain. Because I have so many drives installed, I forget into which SATA socket they are plugged. I know I could crack the case and work with one drive, but that defeats the purpose for the average noddy.


yes and if all those drives were formated with the ubuntu default ext4 file system you would see the lables i believe. but you have them formatted in NTFS haven't you? which is windows format.
to me the best way not to confuse partition ( i have 4 that came on laptop and needed to add at least 2 Ubuntu partitions) is to create empty unformatted disc space and then on install just install to where the unformatted space is.

sda = first disk, sdb second disk etc.
sda1 = first partition on first disk, sda2 second partition on first disk etc.

you can add a feature request on launchpad. perhaps they could make use of some linux command to read dos labels on install. it might come in handy...

---

### Post by wlsemmens on 2013-10-15
Thanks mastablasta, I've solved the black screen issue It is a nVidia chipset, which I did mention in my OP. I know that nVidia drivers are a closed book, but can the generic ones which seem to be available in the repository be added to the ISO and loaded if that chipset is detected?

You are correct in that the easiest way to identify these things is to do some preparation beforehand, from a novice moving over from Windows perspective, it can be quite daunting and many of these pitfalls have never been experienced by the average PC user, it could easily deter them. I'm now downloading and updating my system. Is there a way, to resize the desktop as the launcher is half on, and half off the screen and the menubar is totally off screen. I've tried most of the nVidia drivers from the repository and various screen resolutions, but, so far, nothing has worked.

---

### Post by mastablasta on 2013-10-15
reverse engineered opensource nvidia drivers are included in kernel. however some newer chipsets have proprietary drivers (made by nvidia) available for install. they are offered automaticly upon install if you are connected to internet. when you boot and see desktop - that's the opensource graphics driver. proprietary drivers can't be on CD for legal reasons i believe, which is why they are offered for download after install.

i find it now that install is easier if you do it form within live boot. as you can browse the disks in case you are not sure, identify them etc. or also ask on IRC for quick support. most users on ubuntu support channels will know answers to at least basic and most often asked questions. i was quite scared i would mess it when doing dual boot but luckilly it all worked out.

regarding the screen someone else with nvidia will know more. most certianly the desktop is customizable (resolution, size, place etc.) to a certain point. i also do not use Unity interface but Kubuntu as it is closer to Windows and KDE has (in my opinion) better programmes (though i use certain gnome stuff as well).
.

---

### Post by wlsemmens on 2013-10-15
Thanks for all your help masta, I could not do a live boot because of the nVidia issue it just would not let me get past the keyboard picture on the screen. I've finished downloading all updates and went into a restart as it requested, now the bloody thing freezes solid half way through the loading process the last line on the screen is
* Starting automatic crash report generation                    [ok]
and there it has sat for the last hour!!  I'm over it! Now looking for another Distro, Ubuntu, IMO has gone backwards.

---

### Post by NM5TF on 2013-10-15
> **wlsemmens said:**
> Thanks for all your help masta, I could not do a live boot because of the nVidia issue it just would not let me get past the keyboard picture on the screen. I've finished downloading all updates and went into a restart as it requested, now the bloody thing freezes solid half way through the loading process the last line on the screen is
* Starting automatic crash report generation                    [ok]
and there it has sat for the last hour!!  I'm over it! Now looking for another Distro, Ubuntu, IMO has gone backwards.

you might want to try Linux Mint.....derived from Ubuntu, but sleeker, quicker, more elegant, etc....and it has the Noveau
driver which works great with my Nvidia card....:D

and yes, I STILL use Ubuntu 12.04...and Mint 14....and Arch Linux....:o

just a thought

Tommy

---

### Post by whitesmith on 2013-10-15
> **wlsemmens said:**
> Why is it that the installer only shows the absolute drive name (sda, sdb, etc) but does not seem to show the volume name which would make it much easier installing on a system with multiple drives?Sorry you had installation issues. Put very simply the reason Ubuntu doesn't show volume labels is that labels are a vestige of Windows. Ubuntu derives from Unix, which goes back to 1968 or so. In those dark days storage was the responsibility of tape drives. Labeling a tape, except physically, makes no sense. That thinking hasn't really changed over the years. The nice thing is that after your system is operational, you are free to assign whatever labels you want to the drives in your system. There are 5 in mine, all with names suggestive of their purpose. If this is what you need, you can do the same. I concede that it would be marginally helpful for Ubuntu to recognize volume labels during installation to benefit those, like yourself, who are into dual-boot, and those, like myself, who have same make/same size volumes. Cheers to you and your wife!

---

### Post by oldfred on 2013-10-15
I made the mistake of skipping a port on motherboard. Drives then mount in port order, but if I plug in a flash drive and reboot that flashdrive becomes sdb as that is the missing port order drive. My sda never changes but all the rest may.
If you know serial numbers as shown by BIOS for mounting.
fred@fred-Precise:~$ sudo lshw -C Disk -short
```

H/W path             Device      Class       Description
========================================================
/0/100/1f.2/0        /dev/sda    disk        160GB MAXTOR STM316081
/0/100/1f.2/1        /dev/cdrom  disk        CD/DVDW SH-S183L
/0/100/1f.2/2        /dev/sdb    disk        160GB MAXTOR STM316081
/0/100/1f.2/3        /dev/sdc    disk        640GB WDC WD6400AACS-0
/0/100/1f.2/0.0.0    /dev/sdd    disk        60GB SSD G2 series 64

```

And you can label partitions with gparted when you create them, disk utility afterwards or using command line.
fred@fred-Precise:~$ sudo blkid -o list
```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    (not mounted)  04B05B70B05B6768
/dev/sda2  ext3    backup   (not mounted)  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    /media/SHARE   46CD-C9B2
/dev/sdb2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdb3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdb4  ext4    MavData  /media/MavData 431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdc1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdc2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdc4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdc5  ext4    rr_test  (not mounted)  299894c6-5c2e-4df7-b3ac-ae1dae0ce5c6
/dev/sdc6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdc7  ext4    xubuntu  (not mounted)  6314d8a8-060e-4c02-ad8c-3a2f70e2798b
/dev/sdc8  ext4    Test     (not mounted)  af29c61a-34e9-48eb-9c94-afcb4bb61582
/dev/sdc9  vfat    OLDG     (not mounted)  F6A6-705D
/dev/sdc10 ext4    newhome  (not mounted)  b8a7e331-a716-4ac1-bf58-6ac515606c6d
/dev/sdc11 swap             <swap>         09367687-86d1-4fd0-9b81-2787d3196159
/dev/sdc12 ext4    Puppy    (not mounted)  07e2a08d-37ca-4cf1-877b-f02b0eabcbca
/dev/sdc13 ext4    raring   (not mounted)  508cdeac-baed-4348-9d4f-0fbc315b5855
/dev/sdc14 ext4    kubuntu  (not mounted)  29624e3d-5d9d-4dd9-9f32-2aae54089a5e
/dev/sdc15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdc16 ext4             (not mounted)  ed61920f-fa6a-45a2-bd7c-3ae5502beeb7
/dev/sdc17 ext4    server   (not mounted)  63045773-e42a-46eb-9e96-b93428542527
/dev/sdc18 ext4    pp_test  (not mounted)  117e0c31-7e16-4e8b-90b7-a3c688a34f26
/dev/sdd1  vfat    EFI      (not mounted)  7B30-5ACA
/dev/sdd3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sdd4  ext4    Quantal  (not mounted)  94e634d0-39fb-4994-a685-8ee34747a240

```

---

### Post by QIII on 2013-10-15
Just by way of clarification:

aptitude and apt-get use many of the same processes behind the scenes and the differences between them have become fairly minor over the last few years.  You might say that aptitude provides some extra functionality that apt-get does not, but unless you use it you'd never know.

Both have been updated somewhat recently so that they use the same database of installed packages, so the old problem where you had to use one or the other exclusively to avoid one of them trying to install a dependency the other had already installed is mostly gone.

apt-get uses upgrade and dist-upgrade, aptitude uses what are probably the more understandable commands safe-upgrade and full-upgrade.  aptitude also performs some things like apt-cache and apt-mark, allows the why and why-not commands and does a better job of describing conflicts than apt-get.

aptitude might be considered something half way between apt-get and a full-blown, feature-rich GUI package manager like synaptic.  More features than the former, fewer than the latter.

I use apt-get out of habit and Synaptic when I want some really high end features.  I don't use Kubuntu's muon because in my experience it is a dog -- notice that I say "my experience", which means only that I haven't found it useful and effective.  Others probably love it.

Also...

Drivers, particularly graphics drivers, are sometimes frustrating to deal with.  You have to remember that in a Windows-dominated world OEMs spend most of their time making sure things go easily with Windows.  That is a wise business decision.  They can't spend the same amount of resources on Linux' 2% market share.  Microsoft does not support XYZ's graphics, although that is a common misconception.  Microsoft supports Microsoft.  The OEMs work very hard to make absolutely sure their products work with Windows so that their drivers can be put in the Windows driver-base -- which makes them "plug and play".  But this is important:  OEMs do that, not Microsoft.  OEMs have to earn the "works with Windows" label or they starve.  It's a simple matter of survival.

This doesn't make our lot in the Linux world any easier or the pain in the rear any less.  It just is what it is.  It's not that the Linux community hasn't bothered to make things work or to support XYZ's hardware.  Remember the relationship:  OEMs make their products work with OSes, not the other way around.

Still, it is definitely frustrating and it's a very understandable reason why many people simply turn away from Linux.  That is simply a matter of fact and does not reflect poorly on the efforts of Linux distributors.

Cheers.

---

### Post by wlsemmens on 2013-10-15
Thank you, all, for your comments. I am well aware of the history of the *nix operating systems having been working these silly boxes since the days of DOS. I am also aware of the OEM issues with development and the fact that volume labels are a, relatively, recent invention. I am currently burning a copy of AVLinux which, I hope, will fulfill my needs as a media server. I have shortlisted "mint" so will give that a try, if all else fails. I have not given up on Linux, per se, just Ubuntu, for now. My main "driver" complaint with Ubuntu is that I had a copy of 9.04 that worked "out of the box" on the same machine that I tried to install 12.x on. If the product worked back then, what has changed? Why? Yes, I know, newer hardware, etc.....(Rhetorical question) Thanks for your efforts people.

---

### Post by squakie on 2013-10-16
Just a small history:  nomodeset was added quite a while back to stop the kernel from automatically setting the video mode when that option was added to the kernel. This automatic mode setting (resolution and refresh rates) can result in combinations that the default video card (read "before drivers are installed") or the monitor or both can't display. 

Non-labeled tapes?  Well........back in the "old" days there were also OS's which offered a "catalog" of media - things like disks where in the catalog so the administrator took care of the physical placement while the programming staff just referenced it through this "catalog".  The same with tapes:  If you have rotating sets of backup tapes, would you like to track them manually?  Using this "catalog", tapes where prepared much like a disk drive and added to the catalog as part of a given set.  Again, only the administrator needed to worry about this.  The programmers, etc., referenced these sets either by actual set number or relative set number - no need to know the names of the tapes involved.  Replacing a tape in a set was invivisible to everyone else.  So, actually labeling a tape *did* make sense in some instances.

---

### Post by wlsemmens on 2013-10-16
Thanks for that info squakie. I've had limited success with AV linux, 'cept it would not load reliably at all when I tried to install it. In the end, it did nothing to the unusable version of Ubuntu that I had already tried. Currently I am attempting to install "Ultimate Linux". I actually got to see a splash screen before it displayed a pretty revolving arrow for the mouse cursor. Now that is all that I have. No Menus, No mouse button anythings!, even the keyboard will only change the shape of the arrow if I press <Ctrl><Alt><Esc> no other key combination seems to do anything. The DVD drive is still hunting, but this has been going on for about 1/2 an hour now. How can I install any version of Linux to a USB key from within Windoze as my Lappy is the only reliable machine that I have at the moment.

---

### Post by wlsemmens on 2013-10-16
Solved one problem, Found [This](http://linuxliveusb.com/) when searching for Linux mint, was very quick and painless to create a Linux USB Key in Windoze, now to find a Linux that works with my system.

---

### Post by verymadpip on 2013-10-16
Hi again.
If we had more information about your system  - CPU, RAM & the like - it may be easier to find something suitable for it.
Just a thought.

---

### Post by squakie on 2013-10-16
There at least used to be another boot option along the line of nomodeset which may help.  While it says 915, this used to work with several Intel chipsets:

i915.modeset=0
---- or if that doesn't work ----
i915.modeset=1

---

### Post by mJayk on 2013-10-17
"I installed windows 3.1 and it would not update to windows 8, therefore I am mad!!"

Seriously? you don't see what's wrong here?

---

### Post by Elfy on 2013-10-17
closed now you've joined just to rant

---

