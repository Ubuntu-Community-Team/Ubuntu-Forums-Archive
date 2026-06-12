---
title: "Testing mdadm"
date: 2015-03-03
forum: Server Platforms
---

### Post by chris355 on 2015-03-03
Hello all,

So I have a server that has been running smoothly for a few years now.  I have it set up as RAID5 - containing 6*2TB HDDs.

Recently I have been looking at ways to warn me of any potential issues; I have set up the email alerts (I think).  Now I am wanting to perform a test, or a 'pretend' failure; but here's the thing, I don't want to array to perform a re-build.  This bothers me because if my "alert" setup/configuration isn't working does this mean I need to wait a couple of days for the rebuild to complete just so that I can re-test it?

All the stuff I read (online guides) suggests to do something to degrade the array, but what if I just want to check the 'wiring' so-to-speak?

This leaves me with 2 questions:

1) Can mdadm alerts be tested without having to rebuild arrays?

2) Can mdadm run a command for a specific drive that has failed?  For example I have a command that can change my HDD LEDs to red, so I would want it to run a command like: **redled /dev/sdc** (for example)

Currently I manually check drives, but I am getting older and lazier = checking less frequently.  As my drives are getting older I want to be ahead of any future problems.

Many, many, thanks for your time.

---

### Post by lukeiamyourfather on 2015-03-03
I would setup a test machine or virtual machine for developing the alerts script or utility. Don't do this kind of thing on a machine in production with valuable data. Hopefully it goes without saying but if this is valuable data it should be backed up. Especially with RAID 5 and that many drives that are that large. Chances are not exactly slim that another drive could fail during a rebuild.

In the future consider ZFS on Linux which has features similar to RAID (RAID Z2 is similar to RAID 6). Among many other benefits, transient outages take very little time to repair because ZFS is both a file system and a volume manager and it can track what changes while the drive is offline and repair only those aspects. Traditional RAID is unaware of the file system and is unable to track such changes (so you have to rebuild the whole thing even if not much changed while the drive was out).

---

### Post by nerdtron on 2015-03-03
> 1) Can mdadm alerts be tested without having to rebuild arrays?

I also wrote script for monitoring mdadm outputs or rather the /proc/mdstat output to monitor the state of the software raid. To test the script I just create a virtual machine (virtual box) on my desktop pc and test the crontab script to alert from there.


> 2) Can mdadm run a command for a specific drive that has failed?  For  example I have a command that can change my HDD LEDs to red, so I would  want it to run a command like: **redled /dev/sdc** (for example)

I'm under the impression that your server is a server hardware (not desktop) so doesn't it have indicator LEDS on each HDD?
I'm not aware of any command inside ubuntu that can make a led blink red.

---

### Post by lukeiamyourfather on 2015-03-03
> **nerdtron said:**
> I'm not aware of any command inside ubuntu that can make a led blink red.

Some controllers have this feature accessible to users (typically called locate). However the controller should indicate a failed disk on it's own automatically.

---

### Post by MAFoElffen on 2015-03-03
> **lukeiamyourfather said:**
> Some controllers have this feature accessible to users (typically called locate). However the controller should indicate a failed disk on it's own automatically.
I never thought about using them for that, but yes, 3 of my servers each have 10 hot-swap SAS drives, where the hot-swap trays have LED's that I can blink to indicate that they are who they are supposed to be(?) ...so you can locate that drive quickly.

---

### Post by chris355 on 2015-03-03
Awesome replies, thank you guys very much!

Just to clarify something that appears confusing - the server is a x64 based NAS which acts just like a desktop allowing me to install anything I like on it.  The LEDs would normally indicate hdd issues by changing to red by themselves while using the *original *NAS 'firmware' - so as a work around I have written a driver to allow me to change the state of the LEDs via a command.  I guess I was hoping for an automatic way for this to happen, just as it would have originally.

Both suggestions about the virtual testing is excellent, and I particularly like the idea of a cron script running a quick exam too, (this script could also allow the LEDs to change state - superb)

nerdtron: if you have your script at hand, and if you are happy to share, would you mind posting it for me? :)

lukeiamyourfather: cheers for making me aware of zfs, it sounds great and I'll take a look in to this.  (I do indeed have a separate server running rsync backups).

Thanks heaps.

---

### Post by nerdtron on 2015-03-04
Just a simple test for bash:

See I have three md devices, UU means they are OK, if it is not UU, then there is an error.
```
cat /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 sdb1[2] sda1[0]
      204788 blocks super 1.0 [2/2] [UU]
      
md1 : active raid1 sda2[0] sdb2[2]
      511992 blocks super 1.1 [2/2] [UU]
      
md2 : active raid1 sda3[0] sdb3[2]
      7669752 blocks super 1.1 [2/2] [UU]
      bitmap: 0/1 pages [0KB], 65536KB chunk

unused devices: <none>
```

Now for the script checking UU:
```
#!/bin/bash
# check the UU status of each md device /proc/mdstat
for i in `grep block /proc/mdstat | awk '{print $NF}' | cut -c2,3`; do
    if [ "$i" == "UU" ]
    then
    echo "MD device OK"
    else
    echo "MD device not OK" | mailx -s "MD device not OK" -- myemail@gmail.com
    fi
done

```

setting up email relay is a different config of course but you get the idea.

---

### Post by chris355 on 2015-03-04
Brilliant, I really appreciate this..

how frequent do you run yours?  I was thinking once per day would be enough ..?

Thanks a ton for this idea.

---

### Post by nerdtron on 2015-03-04
Frequency depends on how often you like (or how paranoid you are). It's a very simple script so it won't get take any much resource, every hour or every three hours is enough if you like.

---

### Post by MAFoElffen on 2015-03-04
I do an email to my phone with
```

mdadm --monitor -m myemail@gmail.com /dev/md0 -t

```
But in scripts, while running, the return status of 
```

mdadm -D

```
 is nonzero if there is any problem such as a failed component:

0 indicates the status is okay
1 indicates an error that the RAID mode compensates for
2 indicates a complete failure

---

### Post by lukeiamyourfather on 2015-03-04
> **chris355 said:**
> lukeiamyourfather: cheers for making me aware of zfs, it sounds great and I'll take a look in to this.  (I do indeed have a separate server running rsync backups).

I taught a class on it to a small group last year. The presentation below goes through command by command on an Ubuntu system and talks about the basics of ZFS on Linux.

[http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf](http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf)

This is a presetnation from some of the original developers at Sun back when ZFS was new to the world. It covers some of the design features and differences compared to existing file systems.

[http://www.cs.utexas.edu/users/dahlin/Classes/GradOS/papers/zfs_lc_preso.pdf](http://www.cs.utexas.edu/users/dahlin/Classes/GradOS/papers/zfs_lc_preso.pdf)

This is a pretty good resource that covers most of the ZFS on Linux functionality.

[https://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/](https://pthree.org/2012/04/17/install-zfs-on-debian-gnulinux/)

---

### Post by MAFoElffen on 2015-03-05
Sidenote-- I have an opensource mdadm related project... and host a RAID/LVM testing environment for another project. I set up most my tests in virtuals. Lots faster to setup the test conditions, are contained and disposable. (<-- no intrinsic sentimental attachment)

Although, I do have two test Franken-Server storage servers setup with test drives. Some tests I really want to test out on hardware to see the what-if's. Luckily, I have the support of a local electronics recycler, who gives me drives that fail his pre-screen reconditioning tests.

---

