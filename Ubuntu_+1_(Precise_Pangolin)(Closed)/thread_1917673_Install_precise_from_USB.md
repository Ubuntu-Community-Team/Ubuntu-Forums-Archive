---
title: "Install precise from USB?"
date: 2012-01-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by joshuajon on 2012-01-30
I've downloaded a recent build of precise pangolin that I'd like to test out with a USB drive.  Unfortunately I can't seem to get it boot completely.  It seems to get somewhere into the boot process but then drops to a busybox prompt with (initramfs)

I'm currently trying UNetbootin, but I've also tried cat image > device as well as dd if=image of=device bs=1M in order to get the image onto the USB drive.  

I can boot other operating systems from this usb device so I think the hardware isn't the problem.

Anyone have any other strategies I could attempt?  TIA.

---

### Post by oldos2er on 2012-01-30
Moved to Ubuntu +1 (Precise Pangolin).

---

### Post by bmbaker on 2012-01-30
try downloading a newer iso perhaps it got corrupted

---

### Post by joshuajon on 2012-01-30
Are there md5 hashes available somewhere for the daily builds?  I grabbed this one on Friday 1/27.  

I am downloading the current daily right now.

---

### Post by joshuajon on 2012-01-30
Nevermind, it looks like for dailies they only go back one day so I probably can't check the hash of the image I have.  I'll update this thread again if, after getting the current daily, I'm still stuck in the same situation.

---

### Post by VMC on 2012-01-30
> **joshuajon said:**
> I've downloaded a recent build of precise pangolin that I'd like to test out with a USB drive.  Unfortunately I can't seem to get it boot completely.  It seems to get somewhere into the boot process but then drops to a busybox prompt with (initramfs)

I'm currently trying UNetbootin, but I've also tried cat image > device as well as dd if=image of=device bs=1M in order to get the image onto the USB drive.  

I can boot other operating systems from this usb device so I think the hardware isn't the problem.

Anyone have any other strategies I could attempt?  TIA.

Are you trying to install precise distro on a usb drive or install precise livecd on the usb drive?

I've recently had problems using UNetbootin on Ubuntu.

---

### Post by joshuajon on 2012-01-30
> **VMC said:**
> Are you trying to install precise distro on a usb drive or install precise livecd on the usb drive?

I've recently had problems using UNetbootin on Ubuntu.

My understanding is that all of the .iso images have an option to boot into a live environment or install to disk.  So, I guess 
the answer to your question is I'm installing the livecd.

---

