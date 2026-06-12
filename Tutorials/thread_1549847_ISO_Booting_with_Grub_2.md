---
title: "ISO Booting with Grub 2"
date: 2010-08-10
forum: Tutorials
---

### Post by drs305 on 2010-08-10
This page has been migrated to the Ubuntu Community Documentation site. For the most up-to-date information, please visit:
[https://help.ubuntu.com/community/Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot")

The above page is a sub-page of the main community documentation regarding [Grub2]("https://help.ubuntu.com/community/Grub2").

Thank you to all the users who posted in these threads and expanded our knowledge of Grub 2 since it's introduction.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?p=12073029](http://ubuntuforums.org/showthread.php?p=12073029) 

If you have a known working menuentry not posted on the community [Grub2/ISOBoot/Examples]("https://help.ubuntu.com/community/Grub2/ISOBoot/Examples") page please post it on that page. If you do not have write privileges on that page post the menuentry in the previous link.

**Support threads regarding the wiki and it's content should be created in a suitable forum.**

----

[center][size=4]**[COLOR="DarkRed"]ISO Booting with Grub 2[/COLOR]**[/size][/center]

This thread will detail how to place a menu entry in Grub 2 to allow booting an ISO file stored on your computer without a CD/DVD. Not all ISOs will work with Grub 2. The ISO must be constructed in a manner to allow this method of booting. Currently the Ubuntu family of Live CD ISOs (9.10 and later), Gparted CD, Parted Live CD, and SystemRescue CD, among others, support this feature. As pointed out by *Splooshie123* in Post 240, this method (as described) won't work with the Ubuntu Alternate Installation CD.

I have another thread which covers actually installing Ubuntu from an ISO booted from a Grub promtp. This might be useful for someone who can download the ISO but can't use a CD/DVD. That thread is located here:
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

I have received a report from YorYor in [Grub 2 Basics Post #642]("http://ubuntuforums.org/showpost.php?p=9820329&postcount=642") that at least some image files (.img) can also be booted by Grub 2. An example *menuentry* is included below.

**Note 1:** In addition to being able to use Grub2 to boot Ubuntu (and other) ISOs, **Multisystem** offers additional capabilities which the user may find helpful in booting and testing other OS's ISOs such as Fedora without installing the OS. Thanks to *seanbw* in Post #137 for calling attention to this app.

**Note 2:** I have written a guide on booting the Ubuntu ISO from the Grub *rescue prompt* in order to repair a previously-working installation. The guide also includes instructions on how to install Ubuntu from the rescue prompt via the Live CD ISO or via the Internet.
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")


Being able to mount an Ubuntu ISO via the Grub menu has the following advantages:
[LIST]
[*]There is no need to insert a CD/DVD.
[*]Boot times of the CD/DVD's ISO is normally faster than booting from an actual CD/DVD.
[/LIST]

**Downloading ISOs:**

Note: Users should consider using torrents to download the ISOs, especially after a new release when servers are likely to be very busy.

Here are a few sites from which users can download bootable ISO images:
[LIST]
[*]Ubuntu/Kubuntu/Edbuntu download mirrors:
_[http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors]("http://www.ubuntu.com/getubuntu/downloadmirrors#mirrors")_


[LIST]
[*]If you already know the name of the server and file, you can also download it via the command line. For instance:
```
wget http://ftp.ucsb.edu/pub/mirrors/linux/ubuntu/10.04/ubuntu-10.04-desktop-amd64.iso
```
[/LIST]

[*]SystemRescue CD:
_[http://www.sysresccd.org/Download]("http://www.sysresccd.org/Download")_
Notes: Opens to a command line. Type "wizard" to enable GUI. The GUI contains Firefox, terminal, gparted, file browser, cd/dvd burning, text editor.

[*]Gparted CD:
_[http://sourceforge.net/projects/gparted/files/gparted-live-stable/]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/")_
Notes: Screenshot, terminal, gparted. GUI.

[*]Parted CD:
_[http://sourceforge.net/projects/gparted/files/gparted-live-stable/]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/")_
Notes: Windows users will feel comfortable with this app. Gparted, system profiler/benchmark, PcManFM file browser, terminal, networking.

[/LIST]

**Where to place the ISOs:**

I prefer storing the ISO files on a non-system partition but for simplicity's sake in this post I will make a new folder in the system's /boot folder called "*iso*".  The ISO files will reside in the *sda1* partition in the */boot/iso* folder. In this example, the address of the ISO, translated so Grub2 understands, is: 
*(hd0,1)/boot/iso/<iso_filename>*

Since 'rescue CDs' such as Gparted are loaded into memory and use a self-contained version of linux, the format of the partition does not matter as long as it is one that Grub 2 can recognize. Additionally, the ISOs like Gparted's can be located on a system partition since the partition is not mounted. This allows the real partition to be resized even if the ISO is located in the same partition.

**The user will need to adjust the Grub menu entries to properly point to the correct partition and folder for their own situation.**


**[COLOR="DarkRed"]Notes on ISO locations[/COLOR]**
[LIST]
[*]**Separate /home folder:**  Many Ubuntu users have a separate HOME partition. If the ISO folder or file is placed in your HOME folder, be sure to use the correct path in the menuentry - do not include "/home" in the path. Since a separate /home partition is only mounted by fstab later in the boot process, Grub 2 will not find the file if the path is designated (hdX,Y)/home/*username*/iso/isofilename. 


[*]**Non-Linux Partitions:** If the ISO is stored on a non-Linux partition (NTFS, vfat, etc), the appropriate module must be loaded to ensure Grub2 can read the filesystem. An example of an added module as the first line below the *menuentry* follows. (See *ny6ga's* post #39 for a complete example)
> 
menuentry "Parted Magic" {
insmod ntfs
... continued ....

[/LIST]

[LIST]
[*]The correct Grub 2 path for an ISO file normally found in /home/*username*/iso/isofilename would be **[COLOR="DarkRed"](hdX,Y)/*username*/iso/isofilename[/COLOR]**, with (hdX,Y) being the partition of the separate HOME files and *username* being the user's login name.

[*]Example: / is on sda5, /home/drs305 is on sda10. The iso file is in folder "iso" and the filename is "maverick-desktop-i386.iso". When running Ubuntu, the file can be found at /home/drs305/iso/maverick-desktop-i386.iso.
In Grub 2, the address would be: (hd0,10)/drs305/iso/maverick-desktop-i386
[/LIST]

**To make the new folder in which to store the ISOs:**
```
sudo mkdir /boot/iso
```
Then copy the ISO file(s) as root to this new folder. 
*Note:* If you will have your ISO's stored on another partition, be sure the partition is mounted before copying files to the mount point.

To summarize, I have downloaded the ISOs, placed them in the */boot/iso* folder of the *sda1* partition. If I did a search for the Ubuntu Lucid ISO, it would be shown in:
> /boot/iso/ubuntu-10.04-desktop-i386.iso


**Customizing the menuentries:**

In the following examples, the user can change the title (between the quotation marks) on the *menuentry* line to whatever title is desired.

The filenames reflect the current release version of the ISOs mentioned previously. As newer versions are released the filenames will need to adjusted to reflect the newer filename.


**Making the Grub 2 entry:**

The following line is not necessary but provides feedback during the execution of "update-grub". It generates a line in the terminal when updating Grub to indicate that the 40_custom file contents are being added to the Grub2 menu:
> echo "Adding 40_custom." >&2
**Sample /etc/grub.d/40_custom file:**

**[COLOR="Navy"]The simple way to add entries.[/COLOR]** The easiest way to incorporate ISOs into the Grub2 menu is to add them to the */etc/grub.d/40_custom* file. Leave the [COLOR="Navy"]**existing lines**[/COLOR] in 40_custom as they are, and add the new entries below. The menu items will appear at the bottom of the Grub 2 menu. If you wish the items to appear first, name the menu "06_custom" and make the file executable. Items in "06_custom" will appear before linux and other OS menu items.

**[COLOR="Navy"]Manually creating the menuentry.[/COLOR]** If you create the entry manually, I recommend a slightly different format for the *menuentry*. Incorporating the *set isofile=* line to set the path and filename of the ISO file allows for easier troubleshooting and less confusion. It also allows the user to change only one entry if a file's name changes (e.g. version update). I thank forum user *oldfred*, who showed me this method. For entries not copied directly from the *grub.cfg* file:
> 
menuentry "**Lucid ISO**" {
set isofile="/boot/iso/ubuntu-10.04-desktop-i386.iso"
loopback loop (hd0,1)[COLOR="Navy"]$isofile
[/COLOR]linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=[COLOR="Navy"]$isofile[/COLOR] noprompt noeject
initrd (loop)/casper/initrd.lz
}



> 
[COLOR="Navy"]**#!/bin/sh**[/COLOR]
echo "Adding 40_custom." >&2
[COLOR="Navy"][B]exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.[/B][/COLOR]

menuentry 'ISO Precise ' 		{
isofile=ubuntu-12.04-desktop-amd64.iso
loopback loop (hd0,1)/iso/$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
menuentry 'Oneiric                      ' 		{
isofile=ubuntu-11.10-desktop-amd64.iso
loopback loop (hd0,1)/iso/$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/$isofile  noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry "**Lucid ISO**" {
loopback loop (hd0,1)/boot/iso/ubuntu-10.04-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry "**Karmic 64-bit ISO**" {
loopback loop (hd0,1)/boot/iso/ubuntu-9.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-9.10-desktop-amd64.iso noprompt quiet splash
initrd (loop)/casper/initrd.lz
}

menuentry "**Gparted Live ISO**" {
set isofile="/boot/iso/gparted-live-0.8.0-1.iso"
loopback loop (hd0,1)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
initrd (loop)/live/initrd.img
} 

menuentry "**SystemRescue CD ISO**" {
set isofile="/boot/iso/systemrescuecd-x86-1.5.8.iso"
loopback loop (hd0,1)$isofile
linux (loop)/isolinux/rescue64 setkmap=us isoloop=/systemrescuecd-x86-1.5.8.iso
initrd (loop)/isolinux/initram.igz
}

menuentry "**Parted Magic ISO**" {
set isofile="/boot/iso/pmagic-5.2.iso"
loopback loop (hd0,1)$isofile
linux (loop)/pmagic/bzImage iso_filename=$isofile boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
initrd (loop)/pmagic/initramfs
}

menuentry "Boot IMG - Seagate Tools" {
    linux16 /memdisk bigraw
    initrd16 /SeaTools.img
}

Courtesy of *cbowman57* in Post #54; with Clonezilla ISO located in sda9's root directory (/)
menuentry "**Clonezilla live**" {
set isofile="(hd0,9)/clonezilla-live-1.2.8-3-amd64.iso"
loopback loop $isofile
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

Modified from the post by *Dancer_69*
menuentry "**Gentoo 11** Live DVD" {
set isofile="/boot/iso/gentoo-livedvd-x86-amd64-32ul-11.0.iso"
loopback loop (hd1,6)$isofile
linux (loop)/boot/gentoo root=/dev/ram0 init=/linuxrc dokeymap looptype=squashfs loop=/image.squashfs cdroot initrd=/boot/gentoo.igz isoboot=/boot/iso/gentoo-livedvd-x86-amd64-32ul-11.0.iso
initrd (loop)/boot/gentoo.igz
} 

[LIST]
[*]***Run "sudo update-grub" after saving /etc/grub.d/40_custom to include the new entries into the Grub 2 menu.***
[/LIST]

**Persistence:**
See Post #254 by *NikTh* for information on making an ISO persistent. [http://ubuntuforums.org/showpost.php?p=11970546&postcount=253]("http://ubuntuforums.org/showpost.php?p=11970546&postcount=253")

**More ISO Menuentries:**

If you need to inspect the contents of an ISO for troubleshooting purposes, you can mount it while running a Linux OS with the following commands. You will make a mount point in */mnt* and then mount the ISO to */mnt/temp*. After mounting, you can use a file browser to inspect the contents of */mnt/temp*.
[LIST]
[*]One example of using the mount command to inspect the contents is to check the initrd file. In bootable Ubuntu ISOs (Karmic & later) the file is initrd.lz  In some other third-party ISOs, the file may be initrd.gz rather than initrd.lz.  
[/LIST]


```

sudo mkdir /mnt/temp
sudo mount -o loop /boot/iso/<filename.iso> /mnt/temp
*When you are finished:*
sudo umount /mnt/temp

```


This thread is an update of a closed Karmic Testing thread which was created during the early testing of Karmic and Grub 2:
_[http://ubuntuforums.org/showthread.php?t=1295506]("http://ubuntuforums.org/showthread.php?t=1295506")_


**More ISO Menuentries:**

If you would like to add examples of other ISO menuentries, please start the post with the OS or Utility Name and place the menu entry within "code" tags.

---

### Post by ranch hand on 2010-08-23
Got me going.  Great info, as always, and I am in love with the ability to boot the ISOs.

Thanks for this post.

---

### Post by danageis on 2010-08-25
Quick question:

I notice you said you use a non-system partition for your ISO's, and this makes sense to me.

I am currently running a multi-boot system with 2 partitions and an extended partition with 2 more partitions, and only have 1 ext4 partition for Ubuntu (I don't even have a swap partition right now).

I would really like to add GParted to my GRUB, but would it be ok to put the .iso on my Ubuntu system partition, considering I would be using the iso to resize the partition the .iso is in?

If this would pose a problem, how difficult would it be to create a new partition to store .isos for GRUB, for example what File System would it have to be for GRUB to recognize the disc images?

Thank you very much for any info you could give me regarding this.

---

### Post by drs305 on 2010-08-25
> **danageis said:**
> I would really like to add GParted to my GRUB, but would it be ok to put the .iso on my Ubuntu system partition, considering I would be using the iso to resize the partition the .iso is in?

If this would pose a problem, how difficult would it be to create a new partition to store .isos for GRUB, for example what File System would it have to be for GRUB to recognize the disc images?


The Gparted CD ISO appears to work without mounting the partition within which it is located. This means the ISO can be located in any partition, even one you wish to resize. 

I've always used ext3 or ext4, but I would assume that any format recognized by Grub2 would be acceptable, since the ISO is going to mount and use it's own file system for booting.

---

### Post by danageis on 2010-08-25
cool thank you very much for the quick reply. I followed your tutorial and installed a GPARTED live .iso into GRUB from /boot/iso and used it to shrink my current FAT32 partition and expand my Ubuntu partition to 12GB. thanks!

---

### Post by drs305 on 2010-08-25
> **danageis said:**
> cool thank you very much for the quick reply. I followed your tutorial and installed a GPARTED live .iso into GRUB from /boot/iso and used it to shrink my current FAT32 partition and expand my Ubuntu partition to 12GB. thanks!

Glad it worked. You posed some good questions which I hadn't addressed in the original post. I'm fighting a bad hotel Internet connection today but when I get the chance I'll include a mention of this topic in the original post.

---

### Post by ranch hand on 2010-08-25
I am glad the mounting of partitions was brought up.  I thought maybe I was just not seeing it right.

Hadn't tried it yet but, with great trepidation, was going to.  Now I will just have FUN.

---

### Post by ranch hand on 2010-08-27
I believe that I have to beg to differ with the idea that the drive is not mounted.

If you think about it the partition where the ISO is located MUST be mounted.  Trying to install from the ISO leads to failure due to mounted drives.

I do not think that I would partition from an ISO residing on the same drive.

Seeing that this is the Maverick UNE ISO and there have been problems with the new Ubiquity I am not at all convinced that installing from the ISO is a bad idea.  I will be copying the ISO to another drive and try it from there.

You will get a report.

---

### Post by drs305 on 2010-08-27
I was referring to the Gparted ISO regarding the mounting of the partition, but perhaps I didn't make that clear. At least Gparted doesn't show the partition as mounted, and I was able to resize the partition on which the ISO physically resided using the Gparted ISO. [Added: Perhaps it's possible for Gparted to umount the partition once it's running - I have no idea really.] I did it on a partition I was willing to trash, as I was uncertain of the results.

I did try installing via the LiveCD ISO soon after I learned how to mount it via Grub2, and as you experienced, I was unable to complete a normal install via this method. I belive I only tried this with 9.10.

---

### Post by ranch hand on 2010-08-27
I think I can install the bugger if I use a good ISO from a different drive.  I do not have one of those new fangled thumb drives.  Might be time to see if I can get somewhere they sell them.  Seems the perfect place for ISOs and something to boot from.

I can't see how you can boot an ISO from a drive with out that drive mounted.  The partition has to be mounted.

You can use Gparted from a mounted drive.  I just do not think it is something that I want to do.  I am really good at screwing things up anyway and do not feel I need any help from gparted or any other partition editor.

---

### Post by ranch hand on 2010-08-28
Yuppers, it is installing.  Do not know if it will complete but that is the shaky nature of the new Ubiquity not booting to the ISO.

About 33% done now.

This will work.  Seems a lot simpler than the USB creator or burning a CD/DVD (faster by far than the CD).

This installer is fragile yet.  Clicked, under Unity, on it and got to the partitioner tried to select a partition and it logged out.  fine with me as the Unity desktop doesn't reallly work for me.  Logged into the Ubuntu desktop.

Got to the partitioner and the installer just quit and disappeared.

Opened in terminal and it is still going.

This booting to the buggers is great.

---

### Post by danageis on 2010-09-04
Hi one quick question, can you explain the syntax of the loopback command? I am trying to do this with the 10.10 Ubuntu Netbook Beta 1 iso and I have tried copying it as the 10.04 entry and it does not work.

---

### Post by drs305 on 2010-09-04
> **danageis said:**
> Hi one quick question, can you explain the syntax of the loopback command? I am trying to do this with the 10.10 Ubuntu Netbook Beta 1 iso and I have tried copying it as the 10.04 entry and it does not work.

I do not know if the Netbook ISO is constructed to allow Grub2 booting. Hopefully someone who has used the Netbook ISO can tell us.

As far as the syntax:
(hdX,Y) is the partition on which the ISO file file resides. The first drive is 0, the first partition is 1. So if you have the file on sdb4, it would be (hd1,4).

The next section is the path and filename. The path starts with **/**, which would be the root directory the the designated (sdX,Y) partition. If the file is located in the root folder, the address would be (hdX,Y)/<filename>

If the file was in the /myfiles folder of the partition, the address would be (hdX,Y)/myfiles/<filename>

If you aren't sure if you have the correct address, at the Grub2 menu, you can press "e" to examine the highlighted menuentry. Note the address of the ISO file, then press ESC to return to the main menu and then "c" to get to the Grub2 command prompt. 

You should then be able to type the following, press ENTER, and see your ISO file:
```
ls (hdX,Y)/<path>/
```

As I mentioned at the start of this post, it's possible the netbook version doesn't support Grub booting. It also may be that it is still using initrd.**gz** instead of initrd.**lz**. You can check for this by mounting the ISO with the "sudo mount -o loop /path/isoname /mountpoint" in a running Linux system and checking the contents of the /boot folder.

---

### Post by lombaardcj on 2010-09-06
Thank you so much for this short and concise tutorial to Grub 2 and loading iso's.

I could not load the iso in my home directory until I read a line in your Howto "**[COLOR=DarkRed]Note on placing ISO's in a separate /home folder:[/COLOR]**"

This is where my problem was.  Could not get any other tutorials working?

GREAT INFO!

Another happy user.  No more CD-burning required.

---

### Post by the8thstar on 2010-09-06
Hello,

I am trying to follow your tutorial to install FreeBSD instead of Linux. Do you have any idea what the syntax should be, FreeBSD not being Linux?

Thanks for your help and time.

---

### Post by drs305 on 2010-09-06
the8thstar,

I've never used FreeBSD so I went to the web site and downloaded a couple of the ISOs. It isn't packaged like Ubuntu, so I chose the amd version of the *livefs* ISO and the *bootonly* one. 

When I mounted it and inspected the contents it doesn't appear to match the way Ubuntu ISOs are constructed. 

That doesn't mean it isn't possible - I just don't know enough about it to tell you if it can be done. You will have to wait and see if someone else replies with a way to do it.

---

### Post by RobHK on 2010-09-09
I'd really like to be able to do this but I can't get it to work.

I have Linux Mint 9 Fluxbox (based on Ubuntu 10.4). I tried to install PartEd Magic. I copied your code and changed the version number and the partition number. I have my image on sda7. I saved 40_custom and ran update-grub. grub.cfg has updated correctly. Here is the relevant bit:
```
### BEGIN /etc/grub.d/40_custom ###
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Parted Magic ISO" {
loopback loop (hd0,7)/boot/iso/pmagic-5.4.iso
linux (loop)/pmagic/bzImage iso_filename=/boot/iso/pmagic-5.4.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt
initrd (loop)/pmagic/initramfs### END /etc/grub.d/40_custom ###

```

I was puzzled that you said partition numbers began at 1. I thought they began at 0, like disk numbers. But I tried both (hd0.7) and (hd0,6).

I also tried to install the new Debian version of Mint, but that failed too.

---

### Post by drs305 on 2010-09-09
> **RobHK said:**
> 

With Grub2, the counting scheme changed. Drives still start with 0, but partitions now start with 1. It's just to keep everyone on their toes I suppose. ;-)

With the menuentry you provided, it should work if the image is located on sda7 and the ISO file is located in that partition's /boot/iso folder.

I don't know if it's a cut/paste thing, but the last part of your *menuentry* should be:

[QUOTE]
initrd (loop)/pmagic/initramfs
}
### END /etc/grub.d/40_custom ###


---

### Post by ranch hand on 2010-09-09
Actually if that cut/paste is complete the entry should be;
```

menuentry "Parted Magic ISO" {
loopback loop (hd0,7)/boot/iso/pmagic-5.4.iso
linux (loop)/pmagic/bzImage iso_filename=/boot/iso/pmagic-5.4.iso boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt
initrd (loop)/pmagic/initramfs
}

```
Note the }.  That is where it needs to be.

I noticed that as I am really good at not having it there when I cut/paste things to the custom file.
The "### END /etc/grub.d/40_custom ###" should not be in that line at all but below the }.

---

### Post by RobHK on 2010-09-09
Thanks to both of you. It's my bedtime, but I'll give it another go tomorrow.

---

### Post by RobHK on 2010-09-11
The "}" was indeed the problem. I missed it out when copying.

Parted Magic is now up and running. I can't get the Live DVD to work, but I'm not trying any more. Since it will only be needed once, I burned it to a re-recordable disc. Having PM available on tap is useful though.

Thanks again.

---

### Post by karmila on 2010-10-18
Hi drs35, great tutorial!

I tried this tutorial on my pc, since my motherboard don't have ability to boot from usb, it will save much cd's for each new install.

But i got this message when i tried to boot to iso from grub2.

> Busybox v1.13.3
(initramfs) could not find the ISO /iso/ubuntu-10.10-desktop-i386.iso 
This could also happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of removable device without first unmounting or ejecting it 
To fix this, simply reboot into Windows let it fully started, log in, run 'chkdsk /r', then gracefully shutdown and reboot back into Windows. After this you should be able to reboot again and resume the installation.

I'm sure that i have put the path correctly and tried different iso too but still got this error message. I don't have windows installed.

Is it bios related?

---

### Post by ranch hand on 2010-10-18
I, for one, are glad to here you do not have MS installed on your box.

Two questions;
Is the ISO  on your / partition?
Is it owned by root?

If the answer to both is true then I have not got a clue.  If the answer to either one is false then you need to fix it so it is true.

I know this for a fact as they are mistakes I made.

I use  a / and a /home partition and tried to boot with the entry pointing at my root  partition (OK, so I am simple).

I had left the permissions as they are normally (owned by user).  This will not work as grub is looking for a root file.

To fix both of these I created /etc/aa just for ISOs.  You can't put anything in there except as root, gives me an easy target  to point the menu entry at.

---

### Post by drs305 on 2010-10-18
An easy way to troubleshoot this (well, a not difficult way) is to go to the Grub prompt and try to 'loop' the file.

But first, from the error message, the system is looking for the file in */iso*, meaning that the ISO is located in the *iso* file under the main folder (for example: /iso/ubuntu-10.10-desktop-i386.iso). Is that where it is?

Back to the first paragraph. At the grub prompt (press "c" from the Grub menu) and load the first part of your current *linux* line:
> 
loopback loop (hdX,Y)/<path>/filename.iso

Enter the full path and ISO name.
Example:
loopback loop (hd0,5)/iso/ubuntu-10.10-desktop-i386

Repeat the procedure for the *linux* line. You only have to enter the line through *vmlinuz* before pressing ENTER.
Then do the same for the *initrd* line.
Watch for errors indicating an improper path or invalid or missing file name.

If you have the correct address and ENTER, nothing will happen. If you don't have the correct address, it will say "error: file not found" in which case you have to experiment with the address until you find the correct one.

And, as *ranch hand* notes, if it's in a separate /home folder it can cause confustion. There is a special note in the first part of the guide.

If the command above works the first time, the next thing to check is the *boot=* part of the linux line. (Note is is ***b**oot* and not ***r**oot*. It should normally be "casper". You can inspect the CD's contents from the LiveCD by mounting it and opening a file browser.

If the ISO is on your Desktop:
```
sudo mkdir ~/Desktop/iso
sudo mount -o loop ~/Desktop/ubuntu-10.10-desktop-i386.iso ~/Desktop/iso
nautilus ~/Desktop/iso
```
See if the *casper* folder exists, and if so, that it contains the vmlinuz and initrd.**lz** files.  Note in recent releases it is initrd.**lz**. Older versions were initrd.**gz** Make sure your initrd line matches what is contained in the *casper* folder.

---

### Post by karmila on 2010-10-18
> **ranch hand said:**
> I, for one, are glad to here you do not have MS installed on your box.
:)
> Two questions;
1. Is the ISO  on your / partition?
2. Is it owned by root?
1. Yes, I put the iso at /boot/iso.
2. So, the answer is yes.

My ubuntu partition is at sda2, then i set this on /etc/grub.d/40_custom[I]
menuentry "Maverick ISO" {
loopback loop (hd0,2)/boot/iso/ubuntu-10.10-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-10.10-desktop-i386.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}[/I]

I have tried another iso (Lucid) but still got the same error.

---

### Post by drs305 on 2010-10-18
Edit: See *oldfred's* next post.

karmila,

I duplicated your entry and it worked for me. The only two things that come to mind are the filename (-i386 vs -amd64 or 10.04 vs 10.10) or a filesystem problem. You could also try moving the ISO to another location, such a / or better yet onto another partition.

Assuming the filename is correct, you might boot a LiveCD and do a filesystem check via Disk Utility or command line. You can also just set the system to do one automatically on the next boot with the following command:
```
sudo touch /forcefsck
```

---

### Post by oldfred on 2010-10-18
I think you are missing a /boot

[I]menuentry "Maverick ISO" {
loopback loop (hd0,2)/boot/iso/ubuntu-10.10-desktop-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=[COLOR=Red]/boot[/COLOR]/iso/ubuntu-10.10-desktop-i386.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}[/I]


To make sure you have the same path I prefer this style using a set isofile - example from mine that worked:

menuentry "Ubuntu 10.10 Maverick ISO 64bit" {
    set isofile="/boot/iso/maverick-desktop-amd64.iso"
 
    loopback loop (hd0,2)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

---

### Post by karmila on 2010-10-19
drs305 thanks,

Here is my report:
**1. I 'loop' the file with no error**
My input lines are:
```
loopback loop (hd0,2)/boot/iso/ubuntu-10.10-desktop-i386.iso
linux (loop)/casper/vmlinuz
initrd (loop)/casper/initrd.lz
```

**2. boot= part is fine**
I mounted the iso and all necessary file are exist.

**3. Still can't boot iso from grub**
I once again tried boot the iso and still got the same error also when i change directory the iso to /etc/aa like ranch hand did (yes i had moved the iso to that folder and update-grub :P)
It produces the same error message:
*...could not find the ISO** /iso**/ubuntu-10.10-desktop-i386.iso... *
but this time with an extra line (or maybe i forgot to write it  down before) after (initramfs)
*(initramfs) /scripts/casper_premount/20iso_scan: line 46: Can't open /dev/sdc: No medium found.* 

sda= my primary HDD
sdb= my secondary HDD
sdc= should be my DVD (Not automatically mounted on start up) << Is it related?

---

### Post by karmila on 2010-10-19
Thanks oldfred... I missed that :KS
I don't know if this is only happen to me but i copied the lines from the first post:confused:

Now, i can successfully boot the iso from grub, and it is fast!

I thank You all for helping me. drs305, ranch hand, and oldfred :popcorn:

Since now I can boot the iso, here is my question:
Can I do install ubuntu with this boot method at existing partition or new partition?

---

### Post by oldfred on 2010-10-19
I always thought you had to use a different partition. I know gparted will not let you edit the partition you are in. But someone claimed it worked to install over itself, but I do not believe it would work correctly.

---

### Post by drs305 on 2010-10-19
> **karmila said:**
> Thanks oldfred... I missed that :KS
I don't know if this is only happen to me but i copied the lines from the first post:confused:

Now, i can successfully boot the iso from grub, and it is fast!

I thank You all for helping me. drs305, ranch hand, and oldfred :popcorn:

Since now I can boot the iso, here is my question:
Can I do install ubuntu with this boot method at existing partition or new partition?

The problem is as *oldfred* states that the mounting of the partitions becomes a problem. However, over the past weekend I spent quite a bit of time tinkering with this and think I found a way. Although you have to force unmount the /isodevice, it worked on my system.

The instructions are at the end of the guide I posted called [HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293").

Look at the section "Install Ubuntu - From Live CD ISO". I really would like someone to try it and let me know if it works for them. If you have enough RAM, you shouldn't have to force unmount the isodevice, but I have 3GB found by the default ISO kernel and apparently it wasn't enough. And you don't really need to accomplish all the previous procedures, since the post assumes a broken procedure to start with.

---

### Post by karmila on 2010-10-19
:P

I already read your another thread, [HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293"), before i read your post above. :)

And i had followed the instructions on the thread, since i have only 2GB of RAMs, toram-- option won't work for me. Then I unmounted the /isodevice, *sudo umount -l -r -f /isodevice*, click install and then :guitar:
The installation worked smoothly. Yeah it's cool, now i can install and reinstall dev-release without spend much cd's.

I installed ubuntu at sda6 and /isodevice is under sda2 :popcorn:

---

### Post by drs305 on 2010-10-19
> **karmila said:**
> And i had followed the instructions on the thread, since i have only 2GB of RAMs, toram-- option won't work for me. Then I unmounted the /isodevice, *sudo umount -l -r -f /isodevice*, click install and then :guitar:
The installation worked smoothly. Yeah it's cool, now i can install and reinstall dev-release without spend much cd's.


Thanks for the feedback. I'm still not comfortable with having to force unmount /isodevice but guess I'll have to live with it. 

In my searches I did find one mention that "iso-scan" would not allow unmounting, which seems to be true. I couldn't find another method (findiso, isofrom, etc) which would run the ISO, let alone allow an install.

---

### Post by karmila on 2010-10-19
> **drs305 said:**
> Thanks for the feedback. I'm still not comfortable with having to force unmount /isodevice but guess I'll have to live with it. 

Is it any possible problems with it, or it is "just not elegant"?

---

### Post by drs305 on 2010-10-19
> **karmila said:**
> Is it any possible problems with it, or it is "just not elegant"?

I have not found any problems and don't foresee any. First, you are forcing the unmounting of an ISO boot whose files are not stored, so they can't really be damaged. Secondly, the installation is going to be independent of the *isodevice* and installer, so the same thing applies. 

I thought the installer might crash at some point after forcing the unmount but I've tried it several times and each was successful.

I wanted to allow the installer to be able to unmount the device, but in reality you can unmount *isodevice* before you even start the installation so you are never even presented with the request.

---

### Post by walterav on 2010-12-21
What about chainloading the actual isolinux bootloader and its menu from the .iso file, instead of directly loading the kernel and init files from the grub2 menu? 

Will the loop still work or will the isolinux menu come up but won't boot any parameters because of not find its kernel or init files outside the loop function of grub2.

---

### Post by drs305 on 2010-12-23
> **walterav said:**
> What about chainloading the actual isolinux bootloader and its menu from the .iso file, instead of directly loading the kernel and init files from the grub2 menu? 

Will the loop still work or will the isolinux menu come up but won't boot any parameters because of not find its kernel or init files outside the loop function of grub2.

I played with that idea a bit but wasn't able to get it working. That's not to say it's not possible. The holidays and other things  have me a bit busy at the moment. Perhaps it will become a 'rainy day' project when I can spend some time testing the concept.

---

### Post by walterav on 2010-12-28
> **drs305 said:**
> I played with that idea a bit but wasn't able to get it working. That's not to say it's not possible. The holidays and other things  have me a bit busy at the moment. Perhaps it will become a 'rainy day' project when I can spend some time testing the concept.

Old IDEA:
Booting to the other isolinux.bin might indeed be possible, but getting it to boot the kernel/init from within the grub2 loop-iso it came from, will require some sort of patch to isolinux.bin so it understands that it has been loaded from a loopfile. Like you already figured out, right now it does not work. It will probably load isolinux.bin into the memory but that unknowing version will not find the rest of the files from the loop-iso but will search them on the iso9660 content directly on the filesystem of the CD/DVD.

New IDEA:
Chainloading isolinux.bin from the same iso9660 filesystem on which grub2 booted from, and adding the kernel/initd files all onto the same file-system/directory structure so no multiple *.iso files all non-conflicting files in one filesystem. 
Any experience with that, except for the possible conflicting /casper/ locations.

---

### Post by n6yga on 2011-01-01
I was able to get this working with Parted Magic. However, I had to add a special line:

```
menuentry "Parted Magic ISO" {
	insmod ntfs
	set isofile="/boot/iso/pmagic-5.8.iso"
	loopback loop (hd1,3)$isofile
	linux (loop)/pmagic/bzImage iso_filename=$isofile boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt
	initrd (loop)/pmagic/initramfs
}

```

If you notice, I had to add "insmod ntfs." Otherwise, grub2 could not locate the files on my partition. 

I have a dual-boot system with one common partition and that's where I put the /boot/iso folder.

So, it works flawlessly for me, at least in the context of Parted Magic.

Good job, guys!!!


Mark.

---

### Post by drs305 on 2011-01-01
> **n6yga said:**
> I was able to get this working with Parted Magic. However, I had to add a special line:

```
menuentry "Parted Magic ISO" {
	insmod ntfs
	set isofile="/boot/iso/pmagic-5.8.iso"
	loopback loop (hd1,3)$isofile
	linux (loop)/pmagic/bzImage iso_filename=$isofile boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt
	initrd (loop)/pmagic/initramfs
}

```

If you notice, I had to add "insmod ntfs." Otherwise, grub2 could not locate the files on my partition. 

I have a dual-boot system with one common partition and that's where I put the /boot/iso folder.

So, it works flawlessly for me, at least in the context of Parted Magic.

Good job, guys!!!


Mark.

Thanks for the feedback. I'll put a note in the original post that if the iso is stored on a non-Linux partition the appropriate module must be loaded.

---

### Post by wwarsin on 2011-02-17
Thanks for posting this great tutorial but i am currently not able to get it to work, maybe someone can help?

I currently have a 16GB flash drive partitioned with 
1 10GB fat32
1 5.3GB EXT4
1 700 swapfile

I currently have ubuntu installed on the ext4 partition and i have some ISOs in the fat32 partition i edited the 40_custom file to include this:

```
menuentry "Backtrack ISO" {
insmod vfat
set isofile="/ISO/backtrack/bt4-r2.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
} 
```
and i keep getting the error file not found, if i go to the grub command line i can ls the file by doing this:
```

grub> ls (hd0,1)/ISO/backtrack
bt4-r2.iso
```

I have tried to do different things (adding quotes, getting rid of the variable isofile) but cannot get this to work at all, anyone see what i am doing wrong?

---

### Post by drs305 on 2011-02-17
> **wwarsin said:**
> Thanks for posting this great tutorial but i am currently not able to get it to work, maybe someone can help?

I haven't used BackTrack. One thought is that it might use initrd.gz instead of initrd.lz. You can find out by mounting the .iso file and inspecting the contents. You should probably also check to see if the *vmlinuz* and *initrd* files are located in the "casper" folder:
```
sudo mount -o loop /*path*/bt4-r2.iso /*mountpoint*
```

---

### Post by wwarsin on 2011-02-17
> **drs305 said:**
> I haven't used BackTrack. One thought is that it might use initrd.gz instead of initrd.lz. You can find out by mounting the .iso file and inspecting the contents. You should probably also check to see if the *vmlinuz* and *initrd* files are located in the "casper" folder:
```
sudo mount -o loop /*path*/bt4-r2.iso /*mountpoint*
```

Ah thanks! It now 'tries' to boot, but i get an error (the error repeats about 20 times): 
```
NTFS volume version 3.1.
NTFS volume version 3.1.
EXT3-fs (sdb6): error: couldn't mount because of unsupported optional features (240)

```
I'm not sure what the problem is, i have tried adding 
insmod ntfs
insmod ext3
insmod ext4
but it still gives the same error...

This is what my 40_custom file looks like:
```

insmod vfat
set isofile="/ISO/backtrack/bt4-r2.iso"
loopback loop (hd0,1)$isofile
linux (loop)/boot/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop/boot/initrd.gz
```

Not sure if this is a grub error or a backtrack boot error...

---

### Post by drs305 on 2011-02-18
> **wwarsin said:**
> Not sure if this is a grub error or a backtrack boot error...

I spent a bit of time searching around but still don't have a solution. It's not a G2 error; it's a problem with Backtrack and ext4. If you do a search on "backtrack ext4 240" you will see you are not alone. 

I tried using "rootfstype=ext4" as a kernel parameter, and even tried "toram" with the filesystem.squashfs but I couldn't get anything to work. As the system boots, I believe it's looking at each partition and generating an error because of the ext4.  It fails when it finds ext4 partitions. It's possible there is a switch or setting that could prevent the search of all disks, but I haven't been able to come up with it.

There is a BackTrack linux forum. You may be able to find the answer there. The problem has been around for quite a while, and I find it hard to believe ext4 support is not built in to the ISO, but that is where my searching leads me.

If you find a solution please post back.

---

### Post by wwarsin on 2011-02-19
> **drs305 said:**
> I spent a bit of time searching around but still don't have a solution. It's not a G2 error; it's a problem with Backtrack and ext4. If you do a search on "backtrack ext4 240" you will see you are not alone. 


Thanks for looking for a solution, after quite a bit more searching and just trying different things i still haven't got it to work. I might try to reinstall Ubuntu on an EXT3 partition (or can you downgrade from 4?) and maybe that will work...

---

### Post by drs305 on 2011-02-19
> **wwarsin said:**
> Thanks for looking for a solution, after quite a bit more searching and just trying different things i still haven't got it to work. I might try to reinstall Ubuntu on an EXT3 partition (or can you downgrade from 4?) and maybe that will work...

I have not experimented with downgrading ext4. A problem may be that, in my testing, an error was generated with every ext4 partition on my drive, not just the Ubuntu one. So it's possible that unless all your partitions are ext3 or perhaps vfat/ntfs you may still run into the problem. 

I think I'd try any forum which deals with BackTrack before I risked changing the formatting of my partitions.

---

### Post by Jack Smith on 2011-02-19
Excellent tutorial, thank you drs305.  :biggrin:

---

### Post by drs305 on 2011-02-21
After much tinkering and searching for ext4 solutions, I think I happened across the major stumbling block with BT4. After extracting the files from squashfs I found Grub legacy, who's files as written do not support ISO  booting from the Grub2 menu.

I'm playing a bit with replacing the ISO boot contents with G2, but probably won't spend enough time to complete the experiment.

---

### Post by pindar on 2011-02-23
I'm new to this, but I find this fantastic! I have a macbook with a broken CD drive, and I found it extremely difficult to find a solution for booting it from a usb stick, but I've now got this working with an EFI partition and grub2 installed on that and a large data partition which holds the iso. So far, I have been able to boot ubuntu maverick from iso (and linux mint Julia, which is based on maverick). I have not had any success with a daily build for natty though. Using the same commands from the grub command line:
```

insmod iso9660
set root=(hd1,msdos2)
loopback loop /natty.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/natty.iso noeject noprompt
initrd (loop)/casper/initrd.img
boot
```
will reboot the computer right away; if I enter these commands with a maverick iso, it boots to a full desktop. Same thing happens with a debian iso. So my question is: has anyone tried this with anything else than ubuntu maverick? And been successful? 

Thanks

pindar

---

### Post by cbowman57 on 2011-02-23
I'd prefer to keep my iso's on a non-system partition as well.

Would you please post an example of what you use to help clarify.

TIA

---

### Post by drs305 on 2011-02-23
> **pindar said:**
> I have not had any success with a daily build for natty though.
pindar

This is what I'm using to boot the Natty ISO:
> menuentry 'ISO Natty'                        {
loopback loop (hd1,6)/iso/natty-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/natty-desktop-amd64.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}


The only thing I recall being different in Natty was that the filename isn't the same format as formally released versions. 


@ cbowman57,

The above example is an image file (ISO) located on a separate partition (sdb6) in the /iso folder (/iso/natty-desktop-amd64.iso).

---

### Post by pindar on 2011-02-24
drs305,

that's exactly the code I use (albeit from the grub command line) to boot natty, and the code which boots maverick successfully; with natty, my macbook simply reboots and puts me at the grub screen again. But I know that macs are pretty capricious about this issue, unfortunately. Thanks a lot!

pindar

---

### Post by drs305 on 2011-02-24
> **pindar said:**
> drs305,

that's exactly the code I use (albeit from the grub command line) to boot natty, and the code which boots maverick successfully; with natty, my macbook simply reboots and puts me at the grub screen again. But I know that macs are pretty capricious about this issue, unfortunately. Thanks a lot!

pindar

Does your grub.cfg file load the EFI module (or some other Mac-specific modules)? If so, they may be preloaded by the time you get to the Grub2 menu/command prompt, which is why you can boot from the command line. You can see which modules are loaded from the grub prompt with "lsmod".

It might be as simple as having to load a module, but I'm afraid I have no experience with Grub2 and Macs.

---

### Post by cbowman57 on 2011-02-25
Thanks drs305,

My goal was a bootable clonezilla, with your help and after fixing a couple typos from the clonezilla site I was successful.  This is my entry for anyone that might benefit, it boots from my maintenance partition located on sda9.

menuentry "Clonezilla live" {
set isofile="(hd0,9)/clonezilla-live-1.2.8-3-amd64.iso"
loopback loop $isofile 
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

---

### Post by drs305 on 2011-02-25
cbowman57,

Thanks for the input. I've placed your Clonezilla example in the list in the first post (with attribution of course). :-)

---

### Post by cbowman57 on 2011-02-25
It would appear that something changed with the most recent releases of GParted.  I keep getting a runaway loop error relating to a module binfmt-464c.  Does this indicate that I need to add an insmod entry?  I have all my partitions formatted to ext4 but it makes me wonder if the ISO is using something different internally.

---

### Post by drs305 on 2011-02-25
> **cbowman57 said:**
> It would appear that something changed with the most recent releases of GParted.  I keep getting a runaway loop error relating to a module binfmt-464c.  Does this indicate that I need to add an insmod entry?  I have all my partitions formatted to ext4 but it makes me wonder if the ISO is using something different internally.

The only time I've run into this error is when there is a discrepancy between 32 and 64 bit architectures. Is it possible you are using a new ISO architecture? There are probably other reasons that message would be generated and a search might find the reason it's happening on your system.

---

### Post by cbowman57 on 2011-02-25
I am on a 64-bit machine, the two isos I've tried so far are gparted-live-0.7.0-11 & gparted-live-0.8.0-1.  Both based on Debian Sid I believe.

Do you think it's too much auto-detection going on?  Curious to see what you come up with, assuming you have the time to play with it.

It seems that the problem lies with how it's trying to place the squash.fs into RAM.  Will continue trying some things and see if I stumble upon a solution.

---

### Post by drs305 on 2011-02-25
cbowman57,

I am running 64-bit Maverick with ext4 partitions. I downloaded gparted-live-0.8.0-1.iso from the Gparted/Sourceforge link:
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.8.0-1/]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.8.0-1/")

The file is located in my sdb6 partition in the /iso folder. Here is the working menuentry I tested:
> menuentry "Gparted Live ISO" {
set isofile="/iso/gparted-live-0.8.0-1.iso"
loopback loop (hd1,6)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
initrd (loop)/live/initrd.img
}


I needed to add "config" to avoid the user/password request, but otherwise it ran without problems.

---

### Post by cbowman57 on 2011-02-26
Running the same here.  Thought I'd tried every combination but adding that 'config' made all the difference. Thanks again.

---

### Post by Quackers on 2011-03-04
drs305, you've excelled yourself with this one :-)
I can't believe how fast the live cd desktop appears using this method! 45 seconds after selecting the iso from the grub menu I have a usable live desktop! It's amazing :-) Much better than using cd's or usb's. Fantastic!

One question I may need to google though. Having burned all the iso's to disc or usb, and having now deleted the original iso's, how do I get the iso's back?
I'll do some mooching around :-)
Many thanks for this.

---

### Post by Quackers on 2011-03-05
An update
All the live cd images I have used previously have now been entered in to the grub menu and they all boot.......very quickly :-) (even though I mistakenly did nothing as root - just user).
I do have one problem with the Clonezilla Live iso though. It starts to boot and gets to having mounted all my partitions and then it fails stating that it failed to boot as it couldn't find a live file system.
So having read drs305's bit about inspecting the initrd and hoping to find a lz suffix (but expecting to find a gz suffix) I found it has a img suffix.
I suspect that is the problem.
I have downloaded several different versions and they all have an initrd.img file.
Can anything be done about this?
Thanks

---

### Post by drs305 on 2011-03-05
@ Quackers,

Have you tried the Clonezilla menuentry provided by *cbowman57*? I added it to the original post after he presented it in Post #54. 

My usual routine is to download and check menuentries to make sure they work on my system and I expect I tried his before posting it. However, I find that I only have an older Clonezilla image in my 'iso' folder so it could be something has changed. If his entry doesn't work for you let me know and I'll try getting the latest image and experiment with it.

---

### Post by Quackers on 2011-03-05
Hi drs305, yes I tried that menu entry, courtesy of cbowman57, after editing it for my own file, and it does thesame. I then tried other versions of clonezilla with no improvement.
The menu entry is definitely working ok as clonezilla is starting to boot. It just fails after mounting my partitions.
Actually I just looked at the files again and the intrd.img file is actually a .gz file according to Nautilus. Is there a way to use that initrd?
Thanks boss :-)

Here's my menuentry
```
menuentry "Clonezilla Live cd" {
set isofile="(hd0,6)/nattyalpha/isofiles/clonezilla-live-1.2.6-59-i486.iso"
loopback loop $isofile
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

```

---

### Post by Quackers on 2011-03-05
Aha! :-) It works now!
I changed the second and third lines from
```
set isofile="(hd0,6)/nattyalpha/isofiles/clonezilla-live-1.2.6-59-i486.iso"
loopback loop $isofile
```
to
```
set isofile="/nattyalpha/isofiles/clonezilla-live-1.2.6-59-i486.iso"
loopback loop (hd0,6)$isofile
```
rebooted, et voila! Clonezilla fired right up.
I'm very happy again.
Thanks :-)

---

### Post by drs305 on 2011-03-05
> **Quackers said:**
> 
rebooted, et voila! Clonezilla fired right up.
I'm very happy again.
Thanks :-)

That makes two of us. :-)

I was about to try a couple of things. If they didn't work I was going to put it aside until after I finished my vacation. Now that's not necessary.

---

### Post by Quackers on 2011-03-05
Sorry to interrupt your hols! Do you take your laptop everywhere? :-)
Many thanks drs305. Enjoy the sun :-)

---

### Post by cbowman57 on 2011-03-05
Quackers & drs305,

Good catch.  While my Clonezilla worked as originally posted GParted quit working, and when I tried Clonezilla again it failed to boot as well.  Not sure what explains that, maybe using the set isofile= syntax is a little fragile.  Using Quacker's suggestion I changed my loopback loop entry to include the (hd0,9) and removed it from set isofile, now both GParted & Clonezilla boot up as they should.

Not sure if this has any bearing on why it worked, then stopped working, but I am using the 64-bit version of grub 1.98 20100804-5.

Anyway, thanks to both of you for sorting that out.

---

### Post by drs305 on 2011-03-05
Just a quick note on the 64-bit 'current' version  (1.2.6-59-amd64.iso): It has initrd1.img which is actually a .gz file and it's kernel image is also called "vmlinuz1".  

I haven't been able to get any of the Clonezilla menuentries listed so far work on this version, even adjusting for the initrd1 and vmlinuz1 designations or extracting the .gz initrd1.img. However, the latest test version (1.2.6.8-8.iso) works fine - the kernel and initrd images are back to the conventional initrd.img and vmlinuz designations and the adjusted menuentries work fine.

---

### Post by Quackers on 2011-03-06
Hmm, there was an initrd1.img on one of the clonezilla iso's I tried, but the one that is now booting does not have that.

---

### Post by Briksins on 2011-03-09
Hello, this is great thread with amazing manual, however im very confused with parameters and kernel

here is original example Gparted Live CD:   

> ```

menuentry "Gparted Live ISO" {
set isofile="/boot/iso/gparted-live-0.8.0-1.iso"
loopback loop (hd0,1)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
initrd (loop)/live/initrd.img
} 

```
if i need to make Win7_Ultimate_SP1_x64.iso bootable trough grub from my external hdd, how should looks my code?

```
menuentry "Install Windows 7 SP1 x64" {
set isofile="(/dev/sdXY)/_path_name_/Win7_Ultimate_SP1_x64.iso"
loopback loop $isofile
linux (loop)/......**//What kind of parameters should go here for Win7 installation???**
initrd (loop) /...... **//What kernel should i use for Win7 install**
}
```

---

### Post by drs305 on 2011-03-09
Briksins,

Welcome to the Ubuntu forums.

The Grub2 ISO booting will only work for Linux OS's as far as I know. You can't boot a Windows ISO via this process. Not even all Linux OS's can boot via the manner described in this thread - the ISOs have to be built in a specific manner to allow it.

You can *mount* a Windows ISO to inspect the contents via a "mount -o loop" command but cannot boot it via Grub2.

---

### Post by Briksins on 2011-03-09
Hmmm very sad news, do u have any idea how can i achieve my idea? any other tools? if not GRUB2 maybe Grub4DOS? or something alse?

I have external USB hard drive which contain many fails some of them are images bigger than 6GB so solution like [this]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/") with FAT32 doesnt suets, even Win7.iso is 4.2GB what will not fit on FAT32
So any ideas how can i make multybootable e-hdd with NTFS where *.iso files stored on the same e-hdd?

---

### Post by drs305 on 2011-03-09
> **Briksins said:**
> Hmmm very sad news, do u have any idea how can i achieve my idea? any other tools? if not GRUB2

I have external USB hard drive which contain many fails some of them are images bigger than 6GB so solution like [this]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/") with FAT32 doesnt suets, even Win7.iso is 4.2GB what will not fit on FAT32
So any ideas how can i make multybootable e-hdd with NTFS where *.iso files stored on the same e-hdd?

I don't know enough about Windows to help. I'd ask on a Windows forum - they would have a better idea of how to go about it. It's possible someone on here might have an answer but I wouldn't wait too long for a response here before asking a more suitable audience.

---

### Post by oldfred on 2011-03-09
The FAT 4GB limit is not an issue as you do not copy the ISO to the USB flash drive, but all the files on the ISO.

I have not done it but have saved these links.

non-commercial all versions of windows
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)
[http://arstechnica.com/business/news/2009/12/-the-usb-flash-drive.ars](http://arstechnica.com/business/news/2009/12/-the-usb-flash-drive.ars)
Create Windows 7 USB 
[http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb](http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb)
[http://www.boot-land.net/forums/index.php?showtopic=8944](http://www.boot-land.net/forums/index.php?showtopic=8944)

Create Windows 7 USB
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
[http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx)
[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool)
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

---

### Post by Briksins on 2011-03-10
oldfred Thank you very much!
however the main idea in all links provided wasnt useful to my case, but i was fallowing chain of links in comments and finally find guide which i was looking for so many days
because this gide was so hard to find ill duplicate it here, so it will increase chance to find it in a double for next searcher 
[http://sites.google.com/site/rmprepusb/tutorials/multiisoimdiskautounattend](http://sites.google.com/site/rmprepusb/tutorials/multiisoimdiskautounattend)

a bit of details:
For my case i had to use GRUB4DOS together with ImDisk
so i have finally achieve what i was plan to:

*-multy-bootable E-HDD
*-nice boot menu
*-NTFS partition
*-only one device appear when u plug it in Windows OS
*-images are in .iso and not extracted to the root dir and can be located in any folder on my main DATA NTFS partition
*-same usability as with GRUB2, just add new entry to menu and point to the iso file
*-less problems with syntax in menu config file (IMHO i find GRUB4DOS syntax easier then actual GRUB2)

Thank you all very much!

---

### Post by tipiglen on 2011-03-17
Thanks to chowman's entry, I now have got the hang of it.  Clonezilla working fine.

Thanks for getting me out of a very frustrating loop!

---

### Post by tipiglen on 2011-03-18
For those trying to boot a windoze iso, This may be helpful?
[http://download.cnet.com/Windows-7-USB-DVD-Download-Tool/3000-18513_4-10972600.html](http://download.cnet.com/Windows-7-USB-DVD-Download-Tool/3000-18513_4-10972600.html)

I've not yet been successful getting a linux mint 10 iso to boot from hard disk.  Unetbootin has made me a bootable usb/SDcard, but I'd like to have it available via the iso on my HDD.

Current appropriate portion of 40_custom:```
menuentry "Linux Mint 10 live" {
set isofile="(hd0,3)/boot/isos/linuxmint-10-gnome-dvd-i386.iso"
loopback loop (hd0,3)/boot/isos/linuxmint-10-gnome-dvd-i386.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
gets me well into process, and finishes with busybox and a 'can't find file' for the iso.  It then goes on to suggest I reboot windows to fix a possibly unclean shutdown... I wasn't in windoze, and haven't been for some time.

Grrr!

---

### Post by drs305 on 2011-03-18
*tipiglen*

I think your problem may be identifying the *isofile* variable with the drive/partition. Try it without the "(hd0,3)" at the beginning.
> set isofile="/boot/isos/linuxmint-10-gnome-dvd-i386.iso"


Here is my working entry.
> menuentry 'ISO Mint 9         sdb6'                        {
 loopback loop (hd1,6)/iso/linuxmint-9-gnome-cd-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/linuxmint-9-gnome-cd-amd64.iso noprompt quiet splash
 initrd (loop)/casper/initrd.lz
}


---

### Post by cbowman57 on 2011-03-18
Here is an alternate working entry:

menuentry 'ISO Linux Mint amd64 live' {
set isofile="/linuxmint-10-gnome-dvd-amd64.iso"
loopback loop (hd0,9)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

---

### Post by tipiglen on 2011-03-18
Thanks Chuck!  That works.
[http://tipiglen.co.uk/loveandpeace3.gif](http://tipiglen.co.uk/loveandpeace3.gif)

---

### Post by cbowman57 on 2011-03-18
> **tipiglen said:**
> Thanks Chuck!  That works.
[http://tipiglen.co.uk/loveandpeace3.gif](http://tipiglen.co.uk/loveandpeace3.gif)
Super!  I used the example from drs305 and arrived at that one somehow. ;-)

---

### Post by tipiglen on 2011-03-19
Doc and Chuck,

Thanks again for the helpful hints.  It does seem a wee bit 'trial and error' (with the emphasis on the latter!).

For interest, the mint entry which works for me  (with iso stashed on 'maintenance' partition sda4):```
menuentry 'ISO Linux Mint live' {
set isofile="/linuxmint-10-gnome-dvd-i386.iso"
loopback loop (hd0,4)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
Usually running mint 9.

[http://tipiglen.co.uk/loveandpeace3.gif](http://tipiglen.co.uk/loveandpeace3.gif)
ed

P.S. regarding the windoze usb loader mentioned earlier, it seems that, while it works fine and can be used to install W7 via usb (I have done so), it doesn't really work as a 'live' trial. Much as I hate to admit it, M$ seem to have done a pretty decent job this time with W7.

An interesting tirade:

>     *
          o

What I am saying in essence is that users must not treat freeware like commercial software. For one thing, much of freeware is better than commercial software. Why? Because most people who write freeware actually like computers and programming, and most freeware programs were written by people who, whatever they were doing, were not watching a clock while feeling exploited by a corporation.

    Digression: why do you think Microsoft's software is so dreadful? Simple. It was largely written by people who didn't want to be doing what they were doing, who were the least expensive programmers the personnel division could find to fill empty positions, who were being exploited and who knew it. Programmers who are actually skilled at programming either start their own companies or retire (and maybe write freeware) — but they don't remain corporate lackeys, struggling to repair the latest version of Windows.

    There's an old joke with relevance to this topic. After John Glenn's historic orbital flight, interviewers asked him what he thought as he waited for lift-off. He replied, "I was thinking that the rocket had twenty thousand components, and each was made by the lowest bidder". Commercial software is, by definition, built by the lowest bidder. By contrast, freeware (some of it, anyway) is built by people who actually like what they are doing, and some of them are people the big software corporations could not afford to hire.

Users of freeware must not forget that they didn't pay for the software, and therefore they cannot demand the satisfaction of an imaginary contract between the programmer and themselves. The usual adversarial relationship between a vendor and a consumer simply doesn't exist. I find that users below a certain age never grasp this fact, and invariably it is the youngest users who think they have the right to demand absolutely anything, and who expect satisfaction of any arbitrary whim.

Watching the Internet as I do, I find that the chasm between human beings and consumers is widening. Rather than belabor a point that has been adequately discussed elsewhere, including articles on this site (one example:  Consumer Angst ), I will simply say that people must not treat freeware as though it is commercial software, and must not treat freeware authors as though they can be held responsible for users' expectations. Boys and girls, this is not how freeware works. [http://www.arachnoid.com/freeware/index.html](http://www.arachnoid.com/freeware/index.html)

The price of freedom!
;-)

---

### Post by ghaspias on 2011-03-19
Just one tip and one question:

tip: I avoid cluttering my menu with tens of live cd entries, by placing all those entries in a seperate file. Then I just add one entry to the /etc/grub.d/40_custom:
```
menuentry "livecdimage" {
	root (hd0,1)
	source /livecdimage.grub.sh
}
```
(hd0,1) is a NTFS partition I use for placing the isos.

Question: Any success in booting Fedora iso? I have tried several options, but the Fedora 12/13 boot system doesn't handle it (unless the initrd is extracted and a small tweak is made, which I would like to avoid). 

Here's my live boot menu:
(My machine requires "noapic acpi=force" to boot some recent kernels; your kernel args might be different)

```

menuentry "Ubuntu Lucid netbook 32bit" {
 root (hd0,1)
 loopback loop0 /ubuntu-10.04-netbook-i386.iso
 set root=(loop0)
 gfxpayload=keep
 linux /casper/vmlinuz root=/dev/sda1 loop=/ubuntu-10.04-netbook-i386.iso file=/cdrom/preseed/ubuntu-netbook.seed boot=casper iso-scan/filename=/ubuntu-10.04-netbook-i386.iso acpi=force noapic quiet splash --
 initrd (loop0)/casper/initrd.lz
}

menuentry "Ubuntu Sugar Remix" {
 set ISODEV=(hd0,1)
 set ISOIMG=USR-i386-20100208.iso
 set SEED=USR
 set KPAR="acpi=force noapic quiet splash"
# gfxpayload=keep

 loopback loop $ISODEV/$ISOIMG
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/$SEED.seed boot=casper iso-scan/filename=/$ISOIMG $KPAR --
 initrd (loop)/casper/initrd.lz
}

menuentry "Natty Desktop" {
 set ISODEV=(hd0,1)
 set ISOIMG=natty-desktop-i386.iso
 set SEED=ubuntu
 set KPAR="acpi=force noapic quiet splash noeject"
# gfxpayload=keep

 loopback loop $ISODEV/$ISOIMG
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/$ISOIMG $KPAR --
 initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu Maverick 32bit" {
 set ISOIMG=testdrive/iso/ubuntu-10.10-desktop-i386.iso
 set SEED=ubuntu
 loopback loop (hd0,1)/$ISOIMG
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/$SEED.seed boot=casper iso-scan/filename=/$ISOIMG acpi=force noapic quiet splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Linux Mint 10 (Julia)" {
 set ISOIMG=linuxmint-10-gnome-dvd-amd64.iso
 set SEED=mint
 loopback loop (hd0,1)/$ISOIMG
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/$SEED.seed boot=casper iso-scan/filename=/$ISOIMG acpi=force quiet splash pnpbios=off pci=biosirq --
 initrd (loop)/casper/initrd.lz
}

menuentry "Elementary OS" {
 set ISOIMG=elementary_OS_0.1.6.iso
 set SEED=ubuntu
 loopback loop (hd0,1)/$ISOIMG
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/$SEED.seed boot=casper iso-scan/filename=/$ISOIMG acpi=force quiet splash pnpbios=off pci=biosirq --
 initrd (loop)/casper/initrd.lz
}

menuentry "EMC2 Live" {
 set ISOIMG=ubuntu-10.04-linuxcnc1-i386.iso
 set SEED=ubuntu
 loopback loop (hd0,1)/$ISOIMG
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/$SEED.seed boot=casper iso-scan/filename=/$ISOIMG acpi=force quiet splash pnpbios=off pci=biosirq --
 initrd (loop)/casper/initrd.lz
}

menuentry "Jolicloud" {
 set ISOIMG=Jolicloud-1.0.iso
 set SEED=jolicloud
 loopback loop (hd0,1)/$ISOIMG
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/$SEED.seed boot=casper iso-scan/filename=/$ISOIMG acpi=force quiet splash pnpbios=off pci=biosirq --
 initrd (loop)/casper/initrd.gz
}

menuentry "Fedora 14" {
 set ISOIMG=miguel/F14iso/Fedora-14-i686-Live-Desktop.iso
 loopback loop (hd0,7)/$ISOIMG
 linux (hd0,7)/miguel/F14iso/vmlinuz0 boot=isolinux loop /dev/sda7 root=live:/dev/sda7:/$ISOIMG rootfstype=auto ro liveimg rddebug rdinitdebug rdbreak=pre-mount acpi=force noapic --
 initrd (hd0,7)/miguel/F14iso/initrd0.img
}
#
#menuentry "Fedora 13" {
# root (hd0,1)
# loopback loop /Fedora-13-x86_64-Live.iso
# linux (loop)/isolinux/vmlinuz0 boot=isolinux root=live:/Fedora-13-x86_64-Live.iso rootfstype=auto ro liveimg rdinitdebug rdshell rhgb rd_NO_LUKS rd_NO_MD noiswmd --
# initrd (loop)/isolinux/initrd0.img
#}
#
menuentry "Meego 1.1" {
 root (hd0,1)
 loopback loop /meego-netbook-ia32-1.1.img
 linux (loop)/isolinux/vmlinuz0 boot=isolinux root=CDLABEL=netbook-ia32-x86_64-20101026155 rootfstype=iso9660 ro liveimg rdinitdebug rdshell rhgb rd_NO_LUKS rd_NO_MD noiswmd --
 initrd (loop)/isolinux/initrd0.img
}
menuentry "Network boot" {
# start ipxe or bko or gpxe...
 linux16 /boot/IPXE.krn
}
#
menuentry "USB device" {
 chainloader (hd1,1)+1
}
menuentry "USB image" {
# Don't know if this works...
 set DEV=(hd0,1)
 set IMG=usb.img
 loopback loop $DEV/$IMG
 chainloader (loop)+1
}
```

---

### Post by drs305 on 2011-03-19
ghaspias,

Thanks for providing an example of the tip. I do the same thing (but in a different manner) but don't believe I've shown it in a thread.

From your examples I presume that Fedora 13 and later ISOs boot normally, which probably covers the needs of most users. I don't have a solution for 12 but perhaps someone will respond. My guess it was built before Grub 2 capabilities were incorporated into ISOs.

---

### Post by cbowman57 on 2011-03-19
Ok, I must be doing something wrong.  I used this tip but still have the multiple ISO entries.  I deleted all entries in the 40_custom file except this one and ran update grub.  I am assuming that this should have created sub-menu in my grub menu.

> **ghaspias said:**
> Just one tip and one question:

tip: I avoid cluttering my menu with tens of live cd entries, by placing all those entries in a seperate file. Then I just add one entry to the /etc/grub.d/40_custom:
```
menuentry "livecdimage" {
	root (hd0,1)
	source /livecdimage.grub.sh
}
```


---

### Post by drs305 on 2011-03-19
Chuck,

How about this way. I keep mine in /iso of sda7.

> 
menuentry "ISO Config         sda7" {
        configfile (hd0,7)/iso/ISO_custom.cfg
}


---

### Post by cbowman57 on 2011-03-19
Probably easiest to show you guys what I have.  The result is that I still have my ISO images in the grub menu and a non-working "Live ISOs" entry. I appreciate the help.

My 40_custom
```
#!/bin/sh
echo "Adding 40_custom." >&2
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Live ISOs' {
root (hd0,9)
source /livecdimage.grub.sh
}
```

My livecdimage.grub.sh
```
#!/bin/sh

# exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'ISO Natty amd64 live' {
loopback loop (hd0,9)/natty-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/natty-desktop-amd64.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry 'ISO LXDE Mint i386 live' {
set isofile="/linuxmint-10-lxde-rc-i386.iso"
loopback loop (hd0,9)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/linuxmint-10-lxde-rc-i386.iso noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry 'ISO Linux Mint amd64 live' {
set isofile="/linuxmint-10-gnome-dvd-amd64.iso"
loopback loop (hd0,9)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry "ISO Clonezilla live" {
set isofile="/clonezilla-live-1.2.8-3-amd64.iso"
loopback loop (hd0,9)$isofile 
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

menuentry "ISO Gparted Live" {
set isofile="/gparted-live-0.8.0-1.iso"
loopback loop (hd0,9)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs 
initrd (loop)/live/initrd.img
}
```

---

### Post by drs305 on 2011-03-19
Chuck,

Try making a copy (or renaming the .cfg.sh file) called livecdimage.cfg and add this to your 40_custom file. It assumes your livecdimage.cfg file is in the root directory of sda9:
> 
menuentry 'Live ISOs' {
configfile (hd0,9)/livecdimage.cfg
}


Save the file and update grub.

---

### Post by cbowman57 on 2011-03-19
Thanks drs305, that worked beautifully.

Lesson learned, DON'T rename 40_custom to original-40_custom and expect it not to be imported.  That was the cause of the original ISO entries showing up along with the Image ISO sub-menu. :)

All is well again.

---

### Post by ghaspias on 2011-03-19
sorry, my post wasn't clear in some points...
Using 'source ...' in the menu let's you load all those other entries only when you need them; they are appended to your current standard entries when you select the corresponding menu entry.

As for Fedora, none of my tests where successful. Some of the entries in the listing I posted don't work. I can't say at this moment which ones work, besides Fedora, which I never managed to boot successfully.
For Fedora, the problem has been reported, and there's even a patch for dracut (the system that manages the boot of live system), see [bug#557426]("https://bugzilla.redhat.com/show_bug.cgi?id=557426").

---

### Post by tipiglen on 2011-03-19
> Try making a copy (or renaming the .cfg.sh file) called livecdimage.cfg and add this to your 40_custom file. It assumes your livecdimage.cfg file is in the root directory of sda9:
Quote:
menuentry 'Live ISOs' {
configfile (hd0,9)/livecdimage.cfg
}
Save the file and update grub.

When I try this, I get no custom entries at all on reboot, even though the echo during update-grub says it's adding them....  

I've edited it to refer to my hd0,4 partition, where the isos and config file are....

Any ideas?

P.S.  To examine the contents of an iso file without mounting it, I can right-click it and I'm offered 'open with archive manager' - try it.

Cheers
ed

---

### Post by tipiglen on 2011-03-19
Ghaspias,
Thanks.  Got it working with ```
menuentry "livecdimage" {
	root (hd0,4)
	source /livecdimage.grub.sh
}
```
For cosmetic reasons I commented out the 'tail' line in my renamed custom list (livecdimage.grub.sh)

cool!

---

### Post by greenclone on 2011-04-14
I was trying to install Ubuntu 10.10 Server (32-bit, x86) from hard disk, but when I used vmlinuz and initrd.gz from installation CD, I couldn't get it to work.
I used configuration
> menuentry "Ubuntu 10.10 Server 32-bit CD" {
set isofile="/iso/ubuntu-10.10-server-i386.iso"
loopback loop (hd0,5)[COLOR=Navy]$isofile
[/COLOR]linux (loop)/install/vmlinuz boot=install iso-scan/filename=[COLOR=Navy]$isofile[/COLOR] noprompt noeject
initrd (loop)/install/initrd.gz
}Installation started, but after initial questions about language and keyboard, it reported error that it couldn't mount installation CD.

However, it worked :D when I used vmlinuz and initrd.gz from Ubuntu archives [http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/hd-media/). I have placed the files in the same directory as iso file, and changed my configuration to:
> menuentry "Ubuntu 10.10 Server 32-bit CD" {
set root=(hd0,5)
 set isofile="/iso/ubuntu-10.10-server-i386.iso"
 loopback loop [COLOR=Navy]$isofile
[/COLOR]linux /iso/vmlinuz iso-scan/filename=[COLOR=Navy]$isofile[/COLOR] noprompt noeject
 initrd /iso/initrd.gz
 }                      Any thoughts on why it didn't work with vmlinuz and initrd.gz from installation CD?

---

### Post by drs305 on 2011-04-14
> **greenclone said:**
> However, it worked :D when I used vmlinuz and initrd.gz from Ubuntu archives [http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/hd-media/). I have placed the files in the same directory as iso file, and changed my configuration to:
Any thoughts on why it didn't work with vmlinuz and initrd.gz from installation CD?

My guess, without inspecting the server CD contents by loop mounting the ISO, is that the server CD uses *initrd.[COLOR="DarkRed"]lz[/COLOR]* rather than *initrd.[COLOR="DarkRed"]gz[/COLOR]* and that is why it failed.

Once you added the *initrd.[COLOR="DarkRed"]gz[/COLOR]* file the system found what you had asked it to and was happy.  :-)

---

### Post by doctortonic on 2011-04-14
What I did wrong?

[http://pastebin.com/wxD4ekDJ]("http://pastebin.com/wxD4ekDJ")




[http://img641.imageshack.us/img641/6408/snapshot2ap.png]("http://img641.imageshack.us/img641/6408/snapshot2ap.png")

---

### Post by drs305 on 2011-04-14
> **doctortonic said:**
> What I did wrong?

 
What happens? 

Do you have the ISO entry in your Grub2 menu? 

Your screenshot shows a different 40_custom file but I assume the screenshot was before you edited it to the content in the pastebin link.

Your entry looks correct provided it's in sda5's /iso folder. I can't tell how old your kubuntu.iso file is, but if it's very old or if the Kubuntu ISO is different (I don't think so) you may have an initrd.gz file instead of initrd.lz.

Added: I just downloaded the current kubuntu i386 Desktop daily build ISO, renamed it to 'kubuntu.iso', placed it in a /iso folder and used your menuentry. It booted without problem.

---

### Post by greenclone on 2011-04-15
> **drs305 said:**
> My guess, without inspecting the server CD contents by loop mounting the ISO, is that the server CD uses *initrd.[COLOR=DarkRed]lz[/COLOR]* rather than *initrd.[COLOR=DarkRed]gz[/COLOR]* and that is why it failed.

Once you added the *initrd.[COLOR=DarkRed]gz[/COLOR]* file the system found what you had asked it to and was happy.  :-)

*initrd.lz* doesn't exist on the server CD, so it's not that.

---

### Post by doctortonic on 2011-04-15
I reinstalled the system in the meanwhile. The .iso is the latest Maverick kubuntu version, the pastebin was the config files, the screenshot for showing up the partitions.

It would be cool for grub to automaticaly find *.iso in a folder, for just downloading .iso-;s in that folder and boot them as your hearth wish.

---

### Post by drs305 on 2011-04-15
@ greenclone,

I downloaded the server ISO and it does not contain a 'casper' folder. While I am not familiar with how a linux CD has to be constructed to be bootable from Grub2, I know all the Ubuntu bootable ISOs I have used contain a 'casper' folder which is used for this purpose.

I can't say this is the answer, but it's an avenue you can explore.

---

### Post by seanbw on 2011-04-18
I have a problem with the edubuntu amd64 iso I am trying to run with this method. All the other entries work including Gparted and I can't understand why edubuntu does not work.
It just gives me a blank screen and goes to the boot menu i.e. the press F2 to go to setup/bios screen. I don't understand. Can anyone see anything wrong with my entries? I can't especially as I copied it from the working entries (unless there is a limit to the number of iso images you can put in the iso folder)
My iso folder is in the boot folder and it has exactly the same properties as the rest - owned by root and executable as a program with read and write access to all members user, group and others.
Please - can anyone see anything different? I used zsync to download 2ce as I initially thought that the file wasn't complete but it is because I can mount and access it.
Please help bcos stuff like this keeps me up until I sort it out and I cant especially as my only idea was to use the squashfs to ram but I only have 2 GB of RAM. Ahhhhg...
```

#!/bin/sh
echo "Adding 06_custom." >&2
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Edubuntu Natty Beta 2 ISO" {
set isofile="/boot/iso/edubuntu-11.04-beta2-dvd-amd64.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu Natty Beta 1 ISO" {
set isofile="/boot/iso/ubuntu-beta1.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu Natty Beta 2 ISO" {
set isofile="/boot/iso/ubuntu-11.04-beta2-desktop-amd64+mac.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry "Kubuntu Natty Beta 2 ISO" {
set isofile="/boot/iso/kubuntu-11.04-beta2-desktop-amd64.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry "Xubuntu Natty Beta 2 ISO" {
set isofile="/boot/iso/xubuntu-11.04-beta2-desktop-amd64.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

menuentry "Gparted Live ISO" {
set isofile="/boot/iso/gparted-live-0.8.0-5.iso"
loopback loop (hd0,1)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
initrd (loop)/live/initrd.img
}

menuentry "Automatically Generated Menu Entries:" {
insmod ext2
}

### END /etc/grub.d/06_custom ###

```
:confused:

---

### Post by drs305 on 2011-04-18
@ seanbw

I'm downloading it but because it's a dvd it will take a while. After I download it I'll try mounting it to inspect how it's built.

There is no limit to how many ISOs you can have in a folder (barring disk space limits).

---

### Post by cbowman57 on 2011-04-18
> **doctortonic said:**
> ....
It would be cool for grub to automaticaly find *.iso in a folder, for just downloading .iso-;s in that folder and boot them as your hearth wish.

Look for a program from grml called imageboot, or something similar.  Once installed you just throw an iso into (IIRC) /boot/images then update-grub and it automagically adds them to your grub menu.  Doesn't work for everything but it's pretty slick for the ISOs that it does work with.

---

### Post by drs305 on 2011-04-18
> **cbowman57 said:**
> Look for a program from grml called imageboot, or something similar.  Once installed you just throw an iso into (IIRC) /boot/images then update-grub and it automagically adds them to your grub menu.  Doesn't work for everything but it's pretty slick for the ISOs that it does work with.

I think I found the package, called grub-imageboot:
[http://deb.grml.org/pool/main/g/grub-imageboot/]("http://deb.grml.org/pool/main/g/grub-imageboot/")

I'll have to check it out. It could make this thread a lot less necessary, which would be great.

Thanks *cbowman57* :-)

Added: edubuntu is still downloading...

---

### Post by cbowman57 on 2011-04-18
You are welcome.  

I was hesitant to mention it in this thread, so I'm glad you approve.  

> **drs305 said:**
> I think I found the package, called grub-imageboot:
[http://deb.grml.org/pool/main/g/grub-imageboot/]("http://deb.grml.org/pool/main/g/grub-imageboot/")

I'll have to check it out. It could make this thread a lot less necessary, which would be great.

Thanks *cbowman57* :-)

---

### Post by drs305 on 2011-04-18
> **cbowman57 said:**
> You are welcome.  

I was hesitant to mention it in this thread, so I'm glad you approve.

One of the gratifying things that makes up for the lack of documentation when Grub 2 was introduced is the introduction and availability of new tools to help with booting. 

Just a Grub legacy had *startupmanager*, G2 now has *grub-customizer*, a decent GNU Grub manual, and now the package you've brought to our attention.

Once I've had time to play with it, I'll include a link to *grub-imageboot* prominently in the first post.

The more the merrier!

---

### Post by drs305 on 2011-04-18
> **seanbw said:**
> I have a problem with the edubuntu amd64 iso ...

Well, the good news is that I've downloaded the Edubuntu 64-bit ISO from [_http://cdimage.ubuntu.com/edubuntu/releases/natty/beta-2/_]("http://cdimage.ubuntu.com/edubuntu/releases/natty/beta-2/") and it booted fine to the non-Unity desktop. For my Ubuntu Natty setup (full install, not an ISO boot), I have to add my nvidia driver before I get Unity to work.

Since you are getting a black screen, perhaps it's a video issue, as Grub2 should provide an error message if it finds a problem. If you continue to have problems, perhaps removing 'quiet splash' and substituting 'nomodeset' might work for you. Since your other ISOs boot (and I assume don't use Unity), perhaps this is the problem.

My menuentry is only different in the location. Mine is in my sdb6 partition in /iso, but otherwise it looks like it's similar to your menuentry. I mounted the ISO and the file structure looks identical to my natty ubuntu nightly build.

> 
menuentry 'Edbuntu Test      sdb6'                        {
isofile="/iso/edubuntu-11.04-beta2-dvd-amd64.iso"		
loopback loop (hd1,6)$isofile		
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt quiet splash
initrd (loop)/casper/initrd.lz
}


If it's not video, you might try some of the other kernel options or need to download the ISO image again (ouch) or at least check the MD5SUM (at the link above).

---

### Post by seanbw on 2011-04-19
Thank you for this. It has to be the video. I have tried all the other iso and they work. I have downloaded it twice now. I will try the nomodeset option or the other opton mentioned in another thread. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) which suggested acpi_os.
I will try both. Thank you drs305.
I forgot to include in my post that I use Acer 5720 which has always had a problem its intel gma500 graphics blacklisted.
as said I will try both options and also await your testing of the imageboot software. that will resolve a few issues.
There is another post which discussed multibooting iso using pendrives which is quite similar to what we are doing. I guess it depends on what is comfortable for you but I intend to pursue that option as well.
I will report back my results. Cheers for your quick response as well. eventually i fell asleep.

---

### Post by drs305 on 2011-04-19
> **seanbw said:**
> 
as said I will try both options and also await your testing of the imageboot software. that will resolve a few issues.

As for grub-imageboot, my preliminary testing isn't working. It builds menuentries but they won't boot. I'll have to do a bit of testing to figure out where I'm failing, or perhaps read about the limitations of memdisk.

Please let us know how the 'nomodeset' option works, or whatever you find that allows you to successfully boot the ISO.

---

### Post by seanbw on 2011-04-19
OK I managed to book into edubuntu natty narwhal by using nomodeset but I can't log out and book back in. It does not work like that. I have to shut down and then go through the whole process again. The other options - acpi=off, no_acpi, no_acpi="Linux" does not work so its something to do with its graphics card.
I may now permanently install it into a partition - sda2 to see how it boots besides my normal ubuntu partition on sda1.
If anybody else has a solution, I would be very interested in knowing it.
Also to report - ubuntustudio does not boot as well. The others boot straight from the grub2 menu list - ubuntu natty, kubuntu natty, mythbuntu natty, ubuntu and kubuntu maverick.
Also I discovered that ubuntustudio uses initrd.gz not lz (that is the natty alternative amd64) which was the only version I could get. I could not get the normal amd64.
Anyway, that is where I am. ubuntustudio and edubuntu are the problem ISOs so any ideas welcome.

---

### Post by drs305 on 2011-04-19
> **seanbw said:**
> OK I managed to book into edubuntu natty narwhal by using nomodeset but I can't log out and book back in. 

If you mean when you reboot, that would be understandable since you haven't permanently changed any of the ISO files unless you actually install it to a partition. 

If you install it after booting with nomodeset, hopefully a video driver wil be available so you can permanently avoid having to use the nomodeset option on future boots to your installed OS.

---

### Post by seanbw on 2011-04-25
Just to report back. I found a tool called multisystem on the pendrive site - [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/) that allows the same as this and uses grub2 but it had the same problem. will not boot ubuntustudio and  am determined that I will not burn (bcos it will waste a dvd) so for now - i am giving up.
Just thinking about it - i really dont need multisystem since Ive got grub2 so my new project is: move all the iso from /boot/iso to the usb drive I was using with multisystem and update grub2 (with exception of u-studio).
Cheers

Question
When I try to boot u_studio from ISO I get the message: load kernel first. Does that mean I need to do something like insmode ext2? or why does it say that?. Thx

---

### Post by Quackers on 2011-05-10
Has anyone got SuperGrubdisk2 to boot from grub? Is that possible?

---

### Post by c.cobb on 2011-05-11
Wow thank you, drs305, for starting this thread.

Over a year ago I started experimenting with different ways to set up a LiveUSB. Most of the pieces I wanted were working, but not all of them were working at the same time. Thanks to the notes here, last night I was finally able to pull it all together!

My goal has been a custom Ubuntu that boots from LiveUSB on both a PC and a Mac. A custom version is necessary as my bank uses a Java applet during the login, and now I can use this for secure online banking from anywhere. Yay!


This last year I've been using Puppy Linux, as that was so easy to customize, but there are some things that make it less than ideal, IMO, including that I couldn't get it to boot on a Mac. Now, as malware writers are creating more [threats for Linux and Macs]("http://krebsonsecurity.com/2011/05/weyland-yutani-crime-kit-targets-macs-for-bots/"), it seemed like a good time to get a custom Ubuntu working.

Yesterday I tried using the ['remastersys' script](http://www.geekconnection.org/remastersys/repository/karmic/), and now have everything working using a custom Ubuntu 10.04. Well, almost everything. Still need to figure out what the "Live" version of Ubuntu uses to handle so many networking possibilities. Wired works great, but not yet wireless.

The trick with remastersys was to install [the lupin-casper package as mentioned here]("http://www.remastersys.com/forums/index.php?topic=839.0"). Without that, some of the boot files can't be found. So 'frajadelic' knows about this, but has yet to make it a package dependency--at least as of rev 2.0.18. After installing that, your examples here worked great!


The trick for booting a USB stick on both PC and Mac is to use Grub/whatever in the MBR for the PC, and to have an /efi/boot/ subdirectory with an EFI version of Grub. Then, while booting the Mac, hold down the Option key until you see the drive icons. Select the USB, and it boots right up. You can also insert the USB after the hard disk icon shows up--either way works. It doesn't conflict with the USB stick's MBR loader at all. There are no special requirements for fs type. I'm using Fat32.

I found the EFI Grub2 boot loader in another thread here: [download the 'bootusb.tar.gz' file]("http://ubuntuforums.org/showpost.php?p=7926629&postcount=7") attached to the posting. Unfortunately, I don't have any more information about this other than that it works.

Here's the /efi/boot/grub.cfg entry that is working on my Macbook.

```
menuentry "Ubuntu Custom with Java (from ISO)" {
        fakebios
        search --set -f /boot/iso/ubuntu-10.04-custom-i386.iso
        loopback loop /boot/iso/ubuntu-10.04-custom-i386.iso
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-custom-i386.iso noeject noinstall noprompt --
        initrd (loop)/casper/initrd.gz
}
```

Wow, long post, hope that some of it's useful. One question: It's clear that ISO files must be specially crafted to allow direct booting--do you have any links or pointers for more info? It would really helpful to understand more about what's going on.

For Debian-based distros that are not able to boot from ISO, maybe using the remasterscript to rebuild the ISO is a workaround. It's pretty easy to start using (and it might provide the earlier poster a way to recreate his lost ISOs, FWIW).



After reading so *many* threads about all this where everyone is hung up on optical and they keep asking, "Why do you want LiveUSB? Why not use a CD?," this is indeed a welcome breath of fresh air.
Cheers,

---

### Post by drs305 on 2011-05-11
> **c.cobb said:**
> 
It's clear that ISO files must be specially crafted to allow direct booting--do you have any links or pointers for more info? It would really helpful to understand more about what's going on.


Thanks for providing the information you did. It's helpful, because most of what I've learned and posted was experimentation on my own. Since my use of other distros, RAID, LVM, EFI, etc is very limited, getting other's inputs is important. Which unfortunately leads to your question - no, I don't have any good links for how it works.

In fact, I owe *Quackers* a response, so...

@ Quackers: I downloaded the 1.98 version of SGD but couldn't get it to boot from the G2 menu.

> 
For Debian-based distros that are not able to boot from ISO, maybe using the remasterscript to rebuild the ISO is a workaround. It's pretty easy to start using (and it might provide the earlier poster a way to recreate his lost ISOs, FWIW).

That's an interesting thought. I just used remastersys a week or so ago just to try it out but it hadn't occurred to me to use it in this manner.

> 
After reading so *many* threads about all this where everyone is hung up on optical and they keep asking, "Why do you want LiveUSB? Why not use a CD?," this is indeed a welcome breath of fresh air.
Cheers,
Yes indeed. It's been a long time since I've burned a CD or put an installation ISO a on flash drive.

---

### Post by cbowman57 on 2011-05-11
> **drs305 said:**
> 

In fact, I owe *Quackers* a response, so...

@ Quackers: I downloaded the 1.98 version of SGD but couldn't get it to boot the G2 menu.


I tried with Rescatux, which I think is related to SGD, and couldn't get it to work either.  No real loss since the times I need to use Rescatux I can't get to the grub menu anyway.

---

### Post by Quackers on 2011-05-11
Ok, thanks people for the effort :-)
I'll do some mooching around :-) I like mooching!

---

### Post by Quackers on 2011-05-12
> **cbowman57 said:**
> I tried with Rescatux, which I think is related to SGD, and couldn't get it to work either.  No real loss since the times I need to use Rescatux I can't get to the grub menu anyway.

I was also hoping to put it on a USB flash drive with MultiBootUSB with my other isos, but no good yet :-)

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by cbowman57 on 2011-05-12
> **Quackers said:**
> I was also hoping to put it on a USB flash drive with MultiBootUSB with my other isos, but no good yet :-)

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

That would be handy.  Hope you get it figured out.

---

### Post by Quackers on 2011-05-12
It's not listed as being supported and v3.7 seems to have a problem. v3.5 objects to the locale, hmmmm

---

### Post by c.cobb on 2011-05-13
> **drs305 said:**
> 
   [QUOTE=c.cobb]For Debian-based distros that are not able to boot from ISO, maybe using the remasterscript to rebuild the ISO is a workaround.

That's an interesting thought. I just used remastersys a week or so ago just to try it out but it hadn't occurred to me to use it in this manner.[/QUOTE]

After thinking about this, and searching some more, this may be bad advice. Remastersys is used on an installed system, and the install process eliminates pieces not appropriate for the installed hardware. This is causing some problems already in the custom Ubuntu build I'm working on.

Then thought maybe, for distros that won't boot from ISO, just use [this "ISO editing]("http://thewiki4opentech.org/index.php/How_To_Modify_your_Ubuntu_Live_CD")" process to insert lupin-casper. Then I found [this thread]("http://lists.gnu.org/archive/html/help-grub/2011-04/msg00001.html") with a response that indicates [lupin-casper is specific to remastersys]("http://lists.gnu.org/archive/html/help-grub/2011-04/msg00003.html"), and not ISO booting in general. 

Another response in that thread mentions using [the loopback.cfg file]("http://lists.gnu.org/archive/html/help-grub/2011-04/msg00006.html") and, interestingly, has a pointer to the SuperGrubDisk Wiki [loopback.cfg page]("http://www.supergrubdisk.org/wiki/Loopback.cfg"). Unfortunately I didn't find any information in the SGD Wiki that answers Quacker's question, but maybe it's this config file that's missing, and using the ISO edit process to insert a loopback.cfg file is what's necessary for those non-booting distros. Just some food for thought. 

I'm definitely going to try editing the ISO as an alternative to remastersys.

---

### Post by Jose Catre-Vandis on 2011-05-14
Here's my entry for SliTaz 3 (iso name edited for simplicity)

```
menuentry "slitaz" {
	set isofile="/boot/iso/slitaz.iso"
	loopback loop (hd0,6)$isofile
	linux (loop)/boot/bzImage isofrom=$isofile boot=live quiet vga=792 noeject noprompt
	initrd (loop)/boot/rootfs.gz
}

```

You can edit the vga=792 accordingly for your system.

SliTaz is a bit broken for me at the moment - no keyboard for en/uk and no sound for ACL662 :(

---

### Post by drs305 on 2011-05-14
A bit different from most of our entries.

Thanks Jose.

---

### Post by ranch hand on 2011-05-14
> **drs305 said:**
> A bit different from most of our entries.

Thanks Jose.
Yes indeed.

I have a file of interesting entries.  This one went right in there.

Thanks a bunch.

---

### Post by Bomper on 2011-05-15
> **Quackers said:**
> Has anyone got SuperGrubdisk2 to boot from grub? Is that possible?

Yes, GRUB2 and [[COLOR="Red"]memdisk[/COLOR]]("http://syslinux.zytor.com/wiki/index.php/MEMDISK#Supported_image_types") (from [[COLOR="Red"]Syslinux Project[/COLOR]]("http://syslinux.zytor.com/wiki/index.php/The_Syslinux_Project")).

Sorry, for my bad English :oops:.



**[SIZE="4"]-Super Grub2 Disk (Example: memdisk iso):[/SIZE]**

1.- Search command "memdisk":

```
$ locate memdisk
...
/usr/lib/syslinux/memdisk
...
```

2.- Download [[COLOR="Red"]super_grub_disk_hybrid-1.98s1.iso[/COLOR]]("http://www.bootproblems.com/category/download/supergrub2diskdownload/") to "/boot/iso/".

3.-

```
#-------------------------------------
menuentry "Super GRUB2 Disk v1.98s1" {
#-------------------------------------

   linux16 /usr/lib/syslinux/memdisk iso bigraw
   initrd16 /boot/iso/super_grub_disk_hybrid-1.98s1.iso

}
```



**[SIZE="4"]-Super Grub Disk (Example: memdisk floppy) :[/SIZE]**

1.-Download [[COLOR="Red"]super_grub_disk_english_floppy_0.9799.img[/COLOR]]("http://www.bootproblems.com/category/download/supergrubdiskdownload/") to "/boot/iso/".

2.-

```
#------------------------------------
menuentry "Super GRUB Disk v0.9799" {
#------------------------------------

   linux16 /usr/lib/syslinux/memdisk floppy
   initrd16 /boot/iso/super_grub_disk_english_floppy_0.9799.img

}
```



**[SIZE="4"]-SBM Smart Boot Manager:[/SIZE]**

-INFO [[COLOR="Red"]Smart Boot Manager[/COLOR]]("http://paulski.com/zpages.php?id=1612")

-Download [[COLOR="Red"]SBM Smart Boot Manager (sbm.bin)[/COLOR]]("http://paulski.com/utilguides/sbm.zip") to "/boot/iso/"

or

-extract "[COLOR="DarkRed"]/install/sbm.bin[/COLOR]" from Ubuntu ISO (Only for arch=i386) to "/boot/iso".

```
#---------------------------------------------
menuentry "SBM - Smart Boot Manager (v7.3.1)" {
#---------------------------------------------

  linux16 /usr/lib/syslinux/memdisk floppy
  initrd16 /boot/iso/sbm.img

}
```


[COLOR="Red"]Edit:[/COLOR]



**[SIZE="4"]-SBM - Smart Boot Manager from Ubuntu ISO (only arch=i386):[/SIZE]**


```
#-----------------------------------------------------------------------------
menuentry "UBUNTU 11.04 - Natty Narwhal (32bits) - SBM - Smart Boot Manager" {
#-----------------------------------------------------------------------------

        loopback loop /boot/iso/ubuntu-11.04-desktop-i386.iso
        linux16 (hd0,1)/usr/lib/syslinux/memdisk floppy
	initrd16 (loop)/install/sbm.bin

}
```



[COLOR="Red"]Edit: 15 May 2011 - 23:12h (Spain) :[/COLOR]


**[SIZE="4"]-Plop Boot Manager:[/SIZE] **

Another Boot Manager: [[COLOR="Red"]Plop Boot Manager configuration[/COLOR]]("http://www.plop.at/en/bootmanager.html#rungrub2") for Grub2.

```

#--------------------------------------
menuentry "Plop Boot Manager v5.0.12" {
#--------------------------------------

    set root=(hd0,1)
    linux16 /boot/iso/plpbt.bin

}
```




Salu2.

---

### Post by drs305 on 2011-05-15
Thank you Bomper!

Added: I am not getting it to work yet. Still trying.

---

### Post by Quackers on 2011-05-15
Thanks indeed! I'm trying it now :-)

---

### Post by Quackers on 2011-05-15
Hmm I'm getting syntax errors in grub.cfg when I update-grub.
I'll play with it :-)

---

### Post by Jose Catre-Vandis on 2011-05-16
Thought I would have a go at booting my custom iso created with remastersays. It's based on 10.04 LTS so I used the standard Lucid stanza to see what happened. My isos are on /dev/sda6. 

> menuentry "custom" {
set isofile=/boot/iso/custom.iso
loopback loop (hd0,6)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
Linux (loop)/casper/initrd.gz
}

It boots and I get the first stream of white text flying by, then the graphics kick in and improves the resolution of the white text. Then I get the error, it reoccurs and repeats and boot will go no further. If I press the ESC or Break key the plymouth splash comes up, but this only halts the error reporting until I press the key again
```
stdin: error:0
init: line 3: can't open /dev/sdb no medium found
init: line 3: can't open /dev/sr0 no medium found
init: line 3  can't open /dev/sdb no medium found
init: line 3: can't open /dev/sr0 no medium found

stdin: error:0
init: line 3: can't open /dev/sdb no medium found
init: line 3: can't open /dev/sr0 no medium found
init: line 3  can't open /dev/sdb no medium found
init: line 3: can't open /dev/sr0 no medium found
```
and so on.

Just before this error appears, it shows the device details for my DVD drive, and I don't have an /sdb device (single HDD PC)

Are there any kernel options I can throw at this to get it boot?

Have tried "file=/cdrom/preseed/custom.seed" makes no difference, "boot=live" crashes boot, "isofrom=$isofile" no difference. "quiet splash" just hangs on plymouth screen.

All suggestions welcomed and will be tried out.;)

---

### Post by Quackers on 2011-05-16
Is your system one of those which labels a usb flash drive as /dev/sda rather than /dev/sdb when one is plugged in?
If so, was a USB flash drive plugged in when you made your custom iso?

---

### Post by cbowman57 on 2011-05-16
> **Quackers said:**
> Is your system one of those which labels a usb flash drive as /dev/sda rather than /dev/sdb when one is plugged in?
If so, was a USB flash drive plugged in when you made your custom iso?

Excellent question.  When I was learning how to use the information in this thread I would occasionally get some strange errors relating to memory, on boot up from an iso entry.  Turns out it was due to having a USB drive plugged in and it confused the boot loader.

I wasted some time trying to get valid entries working due to my error.  I posted a couple times about the error here but don't think I ever confirmed & posted the cause & cure.

---

### Post by _duncan_ on 2011-05-16
> **cbowman57 said:**
> Excellent question.  When I was learning how to use the information in this thread I would occasionally get some strange errors relating to memory, on boot up from an iso entry.  Turns out it was due to having a USB drive plugged in and it confused the boot loader.

I wasted some time trying to get valid entries working due to my error.  I posted a couple times about the error here but don't think I ever confirmed & posted the cause & cure.


My experience is somewhat related albeit with a different set-up. Seems like grub sometimes has difficulty with multi-drive set-up. In your case 1 HDD + 1 USB drive. In my case, 1 SATA drive + 1 IDE drive.

To elaborate: I have Lucid installed on an oldish system with 1 80-GB IDE drive and another 160 GB SATA drive. What I notice during normal boot is that Lucid would assign /dev/sda or /dev/sdb to the 2 drives, almost at random. The issue isn't too apparent because the menu entries use UUID to identify the partition, hence the system gets booted regardless of the /dev/sdx assignment to the drives. After boot, if I use a disk utility like the default Disk Utility or GParted, my IDE drive sometimes gets assigned to /dev/sda and sometimes /dev/sdb and vice versa for the SATA drive.

This creates havoc when custom entries are added to grub (like the ISO booting entries) since we usually use /dev/sd? to point to the correct partition instead of UUID.

My workaround to the problem is to have 2 entries for each ISO, one pointing to /dev/sda and the other /dev/sdb. If the first entry doesn't work, then the 2nd entry is sure to work. Just to highlight the randomness of the problem, after a reboot, it is possible that the first entry will work, while the 2nd entry which worked previously, won't work.

I have no problem whatsoever using the ISO booting process described here on newer single-drive set-ups.

---

### Post by cbowman57 on 2011-05-16
@_duncan_; Very informative, important to realize that despite best efforts there are things that can cause an ISO boot failure totally unrelated to a correct grub2/iso setup.

I wasn't certain if my experiences with what I've learned here were isolated incidents or not. thanks :)

---

### Post by Jose Catre-Vandis on 2011-05-16
> **cbowman57 said:**
> Excellent question.  When I was learning how to use the information in this thread I would occasionally get some strange errors relating to memory, on boot up from an iso entry.  Turns out it was due to having a USB drive plugged in and it confused the boot loader.

I wasted some time trying to get valid entries working due to my error.  I posted a couple times about the error here but don't think I ever confirmed & posted the cause & cure.

Hmmmm... the only thing plugged in is my DVD drive ( I have a nettop so no built in DVD drive). I'll try unplugging it and see what happens. 
Alternatively is there a kernel option to stop the boot process looking for other drives, or have I got to dive into initrd.gz or isolinux and sort something out there? (newbie question! :) )

---

### Post by Quackers on 2011-05-16
I don't know of a boot option but there may be one :-)
The point I was really making was that if another drive (of any type - even a flash drive) was plugged in when you made the custom iso it could be that your internal hard drive's designation at the time was /dev/sdb instead of /dev/sda. I thought that might explain why the iso seems to be looking at /dev/sdb. But that's only guessing really :wink:

---

### Post by Jose Catre-Vandis on 2011-05-16
Thanks Quackers, its a good spot. I'll try it out a bit later once I get home from the office :)

[LATER]

Well, unplugged the DVD drive and that error line went away, and have identified /dev/sdb as being the internal multi card reader in my nettop (so can't remove that)(The custom.iso was built on this machine). However, I tried unplugging everything else whilst the errors were being displayed and eventually dropped to busybox with this message:
> (initramfs) Unable to find a medium containing a live file system so I am guessing that the grub stanza is not correctly identifying where the live system is. Have tried a multitude of options which either resulting the same error or a kernel panic :)  off to play some more....

**[SOLVED!]**
You have been reading the meanderings of a blithering idiot in this post! What a **remastersys** iso needs is **lupin-casper** in order to boot up, as previously mentioned in this thread by other cleverer souls. (It also needs casper, but you will get this when you install remastersys in any case)

Fortunately, I still had my custom system in place, so I booted it up and did the following:
```
sudo apt-get update
sudo apt-get install lupin-casper
```
Then I rebuilt the iso using remastersys, and copied the resultant iso file to my /boot/iso directory. Using this stanza
```
menuentry "Custom LIVE" {
        set isofile="/boot/iso/custom.iso"
        loopback loop (hd0,msdos6)$isofile
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile file=(loop)/preseed/custom.seed noeject noprompt --
        initrd (loop)/casper/initrd.gz
}
```
I was presented with a full boot to login/desktop. I'll add "quiet splash" later to the kernel options

:):):)

---

### Post by seanbw on 2011-05-20
> **Quackers said:**
> Has anyone got SuperGrubdisk2 to boot from grub? Is that possible?

Yes but that was using a tool called Multisystem which worked with a lot more distros than multibootUSB did (yes I have tried both and eventually standardsed on multisystem)

Multisystem can be found here: [http://liveusb.info/dotclear/index.php?](http://liveusb.info/dotclear/index.php?) and it also boots grub4Dos, supergrub,PLoP?, rescatux and even my ubuntustudio :P although it added some additional files to it. The site is in French but Google translate does a good job.

I have tried to copy the boot options used by multisystem to grub2 for ubuntustudio but it did not work. came up with load kernel first which was par for grub2 and ubuntustudio. It however did not work for Dreamlinux on my laptop but a visit to the support site for dreamlinux indicated that the error message was usual for DL if you have more than one hdd. 

Both MultibootUSB and multisystem give excellent support as both developers seem to respond almost immediately. Support for Multisystem is given from the Ubuntu-fr site - [http://forum.ubuntu-fr.org/viewtopic.php?id=427605](http://forum.ubuntu-fr.org/viewtopic.php?id=427605)

You might want to try it and see if it works for you. I hope above helps :) Cheers. Sean

PS: drs305 - how was the vacation? Im hoping to come to the States sometime this year. Do some driving around. Hope you enjoyed yourself.

---

### Post by Quackers on 2011-05-20
Thanks for that info seanbw - very useful :-)
Ooh la la, I'll take a look!

---

### Post by fabianofcarlos on 2011-05-24
I came across this post because I wanted to use a USB drive to do some  tests on my computer at work. Was very excited when I was able to easily  create a multiboot menu for some Ubuntu flavors. The problem was I  wanted to test Debian, Fedora, and others as well lol

The answer came after I found a post about Multisystem on pendrivelinux.com

> **seanbw said:**
> Yes but that was using a tool called Multisystem  which worked with a lot more distros than multibootUSB did (yes I have  tried both and eventually standardised on multisystem)...


Though I'm using it right now and it's awesome just like Sean described it, I still wanna thank you all for your time and effort, specially drs305 who started this prolific discussion.
You guys rock! :guitar:

---

### Post by drs305 on 2011-05-24
I appreciate the feedback and identification of additional related resources. I've placed a note in the first post referencing *seanbw's* post regarding multisystem.  And thanks to *fabianofcarlos* for confirming *sean's* 'find'.

---

### Post by ranch hand on 2011-05-26
Does anyone have any idea if Kanotix can be booted with grub?

I can't find any file that looks anything like right for the  initrd line at all (no lz, bz,etc).

---

### Post by Jack Smith on 2011-05-27
> **Quackers said:**
> Aha! :-) It works now!
I changed the second and third lines from
```
set isofile="(hd0,6)/nattyalpha/isofiles/clonezilla-live-1.2.6-59-i486.iso"
loopback loop $isofile
```
to
```
set isofile="/nattyalpha/isofiles/clonezilla-live-1.2.6-59-i486.iso"
loopback loop (hd0,6)$isofile
```
rebooted, et voila! Clonezilla fired right up.
I'm very happy again.
Thanks :-)
 
 
Thank you!  
Thank you!
Thank you!
Thank you!
THANK YOU!!!  
 
I have been bouncing my brain off of this same problem for a good 16 hours now... and was finding nothing but outdated info or solutions that didn't work.  This fixed it and clonezilla is Alive!  along with ubuntu full install, hirens, bitdefender, ubuntu live cd... the list goes on, all from my USB drive.  now to get win7PE working...
 
Again, Thank you to Drs305 for this amazing thread, and thank you to quakers for being specific.

---

### Post by Quackers on 2011-05-28
Lol you're welcome, I'm sure :-)
You haven't got Fedora booting from grub2 have you?  :-)

