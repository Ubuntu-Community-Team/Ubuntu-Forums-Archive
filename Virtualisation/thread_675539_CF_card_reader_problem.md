---
title: "CF card reader problem"
date: 2008-01-22
forum: Virtualisation
---

### Post by kgwurth on 2008-01-22
I have been trying to figure out a way to share disk space between a VM machine and Linux where Linux is the host. I have read that you need to use Samba but I have pretty much given up on trying to get that to work. For some reason my virtual machine can't see anything on the network even though I have everything set up on the same work group. 
So I figured why not use CF card for shared storage. I put the card in the reader and Ubuntu sees the drive and mounts it. I can then copy files from any of my drives that I want to transfer to my virtual drives.
I found that if I bring up the virtual machine and mount the drive I get a message on Ubuntu about unsafe removal.  I found that if I unmount the drive from Ubuntu before I mount it on the virtual machine there are no complaints.
I can then copy the data from the card to my virtual drives and everything is fine.
I then unmount the drive from the VM menu so they drop from the virtual machine.
Now comes the problem... No matter what I do, I can not get the card to re-mount in Ubuntu.  I have tried shutting down vmserver thinking maybe it had the device tied up somehow but that didn't work.  I pull out the card and plug it back in and Ubuntu will just not auto mount it.  I can not seem to do a manual mount.
The only way I have found to get around this is to reboot Ubuntu, replug in the CF card and I am back in business.

There has to be a better solution.
Anyone have any ideas?

Thanks for your assistance
Karl Wurth

---

### Post by RIchard James13 on 2008-01-22
That's not one of those nasty Internal Multi Card Readers is it? Because they only work once and then you have to reboot the system, even in Windows XP. If you have an external one like I do you can unplug the USB cable and then plug it back in again and you can use it again, of course you can't unplug an internal card reader.

I read the following on another web page

> One reason to use the Raw disk image format (the default) is that it can then be mounted with the command:

mount -o loop,offset=32256 your-disk-images-name.img /mnt

This allows you to easily copy files from your system into (and out of) the disk image (the offset is so that the boot sector of the image is not mounted).

Using the raw disk image format does not result in larger files than the other formats (except cloop which is a compressed format) as the reserved space is simply recored as "next follows a string of x million zeros" rather than actually writing x million zeros. This is true for Reiserfs, ext2, ext3 and other Linux filesystems, but apparently not true for Windows.

It does work. but is sloppy compared to networking. Makes you wish that most VM's supported the native filesystem. DosBox does.

What VM are you using?

---

### Post by kgwurth on 2008-01-22
Yup it's one of those nasty internal ones. Came with the HP box.
I am trying to research if I can run a FTP server in ubuntu then use a ftp client in the xp vm vlient client. Since I can't see anything on the network I wonder if I can still use ip addresses.

I am using vmserver 1.04  Everything works great except sharing storage.
I can just use dvd rw but that's a pain

---

### Post by kgwurth on 2008-01-22
Update:

I finally got Samba working. That is by far the best solution

---

