---
title: "[SOLVED] Can't boot Windows XP after Ubuntu installation"
date: 2008-10-19
forum: Windows
---

### Post by Fueled on 2008-10-19
First of all, I want to say that I have already did many searches for this problem, and that I've found lots of posts about it, but none that are exactly appropriate to my problem and that can help me fix it. I hope a personalized thread will do it! Also, please consider that I'm a super-newbie on Linux.

So, this week-end I decided I wanted to try out Linux for the first time. I chose Ubuntu as the distribution package.
Before installing Ubuntu, my HDDs partitioning was set up so:
- 1st HDD (SATA 120GB): 
[INDENT]C:\ (Windows) - 80GB
Free space - 40GB (*which I left out intentionally for Linux*)[/INDENT]
- 2nd HDD (IDE 200GB): 3 partitions (irrelevant)
- 3rd HDD (SATA 500GB): 3 partitions (irrelevant)

I followed Ubuntu's [installation process for dual-booting]("https://help.ubuntu.com/8.04/switching/installing-partitioning.html#installing-partitioning-dual"), and thus created three new partitions (swap, root and home)  using the free space on HDD 1. I was happy that it did not seem necessary to resize the Windows partition, as I had done a fresh install of Windows just the day before, and did not want to do it again!
After installation was completed, the computer was rebooted and I was shown the Grub boot menu. I chose Ubuntu, and it worked fine. I then rebooted and tried Windows XP: this error message was displayed:

[I]"Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file."[/I]

I searched for this particular error message and could find that the problem is probably due to the partitions having changed, and Windows not being happy with that. I could also find that one way to solve that is by modifying the **boot.ini** file. But here starts my headache.
From Ubuntu, I can mount the Windows partition and I can see its contents. But the boot.ini file is nowhere to be found ("Show Hidden Files" is enabled). I did not manually delete it.

I've tried using Windows' Recovery Console, with *bootcfg /rebuild* and *fixboot*, but to no avail.
* Relevant info: when I launch the Recovery Console, I must load the SATA drivers from a floppy disk, otherwise, *bootcfg /rebuild* never finds the Windows partition.
* Relevant info: *bootcfg /rebuild* finds the Windows partition on **D:\**, but Windows was definitely installed on *C:\* before.

I also tried manually creating boot.ini from within Ubuntu and copying content found on the Internet. As I'm not sure on which partition is Windows installed anymore, I tried partition(1) to partition(4), but I get the "Hal.dll" error message in every case.
* Relevant info: since I created boot.ini manually, it is not a system file anymore and not hidden (I don't know how to change the file attributes from Ubuntu).

Well, that's about where I'm at now. At least I can use Ubuntu, but I'd still like to use Windows since I'm used to it and most of my software is installed on it.
I hope someone will be able to assist me!
Thanks in advance! Cheers!

---

### Post by caljohnsmith on 2008-10-19
It sounds like your Windows partition was definitely changed, and it is probably a logical partition now instead of a primary partition. Coincidentally I'm helping someone else at the moment who has almost exactly your same problem:

[http://ubuntuforums.org/showthread.php?t=952048](http://ubuntuforums.org/showthread.php?t=952048)

To start with, please boot your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
And post the results of that. It is important to first see whether Windows is still on a primary partition or a logical one, but it sounds most likely (based on what you describe) that Windows is on a logical partition now since it doesn't have its boot files. We can work from there if you would like help with it. :)

---

### Post by Fueled on 2008-10-19
Hello caljohnsmith and thanks for your reply!

It's a good thing that this problem seems familiar to you!
So, here is the result of the fdisk command:

```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x012e9fd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   167766794    83883366    7  HPFS/NTFS
/dev/sda2       167766795   398267414   115250310    f  W95 Ext'd (LBA)
/dev/sda5       167766858   335533589    83883366    7  HPFS/NTFS
/dev/sda6       335533653   398267414    31366881    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19e719e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   167766794    83883366    7  HPFS/NTFS
/dev/sdb2       167766795   234436544    33334875    5  Extended
/dev/sdb5       167766858   175767164     4000153+  82  Linux swap / Solaris
/dev/sdb6       175767228   215769014    20000893+  83  Linux
/dev/sdb7       215769078   234436544     9333733+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x048faf30

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   398958209   199479073+   7  HPFS/NTFS
/dev/sdc2       398958210   976768064   288904927+   f  W95 Ext'd (LBA)
/dev/sdc5       398958273   797723639   199382683+   7  HPFS/NTFS
/dev/sdc6       797723703   976768064    89522181    7  HPFS/NTFS
```

The 2nd HDD (/dev/sdb) is the right one it seems.
I'll take a look at the thread you suggested while awaiting your response.
Cheers!

---

### Post by caljohnsmith on 2008-10-19
Your fdisk output shows good news, Fueled, namely that your Windows partition on your 120 GB drive (sdb) is still a primary partition. :) It looks like what most likely happened is that Windows put its boot files on the sda drive (200 GB HDD) in the sda1 NTFS partition, because that partition is flagged as bootable. 

So let's see if the boot files are really on sda1:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Note "-l" is a lowercase L and not a one. From that directory listing, see if it includes the three Windows XP boot files:
```
boot.ini
ntldr
NTDETECT.COM
```
If they are there, you'll need to move them back to partition sdb1. You can do that with:
```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
sudo mv /mnt/boot.ini /mnt/ntldr /mnt/NTDETECT.COM /media/sdb1/.
```
Also, I'll need to check your Grub's menu.lst to make sure everything is OK, so please post:
```
cat /boot/grub/menu.lst
```
In the meantime, reboot, try Windows again, and let me know exactly what happens. :)