---

### Post by Jose Catre-Vandis on 2011-05-28
> **Jack Smith said:**
> Thank you!  
Thank you!
Thank you!
Thank you!
THANK YOU!!!  
 
I have been bouncing my brain off of this same problem for a good 16 hours now... and was finding nothing but outdated info or solutions that didn't work.  This fixed it and clonezilla is Alive!  along with ubuntu full install, hirens, bitdefender, ubuntu live cd... the list goes on, all from my USB drive.  now to get win7PE working...
 
Again, Thank you to Drs305 for this amazing thread, and thank you to quakers for being specific.

Clonezilla lives in Parted-Magic-6.x so if you can boot that you have Clonezilla. Lots of goodies in PM6 ;)

---

### Post by Jose Catre-Vandis on 2011-05-28
> **ranch hand said:**
> Does anyone have any idea if Kanotix can be booted with grub?

I can't find any file that looks anything like right for the  initrd line at all (no lz, bz,etc).

See this from the kanotix site:
> How do I use "fromiso" cheatcode?


With this cheatcode you can start from an iso out of a partition, which is much faster then from a CD (HD installations with "fromiso" only takes a fraction of time, some say less then 4 minutes, but with 6-8 minutes its still fast as lightning).

Requirements:
- a functioning grub (on a floppy, a HD-Installation or from the Live-CD)
- a KANOTIX ISO Image e.g.: KANOTIX-2005-04.iso


