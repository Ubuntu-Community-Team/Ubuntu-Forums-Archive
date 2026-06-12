---
title: "[Support] Installing UbuntuCE in an aleady partitioned HDD"
date: 2007-08-06
forum: Ubuntu Christian Edition
---

### Post by Gjs1992 on 2007-08-06
Hello mates,
I have tried an attempt to install UbuntuCE on my machine earlier but failed. I failed beccause I did not know how to partition the HDD prperly and because the setup froze at 70%... When I reboot it gave me "Operating System Not FOund..." So I re-installed Vista and my backups, etc...
So now, I baught a **NEW** HDD and gave the other one to a friend; I partition my Hard Disk into two parts while installing WIndows.
Part 1 is 82 GB, and Part 2 is 150 GB... There's no "Unallocated Space" available at all. So how to take 50 GBs from the 2nd partion without losing my files and Windows? How to make sure that UbiuntuCE does not freeze once again while setup is running?

PS: For those athiests who'll reply with "UbuntuCE sucks." or something similar, please go get a life. I appreciate your work Jereme and I'm one of your great supporters, thanks. :)

---

### Post by pbcartwright on 2007-08-06
install aprorgam called gparted. It allows you to resize partitions:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

then install CE and enjoy!!

---

### Post by Gjs1992 on 2007-08-06
So this program works for Windows? Or is it used for Ubuntu?

---

### Post by mike102282 on 2007-08-06
It is used in Ubuntu, but you can resize any partition.

---

### Post by mysticrider92 on 2007-08-06
I assume the 82gb partition is your Windows boot partition? If so, I would back up the 150gb one (just in case, bad things can happen), defrag the whole drive from Windows (once again, just in case), then use the manual partitioner on the Ubuntu cd (it is the same as gparted).

This is where you need to be careful. You will see a table representing your hard drive. Windows will either be on /dev/hda1 and /dev/hda2 or /dev/sda1 and /dev/sda2 (if the drive is SCSI or SATA). 

Right click the /dev/*da2 and choose resize. Make it so there is 50000mb following (it is shown in megabytes, 50000 mb == 50 gb). You will now have 50gb of free space. Make one ext3 partition filling most of the free space, and one linux-swap partition. The swap is usually twice the size of your ram, but 512mb is probably plenty for any recent system. Be sure not to mess with anything or delete partitions, these changes are basically permanent.

I just wrote this so it would be clear, whether or not you knew all of it.

[edit] Just as a note, the freezing during the install could be a sign that the cd burn was bad, so just be careful.

---

### Post by Gjs1992 on 2007-08-06
Thanks for your very good and detailed guide my friend. :)
Mind you telling me if and how can I run UbuntuCE on a non-primary partition?
Will it affect my Vista crack? :P

---

### Post by mysticrider92 on 2007-08-07
You mean putting Ubuntu on a logical partition, such as /dev/*da5 (or anything higher)? Just follow the same thing, except make /dev/*da3 a 50gb logical partition and put an ext3 partition inside it. I have not personally tested this, but in theory, that is the reason for logical partitions. It should not have any affect on Vista at all.

---

### Post by TravMan63 on 2007-08-08
Yes you can install (various flavors of Linux) in an extended partition.

I installed Elive in extended (and deleted/resized partitions) - without disturbing Ubuntu.

Elive even (as do others) -updated grub - so I could choose...(between the 2).

Gparted works great for this.

#-edit - links

Image of gparted in action:  [http://ubuntuforums.org/attachment.php?attachmentid=37235&d=1183505964](http://ubuntuforums.org/attachment.php?attachmentid=37235&d=1183505964)

Thread [http://ubuntuforums.org/showthread.php?t=491443](http://ubuntuforums.org/showthread.php?t=491443)

note - the image has more partitions than you really need.  Two will work (/ (root) and swap.

---