### Post by ventrical on 2012-01-30
It works well with a stable release , ie; Lucid..  but I have not had any probs with Unetbootin (haven't used it in over 2 years though) I think that the USB drive has to be specially formatted with the HP formatter if you are using Unetbootin.

---

### Post by joshuajon on 2012-01-30
Current unetbootin documentation simply states that the drive must be FAT32 formatted.  I can make bootable filesystems to the same device, with different .isos.

I downloaded the latest daily within unetbootin and rebooted to the same thing: busy box with (initramfs) prompt.

---

### Post by coffeecat on 2012-01-30
@joshuajon, I managed to use today's daily (30th January) to make a successful install from USB, so it should be OK. That was the 64-bit desktop version. I used startup disk creator in my Oneiric system to create the bootable USB. Do you have an Oneiric system you can use?

---

### Post by Baldrick_NZ on 2012-01-30
I have successfully done both with 12.04. Installed the iso to USB and made a working copy installed on a bootable 8gig flash drive.

Both using the 'Start-up disk creator' in 10.04. 

If you just want to create a USB disk which does pretty much what a CDLive disk does, then download a copy of the iso from the daily build website ([http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)) and then launch the Start-Up Disk creator (from memory, Admin>Start-Up Disk Creator), point it to the iso, follow the instructions and viola!

You need to take it a few steps further if you want to create a bootable working OS on a USB drive. I call it my 'puter on a stick'. Let me know if you want to know more about this.

Hope it helps.

Cheers.

---

### Post by Stovey on 2012-01-30
> **Baldrick_NZ said:**
> ...You need to take it a few steps further if you want to create a bootable working OS on a USB drive. I call it my 'puter on a stick'. Let me know if you want to know more about this...

Yes!  I would like very much to do this.  I tried to install Lucid Puppy about 10x on a USB stick with no luck.  How do I make a bootable working OS on a USB drive?

---

### Post by A_T on 2012-01-30
I always change the iso file extention to .img and use usb-imagewriter from the repos to write the image to a usb drive. It works for Ubuntu, Debian, Centos, Fedora, in fact every linux distro I've tried.

---

### Post by VMC on 2012-01-30
> **A_T said:**
> I always change the iso file extention to .img and use usb-imagewriter from the repos to write the image to a usb drive. It works for Ubuntu, Debian, Centos, Fedora, in fact every linux distro I've tried.
Interesting, I'll have to try that. The UNetbooten that doesn't work for me is installed on Fedora.

---

### Post by Baldrick_NZ on 2012-01-30
> **Stovey said:**
> Yes!  I would like very much to do this.  I tried to install Lucid Puppy about 10x on a USB stick with no luck.  How do I make a bootable working OS on a USB drive?

In reality, you need 2 usb sticks. One to install the 'LiveCD' iso on, and the other (min 8gig) you wish to install your workable copy to.

I'm not sure about Lucid puppy, but with Ubuntu 10.04, you could just use the LiveCD itself instead of the first USB stick listed above. I wouldn't suggest installing Lucid itself to USB as a working system, as it's very slow. 12.04, by contrast, if much faster.

So, download the iso and open up the start-up disk creator. Insert the stick you want to create the iso onto into you computer and choose the source iso and format the stick. You should then be ready to create the iso to USB.

Once done, leaving the stick inserted, reboot your PC and while in bios, choose to boot from USB FDD. Wait for the liveCD (now on USB) to boot. You want to choose the option to 'try Ubuntu'.
Insert the new USB stick into the PC. And once it's recognised, click on 'install Ubuntu'. 

When you get to it, you'll want to choose a custom install, so you can choose the flash drive to install to. I think on the splash screen it says something like 'do something else'. 

Make sure that it is the flash drive you're installing to. Usually seen as 'sdc' and the amount of capacity of the drive (8g, in my case).

There will be an option to make the disk bootable. Make sure you tick this option. Then proceed with the install.

Once completed, you should have a fully functioning OS on your USB stick, which should work on any PC which offers USB boot.

There may, in reality, be an easier way, which someone is welcome to suggest. But it worked well for me. Infact I'm using that stick now, writing this.

---

### Post by jerrylamos on 2012-01-30
As a tester I'm usually running 2 or 3 or 4 installs of ubuntu at various different levels on the hard drive, usually 10.04.3 Lucid Lynx LTS or later.

So I have an ubuntu I can boot.  Then I use sudo gparted to format the USB drive, example to ext3 or even 32 bit.

I have a copy of the .iso on the main hard drive in a directory I choose to call .iso for example

/iso/precise-desktop-i386.iso

Copy the desired .iso to the usb drive as is, no disk creator no unetbootin.  Do a df to see what the USB is, in this case /dev/sdb1

then

gedit 40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Pangolin ISO sda1" {
set isofile="/iso/precise-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
menuentry "Pangolin ISO sdb1" {
set isofile="/precise-desktop-i386.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

```
sudo chmod 777 40_custom
sudo cp 40_custom /etc/grub.d
sudo update-grub

At that point you can reboot and choose to run the .iso from either the .iso file on the hard drive or the .iso from the usb drive.

Now to live dangerously you could boot from the hard drive, then to do an install do a df to notice where the isofile is mounted.  Example

sudo umount -r -l /dev/sda

Then I've been able to do an install on the hard drive into a different partition, created by sudo gparted beforehand. 

Alpha time, expect crashes etc.

jerry

---

### Post by Stovey on 2012-01-31
OK, so Precise Pangolin makes it easy to create a "persistent" USB OS.  Great, thanks.

---

### Post by joshuajon on 2012-01-31
Still no luck here.  I'm on debian so I don't have the same repos as ubuntu.  I'll see if I can get usb-imagewriter though and give that a try.

---

### Post by joshuajon on 2012-01-31
OK! I added the ubuntu repos in debian, got usb-imagewriter from there, renamed my .iso as a .img and successfully installed the .img to usb.  

I'm surprised that the normal route I use didn't work, but thanks for the help folks.

---