First we choose a place for the iso and 2 files we need, so we get shorter names. Therefore we create a base-directory: we choose e.g. /dev/hda5, create the directory "kanotix" and copy the iso into it:

# mkdir /media/hda5/kanotix
# mv KANOTIX-2005-04.iso /media/hda5/kanotix

now we move to that directory and mount the iso image:

# mkdir -p /mnt/test
# mount -t iso9660 -o loop,ro /media/hda5/kanotix/KANOTIX-2005-04.iso /mnt/test

now we copy the files miniroot.gz and vmlinuz from the mounted iso image to our directory:

# cp /mnt/test/boot/vmlinuz /media/hda5/kanotix/
# cp /mnt/test/boot/miniroot.gz /media/hda5/kanotix/

Now we have to customize grub a bit, Therefore we edit the file /boot/grub/menu.lst and add the following lines:

### ISO boot
title Kanotix 32bit from ISO
kernel (hd0,4)/kanotix/vmlinuz ramdisk_size=100000 init=/etc/init fromiso=/kanotix/K*.iso noprompt noeject lang=en apm=power-off nomce quiet
initrd (hd0,4)/kanotix/miniroot.gz

With next boot we have a new menu item in grub to start the iso image.

[http://www.kanotix.com/FAQ-id_cat-63.html#q298](http://www.kanotix.com/FAQ-id_cat-63.html#q298)

I know it's for grub=-legacy but should be possible to work up a stanza for grub2??

---

### Post by ranch hand on 2011-05-28
The problem that I see in the current Kanotix ISO with trying that solution is the absents of any .gz file at all.

I just when though it again and there is no;
> 
# cp /mnt/test/boot/miniroot.gz /media/hda5/kanotix/

at all.

For that matter there is not miniroot file of any kind.

Kind of a strange image, at least to me.

---

### Post by Jose Catre-Vandis on 2011-06-03
What's in the boot directory of the iso?

---

### Post by ranch hand on 2011-06-03
> **Jose Catre-Vandis said:**
> What's in the boot directory of the iso?
I may be more simple than I thought.  Just looked at the /isolinux/ part of the ISO and there I found the "live.cfg".  Opening that gives;
> 
label live-en
    menu label Kanotix - EN
    kernel /live/vmlinuz
    append initrd=/live/initrd.img boot=live config utc=yes locales=us quiet splash

among a number of other translations.

Have to play with that a bit I guess.

---

### Post by Quackers on 2011-06-04
I am pleased to say that I have managed to get the Fedora 15 live desktop booting direct from the grub2 menu, though it doesn't actually use the iso file itself, but extracted files from within it.
This may be useful for other iso files that are not constructed in the same way as Ubuntu iso files - but that remains to be seen :-)
Thanks to drs305 for his help in this matter and also to forum user sundar_ima (who wrote this thread and the script in it)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
who did all the original "legwork" involved and has helped me immensely in my quest. All I have done really, is to apply his work to this task.

