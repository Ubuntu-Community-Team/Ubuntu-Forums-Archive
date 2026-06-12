---
title: "Best Way to Install Ubuntu 10.04?"
date: 2011-04-07
forum: System76 Support
---

### Post by Teasdale on 2011-04-07
I've been having intermittent problems with my Ratel almost since I got it, with freezing and then sometimes not booting properly. It was suggested that I upgrade to 10.04, but my issue was intermittent enough that it wasn't worth the hassle. Now it looks like maybe I have no choice; it doesn't look like Ubuntu is going to load.

I downloaded Ubuntu 10.04 on another computer and put the disk in, and it gave me the option to use the Live CD or install. I clicked to install, but it wanted to know whether I wanted to install alongside 9.04 (and keep my existing partitions, I guess?) or do a clean install and erase the disk. At first I chose to erase the whole disk because that seemed simpler (I have all my files backed up). But it got stuck at 5 percent and said it "failed" at partitioning or something like that. Right now I'm using the Live CD.

With a System76 PC, is there a correct way to install? Is the disk already partitioned, so that I should choose the option to install alongside 9.04?

If I use the Live CD, can I access my existing files? I don't see them.

---

### Post by isantop on 2011-04-07
You should be able to access your files from the hard disk. if the partitioning is failing, you'll want to re-download and re-burn the image file; it sounds to me like it got corrupted.

---

### Post by Teasdale on 2011-04-07
I re-tried installing. It apparently already erased the file system and is giving me this error:

"Failed to create a file system.
The ext4 file system creation in partition #1 of SCS13 (0,0,0) (sda) failed."

What does that mean? Is there anything I can do?

---

### Post by Teasdale on 2011-04-07
> **isantop said:**
> You should be able to access your files from the hard disk. if the partitioning is failing, you'll want to re-download and re-burn the image file; it sounds to me like it got corrupted.

So it's probably the CD/iso image that's corrupted, and not the computer itself?

---

### Post by Teasdale on 2011-04-07
Nope, I downloaded a new image on a different computer (Windows this time) and made a new disk, and it's giving me the exact same error in the same place, at 5 percent.

I'm pretty sure this is a 64-bit computer, but maybe my problem is that I'm trying to use the 64-bit version of Ubuntu? Or should I try downloading 9.04 and installing that?

---

### Post by jeffran on 2011-04-07
Did you run md5sum on the downloaded image and install disk? If not,I highly recommend doing that. Instructions here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I had the exact same problem with either 9.10 or 10.04, and it turned out to be a bad download.

Good luck!

---

### Post by Teasdale on 2011-04-07
Thanks, I'll try the md5sum - right now, I'm downloading Linux Mint to see if a different OS makes a difference.

I assume that, whatever I install, whether it's Ubuntu 9.04 or 10.04, or Mint, I still need to install the System76 driver like the instructions say to do when you install 10.10?

---

### Post by Teasdale on 2011-04-07
> **jeffran said:**
> Did you run md5sum on the downloaded image and install disk? If not,I highly recommend doing that. Instructions here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Good luck!

The "hash" matches fine: c19e5139e10df2626055f1d9985856d7

So it isn't the download. And since I downloaded and created a disk from two different PC's using two different operating systems (and even two different brands of disks), then I'm doubting it's the iso download or the disk. Which leaves . . . the PC I'm installing to.

---

### Post by StephenDavison on 2011-04-08
I'd suggest using gparted to re-partition the hdd from the 10.04 live cd.  (I'm pretty sure gparted is on there.)  While you're at it, why not update to 10.10?

My Ratel (pre-installed w/ 10.10) was having some issues related to disk partitions until I dropped the extended and logical partition containing the swap space.  Even booted from a live disk image, it wouldn't let me resize the primary (root) partition until I deleted the extended partition (which served no real purpose anyway).  I ended up creating a smaller partition for the root file system, a separate partition for /home, and put swap in a primary partition instead of the logical one.  Everything works great now.

---

### Post by isantop on 2011-04-08
Actually, this might be a bad disk too. Go ahead and try the other suggestions, but should those fail, go ahead and send us an email at support...at...system76...dot...com. We can get you a new hard disk.

---

### Post by Teasdale on 2011-04-08
Thanks, I'll try what I can and let you know what happens.

---

### Post by Teasdale on 2011-04-08
I tried another installation, I downloaded 9.04, did the md5sum, made a CD, and installed it. It got to 5 percent (same as the other times with 10.04) but, after about 15 minutes, it just started installing. When it finished, I restarted, took the CD out as it said, and it got to a black screen that says 

> 
[Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command 
completions. Anywhere else TAB lists the possible
completions of a device/filename.]

grub>


I'm off to google and see what that means. I'm guessing this installation was not successful.

---

### Post by Teasdale on 2011-04-08
I found[ this]("http://ubuntuforums.org/archive/index.php/t-40504.html"), typed in:

root (hd0)

then after the grub> prompt, I typed kernel /boot/vmlinuz and the tab key.

I got Error 17: Cannot mount selected partition.

Per [this page]("http://www.linuxquestions.org/questions/linux-newbie-8/error-of-grub-minimal-bash-like-line-editing-is-supported-660334/"), I typed in setup (hd0) and got this:

> 
Checking if "boot/grub/stage1" exists . . . yes
Checking if "boot/grub/stage2" exists . . . no

Error 18: selected cylinder exceeds maximum supported by BIOS

grub>


Typing this:

grub> find /boot/grub/stage1

yields this: (hd0,0)


Typing this:

grub> setup (hd0,0)

yields this: 

> 
Checking if "/boot/grub/stage1" exists . . . no
Checking if "/grub/stage1" exists . . . no

Error 15: File not found


---

### Post by Teasdale on 2011-04-09
I repartitioned, tried installing 9.04 (it installed but won't load), and then 10,04. 10.04 installed to 65 percent and is now giving me this error:

> 
[Errno 30] Read-only file system: '/target/usr/src/linux-
headers-2.6.32-28/arch/mips/Makefile"

This is often due to a faulty hard disk. It may help to check
whether the hard disk is old and in need of replacement, or to
move the system to a cooler environment.


I'll take this off-forum now and email system76.

------------------------

Edit: a new hard drive fixed my problem.

---

