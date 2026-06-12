---
title: "Kernel fails to load following a Synaptic smart update"
date: 2004-10-15
forum: Repositories &amp; Backports
---

### Post by AndyJ on 2004-10-15
I will repeat my problem in this forum as I have failed to find a solution using the Ubuntu Users list on the Ubuntu website.

I shut down my PC on Tuesday night after spending time on Ubuntu and 
everything was fine. When I tried to boot it on Wednesday evening, I 
received the following message:

VFS: Cannot open root device “hda5” or unknown-block (0,0)
Please append a correct “root=” boot option
Kernel panic: VFS: Unable to mount root fs on unknown-block (0,0).

As the PC had not been used since I shut down on Tuesday night, I can only assume one of the synaptic updates has caused a problem (I run smart updates every day). Either that or my hard-disk has mysteriously become corrupted at some critical spot. In case it helps I run the K7 version of the kernel.

The section of my Grub menu.lst in question is: 
root (hd0,4)
kernel /boot/vmlinuz-2.6.8.1-3-k7 root=/dev/hda5 ro quiet splash
savedefault
boot

Matt Zimmerman did point out in an initial reply that the initrd line is missing, and indeed he is right. He then asked me to run:

sudo dpkg-reconfigure linux-image-2.6.8.1-3-k7

and send the output. When I asked how I could run this when I can't boot into Linux, his reply was:

"How did you view the grub menu.lst file when you can't boot?

Same answer."

There are actually two answers to this, first is in Grub I can see and edit the boot commands from the menu.lst and the second is that I can mount my Linux partition in BeOS and read the file there.

I have very little real knowledge about Linux or Grub, but my assumption was that I would not be able to run dpkg-reconfigure before I have successfully booted, so can anyone tell me whether I am mistaken in this assumption. I surely can't run the command in BeOS against the Linux kernel (I'm pretty sure BeOS won't even recognise the command).

I have asked for additional help via the Ubuntu-users list and it has gone mysteriously quiet! I also asked whether it is possible to do a non-destructive, repair install of Ubuntu so that it would fix the bits that are wrong without wiping my existing data. I would have thought this should be possible and have seen at the partition selection stage that one of the options is use an existing partition without formatting it, but whenever I tried to use it, the install refused to continue.

Alternatively, is there perhaps a floppy disk image I could use to get past or resolve the problem?

In connection with the missing initrd issue, I read somewhere that there should be an initrd.img with a similar name to the kernel being used. In that case, I would have expected to find a file called initrd-2.6.8.1-3-K7.img or something like it somewhere, wouldn't I (given the name of my kernel file)? But I only find intrd.img on my root directory. My kernel images (and what appear to be closely related config files) are on my /boot directory.

