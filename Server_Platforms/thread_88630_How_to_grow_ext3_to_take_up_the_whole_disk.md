---
title: "How to grow ext3 to take up the whole disk"
date: 2005-11-10
forum: Server Platforms
---

### Post by vinjvinj on 2005-11-10
I have a grid of ubuntu servers which I have built from one disk image. My disk image is 40gig but some of the other servers have larger drives. the Master is setup with two partitions, one partition is for the swap drive (6gig) and (34 gig) for the other partition. I would like to extend the second partition on the larger drives without erasing the data on the drive. 

vinjvinj

---

### Post by 23meg on 2005-11-10
You should be able to use Gparted to resize the partition. Be warned that resizing partitions with existing data is always risky though.

---

### Post by vinjvinj on 2005-11-10
the problem is that i'm in server mode and there is gnome isntalled. Also since I'm dealing with 20 servers I would like to have a command line command that can be scripted. Ideally something which can ask to grow a partition to maxsize.

---

### Post by 23meg on 2005-11-10
parted, to which gparted is a frontend, should do it then.

---

### Post by vinjvinj on 2005-11-11
Thanks. Looks like parted will do the job. But is there a way to have ti grow to maximum instead of specifying the size of the partition. Since I'll be scripting it on a grid of servers. I will not know before hand the exact size of each hard disk. 

Vineet

---

### Post by 23meg on 2005-11-11
parted asks for the partition start/end in megabytes, so you'd need to query for the exact size of each disk. This should be doable using variables and some filtering with a bash script. A great resource to learn about bash is [linuxcommand.org]("http://www.linuxcommand.org"); if you take a look at the tutorials there you should be able to hack together something that will work.

---

### Post by vinjvinj on 2005-11-11
Cool. I'm very comfrtable in python so it would probably be in python! Anyways what would happen if I specified 200gig on parted would it just grow to largest available?

Thanks for your help though.

---

### Post by 23meg on 2005-11-11
Hmm, not sure about that, never tried; maybe you should try it on one of the computers and see what it does. If it worked it would be a dirty but practical solution though.

---

### Post by LordHunter317 on 2005-11-11
Just extending the partition isn't enough, you have to grow the filesystem too.

resize2fs can do this, but not online.  You should take a backup before performing either operation.

---

### Post by vinjvinj on 2005-11-12
I don't understand why you have to resize a partition after you extend it???

ALso what do you mean offline vs online? DO you have to boot off a cd and then resize it? This would kill me when I have to go do this on 25+ servers.

---

### Post by stilus on 2005-11-13
You could just take the partitions in question offline, that is assuming the one who installed the servers followed good practise and kept (amongst others) the OS partition seperate from the disk space you now need to extend and grow.
EMVS/LVM would have been a great help here ...

---

### Post by vinjvinj on 2005-11-16
now the partition space all makes sense. It makes sense to have the OS in it's own partition and the user space in its own partition. Next time I do a build on all the servers I'll have it set up that way. 

Thanks for the advise.

---

