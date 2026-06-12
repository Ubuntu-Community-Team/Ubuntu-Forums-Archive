---
title: "Vista After Ubuntu install?"
date: 2007-12-07
forum: Testimonials &amp; Experiences
---

### Post by Justleftlife on 2007-12-07
So i have this problem lol. I Finally got ubuntu up and going with 0 problems... but in doing that i some how got rid of my vista install. So i was wondering if there is a way for to install vista while ubuntu is still... i dont want ubuntu to leave so i how do i do it.

---

### Post by Vadi on 2007-12-07
Are you sure vista is gone?

When you boot up, you should be able to choose between booting ubuntu/vista.

---

### Post by Justleftlife on 2007-12-07
Oh i am very sure. It gives you an option to hit escape to pick what kind of ubuntu i want to run. But there is no choice for vista. I am kinda sad.

---

### Post by Vadi on 2007-12-07
Oops.

In your installation, do you remember using a slider thing to select how much space you wanted to give to Ubuntu?

---

### Post by Justleftlife on 2007-12-07
I do remember that the second install i had to do to get my Wireless card and video card drivers to work didnt give me a slider to use but i did it 5 am... so i could have over looked at the time and not thought anything of it. if i install vista do you think it over write my ubuntu install?

---

### Post by rsambuca on 2007-12-07
A few things.  You may not have overwritten Vista, it may just be on another partition.  Second, if you have deleted it, you can create a new partition, install Vista, and then restore your grub bootloader without having to re-install Ubuntu.

To see if Vista is still on your computer, open a terminal and enter 

sudo fdisk -l

---

### Post by Justleftlife on 2007-12-07
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris


So this is what i got and it looks like the sda2 might be the partition that vista might be on. but i could be wrong i am really really new to all this.

---

### Post by rsambuca on 2007-12-07
> **Justleftlife said:**
> sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris


So this is what i got and it looks like the sda2 might be the partition that vista might be on. but i could be wrong i am really really new to all this.

Nope.  Your Vista is gone.

---

### Post by Danikar on 2007-12-08
From anything I heard Vista and Linux don't play nice. =( I was going to do the same thing then I just decided to remove Linux entirely. I have enjoyed it thoroughly.

---

### Post by sirdilznik on 2007-12-08
If you have another drive or a free partition then install Vista on that.  Any Windows operating system will overwrite your MBR (Master Boot Record) upon installation.  You will need to reinstall grub afterward to get access to both Vista and Ubuntu.

---

### Post by apothecaryaaron on 2007-12-08
Vista and Ubuntu work with each other just fine.  I messed up the install a couple of times.  I just keep a grub bootdisk handy to rewrite grub to the MBR after Vista does its thing.

---

### Post by lswest on 2007-12-08
you can just re-install Vista and then install a program in windows, which allows you to add a linux entry to the windows bootloader...there is a program called EasyBCD which can be found [here]("http://neosmart.net/dl.php?id=1")  it means you dont have to re-install grub, just install vista and edit the bootloader so you can boot to ubuntu.

tutorial for doing that is [here]("http://apcmag.com/5045/how_to_dual_boot_vista_with_linux")

---

