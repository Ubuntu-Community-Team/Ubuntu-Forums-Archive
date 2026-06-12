---
title: "Ubuntu doesn't recognize encrypted storage drives"
date: 2020-11-12
forum: Security
---

### Post by useless-semicolon on 2020-11-12
I recently made the decision to switch from Windows 10 to glorious Ubuntu. From that, I still have USB and external storage disks that were encrypted using Veracrypt. I have installed Veracrypt and it seems to be able to recognize, mount, and unmount one of my USB drives. However I'd prefer to mount and unmount my encrypted USB easily from the Files application and maybe the disks utility when I'm using keyfiles. I was able to do this from another Linux distro in a live USB but in Ubuntu it just doesn't seem to recognize the contents in the USB. I'm also worried that I'm not properly ejecting my USB because it still lights up after unmounting from veracrypt and I can't seem to find an effective way to eject it. I did try to eject the USB in the disks utility, but it just didn't respond and my USB was still lighting up.

I did a little research and I found that I should install gnome-disk-utlity cryptsetup but it is installed.

Any other suggestions?

Edit:
I was playing around a bit and I learned that pressing the power button on the disks utility is effective in removing the USB as it turns off when I press it. So how can I do the same in the Files application?

---

### Post by EuclideanCoffee on 2020-11-12
Hey, I like your name, useless-semicolon; hope you enjoy your time here. :D

I'm having a hard time understanding the problem, but I think it's because I need to see what you're seeing.

Your files application should be Nautilus on Ubuntu. Is that correct? This is the "default" files application. You shouldn't need to install it. From what I've read online, it should be compatible. You should receive a popup asking for your password to decrypt it. If you're not, I think you might have an issue with the drive. Either it's a file system that Ubuntu cannot recognize and/or it's corrupted somehow (common issue).

You can check your drive with the following terminal tutorial.

```

lsblk | grep disk
sudo badblocks -w -s -o error.log [path to usb]
cat error.log

```

Link to tutorial and other helpful tips: [https://www.cyberciti.biz/faq/linux-check-the-physical-health-of-a-usb-stick-flash-drive/](https://www.cyberciti.biz/faq/linux-check-the-physical-health-of-a-usb-stick-flash-drive/)

So far I think this sounds like a corrupted drive issue. This happens when you format the USB with a filesystem that Ubuntu cannot read or you have some read/write issues when writing to the disk from a different system. This commonly happened to me when I relied on USBs. Today I transfer a lot of my personal documents from a Nextcloud server from my LAN. You can refer to this tutorial: [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-nextcloud-on-ubuntu-20-04)

---

### Post by useless-semicolon on 2020-11-14
Thanks. I got the idea of my username because I'm learning Python and I noticed the codelines don't end with semicolons unlike C.

Anyway, so to clarify I am using the Nautilus files application and my issue is that Nautilus and the disk utility isn't recognizing the contents of a Veracrypt encrypted USB. The disk utility just describes the contents as "Unknown" however I am able to successfully mount, read, and write to files on the USB when using Veracrypt and when using Nautilus and the disk utility in a Debian live USB.

For a test I encrypted another USB using Veracrypt with the following configuration:
> 1) Algorithm: AES
2) Key Hash algorithm: SHA-512
3) Filesystem type: Ext4
4) Quick format enabled
5) Selected the option saying that I will only mount the drive on Linux systems
and the disk utility still described the USB contents as "unknown".

I ran the command [COLOR=#ff0000]sudo badblocks -w -s -o error.log /dev/sdb[/COLOR] as suggested and I got the following output:
> Testing with pattern 0xaa: done                                                 
Reading and comparing: done                                                 
Testing with pattern 0x55: done                                                 
Reading and comparing: done                                                 
Testing with pattern 0xff: done                                                 
Reading and comparing: done                                                 
Testing with pattern 0x00: done                                                 
Reading and comparing: done   

Unfortunately, the log file was empty and I didn't use the f3 tool in the article that you linked because I didn't see it was the type to detect errors but it looks very cool and I'll keep it in mind next time I buy more USBs.

Also I do use online storage but these encrypted USBs contain decryption keys and so I'd prefer to keep using USBs and keep these files out of the cloud. In addition I still may mount the USBs in a Windows sytem so I don't want to use the disk utility encryption feature since it only encrypts using Ext4.

---

### Post by EuclideanCoffee on 2020-11-15
Oh so the problem is that the disk is labelled unknown yet you can access and write to the drive? It sounds like a possible integration issue with gnome disk or that the app is creating a filesystem that mimics something that Ubuntu can read but gnome cannot. If you're reporting a bug, you would need to push this up the chain from security support forums to the developers on Launchpad or elsewhere.

---

