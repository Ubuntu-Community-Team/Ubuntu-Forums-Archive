---
title: "Grub Entries"
date: 2012-05-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Miykel on 2012-05-10
G'Day; Is there a way I can remove extra entries from my Grub Boot Loader ??
e.g

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.3.0-5.dmz.1-liquorix-amd64
Found initrd image: /boot/initrd.img-3.3.0-5.dmz.1-liquorix-amd64
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 8 (loader) on /dev/sda1
  
[  Found Windows 8 (loader) on /dev/sdb1
   Found Windows 8 (loader) on /dev/sdb6  ]
done

These are the two I want to remove, they go nowhere, it happened when i had to do a Grub repair

Regards Miykel

---

### Post by ronacc on 2012-05-10
have you tried running ```
 sudo update-grub 
```  in a terminal ?

---

### Post by Miykel on 2012-05-10
Thanks for the reply Ronacc, yes I did, thats how I got copy of the entries, it's a curious thing as the last two entries are not relevant to any OS, W7 & W8 are installed in their own partitions on the same drive and are accessed through the normal Windows Boot Loader which is the top windows entry in Grub.
 I'm tempted to run the Grub rescue disc from DOS again and see if I can do it through that but if I blow it it will mean reinstalling all three OS's as I don't know how to get into the Windows Boot loader if I damage Grub, rock and a hard place syndrome.
Regards Miykel

---

### Post by ronacc on 2012-05-10
are there actual entries for those in /etc/grub/grub.cfg ? if so you can edit them out using gedit run with gksudo , but they will be re generated next time grub updates . How did you repair grub ?

---

### Post by drs305 on 2012-05-10
Edited:

Grub Customizer probably will work on U+1. The link is in my signature line.

I created a thread on how to tweak Grub. See the 'Tweaks' link. It is *really* geeky, but there is a section which explains how to eliminate a specific partition by editing the Grub scripts. 

If at all possible, I'd definitely try Grub Customizer for your own sanity. You could also turn off the 30_os-prober script and create a custom entry for the Windows entry you wish to keep.

---

### Post by ronacc on 2012-05-10
I think he still wants access to his windows partitions .

---

### Post by drs305 on 2012-05-10
> **ronacc said:**
> I think he still wants access to his windows partitions .

Yes he does. I'll amend the post. Thanks.

---

### Post by grahammechanical on 2012-05-10
This is not true

> it's a curious thing as the last two entries are not relevant to any OS, 

You do have W7 and W8

> W7 & W8 are installed in their own partitions on the same drive

The OS prober in Grub will notice any OS even if it is on a separate drive. These are on the same drive.

If you do not want or need these entries in the Grub menu, then you can use Grub Customizer to hide those entries. It can also be used to hide the entries for older Linux kernels that get replaced by a kernel update.

I recommend Grub Customizer. I use it all the time. It is especially useful if we are doing ISO install testing or have more than one version of Ubuntu on the machine. I do not have Windows but I do have other versions of Ubuntu that I use for testing.

Regards.

---

### Post by ronacc on 2012-05-10
thanks guys for the tip on grub customizer , my test box has 6 drives and more partitions than I have fingers and toes to count on , my grubs are always a byzantine mess and hand editing them is a pain .

---

### Post by drs305 on 2012-05-10
> **ronacc said:**
> thanks guys for the tip on grub customizer , my test box has 6 drives and more partitions than I have fingers and toes to count on , my grubs are always a byzantine mess and hand editing them is a pain .

If Grub Customizer doesn't work out, you can build a custom menu which stays current even when a new kernel is introduced.

Forum member *Cavsfan* wrote a very nice guide on how to do it:
[http://ubuntuforums.org/showthread.php?t=1542338]("http://ubuntuforums.org/showthread.php?t=1542338")

---

### Post by jerrylamos on 2012-05-10
To make sense out of the verbose (!) grub boot choices I do as follows.

I've got a lot of partitions and grub entries make it hard to read.  I can't get rid of the garbage but I can make an entry to appear first or last whichever is convenient.

For an entry to appear last, go into /boot/grub/grub.cfg and find the entry you want last, copy and append it to /etc/grub.d/40_custom.

For an entry to appear first, copy /etc/grub.d/40_custom to /etc/grub.d/06_custom.  Then append an entry from /boot/grub.cfg

Now those entries are pretty verbose.  You can use something simpler.  An example I've used:

/etc/grub.d/40_custom

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Natty /dev/sda7" {
	set root=(hd0,7)
	linux /vmlinuz root=/dev/sda7 ro quiet
	initrd /initrd.img
}

The /vmlinuz and /initrd.img in the root directory are pointers to the /boot where all the long file names are listed.

After that, do a ls -l /etc/grub.d to make sure all the file permissions are the same on all the entries.

sudo update-grub
sudo grub-install /dev/sda             or whatever /dev you're using
Reboot....

Now frequently (!) during development there are verbose garbage entries in grub.cfg so another way out is to have a partition with a ubuntu that still works like lynx or meerkat or ocelot and do the update-grub's there.  I do that all the time on my fast tower with a sata hard drive and an ide hard drive because precise/ocelot get /dev/sdb and /dev/sda screwed up and reversed from boot order and from lynx. Launchpad bug written no response.

Jerry

---

### Post by Miykel on 2012-05-10
Thanks so much for all that guys,
  I used an iso disk"Grub Repair" to repair grub from DOS, which seemed very simply, I have no idea why it should have picked up the last two entries, the first windows entry takes me to the Windows boot loader the last two go nowhere, I installed Liquorix Kernel and updated Grub which gave me the option for the generic or Liquorix kernel but the two bogus windows entries remained, very strange.
Regards Miykel

---

### Post by xebian on 2012-05-10
> **Miykel said:**
> Thanks so much for all that guys,
  I used an iso disk"Grub Repair" to repair grub from DOS, which seemed very simply, I have no idea why it should have picked up the last two entries, the first windows entry takes me to the Windows boot loader the last two go nowhere, I installed Liquorix Kernel and updated Grub which gave me the option for the generic or Liquorix kernel but the two bogus windows entries remained, very strange.
Regards Miykel

These are Windows recovery/fail safe partitions.  Just ignore them, and if you can't then edit /boot/grub/grub.cfg and delete them.

---

### Post by ronacc on 2012-05-10
its possible that when you prepped the drives  something got left on those 2 partitions  sdb1 and sdb6 that grub was finding . I always use gparted to do my partitioning and formating  not parted which is what ubiquity uses . and just deleting a partition might leave something for grub probe to find , I always format after deleting even if I'm not going to use it rightaway.

---

### Post by Miykel on 2012-05-10
Thanks for your contribution xebian, I tried that as well, I've been playing with this for a few days, trawled the net, tried so many things but nothing seems to work, I might just have to ignore it until things go bang again and I do a reload, lol., I'm trying to get to the bottom of this for my own knowledge as much as anything.
Kind Regards Miykel

---

