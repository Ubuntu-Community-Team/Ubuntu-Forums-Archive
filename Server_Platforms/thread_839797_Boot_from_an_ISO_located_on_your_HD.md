---
title: "Boot from an ISO located on your HD"
date: 2008-06-24
forum: Server Platforms
---

### Post by jmz2 on 2008-06-24
Hello,

The situation is that I have a remote server with not physical access and not CD/DVD unit on it.

I want to be able to boot that machine from any LiveCD's ISO's. I suposse there must be a method to store the ISO on the HD and indicate the GRUB to boot from that ISO located in a partition of the disk.

Could you please help me on this?

Many thanks.

---

### Post by cszikszoy on 2008-06-25
I would doubt that this is possible.  Without loading some kind of operating system, there is no way to read the disk, or the .iso file even.  What you might want to look into is a network boot situation.  You should be able to configure the client to search for a bootable image from the network.  You can set this boot option as the highest priority (above the HDD).  Sorry I don't have any more information, but google might be your best friend in this case.

---

### Post by jmz2 on 2008-06-26
Ok, I finally found what I was looking for.

Thanks to: [http://azerthoth.blogspot.com/2008/04/want-to-install-dvd-release-of-linux.html](http://azerthoth.blogspot.com/2008/04/want-to-install-dvd-release-of-linux.html)

---

### Post by cszikszoy on 2008-06-27
I don't understand why you'd want to do this?  The guide you posted links to pendrivelinux... which has guides to put ubuntu 8.04 on a flash drive, so you can install directly from that, without going through all of the work to resize, mount, install, unmount, then resize again.

Just put the 8.04 CD on the flash drive and install from the flash drive.  I've done it before and its very easy and fast for pcs w/o a cd drive.

---

### Post by hyper_ch on 2008-06-27
you'd need to have a live OS into which you can ssh then... right?

---

### Post by jmz2 on 2008-06-28
> **cszikszoy said:**
> I don't understand why you'd want to do this? 

Because I DON'T HAVE physical access to the server, it is on datacenter miles away.

---

### Post by jmz2 on 2008-06-28
> **hyper_ch said:**
> you'd need to have a live OS into which you can ssh then... right?


Correct!!

All this doesn't work without a working OS. The idea is to boot a liveCD from a live OS.

If your remote system crash, you can order a new OS installation and do all steps again. Afterwards boot from your LiveCD ISO located on Hd and do an image restore to recover your old OS.

---

### Post by promodus on 2008-06-29
Are you able to install over the network? 
Do you have access to a DHCP server that is on the same network segment?


If you have access to that, tftp server, you may install over the network just as easy.


[http://ubuntuforums.org/showthread.php?t=829482&highlight=unattended.]("http://ubuntuforums.org/showthread.php?t=829482&highlight=unattended")

---