Can anyone shed any light on all of this and help me resurrect me Ubuntu installation? :( 

All assistance greatly appreciated. With thanks in advance and regards,
AndyJ

---

### Post by stevho on 2004-11-10
> In connection with the missing initrd issue, I read somewhere that there should be an initrd.img with a similar name to the kernel being used. In that case, I would have expected to find a file called initrd-2.6.8.1-3-K7.img or something like it somewhere, wouldn't I (given the name of my kernel file)? But I only find intrd.img on my root directory. My kernel images (and what appear to be closely related config files) are on my /boot directory.

The missing initrd line is the reason for the VFS error.

The essential lines in grub.conf for Ubuntu (varies slightly for other distros) are:-

title  <whatever you want>
root ...
kernel ...
initrd ...

These may specify the full paths to the kernel and initrd images:-
title  <whatever you want>
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.8.1-3-386  root=/dev/hda5  ro
initrd  /boot/initrd.img-2.6.8.1-3-386

Or, assuming you have the correct symlinks in root:  /vmlinuz  and  /initrd.img  to the exact kernel and initrd.img in /boot - which you should have by default, you can simply say:-
title  <whatever you want>
root  (hd0,4)
kernel  /vmlinuz  root=/dev/hda5  ro
initrd  /initrd.img

PS: There's no need to put 'boot' since this is implicit in grub.conf.

---

### Post by LinuxDev on 2004-11-23
Hi all,

I have exactly the same problem, coming just after a synaptic update.
The problem is that I really needed to boot on Windows (dual boot), but as the Windows boot where not on the grub menu anymore, I made a "fdisk /mbr"  in order to boot on Windows.

So now I don't have grub anymore, and don't know how to reinstall it...so I tried to load the ubuntu kernel with the "loadlin.exe" utility, under a dos prompt, but still have the same errors :

VFS : cannot open root device "sda7" or unknown-block(0, 0).
Please append a coorect "root=" boot option
Kernel panic : VFS : unable to mount root fs on unknown-block(0, 0).

So, as I'm a beginner in Linux, could someone explain me what to do, please ? I couldn't reinstall grub or lilo with the ubuntu CD, it gave me something like "error, cannot install on a not clean target".

Thank you very much, and I would like to say that ubuntu looks to be a very good distribution, which works very fine on my laptop (not like Mandrake...), except that problem...

(sorry for my English...)

---

### Post by LinuxDev on 2004-11-24
If I had grub, I could manage to boot with your help, stevho, but now that I uninstalled grub, I don't know what to do to reinstall it again :( I can't install it again with the ubuntu CD.

I think the only way is to reinstall ubuntu, am I rigth ?

Thank you for any help, and sorry to bother you with my newbie problem....

---

### Post by az on 2004-11-24
Did synaptic finish it's update gracefully or did it say something about scrolling up to see the errors encountered...


What is happening to me is that when the kernel is part of the dist-upgrade and there are errors in the setting up of packages, everything stops and synaptic reports that there are errors, but is not really forthcoming to the nature of the errors.  In this case, it would seem that the old initrd is deleted before the new one is put into place (created by mkinitrd during the configurations of kernel-image-)  So you end up turning off your computer withtou an initrd for the next reboot.

---

### Post by darrell on 2004-11-24
to get back grub:

1. Boot into whatever other os you have available.

2. Download a small rescue distro of some sort (look on [http://www.distrowatch.com](http://www.distrowatch.com) for example) Any "live cd" distro will do (there are even some distros which fit on a floppy) - the smaller the better from a download time point of view. Just make sure the distro you pick includes grub.

3. Boot from your new CD/floppy into the rescue distro.

4. Mount your Ubuntu partition (or the distro might have already detected it and mounted it)

5. Make a backup of your Master Boot Record (MBR):
**dd if=/dev/hda of=/choose/some/path/mbr-backup bs=512 count=1**
you might want to do this twice, once putting the backup somewhere on your hard disk, and again putting it on a floppy, just in case.

6. type **grub**
at the grub prompt type **root (hdx,y)** - replace x and y to match the location of your Ubuntu partition,  eg if your Ubuntu partition is hda2, use **root (hd0,1)**; if it is hdb7, use **root (hd1,6)** - you see the pattern.
type **setup (hd0)**
type **quit**

7. now reboot from your hard disk - your grub menu should be back.

8. If there are any problems, you can reboot into your rescue/live distro, and put things back to how they were before you started following this recipe by restoring your backup of the MBR:
**dd  if=/where/you/put/it/mbr-backup of=/dev/hda bs=512 count=1**
type this very carefully, dd is a very powerful command, and you could trash your disk if you make a mistake in the above command. In particular, make sure the numbers (which mean 1 block of 512 bytes) are correct.

darrell

---

### Post by LinuxDev on 2004-11-24
azz  : you described exactly what happened to me, I didn't have inird image anymore after the update, I noticed that. I had a samba upgrade error. So thank you very much for the explanation :)

darrel : cool, I think I have a knoppix live CD, so thank you very much for your help, I'll try this evening if I have time. Thank you so much again ;)

Nice community ;)

EDIT : just to make sure that I understood : my ubuntu partition is on my SATA hdd : sda7, so, at the grub prompt, I should type :

root (sda0,6), is that correct ? thanks ;)

---

### Post by darrell on 2004-11-24
[QUOTE=LinuxDev]azz  : you described exactly what happened to me, I didn't have inird image anymore after the update, I noticed that. I had a samba upgrade error. So thank you very much for the explanation :)

darrel : cool, I think I have a knoppix live CD, so thank you very much for your help, I'll try this evening if I have time. Thank you so much again ;)

Nice community ;)

EDIT : just to make sure that I understood : my ubuntu partition is on my SATA hdd : sda7, so, at the grub prompt, I should type :

root (sda0,6), is that correct ? thanks ;)[/QUOTE]
 I've not any experience with SATA drives, but from a quick google, I understand that grub does not differentiate between SATA & IDE, so you should type (I think):

