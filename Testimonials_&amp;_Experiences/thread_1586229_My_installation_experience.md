---
title: "My installation experience"
date: 2010-10-01
forum: Testimonials &amp; Experiences
---

### Post by mr_flea on 2010-10-01
I had what I figured was probably a simple problem: I didn't want my MBR modified. I figured I'd start by downloading a 10.04 64-bit Desktop image (ubuntu-10.04.1-desktop-amd64.iso), and see if I could find a good way using the standard installer to avoid modifying my MBR. Having found no way to do this with the graphical installer on the livecd, I tried wubi...

Much to my enjoyment, there was a wubi executable already there! I figured it would be pretty easy to run that, have it do all the hard work of adding the entry to BCD, and provide an easy path for uninstallation if I didn't like what I saw. Unfortunately, it seems that wubi will attempt to detect whether it's running from the CD, and if it does detect this condition, it'll just give you directions to install from CD, which doesn't seem very useful. So I tried copying it to my desktop. No luck there, either, as it apparently checks all the drives to ensure that you don't already have an Ubuntu installer somewhere. I removed the installation media (I was using a flash drive, as I prefer it vastly over actually burning a CD, and it usually reads and writes much faster anyway), and ran the wubi executable from my desktop. This time it complied and actually let me put in the information for my wubi installation; I was pretty happy. Unfortunately, what it did next was completely ridiculous. It proceeded to download **the same CD image I had tried to run wubi from, ubuntu-10.04.1-desktop-amd64.iso**. Why couldn't it have used the extracted ISO from my flash drive, instead of downloading the same thing again? Furthermore, it gave me an estimation of about 75 hours to download the ISO:

[IMG]http://dl.dropbox.com/u/11015975/wubi.png[/IMG]
(also, the text antialiasing is really messed up.)

So now I'm downloading the alternative installer, in hopes that it will actually let me install without modifying my MBR. I understand that the standard "desktop" installer probably isn't a good place to put advanced features like installing GRUB to the partition instead of the MBR, but I feel that the bigger issue in this post is that wubi is incredibly misdesigned. Why even ship it with the CD if it won't let you actually USE the contents of the CD? What if I wanted to create a wubi installation, but without an internet connection to download the CD image?

Here's a screenshot of wubi refusing to install if install media is already present, if anyone is curious: [http://dl.dropbox.com/u/11015975/wubi-mediapresent.png](http://dl.dropbox.com/u/11015975/wubi-mediapresent.png)

---

### Post by cgroza on 2010-10-01
You must run wubi from the same folder as the extracted ISO.

---

### Post by armandh on 2010-10-01
it won't

the loader or MBR is going to be modified for normal dual booting
the windows mbr/loader does not like to recognize a non win OS

so the way to do what you want is to put the boot selection/grub files else where. a cd, a usb drive [if that is a boot option] or a floppy. boot option can direct the bios to other than the main hard drive. that MBR can direct things to the partition/drive with the grub loader stuff. 

the above is above my expertise

but I know that if you want a non wubi dual boot without mucking with the main drive MBR the bios will have direct things to some other MBR and from there to the grub start menu

easier to put an old Hdd in the primary drive position and load ubuntu there MBR change and all it will likely pick up the win OS and may not modify its drive's MBR [but not for sure on this]

---

### Post by mr_flea on 2010-10-01
> **armandh said:**
> it won't

the loader or MBR is going to be modified for normal dual booting
the windows mbr/loader does not like to recognize a non win OS

so the way to do what you want is to put the boot selection/grub files else where. a cd, a usb drive [if that is a boot option] or a floppy. boot option can direct the bios to other than the main hard drive. that MBR can direct things to the partition/drive with the grub loader stuff. 

the above is above my expertise

but I know that if you want a non wubi dual boot without mucking with the main drive MBR the bios will have direct things to some other MBR and from there to the grub start menu

easier to put an old Hdd in the primary drive position and load ubuntu there MBR change and all it will likely pick up the win OS and may not modify its drive's MBR [but not for sure on this]

It is possible to get BCD (the Vista/7 bootloader) to load GRUB or another bootloader. This is what wubi does, and I've done it myself before. It won't boot Linux directly, but if you install GRUB to another partition (instead of the MBR), you can get BCD to load up GRUB from that partition.

---

### Post by mr_flea on 2010-10-01
> **cgroza said:**
> You must run wubi from the same folder as the extracted ISO.

The issue is that it WON'T run with the extracted ISO. I eventually got it to use my non-extracted copy of the ISO. If it detects the extracted ISO, it'll instead give you instructions on how to install Ubuntu (see the link to the screenshot.)

---

### Post by Juan Largo on 2010-10-01
> **mr_flea said:**
> 
So now I'm downloading the alternative installer, in hopes that it will actually let me install without modifying my MBR. I understand that the standard "desktop" installer probably isn't a good place to put advanced features like installing GRUB to the partition instead of the MBR ...

Most Linux distributions allow you use their Live CD to install GRUB in the / partition instead of the MBR.  If Ubuntu's Live CD doesn't do this, it should.

---

### Post by arunb on 2010-10-03
I had problems installing 10.04 from a CD, so I used a pen drive, it was faster and had no problems.

CD installations are anyway getting outdated.

---