I should say that this may not be the most elegant way of going about it, but it is the way I did it.

Firstly it is necessary to de-construct the Fedora iso file by mounting the iso as previously described in post #1 of this thread and literally copying some of the resulting files/directories to a separate directory. I created a directory in my home folder called "fedora" for this purpose.
I used the "Fedora-15-i686-Live-Desktop.iso" for this purpose. Other versions may be slightly different!

Extract the following files from the /LiveOS folder
livecd-iso-to-disk
osmin.img
squashfs.img

then extract the following files from the /isolinux folder
initrd0.img (whole .gz file)
vmlinuz0

putting all those files into your new folder. 

then copy that new directory to your Ubuntu root partition (or any chosen Linux root partition)

```
sudo cp -r /home/username/fedora /fedora
```
Obviously the name/path will change if you have done things differently.

then edit /etc/grub.d/40_custom to create your grub menu entry

```
gksu gedit /etc/grub.d/40_custom
```

and add this boot stanza

```
menuentry "Fedora 15" {
set root=(hd1,10)
linux /fedora/vmlinuz0 root=UUID="3623f412-ebb8-451c-aaa9-b7530196248b" live_dir=/fedora rootfstype=auto ro liveimg quiet  rhgb rd_NO_LUKS rd_NO_M
initrd /fedora/initrd0.img
}
```
But where mine uses (hd1,10) and UUID="3623f412-ebb8-451c-aaa9-b7530196248b" replace with your own address and UUID of your chosen root partition.

