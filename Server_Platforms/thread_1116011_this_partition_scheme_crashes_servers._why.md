---
title: "this partition scheme crashes servers. why???"
date: 2009-04-04
forum: Server Platforms
---

### Post by bluethundr on 2009-04-04
Hi guys,

 A hacker friend and I are building some apache servers for a company that's hired us. My first ever apache gig! FTW!!! heh

 Okay, my overwhelming enthusiasm for the project aside I could seriously could use some help.

 So my friend and I came up with a partition scheme that we thought would be sensible for a potentially busy web server. The machines we are using come with 250GB scsi drives. Ample room for the servers we intend to build.

 However, whenever we build servers this way they CONSISTENTLY crash. And neither of us have any idea why. Anyway, here's the plan we came up with:
```

 swap  4096 mb
/boot 25 mb -ro
/ 15 gb
/usr 25 gb
/var/log 25 gb
/home 50 gb
/var/ftp 25 gb
/dev 5 gb
/var/www 100.9 gb

xfs filesystem
```

  The parts are listed in order they are physically created on the drive. IE swap first, /boot second, / third etc.

 However... this is the error we get consistently whenever we try to boot a server built this way:
```

 Starting portmap daemon...portmap: fork: No such device.
Starting NFS common utilities: statd failed!
/etc/rcS.d/S48console-screen.sh: line 40: cut: command not found
/etc/rcS.d/S48console-screen.sh: line 40: [: =: unary operator expected Setting console screen modes and fonts.
/etc/rcS.d/S55bootmisc.sh: line 50: savelog: command not found
[ 14.272718] etch0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[ 14.272779] eth0: 10/100 speed: disabling TSO
```

 I restart the install process and go with a standard, guided layout everything works fine. 

 Initially my thought was to setup root and boot in static parts, and everything else in LVM. However I was having trouble with that approach and (for the first time in my apache work) I am on a deadline. So I canned that project and came up with the scheme I show you above.

 Ideally, if I had my choice, I would like to go with LVM for just about everything. I like the idea of having flexibility of altering part sizes based on production demands as they become apparent. And the ability to establish quotas and notifications in an LVM scheme is very appealing indeed. Which reminds me, can quotas be setup on static parts?

 So when I (out of apparent necessity) went with a standard guided scheme I chose the default LVM layout. Here is how my parts are currently laid out:

```

/ 328 mb
/lib/init/rw 1.7 gb
/dev 10 mb
/dev/shm 1.7 gb
/boot 229 mb -ro
/home 222 gb
/tmp  376 mb
/usr  4.7 gb
/var  2.8 gb

```

