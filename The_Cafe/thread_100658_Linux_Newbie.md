---
title: "Linux Newbie"
date: 2005-12-08
forum: The Cafe
---

### Post by t_huankiat on 2005-12-08
Hi guys, 
this is my first post. I think it'll be better for me to start it here.

I just bought a new T42 back in June after my old R30 "gone" for good due to the harddisk failure. And that time I had something in my mind. Why not make it a dual boot, you know, the common combination of windows + linux.

But my transition hasn't been very smooth. Pardon me, I'm totally a "Window" guy. The process of resize ntfs, repartition for Linux, dual boot etc etc... I was just so overwhelmed by the fact that there's so much you need to do...

oh well, I started up with Slackware, doesn't work too good with my wireless. I tried SUSE. All seems working but I realized my "IBM Recovery Partition" no longer working (or maybe since my installation of slackware I don't know:confused: )... 

So I thought might as well try something new and I found ubuntu. I heard it's a really easy to use distro of Linux and I thought might as well give it a try...

My current progress... OK this is the complicated part. I've been trying out to repartition so that I can have windows, ubuntu, and the "recovery" all working... but so far still no luck! while I'm writing this new post, it's my third time of the week reinstalled my computer:???: (Am I dumb or something...??) 

Still looking around to find a solution... I'm always stuck at the part of repartition and still keeping the "recovery" to work. So to not waste any more time reinstall, I decided to first look around and study about the whole process before I proceed... and that brings me here... Hope I can find a solution from this great community!

---

### Post by wondering_jew on 2005-12-08
One thing you might try is a 3rd party application for windows that will help you partition your hard drive I can't think of one besides partition magic and it cost money but you might find something similar

...this reminds me, the last time I partitioned my hard drive I popped in an install cd for mandrake 8.1 and it had a really easy to use disk partition/resize existing partition utility and then I canceled the install before it did anything else :) 
....perhaps thats something the developers might look into for future releases it would make the install cd perfect if it could resize the windows partition so you can make linux partitions...

One word of advice Is to back up all your important files and such if you haven't and make sure that windows is installed before linux (should something unlikely happen) so that windows won't hide grub

---

### Post by Joe_CoT on 2005-12-08
How do you put the recovery parition back on? do you just pop in the restore cd?

Anyways, if you're reinstalling this much, you're probably best just backing up your data, making the partitions from scratch, and installing everything. After you put the recovery partition on, use the windows installer to make the windows partition, install windows, and then make the linux partition when you install ubuntu.

You can resize the windows partition using partition tragic (in windows) or qtpart (in linux), but for all the pomp and circumstance dynamic partitioners have been given, i've had them fail on me too many times to even bother trying them.

---

### Post by t_huankiat on 2005-12-08
The reason for me to took that really "brave" move to reinstall again and again was I bought a new external HD during the afterthanksgiving sale! and I backed up those important files before I started the "wild journey"...

and as for the reinstallation, I created the IBM recovery CDs (7 in total:???: ) since my recovery partition is no longer recognized and bootable:( Sounds funny, but the CDs are used to recover the reocovery partition. And boot again from the recovery partition to reinstall factory defaults...

---

