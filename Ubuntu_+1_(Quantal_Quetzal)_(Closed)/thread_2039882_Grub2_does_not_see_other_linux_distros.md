---
title: "Grub2 does not see other linux distros"
date: 2012-08-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ts3 on 2012-08-09
Grub2 has been acting strangely over the last 2-3 weeks.  I have 12.10 installed on a laptop with two other distros and I installed the 12.10 grub2 as the bootloader.  

Basically, grub sometimes sees and sometimes does not see one of distros (on sda3) and never sees the other one (on sda1).  Quantal itself is on sda5.

I wrote a couple of very rudimentary scripts custom entries in /etc/grub.d and if I press Shift to open the boot menu I can access sda1.  Sda3 refuses to boot so there's something wrong with that script.

Here's the result of fdisk:

```
tsj@linux-laptop:~$ sudo fdisk -l
[sudo] password for tsj: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37708833

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    41945087    20971520   83  Linux
/dev/sda2        41945088    58718207     8386560   82  Linux swap / Solaris
/dev/sda3        58718208   100663295    20972544   83  Linux
/dev/sda4       100667390   488359935   193846273    f  W95 Ext'd (LBA)
/dev/sda5       100667392   488359935   193846272   83  Linux
tsj@linux-laptop:~$
```

Has anyone seen any unusual grub behaviour recently?

Of course any suggestions how to fix this are welcome :)

Cheers

---

### Post by ventrical on 2012-08-09
Mine is working great here:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00010e57

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   251369235   125683594   83  Linux
/dev/sda2       251369470   976771071   362700801    5  Extended
/dev/sda5       972167168   976771071     2301952   82  Linux swap / Solaris
/dev/sda6       493948928   738417138   122234105+  83  Linux
/dev/sda7       970731520   972156927      712704   82  Linux swap / Solaris
/dev/sda8       251369472   492378111   120504320   83  Linux
/dev/sda9       492380160   493934591      777216   82  Linux swap / Solaris
/dev/sda10      738418688   969156607   115368960   83  Linux
/dev/sda11      969158656   970727423      784384   82  Linux swap / Solaris

Partition table entries are not in disk order
dale@dale-desktop:~$ 

all ubuntu quantal, 1 debian install.

---

### Post by ronacc on 2012-08-10
I'm having no problem with grub2 , my box has 6 drives with 7 installs spread accros 4 of them 2 ubuntu (quantal ) , 2 debian , 2 sabayon , 1 suse and grub2 finds them all and I'm using the grub2 from 1 of my 2 quantal installs to boot everything ,

---

### Post by cecilpierce on 2012-08-10
The new grub 2.00 does not work so well for me, adds alot of useless junk.
I just use 40_custom with burg, or grub and if I add a new os, just add it with an editor.

---

### Post by sgage on 2012-08-10
> **ts3 said:**
> Grub2 has been acting strangely over the last 2-3 weeks.  I have 12.10 installed on a laptop with two other distros and I installed the 12.10 grub2 as the bootloader.  

Basically, grub sometimes sees and sometimes does not see one of distros (on sda3) and never sees the other one (on sda1).  Quantal itself is on sda5.

I wrote a couple of very rudimentary scripts custom entries in /etc/grub.d and if I press Shift to open the boot menu I can access sda1.  Sda3 refuses to boot so there's something wrong with that script.

Here's the result of fdisk:

```
tsj@linux-laptop:~$ sudo fdisk -l
[sudo] password for tsj: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37708833

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    41945087    20971520   83  Linux
/dev/sda2        41945088    58718207     8386560   82  Linux swap / Solaris
/dev/sda3        58718208   100663295    20972544   83  Linux
/dev/sda4       100667390   488359935   193846273    f  W95 Ext'd (LBA)
/dev/sda5       100667392   488359935   193846272   83  Linux
tsj@linux-laptop:~$
```

Has anyone seen any unusual grub behaviour recently?

Of course any suggestions how to fix this are welcome :)

Cheers

I have had similar problems from time to time. I find I have better luck if I make sure all the other installation partitions are mounted before running update-grub.

---

### Post by Cavsfan on 2012-08-11
Deleted

---

### Post by Cavsfan on 2012-08-11
Deleted

---

### Post by ronacc on 2012-08-11
I did have a problem a couple of years ago when sabayon was installing to an LBA partition by default , Ubuntu's grub was not finding that install but was finding others . I don't have any LBA installs right now so I don't know if thats still the case . Is the install that grub isn't finding by any chance on an LBA partition ?

---

### Post by ts3 on 2012-08-11
> **sgage said:**
> I have had similar problems from time to time. I find I have better luck if I make sure all the other installation partitions are mounted before running update-grub.

Thanks, mounting the partitions and running sudo update-grub fixed it.

The frequent kernel updates on 12.10 and the fact that I haven't added the other partitions to /etc/fstab yet  (this is a new install and I haven't done anything fancy) explains the sheer randomness of the appearing and disappearing distros.

Marking the thread as solved & thanks again.

---

### Post by ts3 on 2012-08-11
> **Cavsfan said:**
> If you look at the how to in my sig. it is pretty lengthy but, just pay attention to the green notes about grub 1.99 as it was initally written for 1.98. 
The most important thing is the last post which is my 06_custom entry and everything else is made unexecutable via
**sudo chmod -x /etc/grub.d/10_linux**, etc.

But, the good thing is that once you make the change you never have to mess with it again.
When a kernel is installed, it will always be the one selected when you select that OS.
If you need access to other kernels, you just reverse the commands like the one above.
I made **/etc/grub.d/20_memtest86+**, **/etc/grub.d/10_linux** and **/etc/grub.d/30_os-prober** all unexecutable.
I used **40_custom** for my entries and saved it as **06_custom**, so they would appear first when initially making these changes.
Just pay attention to the top lines in 40_custom as they do need to be changed with grub 1.99 as noted.

Cavsfan, thanks for the suggestions and the link in your previous post.  I still want to figure out why one of my custom scripts does not work so this will help.

Cheers

---

### Post by Cavsfan on 2012-08-12
> **ts3 said:**
> Cavsfan, thanks for the suggestions and the link in your previous post.  I still want to figure out why one of my custom scripts does not work so this will help.

Cheers

You are welcome. I deleted the posts before I read this as it looked like this was an inappropriate place for me to post my suggestion.
But, you still have the link in my sig.
I do recall that when I first installed Quantal, grub2 listed several OS' on the wrong partition.
It even listed Debian Squeeze being on the partition Quantal is on. That is when I customized it.
My screen looks like I want it to look and does not change. I actually ended up copying the 06_custom listed on the last post and saving it in **/etc/grub.d/**
Which made the task very simple for me.
The only problem with grub2 is that customizing it this way causes my windows 7 option to give the false error "no argument specified. Press any key to continue." 
However, if you just wait or press any key it still goes into windows just fine.
And if you do not have any windows installed, there are no problems whatsoever.
Good luck!

---