---

### Post by Fueled on 2008-10-19
Damn! You are quite right! The three files were indeed on *sda1*!

Here's the output from *menu.lst*:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=159cfe29-51da-49bc-a92d-4c593e1ae9c9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=159cfe29-51da-49bc-a92d-4c593e1ae9c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=159cfe29-51da-49bc-a92d-4c593e1ae9c9 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=159cfe29-51da-49bc-a92d-4c593e1ae9c9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=159cfe29-51da-49bc-a92d-4c593e1ae9c9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

```

So now I can see the content of the *boot.ini* file:
```
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft XP Home Edition" /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft XP" /Fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

The three options are my doing I think, when I used *bootcfg /rebuild* I gave a different Windows name every time it seems :|
Do you believe it's OK to remove unnecessary options from it?

Ok, I'm off to try rebooting with Windows!
Back in two!
Thanks!!!

---

### Post by Fueled on 2008-10-19
Ok, it still doesn't work, but at least there's some progress, or so it seems.
Now I get "**NTDLR is missing**" when trying to boot Windows XP.

Hope this sets you on the right track!
Cheers!

---

### Post by Fueled on 2008-10-19
> **caljohnsmith said:**
> 
```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
sudo mv /mnt/boot.ini /mnt/**ntldr** /mnt/NTDETECT.COM /media/sdb1/.
```

Hang on, is the file supposed to be called **NTDLR** or **NTLDR**??
The file on my Windows partition now is called nt**ld**r, but the error message states the nt**dl**r is missing. Could that be the problem?
Would a simple rename resolve it? I'm a bit reticent to try that now...

---

### Post by caljohnsmith on 2008-10-19
OK, we're definitely getting close here.:) The file is indeed "ntldr", so maybe you wrote down the error wrong? We'll find out soon enough anyway.

I would go ahead and modify your boot.ini file since (as you say) you don't need all those other Windows options if Windows is just on your sdb drive; but more importantly we need to correct the "rdisk" specifiers in that file since your Windows will be on the same drive as you are booting from. While you are in Ubuntu do:
```
sudo apt-get install tofrodos
```
Make sure you can install that package, otherwise do not proceed. Next mount your sdb1 Windows partition again and pull up the boot.ini file:
```

sudo mount /dev/sdb1 /media/sdb1
gksudo gedit /media/sdb1/boot.ini
```
Replace what is in that file with:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP" /fastdetect /NoExecute=OptIn
```
Save, quit, and then make sure you do the following:
```
sudo unix2dos /media/sdb1/boot.ini
```
Next we need to correct your Grub menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
At the very bottom of that file, replace the Windows entry with the following:
```
title Microsoft Windows XP Professional
root (hd0,0)
makeactive
chainloader +1
```
Save, reboot, cross your fingers, and let me know exactly what happens when you try to boot Windows. :)

---

### Post by WWSmith36 on 2008-10-19
> At the very bottom of that file, replace the Windows entry with the following:
Code:

```
title Microsoft Windows XP Professional
root (hd0,0)
makeactive
chainloader +1
```

Save, reboot, cross your fingers, and let me know exactly what happens when you try to boot Windows

Since the Xp install is on sdb1 wouldn´t it be hd1,0 with remapping?

---

### Post by Fueled on 2008-10-19
YES! You are my hero of the day! =D>
Windows booted up just fine! I got "Generic volume" installation three times, but I imagine that is for the three partitions I created during Ubuntu's installation.

And yes, you were also right about the NTLDR error message, I was confusing the term.

Once more: thanks! Everything seems in order right now and I can stop pulling my hair off!
Three cheers for you!

---

### Post by caljohnsmith on 2008-10-19
> **WWSmith36 said:**
> Since the Xp install is on sdb1 wouldn´t it be hd1,0 with remapping?
Since his Ubuntu entry uses (hd0,5), and since he mentioned in his first post that Ubuntu boots fine, that would mean he must be booting from his sdb drive on start up. Thus his Windows, being on the same drive, would use (hd0) too. :)

---

### Post by caljohnsmith on 2008-10-19
Glad you can boot Windows now, Fueled. Hope you have at least a little hair left! Cheers and have fun. :)

---

### Post by diego22000 on 2008-11-21
:( can anyone help me i have a similar problem.
ubuntu works, windows xp wont load but its there.
if anyone can help ill post all the info, thanks

---