root (hd0,6)

the next command would be

setup (hd0)

If you have more than the one hard drive, and a mixture of IDE and SATA, I understand that the order in which grub detects the drives could be a bit random, so hd0 might not be your SATA drive. So before the above commands, try (at the grub prompt)

find /boot/grub/stage1

this should list the partitions where grub is found, so you can use this to set the correct drive identifiers in the "root" and "setup" commands.

In any case, the "root" command will tell you the type of partition it finds at the location you specified, and the "setup" command will complain if it can't find a grub installation there.

Note that the "root" command is specifying the drive and partition numbers. The setup command is specifying the drive only, as you are installing grub in the Master Boot Record of the disk.

Also remember to alter the dd commands for backup and restore (if needed) of the MBR to specify the correct device (/dev/sda from what you have said).

---

### Post by az on 2004-11-24
Is this what happened to you?

[https://bugzilla.ubuntu.com/show_bug.cgi?id=2492](https://bugzilla.ubuntu.com/show_bug.cgi?id=2492)

---

### Post by LinuxDev on 2004-11-24
Thank you, the grub commands worked fine ;)
But I've got a problem : I still don't have the initrd.img-2.6.8.1-3-386 file...
I have a initrd.img linked file but 0 size.

Can I download initrd.img-2.6.8.1-3-386 ? I tried dpkg-reconfigure etc...but as I was on a knoppix live CD, it couldn't work :)

Thank you again ;)

AZZ : I didn't have the time to see if I had this samba update bug, I'm sorry, I just saw an error in synaptic and rebooted just after...

---

### Post by darrell on 2004-11-24
glad that the grub stuff worked. Sorry I can't be much help on the initrd problem. I would think that you need to generate yourself a new initrd.img, probably using the mkinitrd command, but I assume you need to run this while in ubuntu - which you can't because it won't boot.  There might be a way to tell mkinitrd to use your ubuntu installation as a basis, even when running your knoppix distro, but I think for safety, one of the ubuntu gurus on here should give advice. I might have some ideas, but they might leave you in a worse state than before. Will follow the thread with interest though.

Perhaps it is possible to *chroot* to ubuntu from your knoppix system, then run *dpkg-reconfigure* or even remove and reinstall the kernel package. But please wait for someone who knows what they're doing to give advice. 

darrell

---

### Post by drmagoo on 2005-01-09
I am reading this thread with interest due to a very similar happening.

Scenario: synaptic smart update, last nite. today this error message:

Uncompressing Linux...Ok booting kernal.
Kernel panic: VFS: Unable to mount root fs on unknown-block (0,0).

I assume this means I am missing the initrd file. Am hoping there is a non-destructive way to restore this.

magoo

---

