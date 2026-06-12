---
title: "dual Raid-1 but only half the quarter of space"
date: 2007-09-17
forum: Server Platforms
---

### Post by Bananaguru on 2007-09-17
Ok, I am making progress but i am puzzeled again :popcorn:

here is what I have

- 80gb drive for startup
- 4x 500gb sata

Here is what I have done:
- install ubuntu server on the 80-Gb.
- create two raid-1 arrays via mdadm on the 4x500Gb:

ARRAY /dev/md0 level=raid1 num-devices=2 UUID=7f9926e5:abdea771:333efd14:6b8b6856
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=1771d77c:9a7fb871:333efd14:6b8b6856

Did the mkfs.ext3 for both and edited the /etc/mdadm.conf with the arrays.

added them to fstab (both 
cherio@box:/$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/md0 on /home type ext3 (rw)       [COLOR="Red"]<--- here is one[/COLOR]
/dev/md1 on /home type ext3 (rw)       [COLOR="Red"]<--- and here is two[/COLOR]


Then did the Samba installation and created a user other then my normal one.

Now i can log-on from my Windows XP laptop to \\box\user

So far so good I think.

Now..... I have two RAID-1 arrays of with each 2x 500gb drive.  So, the space available should be around 1Tb.

When I connect to the server via Windows, i see that i only have 500Gb available (one quarter).

So, i must have done something wrong.  Please help :confused:

Help ?

PS.I see the same from my Apple.... also 500gb instead off 1Tb

---

### Post by HarshReality on 2007-09-17
RAID 0+1: striped sets in a mirrored set (minimum 4 disks; even number of disks) provides fault tolerance and improved performance but increases complexity. The key difference from RAID 1+0 is that RAID 0+1 creates a second striped set to mirror a primary striped set. The array continues to operate with one or more drives failed in the same mirror set, but if two or more drives fail on different sides of the mirroring, the data on the RAID system is lost. 
RAID 1+0: mirrored sets in a striped set (minimum 4 disks; even number of disks) provides fault tolerance and improved performance but increases complexity. The key difference from RAID 0+1 is that RAID 1+0 creates a striped set from a series of mirrored drives. The array can sustain multiple drive losses as long as no two drives lost comprise a single pair of one mirror.

Quoted from Wikipedia... will make a point to say Ive never done a R1 config nor do I know how often that wikipedia is updated but in both those remarks its claiming a min. or 4 disks needed. If your feeling froggy have you tried taking one of the boxes and creating a single array using all 4 disks and then just creating partitions to seperate data?

---

### Post by Bananaguru on 2007-09-17
Yeah, you are right, but I dont really need the speed, its just a dumb file server (ohh and print server once I get that working).

Stripping only adds to the complexity. If i wanted a bigger array I would have done RAID-5. I guess salvaching a raid-5 is as much of a mess as raid-10. 

So, I want two Raid-1 arrays.....  but i am sure i am missing something. I think i will read backinto Raid 10.

But why ca't I just have two raid-1 array ?

---

### Post by Bananaguru on 2007-09-17
Should I do then:

mdadm --create /dev/md3 --chunk=64 --level=0 --raid-devices=2  /dev/md0  /dev/md1 

??

This is to make Raid-1 /md0  and Raid-1 /md1 into a RAID-10 /md3 ?

:confused:

---

### Post by gombadi on 2007-09-17
> 
cherio@box:/$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/md0 on /home type ext3 (rw) <--- here is one
/dev/md1 on /home type ext3 (rw) <--- and here is two


You are mounting both arrays on /home.

It will mount the first array from md0 and give you 500GB of space then it will mount the second array from md1, and mask the first array(md0) out. The result is that you will only see 500GB available from md1.

Mount them in different locations. i.e. /home and /home1 and then do a df -h and see what is available.

---

### Post by Bananaguru on 2007-09-18
thanks for the input, it show that I dont really know what I am doing other then copy-pasting from web-pages :-)

Anyway, I have created a raid-o arrary of the two raid-1's.

And then I mount only the last RAID-o arrary to home.

Now it works. I hope I did it right, the space is correct although with quite some overhead.

Questions:

- it is possible to have two drives creating a volume for /home ? (this is to avoid different directories /home /home1 (or didnt i understand it)

- does someone have experience wiht the stability of RAID-5 in Ubuntu ? (software raid) I have quite some overhead on the current three arrays.

thanks,

B

PS. remember that I started this last weekend, this being my first linux encouter and I am not even een IT engineer. So, it take me a while to catch up/on

---

### Post by gombadi on 2007-09-19
You can't directly have more than one drive mounted in one place.
Your options are raid-0, as you currently have done or lvm which would give the same effect as the raid-0 array you have. Both mean another layer of work for the kernel but then again I doubt you will notice any difference in performance.

Raid-5 is just as stable as raid-1 or raid-0. If you use one then the others should be fine.

You started a week ago and you have raid arrays up and running. You are doing well :) It took me longer to get a raid array on any of my systems - disk were a bit expensive back then :)

---

### Post by koenn on 2007-09-19
> **Bananaguru said:**
> Questions:
- it is possible to have two drives creating a volume for /home ? (this is to avoid different directories /home /home1 (or didnt i understand it)

I think that's done with LVM (Logical Volume Manager)
[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

As I understand it (never used it !), LVM combines multiple physical volumes (partitions, disks, ...) into a logical volume (that you then can mount). 
In your case, /dev/md0 and /dev/md1 would be the physical volumes. The fact that they are arrays themselves, shouldn't really matter, as each array presents itself as a device (or a volume). 
At least, that's what i think.

---

### Post by Bananaguru on 2007-09-20
Thanks again for all the input.  After carefull thinking, I am gonna stick for the moment with Raid'10. Perhaps later I will try LVM. (depending on the my experience wih recovery).

Now, I am gonna think about disaster recovery. Since now I have got something that is working, for sure it will go wrong in the future.

And its better to test now, while its still empty.

I will check two things.First is the simple drive failure. Which shouldnt be to diffilcult.

But the point I am more concerned about is system-drive failure since I have no idea how that will work. When I lose all my configuration etc et etc.

I´ll repost into a new thread with questions on that.

Thanks all,

B

---

### Post by koenn on 2007-09-20
> **Bananaguru said:**
> 
But the point I am more concerned about is system-drive failure since I have no idea how that will work. When I lose all my configuration etc et etc.

From what I heard, it's quite possible to reconfigure a software raid on a different system and reuse the disks to get access to the data again. 
It would probably require you to document your raid config very well, and redo the same thing on the new system. 
It's definitely a good idea to practise this without 'real' data and get the procedure straightened out so that, in case of a real disaster, you know what steps to take, in what order, and have access to all the information you need. 
Have fun !

---

### Post by Bananaguru on 2007-09-24
Thanks, for some reason one of my drives dropped out of the array. (sdb of md0).

Its an easy fix with:  mdadm /dev/md0 -a /dev/sdb, and its re-syncing now.

I wonder why it dropped out. I guess that my config isnt right yet and it works because of luck, not logic. 

Have to do more reading on this to make sure I got it solid.

B

(in the mean time I got Samba working providing access for my Apples and XP boxes, still working on Wake-on-Lan, got some network issues with that)

---