Ok. Now I must admit that while my apache skills were enough to get me the job, I am a novice at much of this. Namely, I never went too wild in my partitioning schemes in my little toy web servers so I don't know for instance why anyone would ever need a separate part for say  ```
/lib/init/rw
``` or ```
/dev/shm 
```. 

What's so magical about those places that they might need their own partitions? It seems to me that if I am going to start running with the big dogs and not just mucking about with toy websites every once in a while I better RTFM on this stuff and quick! If I knew where to look for the manual on this particular topic, that is! ;-) 

So ultimately, and finally, my question is this. WHY on earth did the original partitioning scheme that me and my friend made not work?!?!?!? And secondly, let's say for the sake of argument that our original idea was so flawed that we have to abandon it and go with something different. Any harm in going with the default LVM layout on a fairly busy web server (supporting say 1,000 or so people a month to start)?

Thanks! I always get the best advice from you guys and I'm looking forward to hearing your thoughts!

---

### Post by koenn on 2009-04-04
I think the separate /dev partition isn't going to work, and might be the reason for an error such as "No such device."

You can't just arbitrarily toss around parts of the file hierarchy on separate partitions. Stuff that is going to be used before you can mount other filesystems, needs to remain in the / partition.

besides that, /dev is a collection of file handlers to things that aren't really files, so  it doesn't even need a separate partition 

something similar is going on with e.g. /proc, /sys, /lib/init/rw, /dev/shm ;
you don't create those partitions, the system creates them as filesystems so they can be threated as files, but they aren't. 

You're hacker friend didn't know any of that ?

---

### Post by bluethundr on 2009-04-04
> **koenn said:**
> I think the separate /dev partition isn't going to work, and might be the reason for an error such as "No such device."

You can't just arbitrarily toss around parts of the file hierarchy on separate partitions. Stuff that is going to be used before you can mount other filesystems, needs to remain in the / partition.

besides that, /dev is a collection of file handlers to things that aren't really files, so  it doesn't even need a separate partition 

something similar is going on with e.g. /proc, /sys, /lib/init/rw, /dev/shm ;
you don't create those partitions, the system creates them as filesystems so they can be threated as files, but they aren't. 

You're hacker friend didn't know any of that ?
hmm! I guess not! Now he knows and so do I! Thanks! I'll be sure to show him this thread. Also, as to my question about establishing quotas and notifications on static parts... doable?

---

### Post by koenn on 2009-04-04
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas)

so, you have a company paying you for your linux expertise that you substitute with forum posts, and you're learning the ropes on what to them is a production server that will be exposed to the internet ?

---

### Post by bluethundr on 2009-04-04
> **koenn said:**
> [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch28_:_Managing_Disk_Usage_with_Quotas)

so, you have a company paying you for your linux expertise that you substitute with forum posts, and you're learning the ropes on what to them is a production server that will be exposed to the internet ?
yes!!!! and thank you for the sterotypical, snarky computer guy response. 

and thanks too for the info...

---

### Post by koenn on 2009-04-04
> **bluethundr said:**
> yes!!!! and thank you for the sterotypical, snarky computer guy response. 

I owe it to myself and my fellow 'computer guys'. If you screw up, you give the the real pros a bad name ...

---

### Post by bluethundr on 2009-04-04
> **koenn said:**
> I owe it to myself and my fellow 'computer guys'. If you screw up, you give the the real pros a bad name ...


whatever dude. ok, you win. you are BETTER than me in every way. satisfied, nao? hey, it's either this or pump gas. by the way, those things you may have heard of? you know seeing sunlight once in a while and kissing girls? highly recommended! you should try it some time! ;-)

---

### Post by koenn on 2009-04-04
> **bluethundr said:**
> whatever dude. ok, you win. you are BETTER than me in every way. hey, it's either this or pump gas. by the way, those things you may have heard of? you know seeing sunlight once in a while and kissing girls? highly recommended! you should try it some time! ;-)

well, I'm sure it beats pumping gas.

by the way, those other things, my wife does tell me to get from behind the computer and out of the house some times, but I don't think she'll agree with me going around kissing girls (or boys, for that matter)

not all of us here are teenagers, you know ...
:)

---

### Post by bluethundr on 2009-04-04
> **koenn said:**
> well, I'm sure it beats pumping gas.

by the way, those other things, my wife does tell me to get from behind the computer and out of the house some times, but I don't think she'll agree with me going around kissing girls (or boys, for that matter)

not all of us here are teenagers, you know ...
:)

hahaha! okay, man! peace? can we all just get along? can we stop stereotyping each other based on what we know and don't know?

---

### Post by koenn on 2009-04-04
> **bluethundr said:**
> hahaha! okay, man! peace? 

no problem.

---

### Post by bluethundr on 2009-04-04
> **koenn said:**
> no problem.

cool beans. ;-)

---

### Post by cariboo on 2009-04-04
I might be an idea to brush up on the Linux File System [Hiearchy]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/"), before setting up any partitions.

Jim

---

### Post by kpatz on 2009-04-04
Don't put /dev or /usr in their own partitions.  /dev is a special filesystem that has device nodes in it, and is "mounted" automatically on boot.  /usr has files in it that are needed during boot but won't be available until the mounts happen...

Otherwise, you should be good to go.

---

### Post by koenn on 2009-04-05
> **kpatz said:**
> Don't put /dev or /usr in their own partitions.  /dev is a special filesystem that has device nodes in it, and is "mounted" automatically on boot.  /usr has files in it that are needed during boot but won't be available until the mounts happen...

you're right about /dev (see post #2 in this thread) but you're plain wrong about /usr

/usr contains mostly end-user applications, and can have its own partition. It's even not unusual to have NFS mount /usr off a remote system.

binaries that are required before /usr is mounted go in /bin and /sbin.

---

### Post by netztier on 2009-04-05
> **bluethundr said:**
> 
Initially my thought was to setup root and boot in static parts, and everything else in LVM. However I was having trouble with that approach and (for the first time in my apache work) I am on a deadline. 

I strongly suggest to revert that decision while you still can, or it's going to come for you before you're out of the door of that shop after handing over the server. And once the data's started growing on these drives, repartitioning is going to take quite some (down)time.

LVM isn't that hard, and now since that part with /dev is sorted out, you should be quite safe go set it up. Are the disks in some mode of redundancy (RAID1 or 5), and do you have a proper backup strategy?

regards

Marc

---

### Post by bluethundr on 2009-04-08
> **netztier said:**
> I strongly suggest to revert that decision while you still can, or it's going to come for you before you're out of the door of that shop after handing over the server. And once the data's started growing on these drives, repartitioning is going to take quite some (down)time.

LVM isn't that hard, and now since that part with /dev is sorted out, you should be quite safe go set it up. Are the disks in some mode of redundancy (RAID1 or 5), and do you have a proper backup strategy?

regards

Marc

Great advice! Thank u! LVM is now configured on all 3 web servers. :guitar:

---