Then run ```
sudo update-grub
```
to put the new menu entry into grub.

Reboot and you should see Fedora 15 at the bottom of your grub menu. If you select it, it will hopefully boot the Fedora live desktop :-)

---

### Post by tsger on 2011-06-07
Anyone able to boot the Debian Live iso from Grub2?

---

### Post by drs305 on 2011-06-07
> **tsger said:**
> Anyone able to boot the Debian Live iso from Grub2?

I downloaded and tried but was unable using standard techniques. If nobody else replies, you might try Multisystem/Multiboot mentioned in Post # 137.

---

### Post by dancer_69 on 2011-06-14
Hello,
I'm trying to boot gentoo 11 live dvd from grub2 menu, but I have some problems.
Here is the menuentry which I have in 40_custom:

```
menuentry "Gentoo 11 Live DVD" {
insmod ntfs
set isofile="/gentoo-livedvd-x86-amd64-32ul-11.0.iso"
loopback loop (hd1,2)$isofile
linux (loop)/boot/gentoo root=/dev/ram0 init=/linuxrc dokeymap looptype=squashfs loop=/image.squashfs cdroot initrd=gentoo.igz isoboot=/gentoo-livedvd-x86-amd64-32ul-11.0.iso
initrd (loop)/boot/gentoo.igz

}
```
I have the gentoo iso file on root directory of an ntfs disk.
I copied the specific looptype entries from here:
[https://gist.github.com/907965](https://gist.github.com/907965)

The problem is that the kernel loads, but I get an error in some point:

media not found
could not find cd to boot, something else needed
Determining Root device....
could not mount specified ROOT, try again
could not find the ROOT block device in .

Any ideas?

---

### Post by C.S.Cameron on 2011-06-14
> **tsger said:**
> Anyone able to boot the Debian Live iso from Grub2?

Sundar seems to have it booting with the MultiBootUSB sctipt.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by drs305 on 2011-06-14
> **dancer_69 said:**
> Hello,
I'm trying to boot gentoo 11 live dvd from grub2 menu, but I have some problems.

The problem is that the kernel loads, but I get an error in some point:

media not found
could not find cd to boot, something else needed
Determining Root device....
could not mount specified ROOT, try again
could not find the ROOT block device in .

Any ideas?

I hadn't tried gentoo so I downloaded the iso and took a look. When I mounted it and looked at the file structure, I think I found at least one reason why your menu entry isn't booting:
> linux (loop)/boot/gentoo root=/dev/ram0 init=/linuxrc dokeymap looptype=squashfs loop=/image.squashfs cdroot [COLOR="Red"]initrd=gentoo.igz[/COLOR] isoboot=/gentoo-livedvd-x86-amd64-32ul-11.0.iso

The *gentoo.igz* file is located in the /boot folder, so I believe the address needs to be changed:
> 
linux (loop)/boot/gentoo root=/dev/ram0 init=/linuxrc dokeymap looptype=squashfs loop=/image.squashfs cdroot [COLOR="Red"]initrd=/boot/gentoo.igz[/COLOR] isoboot=/gentoo-livedvd-x86-amd64-32ul-11.0.iso


I tried booting the ISO with your menu entry and it failed. Once I made the change to the *gentoo.igz* location it booted to the sign in screen (I didn't have time to actually explore the contents). Other than my iso being on an ext4 partition and having a different iso location, everything else was the same.

---

### Post by dancer_69 on 2011-06-14
I can boot to gentoo, until I get the error described above.
The change to initrd=/boot/gentoo.igz didn't made any difference.
I'm stuck in the same point(when searching for media) and getting the above errors.
If you find a way, let me know.
Thanks.

---

### Post by drs305 on 2011-06-14
I tried again and this time actually booted into Gentoo without problems with the following menuentry. I was asked to select the keymap but otherwise it booted to the log in screen and allowed me to enter to the Gentoo Desktop.

The differences between my setup and yours: 
[LIST]
[*]My ISO is on sdb6 in the /iso folder.
[*]It is located on an EXT4 partition and not NTFS (although I left the insmod module line in the entry).
[*]The original file I downloaded did not include the "gentoo-" at the start. I renamed it so I know what the ISO is. I assume you did the same, unless you downloaded from a different source and it already included "gentoo-". I'm also assuming you have a 64-bit system.
[*]I am using Grub 1.99RC, although I don't think the changes affect this issue.
[*]I downloaded the ISO from: [http://mirrors.nl.kernel.org/gentoo//releases/amd64/11.0/]("http://mirrors.nl.kernel.org/gentoo//releases/amd64/11.0/")
[*]It's not a difference, but I found it odd that "initrd" is in the linux line but also has the normal "initrd" line.
[*]I also expected I might have to experiemnt with the "root=/dev/ram0" entry but it worked without modification. I also didn't find a "linuxrc" anywhere on the disk, again it didn't seem to make a difference.
[/LIST]

I've highlighted entries which would be different than yours:
> 
menuentry "Gentoo 11 Live DVD" {
insmod ntfs
set isofile="**/iso**/gentoo-livedvd-x86-amd64-32ul-11.0.iso"
loopback loop (**hd1,6**)$isofile
linux (loop)/boot/gentoo root=/dev/ram0 init=/linuxrc dokeymap looptype=squashfs loop=/image.squashfs cdroot initrd=**/boot/**gentoo.igz isoboot=**/iso**/gentoo-livedvd-x86-amd64-32ul-11.0.iso
initrd (loop)/boot/gentoo.igz
}

---

### Post by dancer_69 on 2011-06-14
I think that, the ntfs drive is more possible to make the difference(or the fact that I'm using a 32bit installation). I don't think that the existance of a folder in which is the isofile, could make a difference.
Anyway I will test both(to copy the iso to ext4 partition/put it on an iso folder) to see.

EDIT:
Same issue in both tests. Maybe I need an 64bit system.
I've tested the iso and it boots fine on virtual box, so the image isn't corrupted(I downloaded from gentto mirrors).
insmod ntfs or isoboot line don't made any difference either. Same issue either are there or not(for ext4 disk)

---

### Post by drs305 on 2011-06-14
I would not expect the 32-bit ISO to contain "amd64" in the name. I went back to the ISO download page and even when I selected "x86" it took me to the same "amd64" version (on several different mirrors). While I don't know anything about Gentoo, this strikes me as very odd and quite possibly a bug or link problem. If Gentoo is naming their 32-bit version "amd64" there are going to be a lot of confused users...

---

### Post by grubu on 2011-07-20
Hello drs305,

a big pack of  :popcorn: and a big thank you for sharing your guide.

Amazing! A solution on grub2, great! So I bet there are no difficulties
of booting your isos out of any kind of partition except a swap or a non-formated one :)

I played a long time with grub4dos, do you also know about it?
I think the contigous iso-image thing should be gone with grub2 also, right?

:guitar:

So we all have the possibility to work at what ever we want when also
having a partition or a file called 'casper-rw' containing our working-equipment
and we can decide to repair our broken ubuntu a litlle later. :P 
I dreamed of such a way and now its reallity, yeah! ;)

By the way give Slitaz a try one of the fastest booting isos I have seen.

[http://www.slitaz.org/en/](http://www.slitaz.org/en/)

Yours grubu

---

### Post by tumutanzi on 2011-07-22
Have never tested.

---

### Post by grubu on 2011-07-24
It seems that grub2 is not able to boot an iso-image from a ntfs-partition,
can someone agree to that fact ?

---

### Post by Quackers on 2011-07-24
Yes it can, but you need to add the line
insmod ntfs
at the start of the stanza.

---

### Post by grubu on 2011-07-24
Hi Quackers,

thanks for the fast answer. So if my first primary-partiton is a ntfs one,
I would just have something like that:

menuentry "Parted Magic 5.2 (i386 iso-image)" {
insmod ntfs
set isofile="/booting-isos/pmagic-5.2.iso"
loopback loop (hd0,0)$isofile
linux (loop)/pmagic/bzImage iso_filename=$isofile
 boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt
initrd (loop)/pmagic/initramfs
}

? Are there any other insmod switches for other kinds of partitions?

---

### Post by Quackers on 2011-07-24
I don't have a Parted Magic one (I use gparted live iso) but that looks reasonable if your Parted Magic iso is in a file called booting-isos in a NTFS partition.
Actually (hd0,0) won't work with grub2 I think. With grub legacy that might work but grub2 considers that partitions numbers begin at 1, iirc. That means that (hd0,0) should be (hd0,1) if the partition you are looking for is /dev/sda1

---

### Post by grubu on 2011-07-24
Ah very good to know I think I have read that somewhere before.
So I will keep this in brain first primary on old grub would always be (hd0,0)
and for grub2 it would be always (hd0,1).

I also found something like:
insmod part_msdos
insmod ext2

so maybe you can always put the insmod infront containing the partition-type you're using? like:

insmod part_msdos (should be a FAT16?)
insmod ntfs
insmod ext2
insmod ext3
insmod ext4

and the insmod iso9660 would declare the kind of the iso-image right?

---

### Post by Quackers on 2011-07-24
Here is my stanza in /etc/grub.d/40_custom for gparted, which is in a file called isofiles in a NTFS partition, sda4, for comparison.
```
menuentry "Gparted Live 0.8.0-3" {
insmod ntfs
set isofile="/isofiles/gparted-live-0.8.0-3.iso"
loopback loop (hd0,4)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
initrd (loop)/live/initrd.img
} 
```

---

### Post by drs305 on 2011-07-24
Adding **insmod ntfs** should be all that is required.

I copied my pmagic 5.2 iso over to an ntfs partition, added the ntfs module to the menuentry and it booted without any problem.

---

### Post by grubu on 2011-07-24
Thank you guys for the fast helping.
To get a better understanding on grub2 the insmod thing was left to know about.

I think normally I would put the isos into the fastest filesystem, by the way what 
do you prefer as iso-containing-fs, ext2? 
Did you count the booting times on different filesystems?

---

### Post by Quackers on 2011-07-24
I have no idea which is faster, if any.
Most of my isos are on a shared data partition of type NTFS. Grub2 boots them very quickly :-)

---

### Post by grubu on 2011-07-24
Yes, I think there should be no major advantages as just the one of the
filesystem itself. I think I would prefer an ext2 partition within an extended one
as iso-container. This could be a little slower because I would put a primary ntfs
and a primary swap infront of the extended one.

---

### Post by drs305 on 2011-07-24
I have never noticed a speed difference on my machine regarding which filesystem the ISO is stored on. 

In reference to one of the earlier posts regarding modules:

There is an ext2 module but no specific ext3 or ext4 modules - ext2 will do for all. 

Also, some modules may be loaded by default. One is usually part_msdos, for instance, which is loaded in the first part of grub.cfg (from the 00_header script).

If you are wondering which modules are loaded before any specific menuentry is run, at the Grub 2 menu press 'c' to get to the grub prompt and then type:
```
lsmod
```

---

### Post by grubu on 2011-07-24
Thank You drs305,

em maybe you also have a link for me where I can find a
reference on what can be done at the command-promt of grub2.

I am also searching on it at the moment. Oh, I think I found something here:
[URL="http://members.iinet.net/%7Eherman546/p20/GRUB2%20CLI%20Mode%20Commands.html"]http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html
[/URL]
Em Quackers,
as grub2 now begins with (hd0,1), we should have the fact that a
sudo fdisk -l
gives us exactly what we need so if we have for example
/dev/sda1   *        2048 ...  HPFS/NTFS
/dev/sda2 ....  82  Linux swap / Solaris
(hd0,1) is the ntfs and the swap is (hd0,2)
so the sda# will always be exactly the hd0,# ,right?
Let's say we have just one harddisk installed.

---

### Post by drs305 on 2011-07-24
> **grubu said:**
> em maybe you also have a link for me where I can find a reference on what can be done at the command-promt of grub2.

I am also searching on it at the moment. Oh, I think I found something here:
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)

Herman has been a Grub guru from long ago, initially with Grub legacy and now with Grub 2.

Here is the 'commands' section from the 'official' Grub 1.99 manual:
[http://www.gnu.org/software/grub/manual/grub.html#Commands]("http://www.gnu.org/software/grub/manual/grub.html#Commands")
Section 14.3 has a list of the grub terminal commands.

---

### Post by grubu on 2011-07-24
Thanks drs305,

> 
Herman has been a Grub guru from long ago, initially with Grub legacy and now with Grub 2.

Here is the 'commands' section from the 'official' Grub 1.99 manual:
[http://www.gnu.org/software/grub/man....html#Commands]("http://www.gnu.org/software/grub/manual/grub.html#Commands")
Section 14.3 has a list of the grub terminal commands.
that's exactly what I was looking for, great.

---

### Post by grubu on 2011-07-24
As the thread is called 'ISO Booting with Grub 2' it might be not the right place 
for this question so I will put it into your other thread called [[COLOR=green]Grub 2 Basics[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275&page=78").

---

### Post by grubu on 2011-07-27
Thank you Quackers, this one works like a charm, I just replaced the uuid by the label=name. 
It installed without any difficulties, all on just one hd, very nice. 
Fedora 15 was just installed without the bootloader and later then added by update-grub
from our loved 10.04 LTS on the other partition. This would be one of the easiest ways to 
test out the gnome3-platform :) thanks.

> **Quackers said:**
> I am pleased to say that I have managed to get  the Fedora 15 live desktop booting direct from the grub2 menu, though it  doesn't actually use the iso file itself, but extracted files from  within it.
This may be useful for other iso files that are not constructed in the  same way as Ubuntu iso files - but that remains to be seen :smile:
Thanks to drs305 for his help in this matter and also to forum user sundar_ima (who wrote this thread and the script in it)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
who did all the original "legwork" involved and has helped me immensely  in my quest. All I have done really, is to apply his work to this task.

I should say that this may not be the most elegant way of going about it, but it is the way I did it.

Firstly it is necessary to de-construct the Fedora iso file by mounting  the iso as previously described in post #1 of this thread and literally  copying some of the resulting files/directories to a separate directory.  I created a directory in my home folder called "fedora" for this  purpose.
I used the "Fedora-15-i686-Live-Desktop.iso" for this purpose. Other versions may be slightly different!

Extract the following files from the /LiveOS folder
livecd-iso-to-disk
osmin.img
squashfs.img

then extract the following files from the /isolinux folder
initrd0.img (whole .gz file)
vmlinuz0

putting all those files into your new folder. 

then copy that new directory to your Ubuntu root partition (or any chosen Linux root partition)

```
sudo cp -r /home/username/fedora /fedora
```Obviously the name/path will change if you have done things differently.

then edit /etc/grub.d/40_custom to create your grub menu entry

```
gksu gedit /etc/grub.d/40_custom
```and add this boot stanza

```
menuentry "Fedora 15" {
set root=(hd1,10)
linux /fedora/vmlinuz0 root=UUID="3623f412-ebb8-451c-aaa9-b7530196248b"  live_dir=/fedora rootfstype=auto ro liveimg quiet  rhgb rd_NO_LUKS  rd_NO_M
initrd /fedora/initrd0.img
}
```But where mine uses (hd1,10) and  UUID="3623f412-ebb8-451c-aaa9-b7530196248b" replace with your own  address and UUID of your chosen root partition.

Then run ```
sudo update-grub
```to put the new menu entry into grub.

Reboot and you should see Fedora 15 at the bottom of your grub menu. If  you select it, it will hopefully boot the Fedora live desktop :smile:

---

### Post by drs305 on 2011-07-28
I have installed without issue the Oneiric daily build several times in the past month from a partition-mounted ISO image. Today I noted I had to choose a user during start.

If you select the default, the "Install" icon does not appear on the Desktop (although it is the top item in the launcher). 

More importantly, when logging in with the default user you will be unable to gain admin privileges - there is no associated password.

To be able to use "sudo", log in by choosing 'Other', then enter "Ubuntu" with a blank password. Upon log in, the "Install" icon will be on the Desktop and the user will be able to invoke "sudo" (no password will be requested).

I don't know how long the Oneiric LiveCD will act this way, but I thought I'd note it here.

---

### Post by grubu on 2011-08-23
Hello there, here is another one, you should give it a try,
 I really like this amazing Linux-Project. Thanks to Patrick Verner 
for realizing Parted Magic, it seems to be the best solution for getting 
hands onto a broken system by providing a lot of very useful utilities. 

Parted Magic was last updated on 2011-08-04,
you can find it at [http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)

This one was downloaded in my case and put into /dev/sda8/isofilesdirectory:
[http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%206.6/pmagic-6.6.iso/download]("http://sourceforge.net/projects/partedmagic/files/partedmagic/Parted%20Magic%206.6/pmagic-6.6.iso/download")
 
```

menuentry "Parted Magic 6.6 Iso-Image" {
isofile=pmagic-6.6.iso
loopback loop (hd0,8)/isofilesdirectory/$isofile
linux (loop)/pmagic/bzImage iso_filename=/isofilesdirectory/$isofile edd=off noapic 
load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=0 loglevel=0 keymap=us vga=791
initrd (loop)/pmagic/initramfs
}

```For further information on the next iso have a look at the gNatty Gnome Live ISO thread
at: [http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

you should give [cbowman57]("http://ubuntuforums.org/member.php?u=1089002")'s ubuntu natty with gnome3 build-in a try by

> **grubu said:**
> 
```

menuentry 'gNatty cbowman-s Gnome3 amd64 v3 Live CD ISO' {
isofile=gnatty-amd64-v3.iso
loopback loop (hd0,8)/isofilesdirectory/$isofile
linux (loop)/casper/vmlinuz boot=casper 
iso-scan/filename=/isofilesdirectory/$isofile noprompt noeject nosplash  quiet locale=en_US bootkbd=us console-setup/layoutcode=us  gfxpayload=1024x768x16
initrd (loop)/casper/initrd.lz
}

```Both isos were tested on an ubuntu-natty 11.04 amd64 machine

---

### Post by Dezfor on 2011-09-06
Thanks, thread helped me. But I still can't boot backtrack-linux with Grub2. BT5 is based on Ubuntu distro, so I tried to boot it with Ubuntu's options:
```
menuentry "BT5-GNOME-32" {
set isofile="/BT5-GNOME-32.iso"
loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
But this doesn't work. Could somebody help me with this issue?

---

### Post by drs305 on 2011-09-06
> **Dezfor said:**
> Thanks, thread helped me. But I still can't boot backtrack-linux with Grub2. BT5 is based on Ubuntu distro, so I tried to boot it with Ubuntu's options:
```
menuentry "BT5-GNOME-32" {
set isofile="[COLOR="Red"]**/**[/COLOR]BT5-GNOME-32.iso"
loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
But this doesn't work. Could somebody help me with this issue?

Are you getting a "you must load the kernel first" type message. If so, it's not finding the kernel file. Is the filename uppercase?

It could be the way you have set the isofile. Try this (omitting the / from the iso title and adding it on the loopback line):

> menuentry "BT5-GNOME-32" {
set isofile="BT5-GNOME-32.iso"
loopback loop (hd0,2)**/**$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

Normally I download the ISO and try to come up with the correct settings. I did this for BT4 but the ISO size is just too large for me to do it again for BT5.

---

### Post by agibby5 on 2011-09-06
> **greenclone said:**
> I was trying to install Ubuntu 10.10 Server (32-bit, x86) from hard disk, but when I used vmlinuz and initrd.gz from installation CD, I couldn't get it to work.
I used configuration
Installation started, but after initial questions about language and keyboard, it reported error that it couldn't mount installation CD.

However, it worked :D when I used vmlinuz and initrd.gz from Ubuntu archives [http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/hd-media/). I have placed the files in the same directory as iso file, and changed my configuration to:
Any thoughts on why it didn't work with vmlinuz and initrd.gz from installation CD?

Were you able to get the install to complete?  This gets me past not being able to boot but when I get past selecting the keyboard layout, I get errors about not being able to find the installer ISO.  Ideas?

I'm using the following:
```
menuentry "Ubuntu Server 10.04.3 x64" {
    set root=(hd0,5)
    set isofile="/boot/isos/ubuntu-10.04.3-server-amd64.iso"
    loopback loop $isofile 
    linux /boot/vmlinuz/vmlinuz iso-scan/filename=$isofile noeject noprompt
    initrd /boot/vmlinuz/initrd.gz
}
```

---

### Post by SPK201 on 2011-09-11
> **Quackers said:**
> I am pleased to say that I have managed to get the Fedora 15 live desktop booting direct from the grub2 menu, though it doesn't actually use the iso file itself, but extracted files from within it.
This may be useful for other iso files that are not constructed in the same way as Ubuntu iso files - but that remains to be seen :-)
Thanks to drs305 for his help in this matter and also to forum user sundar_ima (who wrote this thread and the script in it)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
who did all the original "legwork" involved and has helped me immensely in my quest. All I have done really, is to apply his work to this task.

I should say that this may not be the most elegant way of going about it, but it is the way I did it.

Firstly it is necessary to de-construct the Fedora iso file by mounting the iso as previously described in post #1 of this thread and literally copying some of the resulting files/directories to a separate directory. I created a directory in my home folder called "fedora" for this purpose.
I used the "Fedora-15-i686-Live-Desktop.iso" for this purpose. Other versions may be slightly different!

Extract the following files from the /LiveOS folder
livecd-iso-to-disk
osmin.img
squashfs.img

then extract the following files from the /isolinux folder
initrd0.img (whole .gz file)
vmlinuz0

putting all those files into your new folder. 

then copy that new directory to your Ubuntu root partition (or any chosen Linux root partition)

```
sudo cp -r /home/username/fedora /fedora
```
Obviously the name/path will change if you have done things differently.

then edit /etc/grub.d/40_custom to create your grub menu entry

```
gksu gedit /etc/grub.d/40_custom
```

and add this boot stanza

```
menuentry "Fedora 15" {
set root=(hd1,10)
linux /fedora/vmlinuz0 root=UUID="3623f412-ebb8-451c-aaa9-b7530196248b" live_dir=/fedora rootfstype=auto ro liveimg quiet  rhgb rd_NO_LUKS rd_NO_M
initrd /fedora/initrd0.img
}
```
But where mine uses (hd1,10) and UUID="3623f412-ebb8-451c-aaa9-b7530196248b" replace with your own address and UUID of your chosen root partition.

Then run ```
sudo update-grub
```
to put the new menu entry into grub.

Reboot and you should see Fedora 15 at the bottom of your grub menu. If you select it, it will hopefully boot the Fedora live desktop :-)

I followed your instruction, but when I try to boot Fedora, it says that the Kernel can't be initialized. I doubt this can even work with only 5 files from the .iso.

Are you sure that I don't need the full .iso to be present somewhere?
And why do you link a MultiBoot USB topic, does it have anything to do with the Fedora Grub 2 boot? What if I don't have a USB bootable PC?

I hope someone can solve the mysteries.

---

### Post by buntu63 on 2011-09-18
> **drs305 said:**
> [CENTER][SIZE=4]**[COLOR=DarkRed]ISO Booting with Grub 2[/COLOR]**[/SIZE][/CENTER]



hi! can i do that with a mint 11 LXDE .iso that i need to mount on other box?

---

### Post by drs305 on 2011-09-18
> **buntu63 said:**
> hi! can i do that with a mint 11 LXDE .iso that i need to mount on other box?

I haven't tested Mint 11, but you should be able to do it using the standard ISO menuentry. Mint uses the same structure as Ubuntu.

---

### Post by buntu63 on 2011-09-18
it'd be hipernice do it with some 'tool' automatically :emo lazy: :p

---

### Post by Dezfor on 2011-10-16
> **Dezfor said:**
> Thanks, thread helped me. But I still can't boot backtrack-linux with Grub2. BT5 is based on Ubuntu distro, so I tried to boot it with Ubuntu's options:
```
menuentry "BT5-GNOME-32" {
set isofile="/BT5-GNOME-32.iso"
loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
But this doesn't work. Could somebody help me with this issue?

> **drs305 said:**
> Are you getting a "you must load the kernel first" type message. If so, it's not finding the kernel file. Is the filename uppercase?

It could be the way you have set the isofile. Try this (omitting the / from the iso title and adding it on the loopback line):



Normally I download the ISO and try to come up with the correct settings. I did this for BT4 but the ISO size is just too large for me to do it again for BT5.
A have a trouble with loading VFS. Here is report picture: [http://img846.imageshack.us/img846/506/img4613l.jpg](http://img846.imageshack.us/img846/506/img4613l.jpg)

---

### Post by drs305 on 2011-10-16
> **Dezfor said:**
> A have a trouble with loading VFS. Here is report picture: [http://img846.imageshack.us/img846/506/img4613l.jpg](http://img846.imageshack.us/img846/506/img4613l.jpg)

This is the standard error when the kernel or initrd image can't be found or loaded for some reason. You can see in the messages that it is suggesting the "root=" entry (probably in your 'linux' line) is in error, meaning it's not finding the files.

Have you read posts 41-48. I dealt with BT earlier and wasn't able to come up with a solution. I did discover that, at least at the time, BT was using Grub legacy and so the ISO was probably not being constructed to boot from an ISO. Things may have changed since then since it's now version 5...

As suggested in one of those posts, you might try mounting the ISO with 'loop' in a running Linux OS so you can explore what and where files are included. Check that the initrd image is an 'lz' and not a 'gz', etc.

---

### Post by Dezfor on 2011-10-16
> **drs305 said:**
> This is the standard error when the kernel or initrd image can't be found or loaded for some reason. You can see in the messages that it is suggesting the "root=" entry (probably in your 'linux' line) is in error, meaning it's not finding the files.

Have you read posts 41-48. I dealt with BT earlier and wasn't able to come up with a solution. I did discover that, at least at the time, BT was using Grub legacy and so the ISO was probably not being constructed to boot from an ISO. Things may have changed since then since it's now version 5...

As suggested in one of those posts, you might try mounting the ISO with 'loop' in a running Linux OS so you can explore what and where files are included. Check that the initrd image is an 'lz' and not a 'gz', etc.
Thanks for explanation. I've just read your posts 41-48. BT5 has initrd.**gz**. I can extract it later and look at grub version.

---

### Post by drs305 on 2011-10-16
> **Dezfor said:**
> Thanks for explanation. I've just read your posts 41-48. BT5 has initrd.**gz**. I can extract it later and look at grub version.

Thanks for posting the update. It would be nice if it now uses Grub 2, but the Ubuntu releases transferred to .lz so I would guess BT is still not quite the same. But let us know about BT5.

---

### Post by Dezfor on 2011-10-16
> **drs305 said:**
> Thanks for posting the update. It would be nice if it now uses Grub 2, but the Ubuntu releases transferred to .lz so I would guess BT is still not quite the same. But let us know about BT5.

BT5 uses Grub 2 ;)

P.S. I found my mistake - I used lz instead of gz in boot options. Now I get other error while booting:
> init: line 3: can't open /dev/sdb no medium found
init: line 3: can't open /dev/sr0 no medium found

The same error is given in post 129 and solution is given in 135,136. I'll try tomorrow something to do with it

**P.S.**
I won't try to launch it due to lack of time

---

### Post by klein de usa on 2011-11-15
hi 
i'm having a problem getting grub to display a menu entry from 40_custom file. and i can't figure out why. i'm trying to boot a iso file in /home/isos/clonezilla-live-1.2.10-14-amd64.iso. the bad part is, it is the second machine i have done this too and the first machine was a mess also i'm not sure how i got it to pick up the menu entry but it is there. and boots clonezilla fine.

now i'm on the second machine and i can't get it to pick up the menu entry, i have grub customizer installed, i changed the resolution to 1024x768x16 and have a picture being displayed.

i have run update-grub and the 40_custom file is in grub.cfg 
when i open up grub customizer clonezilla live is displayed with a check beside it.
but it isn't being displayed when i boot grub. 

i went in and took the check out of grub customizer setting it back to what ever the default video resolution is and disabled the picture rebooted and still no menu entry for clonezilla 

so i went in grub.cfg file and took out the text that was added from the 40_custom file the lines with # the warning, rebooted and still no entry for clonezilla.

i have the two computers where i can see both screens at the same time and as far as i can tell the 40_custom entries are the same, is there anything else i can try ?

the only thing is both have pcie nvidia cards one computer is a dell the other is a hp both running 10.04.3 64bit. but i can't see the video cards being the problem.

---

### Post by klein de usa on 2011-11-15
update i spoke too soon 
as a last ditch effort i copied my 40_custom file from the working computer to the computer i was still having problems with, and it worked, i had copied and pasted from gedit before, must of been something grub didn't like about that. 

when i started this i was going to put it on it's own partition but was having problems with it, but having it on sda2 /home/isos worked well and clonezilla will back up sda2 even though that is where the iso file is.

---

### Post by drs305 on 2011-11-15
Edit: Nevermind. I see you have solved the issue.

> **klein de usa said:**
> hi 
i'm having a problem getting grub to display a menu entry from 40_custom file. and i can't figure out why. 

Since you say the 'update-grub' command is locating the 40_custom file, are you sure the Grub menu you see at boot is the same Grub menu you are editing? If you have more than one linux OS on your computer it's possible that another OS's Grub is the one displaying the menu. 

You can usually tell by looking at the top menu entry if you haven't adjusted the order of the grub scripts (10_linux, then 30_os-prober, then 40_custom). Another way I sometimes check is to manually edit /boot/grub/grub.cfg and make a typo in the first entry's title and see if that appears in the menu (don't update-grub in this case, as it would erase any manual entry you make).

If you run the boot info script and post the RESULTS.txt we may be able to tell why it's not showing up. There's a link to the script in my signature line, "BIS".

---

### Post by aurelianox on 2011-11-15
Hi,
I've a laptop with a broken cd, no usb-boot bios and an dual-boot system (xp/ubuntu) on it. I want to upgrade to Oneiric but I was able only to start the Oneiric-ISO live. When I try to install it (firstly on /), it stops the installation procedure because of  the ISO-file is on a mouted partition.
I've tried to get around it by moving the ISO-file to the Windows-partition, by insmod module, but despite the ISO-file boot normally I've the same problem with mounted partition.
I think it's because both partitions (sda1-sda2) are in the same disk (sda), but being on a laptop, it could not be otherwise.
Any suggestions?
Thanks

---

### Post by drs305 on 2011-11-15
aurelianox,

Welcome to the Ubuntu forums!

If you boot the Ubuntu ISO to the Desktop and then click on "Install", the first time it stops to ask you for input open a terminal and run the following command:
```
sudo umount -lrf /isodevice
```
Then continue with the installation. You shouldn't get the "mounted" error message any longer.

I haven't had the 'sda' problem, which may be because the times I've installed the ISO it has been on a different drive's partition. I can't remember, so let me know if the 'sda' error message persists.

---

### Post by aurelianox on 2011-11-19
Thank you so much,
your suggestion worked!
I think it would be useful if you put this little trick on the wiki page for those that have only one disk on own pc, like notebooks, and would like to install the ISO.
Thank again,
regards.

---

### Post by drs305 on 2011-11-19
> **aurelianox said:**
> Thank you so much,
your suggestion worked!
I think it would be useful if you put this little trick on the wiki page for those that have only one disk on own pc, like notebooks, and would like to install the ISO.
Thank again,
regards.

Glad it worked.

I've added a note in the introduction section of this thread about another one I created which details installing Ubuntu from an ISO file:
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

The Ubuntu community doc I wrote about [_GRUB2_]("https://help.ubuntu.com/community/Grub2") has already been identified as being too long. I don't have a section in the 'official' documentation about how to boot from an ISO. It would probably make a useful independent page.

---

### Post by mcgrete on 2012-01-05
> **cbowman57 said:**
> Thanks drs305,

My goal was a bootable clonezilla, with your help and after fixing a couple typos from the clonezilla site I was successful.  This is my entry for anyone that might benefit, it boots from my maintenance partition located on sda9.

menuentry "Clonezilla live" {
set isofile="(hd0,9)/clonezilla-live-1.2.8-3-amd64.iso"
loopback loop $isofile 
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

> **Jack Smith said:**
> Thank you!  
Thank you!
Thank you!
Thank you!
THANK YOU!!!  
 
I have been bouncing my brain off of this same problem for a good 16 hours now... and was finding nothing but outdated info or solutions that didn't work.  This fixed it and clonezilla is Alive!  along with ubuntu full install, hirens, bitdefender, ubuntu live cd... the list goes on, all from my USB drive.  now to get win7PE working...
 
Again, Thank you to Drs305 for this amazing thread, and thank you to quakers for being specific.


***************
**pythonscript & cbowman57:**
I have had troubles getting this to work.  Struggled for some time :confused:; found this tweak. Was partially successful - not exactly what I was looking for, but perhaps my goal was unattainable.

I vave 10.04LTS and 11.10 installed, both with separate / and /home partitions.  All installed on logical partitions.  Other primary partitions exist.  All on /dev/sdb.  Other drive is /dev/sda, which has Windows partitions only.  I have GRUB2.  I modified "40_custom" file, saved configuration, and loaded into MBR which is on /dev/sda.  (Used Grub Customizer)

1) I tried to create a partition /dev/sdb11 (ext3) that only contains the clonezilla iso file (no OS).  Tried:
#menuentry "Clonezilla live" {
#set isofile="(hd1,11)/clonezilla-live-1.2.11-23-amd64.iso"
#loopback loop $isofile
#linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" #ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
#initrd (loop)/live/initrd.img

Results:
error: cannot read the Linux header.
error:  you need to load the kernel first.

2) I also tried placing iso file in both / directories for /dev/sdbXX, where XX is partition for 10.04LTS or 11.10 respectively.  Modified path:
set isofile="(hd1, 8 )/media/Ub11.10ROOT/clonezilla-live-1.2.11-23-amd64.iso" # Had to add spaces before & after '8' to avoid Smilies appearing...
and
set isofile="(hd1,9)/clonezilla-live-1.2.11-23-amd64.iso"

Results: failed.
11.10 -->
error: file not found
error: cannot read the Linux header.
error:  you need to load the kernel first.
10.04LTS -->
script started to run...ended with indefinite loop:
/init : line7: /lib/udev/path_id: not found
/init : line7: /lib/udev/path_id: not found
/init : line7: /lib/udev/path_id: not found...

**Saw the tweak from cbowman57, and tried it.**
Case A:
menuentry "2-Clonezilla live" {
set isofile="/clonezilla-live-1.2.11-23-amd64.iso"
loopback loop (hd1,11)$isofile
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}
Result: 
error: cannot read the Linux header.
error:  you need to load the kernel first.

**Case B & C below, both worked with cbowman57's tweak.**
# Case B
menuentry "2-Clonezilla live from 11.10ROOT..." {
set isofile="/clonezilla-live-1.2.11-23-amd64.iso"
loopback loop (hd1, 8 )$isofile # Had to add spaces around '8' to avoid Smilies appearing...
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}
# Case C
menuentry "2-Clonezilla live from 10.04LTS ROOT..." {
set isofile="/clonezilla-live-1.2.11-23-amd64.iso"
loopback loop (hd1,9)$isofile
linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" ocs_live_keymap=\"\" ocs_live_batch=\"no\" ocs_lang=\"\" vga=788 ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}


**So, the recent iso file doesn't have some of the issues with initrd.img file as in the past from earlier in this thread**.:D

**Question:**  I am confused.  It appears that I need to boot an OS in order to launch the iso file, as my Case A fails.  :confused:Is that correct?  If not, then how might I be successful to boot with is from /dev/sdb11?  

**Otherwise, I have the following question**:  If I use Case B (11.10 Ubuntu with ClonezillaLive-iso), will I have any issues attempting to use CloneZilla to backup the / and /home partitions for 11.10 distro?  

Similarly, if I use Case C, will I have issues attempting to backup / and /home for 10.04LTS?

I hate to appear lazy, I only just now got CloneZilla to launch at boot after hours of web searching and trials and I have not tested my question above. Was hoping to save time, as it was not clear to me from earlier posts and questions.  Also, I really would like the ability to boot from /dev/sdb11.

Request for pythonscript:  Could you update the original post that references cbowman57's menuentry to now include his tweak?  That would have save me quite a bit of time, perhaps it will help others.  Also, might want to reference caution on versions of CloneZilla iso's with regards to initrid.img / initrid1.img in #69, and indicate that "clonezilla-live-1.2.11-23-amd64.iso" is release (apparently) with initrid.img in format desired without kernel issues.

Thanks!

---

### Post by HittingSmoke on 2012-01-07
I came here looking for a solution to dual booting an Ubuntu live USB drive with a Windows installer.

It appears this hasn't been solved here yet, but I'd like to know if anyone's made any progress on this.

I see a lot of people saying it's not possible. However, YUMI supports dual booing with Linux (and other) live environments along side Windows installers using syslinux.

Would it be possible to point GRUB to a syslinux configured to boot the Windows installers?

---

### Post by drs305 on 2012-01-07
HittingSmoke

The only syslinux menuentry I've played with was for booting the SuperGrub iso. This is the format I had to use. I doubt it will help you a lot, but I don't use Windows enough to provide anything else:
```
menuentry "Super GRUB2 Disk v1.98s1" {
isofile="/iso/super_grub_disk_hybrid-1.98s1.iso"
insmod memdisk.mod
linux16 (hd0,13)/usr/lib/syslinux/memdisk iso bigraw
initrd16 (hd1,6)$isofile
}
```

---

### Post by miyalys on 2012-01-27
Thank you for writing this guide, drs305! This process of trying to get this to work has helped me understand GRUB2 and GRUB in general better.
For some reason, though, I still can't get it to work.

This is in my 40_custom:
```
menuentry "ubuntu-11.10-desktop-i386.iso" {
    insmod ext2
    set isofile="(hd0,9)/images/ubuntu-11.10-desktop-i386.iso"
    loopback loop $isofile
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet noprompt splash
    initrd (loop)/casper/initrd.lz
}
```The image is on sda9, an ext4 partition, which is also /, and the iso is in /images/ubuntu-11.10-desktop-i386.iso
I just added "insmod ext2" as a test to see if that made a difference, but it didn't.

However whenever I select it in the menu my computer gives no feedback whatsoever and reboots immediately! Strange.

EDIT: My distro is Arch Linux if that makes any difference? Is "iso-scan" distribution specific?

I've also crosschecked with this [https://wiki.archlinux.org/index.php/Grub2#Booting_an_Ubuntu_ISO_Image_from_the_GRUB2_Screen](https://wiki.archlinux.org/index.php/Grub2#Booting_an_Ubuntu_ISO_Image_from_the_GRUB2_Screen)

...(which uses "iso-scan"), but it still just reboots my computer.

---

### Post by drs305 on 2012-01-27
Biowaste,

I tried rebooting into my 11.10 ISO and it 'booted' normally. I then tried modifying your menuentry for my ISO location and it failed with reclying 'ordered data mode' errors. 

I tried altering two of your settings but it still failed, so here is my working entry, modified to your settings. 

```

menuentry 'ubuntu-11.10-desktop-i386.iso'                        {
isofile=ubuntu-11.10-desktop-i386.iso
loopback loop (hd0,9)/images/$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/images/$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

```

Try this as an entry and see if it works. 

The easiest way may be to just cut/paste the above to /etc/grub.d/40_custom and update grub. That should put it at the bottom of your existing menu choices as long as 40_custom is executable.

---

### Post by oldfred on 2012-01-27
I also made this mistake the first time. The hd0,9 cannot be in the set iso file as the second use of the $isofile should not have it.
Note that drs305 has it correct.

set isofile="[COLOR=Red](hd0,9)[/COLOR]/images/ubuntu-11.10-desktop-i386.iso"

Should be:
set isofile="/images/ubuntu-11.10-desktop-i386.iso"

And then only the next line has the drive, partition:
loopback loop [COLOR=Red](hd0,9)[/COLOR]$isofile

Whether the / or /images is in the set iso or not is not critical but you need it in all places.

---

### Post by miyalys on 2012-01-27
Thanks, drs305!

I deleted all the old entries from trying to get it to work from 40_custom, copy pasted yours
and updated grub.cfg with the "sudo grub-mkconfig -o /boot/grub/grub.cfg" command, but it still just reboots my computer. 

I wondered if the error relates to the .iso, but then I just tried with a 64-bit iso, changing the name accordingly, but that didn't work either, and the i386 iso also worked fine when I just tried to mount and browse around in it. I also tried to find some sort of grub2-log, but no luck with that either.

EDIT: Right, oldfred! Thanks for the info which will get me one step closer, but it appears it still doesn't work on my end. Maybe something else is (also) causing it?

---

### Post by drs305 on 2012-01-27
Biowaste,

You could write the menuentry lines down, boot to the Grub menu, and then press 'c' to get to the Grub prompt.

Then type each line (excluding the 'menuentry' line itself) and press ENTER to see if any errors are generated. This would find errors such as partition number or drive number, filename issues, etc.

If you get no feedback after entering all the lines, press CTRL-x to boot what you have entered to see if it boots.

If not, can you tell what the error messages are as it boots?

I don't know of differences between Arch and Ubuntu's grub. I do know Ubuntu has made some changes, but I wouldn't expect them to affect this issue. And Grub 1.99 and Grub 1.98 shouldn't make a difference either AFAIK.

---

### Post by miyalys on 2012-01-29
I tried typing in the lines manually, changing the iso file name to 1.iso to eliminate the risk of that being the error, and using an ubuntu x64 image. The first two lines were accepted, no complaints, but when I typed in the third:
```
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/images/$isofile noprompt noeject
```
...it rebooted instantly, no messages. I then tried to type it in again, this time changing the parameters to the ones used in the arch example*, ie.
```
quiet noeject nopromt splash --
```, but it still just rebooted instantly. Strange.

* [https://wiki.archlinux.org/index.php/Grub2#Booting_an_Ubuntu_ISO_Image_from_the_GRUB2_Screen](https://wiki.archlinux.org/index.php/Grub2#Booting_an_Ubuntu_ISO_Image_from_the_GRUB2_Screen)

---

### Post by drs305 on 2012-01-29
> **Biowaste said:**
> 
...it rebooted instantly, no messages. I then tried to type it in again, this time changing the parameters to the ones used in the arch example*, ie.
```
quiet noeject nopromt splash --
```, but it still just rebooted instantly. Strange.

It has me puzzled as well. I just rebooted and tried typing the commands manually. Even made intentional typos (such as 'nopromt') but could not get it to abort and reboot.

Here are a few very random thoughts.

You tried the 64-bit version. I assume your system is 64-bit capable.

After entering the first two lines, try:
"set" and review what Grub 2 is about to use.
"ls (loop)/casper/" to make sure Grub 2 can actually see 'vmlinuz'

---

### Post by miyalys on 2012-01-29
Success! :KS

Those two commands you posted made me find the reason, which could've probably been found had I posted my grub.cfg earlier, so you could've spotted the somewhat newbieish error on my part.
After looking through the output of set, and seeing ls (loop)/casper/ also rebooting my computer, I looked more closely at ls, which gave me the partition names hd0,msdos1, hd0,msdos2 etc. incl. msdos9. I then tried that name, hd0,msdos9, instead, and am now inside an Ubuntu live disk! I don't really understand why GRUB2 just reboots, instead of outputting some error, ideally saying the partition doesn't exist?

Arch writes about partition naming right here, but it's probably GRUB2 universal?:
"Device naming has changed between GRUB and GRUB2. Partitions are  numbered from 1 instead of 0 while drives are still numbered from 0, and  prefixed iwith partition-table type. For example, [COLOR=#222][FONT=monospace]/dev/sda1[/FONT][/COLOR] would be referred to as [COLOR=#222][FONT=monospace](hd0,msdos1)[/FONT][/COLOR] (for MBR) or [COLOR=#222][FONT=monospace](hd0,gpt1)[/FONT][/COLOR] (for GPT) using GRUB2.":
[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)

I had noticed those msdosX-names before, but I didn't realise it was GRUB2s (only) names of my partitions, also when I knew those partitions were ext2, ext4 and so on. But apparently, because Windows was installed first to prevent all that Windows refusing to cooperate with other OS's with boot.ini/ntldr, the partition table itself is somehow specifically Windows-like. Inside fstab, mtab etc. they're all called sda9 and so on, so no msdosX there.

Thanks for guiding me through this and making this work, and sorry about not realizing this sooner on my part, looking at grub.cfg. I've written some of this information on GRUB2 down and will add set and ls as general trouble shooting tools within the GRUB prompt, for the next time I need to fix some problem or make something work within it! :)

EDIT: Actually, after more experiments, it appears as if it works regardless of whether I use hd0,9 or hd0,msdos9. What made the difference was that I explicitly added "insmod iso9660" as a test beforehand.

---

### Post by mikewhatever on 2012-02-08
Hi,
been trying to boot the daily ISO of precise, and, though a menu entry is added to grub.cfg, it does not appear at boot.

```
/etc/grub.d/40_custom

#!/bin/sh
echo "Adding 40_custom." >&2 
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Precise ISO" {
set isofile="/boot/iso/precise-desktop-amd64.iso"
loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
} 

```

```

~$ ls /boot/iso
precise-desktop-amd64.iso

```

Grub.cfg at pastebin: [http://pastebin.com/denVHDmi](http://pastebin.com/denVHDmi)

---

### Post by oldfred on 2012-02-08
@mikewhatever
Did you paste your 40_custom directly into grub.cfg and not into 40_custom and run sudo update-grub?

---

### Post by mikewhatever on 2012-02-08
No, I've done exactly as instructed in post #1, pasted the lines into 40_custom and ran update-grub.
Is something wrong with grub.cfg?

Here's what I get when updating grub:
```

~$ sudo update-grub
[sudo] password for hp: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Adding 40_custom.
done


```

However, on reboot, there are the regular Ubuntu lines and WindowsXP, but nothing else.

---

### Post by oldfred on 2012-02-08
Previous poster added this:
insmod iso9660

I still boot with 11.10 so my version of grub is a bit older. This is my entry, but I boot from a gpt drive, so I have the insmod part_gpt.

```
menuentry "Ubuntu 12.04 Precise ISO 64bit" {

    set isofile="/iso/precise-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd0,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}
```

---

### Post by mikewhatever on 2012-02-08
Adding 'insmod iso9660' didn't make a difference.

---

### Post by drs305 on 2012-02-08
Mike,

Are you sure the Grub you are updating is the one controlling your boot? If you have more than one OS with Grub, it could be another OS's grub is controlling the boot and that is why you aren't seeing the 40_custom addition. 

In cases like this, I either check the first entry in the Grub menu to see which kernel it is, or if I have multiple OS's with the same kernel, I make a deliberate typo in the first menuentry of grub.cfg (but don't update-grub) to ensure I'm working with the correct files.

You make the OS your are currently working in the default as far as grub is concerned by running, with X being the drive letter (a,b,c, etc):
```
sudo grub-install /dev/sdX
```

---

### Post by mikewhatever on 2012-02-08
Nah..., I only have Ubuntu 10.04 and Windows XP, so there is only one installation of Grub. There aren't any boot partitions either.

```

~$ sudo fdisk -l
[sudo] password for hp: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3609    28989261    7  HPFS/NTFS
/dev/sda2            3610        9730    49161216   83  Linux


```

Could it be that grub2 in Lucid doesn't support booting ISOs?

---

### Post by oldfred on 2012-02-09
I am primarily using Maverick and I am sure I booted ISO with Lucid.

I know the newer versions of grub 1.99 do not like typos. I had a typo in my 40_custom from the beginning but when I upgraded to grub 1.99 my 40_custom would not update. I found it was writing an error file. Once I fixed typo it was ok. Do you have another copy of grub.cfg, I forget what it renamed it but it was obvious it was an error of grub.cfg.

---

### Post by mikewhatever on 2012-02-09
Oldfred, no, there is only one copy of grub.cfg:
```
~$ ls /boot/grub | grep grub
grub.cfg
grubenv

```

---

### Post by drs305 on 2012-02-09
I'll try to use your menuentry the next time I boot and see what happens on my machine.

Just tagging on what *oldfred* stated with my own experience. On the occasions my entry was erroneous, there were times I ran the update-grub command, saw the command progressing through the various scripts, but failed to notice the final terminal output which said there was an error in the script. 

If Grub finds an error, it tells you and the grub.cfg file is not updated. I only noticed it when my grub file didn't change ( I had it open in a text editor) and I went back and inspected the terminal output.

---

### Post by drs305 on 2012-02-09
Ok, I added your custom file to /etc/grub.d/ , made it executable and it was added to the grub.cfg menu and was visible on booting. After manually adjusting values for it's location on my computer the menuentry booted correctly.

Since your custom menu is 40_custom and will appear at the bottom of the menu, have you tried scrolling down to make sure the final entry isn't 'hidden' below the visible menu?

Also, have you tried editing the name in the first menuentry of grub.cfg and made sure that name appears at the top of your menu on booting. It's just another confirmation that the menu you are editing is the one that you see. 

In a similar vein, you could try renaming the comment in the 40_custom file to something more customized, such as *echo "Adding my_40_custom." >&2 * to make sure that is the one you see in the terminal as you run the update-grub command. If you experiment with this, do it first and run update-grub before tweaking the menuentry title technique in the previous paragraph, since that change would be erased.

---

### Post by mikewhatever on 2012-02-09
Thanks for your input, drs305 and oldfred. As you can imagine, I've been looking for typos, errors and double grub.cfg files, but found none so far.

I've changed 'Adding 40_custom.' to 'Adding my_40_custom, and hello drs305 and oldfred', and sure enough:
```

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Adding my_40_custom, and hello drs305 and oldfred
done

```

I've tied scrolling to the bottom of grub menu to make sure nothing was hidden, but no, the last line was for Windows XP.

How do I change the first menu entry?

---

### Post by drs305 on 2012-02-09
> **mikewhatever said:**
> 
How do I change the first menu entry?

Edit /boot/grub/grub.cfg as root (gksu gedit /boot/grub/grub.cfg). Just change something within the menuentry title that would be recognizable when you boot. Save the file but don't run any update-grub commands until after you reboot.

While you have the file open, you might just make sure the menuentry isn't hidden in a submenu. You could do a search for 40_custom within the file to try to find the entry if it's been added. The 40_custom section should be it's own listing and I haven't seen any reports where it got included in the 30_os-prober section of grub.cfg. 

Note: A submenu begins with "submenu" and ends with two consecutive lines with only  **}**

Your situation has me baffled since you see the grub.cfg file updated in the terminal including a reference to 40_custom. This means 40_custom is found and executed. I suppose you could also check date after the update in a file browswer).

I thought maybe it might have something to do with the 'tail' command in the 40_custom script but I used it exactly as you posted it and it still displayed in my menu. (In this case, I've always used the +N value as the line number of line to start the import, starting from the top of the file -- +7 in your example).

Here's a command that might save you a bit of booting. You can see what menuentries should be visible the next time you boot, assuming the system uses this grub.cfg file:
```
grep 'menuentry' /boot/grub/grub.cfg
```

---

### Post by mikewhatever on 2012-02-10
Well, I've changed the first Ubuntu menuentry to 'Ubuntu Lucid' and it did show at boot, also tried moving the Windows XP section from the 30_os_prober section to 40_custom and it worked. The entry for Windows is in the boot menu, but not the ISO entry.

```

grep 'menuentry' /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Precise ISO" {
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {


```

Here's what 40_custom in grub.cfg looks like now:
```

### BEGIN /etc/grub.d/40_custom ###
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Precise ISO" {
set isofile="/boot/iso/precise-desktop-i386.iso"
loopback loop (hd0,2)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
} 

menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
        insmod ntfs
        set root='(hd0,1)'
        search --no-floppy --fs-uuid --set 04D4BECED4BEC0EA
        drivemap -s (hd0) ${root}
        chainloader +1
}

### END /etc/grub.d/40_custom ###


```
[COLOR="DarkRed"]Moderator Note: There is a space following "}" in the Precise menuentry which caused a problem. It was discovered later in this thread.[/COLOR]

---

### Post by mikewhatever on 2012-02-10
Success!!!
[s]Just changes double quotes in [COLOR="Blue"]set isofile="/boot/iso/precise-desktop-i386.iso"[/COLOR] to single quotes.[/s]

see #226 below

---

### Post by ranch hand on 2012-02-10
Great job.  Should have caught that myself.

---

### Post by drs305 on 2012-02-10
> **ranch hand said:**
> Great job.  Should have caught that myself.

Something to remember I guess, but double quotes also work. The problem escaped us because what gets printed here are "straight quotes" but perhaps his file was using "curly" quotes, which we couldn't see.

Anyway, to *mikewhatever*, :-)  :-)

Happy Ubuntu-ing !

---

### Post by mikewhatever on 2012-02-19
I've done some more testing, and it looks like the problem was not the quotes, but a space after } at the very end. It's not visible in the stuff I posted, but appears in nano as a green block at the end (see the pic). The space was there when I copy/pasted the entry from post #1 into 40_custom.
Surprised it hadn't come up till now.

---

### Post by drs305 on 2012-02-20
mikewhatever,

Which post contains the extra space? The only one I found for Precise was in your post #222. Is there another one in this thread?

---

### Post by mikewhatever on 2012-02-20
Well, I've copy/pasted the following entry from post #1. Not really sure how the space got there, perhaps when copying. It happened to me twice on two different computers, oddly enough, I can't reproduce it now, but yes, there is definitely a space in #222 and in #209.

```
menuentry "Lucid ISO" {
set isofile="/boot/iso/ubuntu-10.04-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

```

---

### Post by drs305 on 2012-02-21
I added a note in Post #222 regarding the extra 'space' in case someone attempts to copy it. I left the space for *historical* purposes.

---

### Post by e64462 on 2012-03-26
I'm getting the impression that my 40_custom file isn't even getting read by update-grub2. I've tried a bunch of modifications, and update-grub2 wasn't throwing any errors or doing much of anything at all for that matter, so I tried adding the echo line, as described in OP. The following blurbs are my configurations:

> /etc/grub.d/40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding 40_custom." >&2
```

```
nick@desktop:~$ sudo update-grub2 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-32-generic
Found initrd image: /boot/initrd.img-2.6.35-32-generic
Found linux image: /boot/vmlinuz-2.6.35-31-generic
Found initrd image: /boot/initrd.img-2.6.35-31-generic
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Linux Mint 12 Lisa (12) on /dev/sdc2
done
```

As you can see, nothing was echoed. Is there a reason this file isn't getting read?

Best
Nick

---

### Post by mikewhatever on 2012-03-26
Check if it is executable: 'ls -l /etc/grub.d/40_custom'.

---

### Post by e64462 on 2012-03-26
Sure is

> nick@desktop:~$ ls -l /etc/grub.d/40_custom 
-rwxr-xr-x 1 root root 240 2012-03-26 01:30 /etc/grub.d/40_custom


---

### Post by oldfred on 2012-03-26
Does grub.cfg show your entries?

I have os-prober turned off and it see no echo of 40_custom, but the entries are in my grub.cfg. I once had a typo in 40_custom and it did not update grub.cfg but wrote a grub.cfg.??? error file. I forget exactly what it called it.

---

### Post by e64462 on 2012-03-26
Oh that's weird. Well, I googled how to disable os-prober, and all I found was
> [https://www.cboyer.net/2010/03/disable-os-prober-in-grub-2/](https://www.cboyer.net/2010/03/disable-os-prober-in-grub-2/)
> $ echo "GRUB_DISABLE_OS_PROBER=true" | sudo tee -a /etc/default/grub
$ sudo grub-mkconfig -o /boot/grub/grub.cfg
So I double checked /etc/default/grub, and that switch isn't present.

But, from /boot/grub/grub.cfg:

> ...
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding 40_custom."
### END /etc/grub.d/40_custom ###
...

I need to get to work, but I guess I'll try adding the blocks to 40_custom again and restarting to see if they're there. I'll report back later.

---

### Post by e64462 on 2012-03-26
So even though the /boot/grub/grub.cfg file is populated with the contents of /etc/grub.d/40_custom, when I go to boot the entry at startup I get error messages about first loading the kernel and such.

The filename with full path is:
> /home/nick/downloads/gparted-live-0.12.0-5.iso

And I have /home mounted on a separate partition, that partition is:

> nick@notebook:~/downloads$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              11G  2.9G  7.1G  30% /
none                  1.5G  316K  1.5G   1% /dev
none                  1.5G  184K  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
/dev/sda5              15G  6.1G  7.5G  45% /home

The relevant entry in /boot/grub/grub.cfg that update-grub2 entered is:
> ...
### BEGIN /etc/grub.d/40_custom ###

# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Gparted live" {
	set isofile="/downloads/gparted-live-0.12.0-5.iso"
	loopback loop (hd0,5)$isofile
	linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
	initrd (loop)/live/initrd.img
}

### END /etc/grub.d/40_custom ###

I was trying to follow the documentation on the gparted website:
> [http://gparted.sourceforge.net/livehd.php](http://gparted.sourceforge.net/livehd.php)
> Alternatively from GParted live version 0.4.8-7 onwards, you can use only the GParted live iso file in grub2 (Thanks to the patches files from grml). For example, put gparted-live-0.5.2-9.iso in dir /home/isos/, then make the grub2 custom file /etc/grub.d/40_custom like:

    menuentry "Gparted live" {
      set isofile="/home/isos/gparted-live-0.5.2-9.iso"
      loopback loop $isofile
      linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
      initrd (loop)/live/initrd.img
    }
    

Then run "update-grub2" to update your grub2 config. 

I tried copying their example more or less verbatim, but it didn't work, and neither did the modifications I listed above. Any advice?

---

### Post by mikewhatever on 2012-03-26
Assuming that your home partition is /dev/sda5, and the ISO is in /home/nick/downloads/gparted-live-0.12.0-5.iso, try this: 


```
menuentry "Gparted Live ISO" {
set isofile="/nick/downloads/gparted-live-0.12.0-5.iso"
loopback loop (hd0,5)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
initrd (loop)/live/initrd.img
}
```

---

### Post by e64462 on 2012-03-26
Welp, I'm an idiot for leaving off the /nick/.. part of the directory... Sigh, seems to have worked (on my laptop anyways). Thanks for the help mikewhatever!

Best
Nick

---

### Post by oldfred on 2012-03-26
I think        mikewhatever has the right idea but needs one more entry. When grub loads no file system are mounted in Ubuntu so all files have to come from a / (root) path. That is why I often create a /iso in /boot so the path is /boot/iso.

In this case I think it should be:

set isofile="[COLOR=Red]/home[/COLOR]/nick/downloads/gparted-live-0.12.0-5.iso"

If from Nautilus you go to computer the first entry is /home the in /home will be /nick etc.

Correction, maybe. It turns out that if /home is a separate partition the entry suggested by milewhatever will be correct. But if /home is inside / (root) then the additional /home would be required (I think :) )

---

### Post by e64462 on 2012-03-26
That thought occurred to me, but I think it's rectified by the third line, which specifies the disk and partition number:

> loopback loop [COLOR="Red"](hd0,5)[/COLOR]$isofile

In any case, copying the block that mikewhatever posted worked a treat.

Thanks for all the help!

Best
Nick

---

### Post by Splooshie123 on 2012-03-28
drs305, I think you'd better mention that this procedure won't work with alternate CDs.

I tried (after adjusting menu entries for slightly different iso structure) and get an error where the installer complains the CD is not mounted, which isn't possible because we're booting from an alternate iso.

I have confirmed that using a LiveCD iso will work but alternate iso will fail.

---

### Post by nico23 on 2012-04-09
Any way to boot elive iso with grub2?

---

### Post by drs305 on 2012-04-09
> **Splooshie123 said:**
> drs305, I think you'd better mention that this procedure won't work with alternate CDs.

I tried (after adjusting menu entries for slightly different iso structure) and get an error where the installer complains the CD is not mounted, which isn't possible because we're booting from an alternate iso.

I have confirmed that using a LiveCD iso will work but alternate iso will fail.

I experimented on a very old laptop last night and was able to get it to work. The alternate CD is not built the same way as the normal installation CDs. It required several extra steps which took a bit of sleuthing for me to figure out. Unfortunately I didn't document each (successful) step I took, as there were quite a few failures along the way.

If someone gets really stumped or I get a bit of free time I'll try to document it but it's pretty low on my list at the moment.

Thanks for pointing out this behavior - I'll put a line in the original post.

---

### Post by LordNeo on 2012-04-10
Hello all,

First of all i want to thanks a lot for all the info in this thread wich helped me a lot doing most of what i want to do.

**My goal**: Being able to boot ubuntu (installed) and several isos to test or install OS.

I have a harddrive (250gb) that i use as a portable HD, i installed ubuntu (with grub2) in a small partition (20gb) leaving the rest for a fat partition and swap (500mb).

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda2        39065598   488396799   224665601    5  Extended
/dev/sda5        39065600   487305215   224119808    b  W95 FAT32
/dev/sda6       487307264   488396799      544768   82  Linux swap / Solaris

```/dev/sda5 is mounted in the system as /Backup (not really important anyway) and the uuid is B9D5-22AD

So i saved lots of isos from different OS in order to have a portable disk that not only is able to boot Ubuntu on any computer i use (saving my stuff and having a partition to share files with Windows systems) but it also uses the Grub menu to allow to boot several other distros like: Mint, Debian, RH, Mandriva, BT5 (really thanks for this), GParted and a loooong list of etc.

My current issue is booting distros that use **syslinux** (vesamenu.c32 and that kind of stuff) and also trying to boot a **WinXP** and **Win7 iso** using the same formula...

**Currently i use this code to automatically get the correct hdX,Y and do the mounting stuff**

NOTE: The isos are in the root of the partition, i'll move them later when i'm done

```
menuentry "ISO XXXXX" {
        set diskuuid=B9D5-22AD
        search --fs-uuid $diskuuid --set=root --no-floppy
        loopback loop ($root)/isofile.iso
...
...
}
```for some distros was as easy as chaging the root to (loop) or (loop,msdos1) after the loopback line and using "chainloader +1" but for the distros using syslinux and the Win* isos, i couldn't find a correct configurations.

For testing purposes i use the **xpud-0.9.2.iso** (it uses syslinux) because it's light (69mb) but i get to a clean screen and the cursor blinking in the top.

Thanks for reading and any advice is really appreciated

Best regards,
LordNeo

---

### Post by oldfred on 2012-04-10
I do not think it matters that it is syslinux once installed on a CD or flash drive, it is whether it can be booted with grub2 and a loopmount.

I look at the syslinux or isolinux.cfg file for boot folder & parameters. 

This is the isolinux.cfg entry 

LABEL en
MENU DEFAULT
MENU LABEL English
KERNEL /boot/xpud noisapnp quiet
APPEND initrd=/opt/media lang=en kmap=us 

But some distributions or configurations just cannot be directly booted. Puppy I had to extract its main file into the / of my flash. 

I was never able to boot a Windows repair CD ISO by copying with Ubuntu to a flash drive. I burned it to a working CD and then used that CD to copy to a flash drive. I was then able to install grub and just use a standard chain load entry to boot it. Since it was so small I then shrunk the partition created another and put several more repair ISO and used the grub to loop mount those.

---

### Post by LordNeo on 2012-04-10
> **oldfred said:**
> I do not think it matters that it is syslinux once installed on a CD or flash drive, it is whether it can be booted with grub2 and a loopmount.

I look at the syslinux or isolinux.cfg file for boot folder & parameters. 

This is the isolinux.cfg entry 

LABEL en
MENU DEFAULT
MENU LABEL English
KERNEL /boot/xpud noisapnp quiet
APPEND initrd=/opt/media lang=en kmap=us 

But some distributions or configurations just cannot be directly booted. Puppy I had to extract its main file into the / of my flash. 

I was never able to boot a Windows repair CD ISO by copying with Ubuntu to a flash drive. I burned it to a working CD and then used that CD to copy to a flash drive. I was then able to install grub and just use a standard chain load entry to boot it. Since it was so small I then shrunk the partition created another and put several more repair ISO and used the grub to loop mount those.

I'm about to do that to solve the WinXP Win7 issue, but i'm trying to use the unetbootin aproach to see if i can do it with another bootloader or chaining one bootloader to another

---

### Post by drs305 on 2012-04-10
LordNeo,

I have the xpud 0.9.2 and 0.9.5 ISO's on my system. I don't have any working menuentries. This means I tried creating a working menuentry but was unable to do so. As did *oldfred*, I mounted the ISO and inspected the contents but the file doesn't appear to be built to a standard usable by Grub for ISO booting.

---

### Post by LordNeo on 2012-04-11
> **drs305 said:**
> LordNeo,

I have the xpud 0.9.2 and 0.9.5 ISO's on my system. I don't have any working menuentries. This means I tried creating a working menuentry but was unable to do so. As did *oldfred*, I mounted the ISO and inspected the contents but the file doesn't appear to be built to a standard usable by Grub for ISO booting.
Ok, thanks a lot for the info, i'll go straight ahead for the grub2->syslinux chainload.

Best regards

---

### Post by bedbug on 2012-04-11
Thinkin' of booting Chakra GNU/Linux iso ...

to boot chakra-2012.02-Archimedes-CD-i686.iso using grub2
do this : change (hd0,5) to suit your need


/etc/grub.d/40_custom 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu 12.04" {
set isofile="/iso/precise-desktop-i386.iso"
loopback loop (hd0,5)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
initrd (loop)/casper/initrd.lz
}
menuentry "Chakra Linux 2012.02" {
    set isofile="/iso/chakra-2012.02-Archimedes-CD-i686.iso"
    loopback loop (hd0,5)$isofile
    linux (loop)/chakra/boot/i686/chakraiso chakraisolabel=CL_20120208 img_dev=/dev/sda5 img_loop=$isofile earlymodules=loop xdriver=no lang=enus quiet
    initrd (loop)/chakra/boot/i686/chakraiso.img
}



don't forget: sudo update-grub2

---

### Post by bedbug on 2012-04-11
/boot/grub/grub.cfg

menuentry "Chakra Linux 2012.02" {
    set isofile="/boot/iso/chakra-2012.02-Archimedes-CD-i686.iso"
    loopback loop $isofile
    linux (loop)/chakra/boot/i686/chakraiso chakraisolabel=CL_20120208 img_dev=/dev/sdb1 img_loop=$isofile earlymodules=loop xdriver=no lang=enus quiet
    initrd (loop)/chakra/boot/i686/chakraiso.img
}

---

### Post by HotForLinux on 2012-04-16
I'd like to know if anyone has finally been able to ISO-Boot BackTrack 5,2 using grub.
My boot process shows a splash image and stops saying that there's an error in init line3 and cannot access /dev/r0 (or something like that). Then I'm thrown to a minilinux with a prompt that says initramfs, but xI can't run **starx** from there.

---

### Post by NikTh on 2012-05-25
Is there any possibility to add a persistence space for use ? I did some workaround but with no luck. 
I added Ubuntu 12.10 and file named casper-rw . (with dd command) . Then i placed a filesystem with mkfs.ext4 to that file. 
My menu entry is
```
menuentry "Quantal Live" {
set isofile="/boot/ISO/quantal-desktop-i386.iso"
loopback loop (hd0,msdos3)$isofile
linux (loop)/casper/vmlinuz boot=casper [COLOR=Red]persistent rw[/COLOR] iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
``` but still no luck. 
Any ideas ?
Thanks .

---

### Post by drs305 on 2012-05-26
> **NikTh said:**
> Is there any possibility to add a persistence space for use ? I did some workaround but with no luck. 

I haven't tried making an ISO perisistent. I'll do a bit of checking and see if I can come up with anything. Perhaps someone else reading this thread will have some ideas.

---

### Post by NikTh on 2012-05-26
> **drs305 said:**
> I haven't tried making an ISO perisistent. I'll do a bit of checking and see if I can come up with anything. Perhaps someone else reading this thread will have some ideas.

Ok , &#921;  found*  it. !

You must create a partition with ext4 and name it (Label) casper-rw . (i created 2Gb logical partition inside Extended )
It wants partition , NOT a file like a tried . 
Then you must add to grub two parameters **persistent rw **, like mentioned above post but TO THE END after **noeject**
When you boot to live session you will see the casper-rw already mounted , add a user with admin privileges , logout-login and from now on anything changes you do , saved to casper-rw . 
Its like LiveUsb with persistent space. Useful to me. 
Thanks

*Gredits goes to user  **simosx** ( from local ubuntu greek forums who found this solution , as he read this --> [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence) documentation)

---

### Post by drs305 on 2012-05-26
NikTh,

Thanks for posting the information. I'll add a note in the original post as this information could be very valuable for those wishing to save their changes.

---

### Post by ron999 on 2012-05-28
Hi
This has been an interesting post.:p
Thanks drs305 and everybody else.;)

I tried various permutations of:- loopback loop (hdx,y)$isofile
But got errors...
Error:Can't find file
Error:No such disk
Error:You need to load the kernel first

It's fixed now though.
This is the entry that works for me.
```
menuentry "Xubuntu Precise ISO" {
set isofile="xubuntu-12.04-desktop-i386.iso"
loopback loop /boot/iso/$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```

:guitar:

---

### Post by drs305 on 2012-05-28
> **ron999 said:**
> 
This is the entry that works for me.
```
menuentry "Xubuntu Precise ISO" {
set isofile="xubuntu-12.04-desktop-i386.iso"
loopback loop /boot/iso/$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```

:guitar:

Glad you have it working. I happened to playing with the ISOs this morning as well - the latest SystemRescueCD.

I checked my Precise entry and it worked as I had it in the original post, but I've now updated the entry from the Beta to the final release version.

Happy Ubuntu-ing !

---

### Post by ron999 on 2012-05-29
Hello again.
I can boot from SliTaz-3 iso with GRUB2.:)
(Post #122 Jose Catre-Vandis explains).

But I can't boot from SliTaz-4 iso with GRUB2.:(

According to Google this is possibly because SliTaz-4 contains multiple rootfs*.gz files.
Apparently GRUB2 can't handle these (yet).

Is there a way to overcome this?


[COLOR="DarkRed"]Edit Added by drs305: Jump to post #263 for a solution:  [http://ubuntuforums.org/showpost.php?p=12014308&postcount=263]("http://ubuntuforums.org/showpost.php?p=12014308&postcount=263")[/COLOR]

---

### Post by drs305 on 2012-05-29
> **ron999 said:**
> Hello again.
I can boot from SliTaz-3 iso with GRUB2.:)
(Post #122 Jose Catre-Vandis explains).

But I can't boot from SliTaz-4 iso with GRUB2.:(

According to Google this is possibly because SliTaz-4 contains multiple rootfs*.gz files.
Apparently GRUB2 can't handle these (yet).

Is there a way to overcome this?

I downloaded the ISO and experimented with it. You are correct - it has 4 rootfs.gz files. 

I finally got this menuentry to boot Slitaz-4.0. It asked about language and keyboard layout and dropped me at the login prompt. I didn't know what to type for the user and PW but it looked like it would have let me proceed:

This was on my sdb6 partition in the /iso folder.
> 
menuentry 'ISO Slitaz-4.0                            ' 		{
isofile=slitaz-4.0.iso
loopback loop (hd1,6)/iso/$isofile
linux (loop)/boot/vmlinuz-2.6.37-slitaz isoloop=/iso/$isofile
initrd (loop)/boot/rootfs4.gz
}

---

### Post by drs305 on 2012-05-29
> **ron999 said:**
> Hello again.
I can boot from SliTaz-3 iso with GRUB2.:)
(Post #122 Jose Catre-Vandis explains).

But I can't boot from SliTaz-4 iso with GRUB2.:(

According to Google this is possibly because SliTaz-4 contains multiple rootfs*.gz files.
Apparently GRUB2 can't handle these (yet).

Is there a way to overcome this?

I downloaded the ISO and experimented with it. You are correct - it has 4 rootfs.gz files. 

I finally got this menuentry to boot SliTaz-4.0. It asked about language and keyboard layout and dropped me at the login prompt. I didn't know what to type for the user and PW but it looked like it would have let me proceed:
EDIT: it appears the default username is "tux" with no password.

This was on my sdb6 partition in the /iso folder. I had to designate rootfs4.gz
> 
menuentry 'ISO Slitaz-4.0                            ' 		{
isofile=slitaz-4.0.iso
loopback loop (hd1,6)/iso/$isofile
linux (loop)/boot/vmlinuz-2.6.37-slitaz isoloop=/iso/$isofile
initrd (loop)/boot/rootfs4.gz
}

---

### Post by ron999 on 2012-05-29
Hi
I found some info on the web.

Need to make one rootfs.gz file like this:-
```
cat rootfs1.gz rootfs2.gz rootfs3.gz rootfs4.gz > rootfs.gz
```

Then I used isomaster to replace 4 files with 1 new one, and re-named the iso **slitaz-4.x.iso**.

This GRUB2 menuentry works for me:-
```
menuentry "Slitaz 4" {
isofile="/boot/iso/slitaz-4.x.iso"
loopback loop $isofile
linux (loop)/boot/bzImage isofrom=$isofile boot=live noeject noprompt autologin lang=en_GB kmap=uk
initrd (loop)/boot/rootfs.gz
}
```

When SliTaz-4 boots it opens to a terminal.
Command [FONT="Courier New"]**lxpanel**[/FONT] opens the bottom panel with a menu.

I don't know whether it's worth jumping through all of these hoops.
SliTaz-3 is probably good enough for me.:P

---

### Post by Jose Catre-Vandis on 2012-06-03
@ ron999

Inspecting isolinux.cfg Slitaz 4 seems to boot live with this line

```
LABEL slitaz
	MENU LABEL SliTaz Live
	kernel /boot/isolinux/ifmem.c32
	append 192M core 160M gtkonly 100M justx 48M base noram
```

Booting all four rootfs files will only boot to core. Might be worth playing around with this.

I think Slitaz 4 is a vast improvement on 3, so now you have jumped through the hoops it may be worth sticking with.

---

### Post by ron999 on 2012-06-03
> **Jose Catre-Vandis said:**
> 
LABEL slitaz
	MENU LABEL SliTaz Live
	kernel /boot/isolinux/ifmem.c32
	append 192M core 160M gtkonly 100M justx 48M base noram

Hi
If you can translate this into a GRUB2 menuentry it would eliminate my hoops for other punters. :)

---

### Post by Jose Catre-Vandis on 2012-06-03
> **ron999 said:**
> Hi
If you can translate this into a GRUB2 menuentry it would eliminate my hoops for other punters. :)

LOL - I was hoping you weren't going to say that :)

I'll see what I can do.

[EDIT]

Hmmm, seems to be searching for a root filesystem. If I feed it the root filesystem where the iso is the boot process gets a bit further then stalls when it can't find some modules. I think we want rootfs1.gz for the main boot having reviewed isolinux.cfg again. Progress so far:
```
menuentry "Slitaz 4 LIVEISO" {
set root='(hd0,msdos1)'
isofile="/boot/iso/slitaz4.iso"
loopback loop (hd0,msdos1)$isofile
linux (loop)/boot/bzImage isofrom=$isofile boot=live root=/dev/sda1 noeject noprompt autologin lang=en_GB kmap=uk
initrd (loop)/boot/rootfs1.gz
}
```

---

### Post by Jose Catre-Vandis on 2012-06-10
After a bit of searching, the clever boys and girls at SliTaz had the answer. They recognised the issues of setting up USB installs with their "4 in 1" release iso, so created a core iso with just one rootfs.gz. This made booting from the iso simple. My parameters can probably be improved on but this worked for me:

Download the core iso:
```
http://mirror.slitaz.org/iso/stable/flavors/slitaz-4.0-core.iso
```

and copy this to your /boot/iso directory.

Add the following to your grub configuration:

```
menuentry "slitaz-4-core" {
	set isofile="/boot/iso/slitaz-4.0-core.iso"
	loopback loop (hd0,msdos8)$isofile
	linux (loop)/boot/bzImage isofrom=$isofile boot=live quiet vga=792 noeject noprompt autologin lang=en_GB kmap=uk
	initrd (loop)/boot/rootfs.gz
}
```

You will need to edit this line to suit your system:
```
loopback loop (hd0,msdos8)$isofile
``` and change any locale parameters too.

Initally you get a blank screen and think its not working, then all of a sudden you get penguins and then a desktop :)

---

### Post by drs305 on 2012-06-10
> **Jose Catre-Vandis said:**
> After a bit of searching, the clever boys and girls at SliTaz had the answer. 

Seems like they have done more or less what *ron999* did manually to make it easier for the user.

I'll add a note to check your comment to an earlier post about SliTaz. Thanks for sharing the information.

---

### Post by ron999 on 2012-06-10
Hi
This "slitaz-4.0-core.iso" method is better because...
it boots to a desktop instead of a terminal
and...
the sound works OK (previously the alsamixer seemed to be missing).

Kudos to Jose Catre-Vandis
):P

---

### Post by luofeiyu on 2012-06-12
here is my menu 
menuentry 'install  debian  from   hybrid'{
        insmod part_msdos
        insmod ext2
        set isofile='(hd0,msdos7)/tiger/debian/debian-hybrid.iso'
        loopback  loop  $isofile
        linux   (loop)/install/vmlinuz
        initrd  (loop)/install/initrd.gz
}

debian-hybrid.iso  is a hybrid.iso which is dowdloaded  from 
 [http://debian.osuosl.org/debian-cdimage/6.0.4-live/i386/iso-hybrid/debian-live-6.0.4-i386-gnome-desktop.iso](http://debian.osuosl.org/debian-cdimage/6.0.4-live/i386/iso-hybrid/debian-live-6.0.4-i386-gnome-desktop.iso)

the script can boot ,but after i select  country,language,keyboard,
i get : 
no common cd-rom was detected

what's the matter?

---

### Post by drs305 on 2012-06-12
> **luofeiyu said:**
> here is my menu 
menuentry 'install  debian  from   hybrid'{
        insmod part_msdos
        insmod ext2
        set isofile='(hd0,msdos7)/tiger/debian/debian-hybrid.iso'
        loopback  loop  $isofile
        linux   (loop)/install/vmlinuz
        initrd  (loop)/install/initrd.gz
}

debian-hybrid.iso  is a hybrid.iso which is dowdloaded  from 
 [http://debian.osuosl.org/debian-cdimage/6.0.4-live/i386/iso-hybrid/debian-live-6.0.4-i386-gnome-desktop.iso](http://debian.osuosl.org/debian-cdimage/6.0.4-live/i386/iso-hybrid/debian-live-6.0.4-i386-gnome-desktop.iso)

the script can boot ,but after i select  country,language,keyboard,
i get : 
no common cd-rom was detected

what's the matter?

I haven't experimented with Debian's ISO but most debian-based ISOs include additional entries on the 'linux' line such as 

> boot=casper iso-scan/filename=/<path>/$isofile noprompt noeject

I'm  downloading the ISO but don't know how soon I'll get around to testing it.

If you come up with a solution in the meantime please post it here.

---

### Post by luofeiyu on 2012-06-12
if i put  vmlinuz,initrd.gz  in  /home/tiger/debian/
 which are dowloaded from 
[http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/hd-media/vmlinuz](http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/hd-media/vmlinuz)

[http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/hd-media/initrd.gz](http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/hd-media/initrd.gz)

,rewrite my menu as the following :

menuentry 'install debian from hybrid'{
insmod part_msdos
insmod ext2
set isofile='(hd0,msdos7)/tiger/debian/debian-hybrid.iso'
loopback loop $isofile
linux (hd0,msdos7)/tiger/debian/vmlinuz
initrd (hd0,msdos7)/tiger/debian/initrd.gz
}

then i can make it run .it's ok 

i want to know why can't boot from iso with vmlinuz,initrd.gz in the iso ?

there is no   Directory  “casper" in  debian .

---

### Post by drs305 on 2012-06-12
> **luofeiyu said:**
> if i put  vmlinuz,initrd.gz  in  /home/tiger/debian/
 which are dowloaded from 
[http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/hd-media/vmlinuz](http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/hd-media/vmlinuz)

[http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/hd-media/initrd.gz](http://ftp.nl.debian.org/debian/dists/squeeze/main/installer-i386/current/images/hd-media/initrd.gz)

,rewrite my menu as the following :

menuentry 'install debian from hybrid'{
insmod part_msdos
insmod ext2
set isofile='(hd0,msdos7)/tiger/debian/debian-hybrid.iso'
loopback loop $isofile
linux (hd0,msdos7)/tiger/debian/vmlinuz
initrd (hd0,msdos7)/tiger/debian/initrd.gz
}

then i can make it run .it's ok 

i want to know why can't boot from iso with vmlinuz,initrd.gz in the iso ?

there is no   Directory  “casper" in  debian .

Regarding casper, that's true. 

I now understand what you have done but can't answer you. I don't know if the files you downloaded are identical to those in the ISO.

I've been trying to find the correct combination for a little while now - so far mirroring your earlier results. There are multiple kernel/initrd images in the iso. I don't know if they are identical (same names) but so far I haven't gotten the correct combination.

I've found vmlinuz and initrd.gz in:
/install
/install/gtk
/debian/debian/install
/debian/debian/install/gtk


I've found vmlinuz, vmlinuz2, initrd.img and initrd2.img in:
/live
/debian/debian/live
/debian/debian/live/gtk

The ISO also has filesystem.squashfs files so I'm trying alternate means to get it to boot from only from the ISO. I'm not confident I'll come up with the answer but I'll keep tinkering.

---

### Post by luofeiyu on 2012-06-13
there three ways to run debian cd :
1.live(just to run not to install it)
/live 
the initrd.gz , vmlinuz in /live  belong to live way to run.

2.text install
/install
the initrd.gz , vmlinuz in /install  belong to text install way to run.

3.gui  install 
/gtk
the initrd.gz , vmlinuz in /gtk   belong to gui install way to run.

they are different.

what confused me is :
set isofile='(hd0,msdos7)/tiger/debian/debian-hybrid.iso'
loopback loop $isofile
linux (hd0,msdos7)/tiger/debian/vmlinuz
initrd (hd0,msdos7)/tiger/debian/initrd.gz

it is ok

set isofile='(hd0,msdos7)/tiger/debian/debian-hybrid.iso'
loopback loop $isofile
linux (loop)/install/vmlinuz
initrd (loop)/install/initrd.gz

can't run ,
you can try it to make a experiment.

---

### Post by ntzrmtthihu777 on 2012-06-17
First of all let me say thank you for such a wonderful thread, the info contained within is great!

Second of all, I'm still a linux noob but I'm getting better each day.

So with that in mind, is there any way you know of to change an iso not  normally bootable (say lupu-528.005.iso) into one that is? I noticed at  the beginning of the thread that you need initrd.lz instead of  initrd.gz, so I tried
gzip -dc /mnt/casper/initrd.gz | cpio -id
then
find . | cpio --quiet --dereference -o -H newc | lzma -7 > ~/new-initrd.lz[FONT=Ubuntu]

to change it, but that does not do it. Is there something more that needs to be done?[/FONT]

---

### Post by drs305 on 2012-06-17
ntzrmtthihu777,

Puppy does use an initrd.gz file.

I haven't been able to come up with a working menuentry for the Puppy Linux lupu-528.005.iso file. I've found a few USB references about needing to extract files onto the partition but that's beyond my interests.

If anyone comes up with a bootable Puppy ISO menuentry please post it!

---

### Post by ntzrmtthihu777 on 2012-06-17
> **drs305 said:**
> ntzrmtthihu777,

Puppy does use an initrd.gz file.

I haven't been able to come up with a working menuentry for the Puppy Linux lupu-528.005.iso file. I've found a few USB references about needing to extract files onto the partition but that's beyond my interests.

If anyone comes up with a bootable Puppy ISO menuentry please post it!
I knew that, just thought it had to be changed into a .lz file. Thank you!

---

### Post by Brizvegan on 2012-06-18
Hi,
Thanks to this thread and others, I've been able to make a multiboot iso usb stick booting Ubuntu/Linux Mint live isos and others like Clonezilla and GParted and also boot these isos from my hard drive.

Here's the problem:
**This iso will boot successfully on a usb flash drive (ext2) with this menuentry** - SolusOS-1.iso (32-bit) - [http://solusos.com/](http://solusos.com/)  

```
menuentry "SolusOS-1 Eveline ISO" {
    loopback loop /solusos-1.iso
    linux (loop)/live/vmlinuz fromiso=/dev/disk/by-label/MULTIBOOT/solusos-1.iso  boot=live config live-media-path=/live quiet splash union=unionfs --
    initrd (loop)/live/initrd.lz
}
```**but I can't get it to boot from my hard drive.**
The current location of the iso is:  /boot/isos on /dev/sda8 (ext4).

I've tried placing in in the root of the partition - not in a folder.
Tried placing it in its own ext2 partition closer to the beginning of the disk.
Tried adding "insmod ext2" etc. etc. etc.  :confused:

I delete "quiet splash" so I can see the boot process, and I usually get to a line
> Begin: Running /scripts/live-premount .... done.Then a blinking cursor ..... waits, then "Boot failed" and a busybox .... ( initramfs) prompt ..... and a message
> live-boot will now start a shell.  The error message was: 
Unable to find a medium containing a live file system.I've tried many variations of the above menuentry, without success.
I'm obviously missing some vital part of the equation, but don't know enough about the process to figure it out.

I don't know why it will work on the usb stick and not on the hard drive, when the other isos (which also boot from the same usb stick), that are placed in the same hdd location will work.

BTW - I had to reformat the usb stick to ext2 from fat32 because this iso wouldn't boot from one formatted as fat.

Does anyone know how to "convert" the working usb menuentry to one for a hard drive?

---

### Post by drs305 on 2012-06-18
> **Brizvegan said:**
> 
I've tried many variations of the above menuentry, without success.
I'm obviously missing some vital part of the equation, but don't know enough about the process to figure it out.


I can't either. I've tried as many variations on my drive as I can think of without success. It really shouldn't be that hard but I haven't come up with a working menuentry.

---

### Post by Brizvegan on 2012-06-18
Thanks for trying :smile:

I think if you **really** want to boot isos like this (Debian) from your hdd, you can extract some files from the iso, copy them to your hdd and then make a Grub2 entry from that .... maybe that's the only  way to go, for now.

Something like this:
[http://www.linuxquestions.org/questions/debian-26/cannot-boot-debian-live-iso-from-usb-using-grub2-902012/page2.html](http://www.linuxquestions.org/questions/debian-26/cannot-boot-debian-live-iso-from-usb-using-grub2-902012/page2.html)

It's no big deal - I'm happy I got it working from the usb stick, which was my original intention - but it's just frustrating that you can't do it on your hard drive as easily as the other isos! :mad:

Thanks also for your hard work on this thread - it's been very helpful and I've learned about Grub2 by following it.

Brizvegan

---

### Post by ntzrmtthihu777 on 2012-06-20
Another question: Is there a way to boot iso's 'live,' that is to save changes between boots? I ask because I'm running on a HP dv9000, and I need restricted drivers to make the screen look right. For the sake of example, can you do this with Lucid Lynx?

---

### Post by drs305 on 2012-06-20
ntzrmtthihu777,

I haven't experimented with this. The terms to search would be "persistent", Ubuntu, and ISO. I know you will get hits for bootable USB drives - I'm not sure about ISOs. I believe remastersys can do this for you so add this to your search terms if nobody else responds.

---

### Post by ron999 on 2012-06-20
@drs305
Hi
For people with 64-bit machines...
If they boot a 32-bit Ubuntu iso...
will they be able to run 32 bit programs instead of 64-bit programs?

---

### Post by ntzrmtthihu777 on 2012-06-20
Excellent, thank you very much. I'll repost whatever I find to make this more a 'one stop shop' for all .iso booting needs. I noticed that you have a list of menu entries that do boot from iso. perhaps you could list .iso's that just won't boot that way. I know lucid puppy is one, got the info from the puppy forums

---

### Post by drs305 on 2012-06-20
> **ron999 said:**
> @drs305
Hi
For people with 64-bit machines...
If they boot a 32-bit Ubuntu iso...
will they be able to run 32 bit programs instead of 64-bit programs?

Yes. 

In fact, there was a long period where many users elected to install the 32-bit version on 64-bit machines because drivers and apps weren't as available in 64-bit.

---

### Post by ron999 on 2012-06-20
> **drs305 said:**
> Yes. 
;)
Have you got a 64-bit machine and a bootable 32-bit Ubuntu iso at present?

---

### Post by drs305 on 2012-06-20
> **ron999 said:**
> ;)
Have you got a 64-bit machine and a bootable 32-bit Ubuntu iso at present?

Yes, I do. The 32-bit one is for my laptop. What you can't do is chroot with different architecture, if that is what you are thinking about.

---

### Post by ntzrmtthihu777 on 2012-06-20
I sense a challenge in the making

---

### Post by drs305 on 2012-06-20
> **ntzrmtthihu777 said:**
> I sense a challenge in the making

Could be, but I'll be offline in about 10 minutes. So you can be my substitute.

---

### Post by ntzrmtthihu777 on 2012-06-20
> **drs305 said:**
> Could be, but I'll be offline in about 10 minutes. So you can be my substitute.
>< I don't think I'd be an apt substitute seeing as I only have been using ubuntu for about a month, but I'll do my best...what the heck is  a chroot @.@

---

### Post by drs305 on 2012-06-21
> **ntzrmtthihu777 said:**
> >< I don't think I'd be an apt substitute seeing as I only have been using ubuntu for about a month, but I'll do my best...what the heck is  a chroot @.@

It's a procedure to change the root to a different location. In my Grub posts, it usually involves booting a LiveCD, mounting your real installation's partition, copying certain LiveCD system files to the mounted partition, and then using the 'chroot' command. This allows the commands you run to change your real installation's system files.

In a chroot, you can add packages such as a new kernel (or old kernel), update Grub, etc. Without using the chroot procedure the commands would attempt to change the LiveCD's files, which would fail and be non-persistent. Google I'm sure would have a better explanation.  ;-)

---

### Post by L_V on 2012-06-29
Booting BT5 iso file with grub2 is currently not possible without modifying initrd file.

But, a workaround consisting in loading a modified initrd file proposed here: [http://this.is.thoughtcrime.org.nz/multi-boot-bt5-from-usb-with-grub2](http://this.is.thoughtcrime.org.nz/multi-boot-bt5-from-usb-with-grub2)

---

### Post by ntzrmtthihu777 on 2012-07-01
> **L_V said:**
> Booting BT5 iso file with grub2 is currently not possible without modifying initrd file.

But, a workaround consisting in loading a modified initrd file proposed here: [http://this.is.thoughtcrime.org.nz/multi-boot-bt5-from-usb-with-grub2](http://this.is.thoughtcrime.org.nz/multi-boot-bt5-from-usb-with-grub2)
Oo oo oo, this is just what I was about to look for! Thankyouthankyouthankyou!

---

### Post by drs305 on 2012-07-03
This page has been migrated to the Ubuntu Community Documentation site. For the most up-to-date information, please visit:
[_https://help.ubuntu.com/community/Grub2/ISOBoot_]("https://help.ubuntu.com/community/Grub2/ISOBoot")

The above page is a sub-page of the main community documentation regarding [_Grub2_]("https://help.ubuntu.com/community/Grub2").

A thread for discussion of the wiki can be found at: _[http://ubuntuforums.org/showthread.php?p=12073029](http://ubuntuforums.org/showthread.php?p=12073029) _

If you have a known working menuentry not posted on the community [_Grub2/ISOBoot/Examples_]("https://help.ubuntu.com/community/Grub2/ISOBoot/Examples") page please post it on that page. If you do not have write privileges on that page post the menuentry in the previous link.

Thank you to all the users who posted in these threads and expanded our knowledge of Grub 2 since it's introduction.

**Support threads regarding the wiki and it's content should be created in a suitable forum.**

Thread Closed.

---

