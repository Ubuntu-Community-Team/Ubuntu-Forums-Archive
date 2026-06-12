---
title: "137GB problem"
date: 2008-11-18
forum: Server Platforms
---

### Post by Vegan on 2008-11-18
My IBM 300 GL like many computers of that period have a limit of 137GB that the BIOS can see as they lack support for LBA48.

I have complained tO IBM that this is a defect and wanted to have it fixed but they refuse.

So to cure the problem, is to use various partitioning schemes. Messy but no other way.

Disk /dev/sda: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cd97cd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3598    28900903+  83  Linux
/dev/sda2            3599        3738     1124550    5  Extended
/dev/sda5            3599        3738     1124518+  82  Linux swap / Solaris
root@ubuntu:~$

so this small disk can boot no problem. But if I use a 500 GB disk, I am not we lucky. Thoughts?

:guitar:

---

### Post by volkswagner on 2008-11-18
I am no expert.  

You can have four primary partitions in linux.  I don't know the limitation of extended partitions.

You can partition to your hearts content.

LIKE;

Three or Four Primary partitions-
     Mount Point                size
         /                    130 Gig
         /home                130 Gig
         /BigFatWhatever      130 Gig
or       /var
         /home/user1
         /var/www

Secondary partition 1:   130 Gig
       Mount point            size
         /var/www/site1       130 Gig

Secondary partition2:    Remaining
       mount point        size

          /some/insane    whatever gigs
          /swap           you know




You are right.  Messy.

---

### Post by caljohnsmith on 2008-11-18
All you need to do is create a ~200 MB partition at the beginning of your 300 GB drive (in addition to the other partitions you want to create), and then when you go through the Ubuntu installer, simply set the mount point on that 200 MB partition as "/boot". That way all your boot files will be within the first 200 MB of your HDD, and your BIOS can certainly handle that. :)

---

### Post by Vegan on 2008-11-19
Reviewing the du -h command reveals Ubuntu itself needs little space so I was considering a small 20 GB partition for the OS, some swap and rest for the web sites.

Even 20 GB is overkill for the server files. The SQL stuff does have potential to grow slightly from phpBB accumulations. Moving the directory is one idea.

I like the IBM as it consumes so little power. It makes its so cheap to operate.

:guitar:

---