### Post by rnimz on 2005-01-30
I am going through the same thing (updated kernel (not samba) with synaptic and now both kernel versions are missing their respective initrd.img files. I think I can get the system up and running again since I can access it via the Ubuntu live CD I burnt, but I need a copy of the stock /boot/initrd.img-2.6.8.1-3-386 file in order to accomplish this. If I'm correct, I just need a copy of the stock install file, since I haven't done any modifications to the kernel. Is it possible for someone to tar.gz this file up and email it to me (reid@reidnimz.com) or is it possible to post it for download somewhere? Any help would be appreciated...

Reid

---

### Post by florizs on 2005-03-17
Help!
I have the same problem, I updated Ubuntu and had an Samba error,
I rebooted since I had to go Ubuntu won't boot and loading the newest kernel gives the error: Kernel panic: VFS: Unable to mount root fs on unknown-block (0,0).
loading the other kernels gives a "file nog found" error.

I have a dualboot system with WindowsXP but am in urgent need of my data on Ubuntu.
now I've come to the conclusion that my initrd line  is missing in the latest kernel and the older kernels won't boot in Grub. 
There is however a initrd.img file in the root directory.

I don't know what to do, since I have no way to reinstall my initrd file.
does anyone have some suggestions? 

I also have some questions and it could be very helpfull if someone would anwser them.

- will installing Hoary overwrite my data in /home/user/?
- is there anyway to install the initrd file via the live cd?
- what is the initrd file anyway?
- how come the old kernel/initrd file is deleted can't it be moved?

If someone could help this Newbie I'd be rather gratefull
tnx Florizs

---

### Post by paretooptimum on 2005-03-25
I would just like to add that one of my three ubuntu machines is having the same problem. Anyone have a solution?

---

### Post by florizs on 2005-03-25
I took a rather radical solution now,
I booted windows and copied my home to the NTFS partition.
then i switched to Hoary

Hoary is excelent, I recommend it to everyone

---

### Post by geppy on 2005-05-30
I'm running Hoary, and I've also been experiencing this problem.  I wasn't sure when the breakage occured, but when I moved my computer last Thursday, it would not boot up again.  I haven't had time to mess with it... I just backed up my other hard drive using Gnoppix and put on another Hoary install (which I'm currently using).  I have a little time now, so I've chrooted into my normal Ubuntu install, and I do indeed have a correctly-formatted /boot/grub/menu.lst, and I have an imitrd of 4.1 mb.

I had tried at first just booting to 2.6.10-3-386, which worked perfectly, aside from my inability to install the older nvidia module package (thank you, auto-magic package goodness), so I could not boot into X with 3d acceleration (and I was at a LAN party, so that was rather a bad deal for me).

I've tried 'dpkg install --reinstall linux-image-2.6.10-5-386', to no avail.  I'm now trying 'sudo dpkg-reconfigure linux-image-2.6.10-5-386', and if that does not work, I think that I might just try to chase down an older package of the nVidia package (it's bad form to use the nVidia installer in Ubuntu, doncha know).

Hrm, the 'sudo dpkg-reconfigure linux-image-2.6.10-5-386' just failed with:
[quote=bash]root@geppy:/ # sudo dpkg-reconfigure linux-image-2.6.10-5-386
/usr/sbin/dpkg-reconfigure: linux-image-2.6.10-5-386 is broken or not fully installed
[/quote]

I'm now trying 'sudo dpkg -i /var/cache/apt/archive/linux-image-2.6.10-5-386_2.6.10-34_i386'.  Hmph, it gives this:
[quote=bash]root@geppy:/var/cache/apt/archives # sudo dpkg -i linux-image-2.6.10-5-386_2.6.10-34_i386.deb
(Reading database ... 135950 files and directories currently installed.)
Preparing to replace linux-image-2.6.10-5-386 2.6.10-34.1 (using linux-image-2.6.10-5-386_2.6.10-34_i386.deb) ...
The directory /lib/modules/2.6.10-5-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.10-5-386 ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.10-5-386
Found kernel: /boot/vmlinuz-2.6.8.1-3-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.10-5-386 (2.6.10-34) ...
[b]/usr/sbin/mkinitrd: neither /dev/fd or /proc/self/fd exists!
Try mounting the proc filesystem: mount -tproc none /proc
Failed to create initrd image.
dpkg: error processing linux-image-2.6.10-5-386 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.10-5-386
[/b][/quote]

Well, 

/dev/fd is the "floppy device handler", or so says Google.  This is a silly reason for the kernel not to build the initrd image.

After 'sudo mount -tproc none /proc', the kernel seems to install perfectly.  I suppose that this wasn't the original problem, this is just a problem with it being chrooted into.  Anyhow, here's the new dpkg-reconfigure:
[quote=bash]root@geppy:/var/cache/apt/archives # sudo dpkg -i linux-image-2.6.10-5-386_2.6.10-34.1_i386.deb
(Reading database ... 135950 files and directories currently installed.)
Preparing to replace linux-image-2.6.10-5-386 2.6.10-34.1 (using linux-image-2.6.10-5-386_2.6.10-34.1_i386.deb) ...
The directory /lib/modules/2.6.10-5-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.10-5-386 ...
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.10-5-386
Found kernel: /boot/vmlinuz-2.6.8.1-3-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.10-5-386 (2.6.10-34.1) ...
cpio: (0xffffe000): No such file or directory
cpio:   /lib/ld-linux.so.2 (0xb7feb000): No such file or directory
Not touching initrd symlinks since we are being reinstalled (2.6.10-34.1)
Not updating image symbolic links since we are being updated (2.6.10-34.1)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.10-5-386
Found kernel: /boot/vmlinuz-2.6.8.1-3-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


[/quote]

And those are with different kernel packages residing in /var/cache/apt/archive/, with different md5sums.

Here I am, off to reboot and see how it goes.

---

### Post by geppy on 2005-05-30
That seems to have not changed anything.

---

### Post by zond on 2005-09-07
Have you tried to install the linux-arch pkg's??
I gues that linux-images pkg's install only the boot scripts and files, not the entire kernel with modules and etc.

If you are on an 386 arch, you should try installing linux-386...

Hope it helps.

---

### Post by RawMustard on 2005-09-09
[QUOTE=geppy]That seems to have not changed anything.[/QUOTE]

Hi, I'm at the same stage as you after performing an update last night to linux-image-2.6.10-5-686-smp_2.6.10-34.5_i386.deb.

Went through the same routine as you did after my machine failed to boot, all I get is a grub prompt and my pc speaker sreaching its tits off at me :(

Most disheartening to say the least, I've had to boot up the virus to try and get some sense of all this  ](*,)

---

### Post by Liz on 2005-09-10
[QUOTE=drmagoo]I am reading this thread with interest due to a very similar happening.

Scenario: synaptic smart update, last nite. today this error message:

Uncompressing Linux...Ok booting kernal.
Kernel panic: VFS: Unable to mount root fs on unknown-block (0,0).

I assume this means I am missing the initrd file. Am hoping there is a non-destructive way to restore this.

magoo[/QUOTE]
 i didnt get Kernel panic: VFS: Unable to mount root fs on unknown-block (0,0) error..mine is just stuck on " uncompressing linux...ok..booting the kernel  "

thats it....hope someone can help..id reinstall..but there are alot of files on there that we dont really want to lose...(mps3..my sons pc)

if anyones got any ideas...im listening.

---

### Post by FiliusVitae on 2005-09-10
It seems to me that the problem is the kernel.

have any of you tried booting the machine with a livecd (Gentoo, Knoppix or something), chrooting into the Ubuntusystem and compile a wery minimal static vanilla kernel just to get the machine booted and then reinstall a different kernelimage  with apt-get?

---

### Post by Liz on 2005-09-12
[QUOTE=FiliusVitae]It seems to me that the problem is the kernel.

have any of you tried booting the machine with a livecd (Gentoo, Knoppix or something), chrooting into the Ubuntusystem and compile a wery minimal static vanilla kernel just to get the machine booted and then reinstall a different kernelimage  with apt-get?[/QUOTE]

 i ended up going to ubuntu channel on irc and getting help there. we did try the liveCD but that didnt want to work properly without having to manually mount /proc folder and fussying around some. 

in the end, with help from robotgeek on irc, we used the  Ubuntu installation CD, booted into 'rescue' mode..got to a prompt, and went into /var/cache/apt/archives and sudo dpkg linux-image (previous kernel) and rebooted into that. 
no idea why the updated kernel wouldnt work on my sons pc, where as it works fine on mine. 

hope this helps someone else ..

---

### Post by kevzubuntu on 2005-09-13
[QUOTE=Liz]i ended up going to ubuntu channel on irc and getting help there. we did try the liveCD but that didnt want to work properly without having to manually mount /proc folder and fussying around some. 

in the end, with help from robotgeek on irc, we used the  Ubuntu installation CD, booted into 'rescue' mode..got to a prompt, and went into /var/cache/apt/archives and sudo dpkg linux-image (previous kernel) and rebooted into that. 
no idea why the updated kernel wouldnt work on my sons pc, where as it works fine on mine. 

hope this helps someone else ..[/QUOTE]

Could someone please direct me to a simple step by step guide to try fixing this without re-installing and losing all my data... as My dual boot sits at:

uncompressing linux...ok..booting the kernel 
_

using both grub normal and recovery menu item

... i think this happened after the latest auto upgrades. I have a Knoppix live cd but dont really know where to start fixing this and to be honest mentions of chrooting and  sudo dpkg linux-image from a live cd have lost me?

Thanks for any help

---

### Post by Liz on 2005-09-18
[QUOTE=kevzubuntu]Could someone please direct me to a simple step by step guide to try fixing this without re-installing and losing all my data... as My dual boot sits at:

uncompressing linux...ok..booting the kernel 
_

using both grub normal and recovery menu item
[/quote]

ooh, did someone manage to help kevzubuntu?
if you still need help, ill give it a go and try to explain how mine got fixed.

---

### Post by chunk on 2005-09-29
Why is this problem happening?

Alas, I was really enjoying ubuntu, but mysterious problems like these are why I stopped using Windows years ago. I guess I'll just need to stick with Kanotix.

---

