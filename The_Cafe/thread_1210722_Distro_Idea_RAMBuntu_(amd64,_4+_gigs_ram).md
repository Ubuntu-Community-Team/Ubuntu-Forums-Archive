---
title: "Distro Idea: RAMBuntu (amd64, 4+ gigs ram)"
date: 2009-07-11
forum: The Cafe
---

### Post by earthpigg on 2009-07-11
[SIZE="4"]_thought exercise._[/SIZE]

RAM is dirt cheap.
SSD's give outstanding performance, but is quite expensive.

why not have your computer copy the contents of your / and /home partitions into [RAM]("http://en.wikipedia.org/wiki/RAM_disk") at boot, and then copy them back to your hard drive at shut down?

_**advantages:**_ lightning fast performance. the *speed of RAM* isn't quite as fast as a speeding bullet, but its close. finally, something to do with all that RAM!

_**disadvantages:**_ 

*storage space.* it is quite possible to have a machine able to surf the web, check out youtube, play dvd's, and do word processing in under 3gb of hard drive space. playing around in VM, i had all of this at about 1.6gb.

*power loss*. an unexpected power failure could potentially be catastrophic. users would be strongly encouraged to have a UPS.

*slow boot and shut down*. booting would involve copying the entire contents of the / partition into RAM. shut down would involve copying all of that back onto the hard drive.

*system requirements*. 4 gigs of ram seems to be increasingly common now-a-days. that would be a minimum requirement. 3 gigs would be 'hard drive', 1 gig of ram. a conventional hard drive would still be needed for storage of music, pictures, etc.



**_implementation._**

ubuntu minimal with lxde, using all the traditional lightweight software.

stick to the ubuntu philosophy and whatnot so, hopefully, the name 'RAMBuntu' and the ubuntu logo, etc, could be used.

*default partition scheme:*

R = total system ram.

/ partition would be .75R.

.25R would be left alone, to be used as conventional ram. 

1R for swap. 

remainder of hard drive would be the partition intended for music, videos, etc.

/ would be copied into ramdisk at boot. after the copying is complete, the system continues to boot from that ramdisk. at this point, the hard drive's / partition would be unmounted and not written to again until shut down.

the home folder would only be used for software configuration files. users would be strongly encouraged not to store anything else there. 

alternatively -- /home could remain on the traditional hard drive. <-- trying a few configurations would be needed. just how much faster does firefox load, for example, if firefox is already in ramdisk, but the bookmarks and personal settings are on a traditional hard drive?


*software limitations:*

looking at my own computer, i can see that several pieces of software would be completely out of the question - virtualbox is at the top of that list, obviously :P

the apt-get cache would need to be cleaned on a regular basis. perhaps automatically at boot, perhaps limit it to 100mb. limit all system logs to 25kb or something like that.

---

### Post by monsterstack on 2009-07-11
I had a [similar idea]("http://ubuntuforums.org/showthread.php?t=1197798") just a couple of weeks ago. I too thought of the Rambuntu name, although I was considering Debram instead. Oh well!

A kind member gave me the link to a Gentoo forum [thread]("http://forums.gentoo.org/viewtopic-t-296892.html") [gentoo.org] where a few people were trying this idea out with only a gigabyte of RAM, so it most certainly can be done. In the guy's test runs, Firefox opened in 0.01 seconds, which goes to show the performance benefits you can achieve. I haven't got my new RAM yet (I'm getting lots soon!) but when I do I'll be actively pursuing this. I want to make a shell script that'll open 30 applications and time it to see how long it takes. I can't wait. :)

---

### Post by Mehall on 2009-07-11
Design a script which you can run on boot, which copies the contents of / (excluding /root /home etc. as noted in the gentoo forums thread) to a ramdisk.

If required, have a script you call to shutdown (alias it to shutdown, obv) which saves any changes back to the HDD, and THEN shutsdown, though that may not be neccesary. (especially since /home would be on the HDD anyway)

---

### Post by Bart_D on 2009-07-11
> **earthpigg said:**
> [SIZE="4"]...
SSD's give outstanding performance, but is quite expensive.....

The OCZ Vertex 30gb(MORE than enough for Linux or Windows) costs around $150(US), which is **ONLY** around $40(US) more than a 7200 RPM WD Caviar Black....and the SSD price is falling.  Boot up and shut down times are lightning fast with the Vertex.  Set 2 up in RAID0 and your need for speed is set for life!

PLUS, I'd imagine that the average Linux user has less than 4GB of RAM and/or does not have a 64 bit processor which is NEEDED to access ALL 4GB!

---

### Post by Mehall on 2009-07-11
> **Bart_D said:**
> The OCZ Vertex 30gb(MORE than enough for Linux or Windows) costs around $150(US), which is **ONLY** around $40(US) more than a 7200 RPM WD Caviar Black....and the SSD price is falling.  Boot up and shut down times are lightning fast with the Vertex.  Set 2 up in RAID0 and your need for speed is set for life!

PLUS, I'd imagine that the average Linux user has less than 4GB of RAM and/or does not have a 64 bit processor which is NEEDED to access ALL 4GB!

ONLY $150 for a 30GB ssd?

that's ONLY to you?!?

I can pay £50 for a 320GB traditional HDD!!!

That's OVER 10 times the capacity! For less than half the price!

---

### Post by init1 on 2009-07-11
I do something similar to that with Slitaz. I run the system like a live CD, except /home is on my hard drive. Therefore, everything but my personal files and settings get copied into RAM when I boot. It's very fast.

---

### Post by Bart_D on 2009-07-11
I'm not saying that people should sprint out the door and buy SSDs....hehe, I sure as hell WON'T....but with falling prices, you can overcome that slow startup/shutdown issue.  Plus, **more importantly**, you won't have to risk data loss in the event of a power surge.

And capacities are irrelevant here because you don't NEED more than a 10 GB HDD for Linux, so the fact that you got a 320 GB HDD for less than the price of a 30 GB SSD doesn't mean much...cause the drive is slower!

---

### Post by Mehall on 2009-07-11
> **Bart_D said:**
> I'm not saying that people should sprint out the door and buy SSDs....hehe, I sure as hell WON'T....but with falling prices, you can overcome that slow startup/shutdown issue.  Plus, you won't have to risk loss in the event of a power surge.

And capacities are irrelevant here because you don't NEED more than a 10 GB HDD for Linux, so the fact that you got a 320 GB HDD for less than the price of a 30 GB SSD doesn't mean much if the drive is slower!

Except for all your user data maybe?

@init1: Care to tell us how?

---

### Post by ericab on 2009-07-11
> **Mehall said:**
> Except for all your user data maybe?

@init1: Care to tell us how?

i second this request
+1

---

### Post by linuxguymarshall on 2009-07-11
On a desktop this is a horrible idea. But on netbooks this would be an excellent alternative to SSDs because RAM is cheaper and lighter.

---

### Post by uljanow on 2009-07-11
You can [already do that]("https://wiki.ubuntu.com/BootToRAM"). There used to be an option or still is to pass an argument like toram to the Ubuntu Live cd. Only changes are written to disk (cow).


What I do like to see is an initramdisk (max 8MB) that supports different hardware and boots in 3 seconds and is similar to Splashtop.

---

### Post by earthpigg on 2009-07-11
> **linuxguymarshall said:**
> On a desktop this is a horrible idea. But on netbooks this would be an excellent alternative to SSDs because RAM is cheaper and lighter.

part of the idea is to make the most of what many of us already have, but dont really make any use of.

....and, *because i can*. ;)

---

### Post by Psyphre on 2009-07-11
I actually want to challenge this idea that RAM is insanely fast (for use with applications anyway).

Ive heard alot about using ram as storage and how lightning fast it is, so I gave it a try today. I created a 1gb storage folder using tmpfs and mounted it. I then tried a few experiments such as the following:

1) Copied over a large folder of images. Used eye of gnome to browse through them. Took just as long to load each image as i pressed 'next'.

2) Copied over a movie (.avi format) and played it. Took just as long to open it as normal and no noticable benefit when grabbing the slider and moving it back and forth.

3) Copied over a folder which held an application in it. Took just as long as normal to load that application. There was no lightning fast loading of the program.

Now im in no way an expert, im a noob, so im not saying your wrong (infact I hope your right because i want to use it too), its just that from what ive shown above i cannot see the slightest shred of speed increase.

Am i doing something wrong?

---

### Post by linuxguymarshall on 2009-07-11
> **earthpigg said:**
> 
....and, *because i can*. ;)

That is something I can relate to ;)

---

### Post by init1 on 2009-07-11
> **Mehall said:**
> Except for all your user data maybe?

@init1: Care to tell us how?

> **ericab said:**
> i second this request
+1
1. Create a new partition on your hard drive
2. Boot up Slitaz from the CD and copy /home/tux into that partition
3. Reboot (still using the CD) and type home=/dev/yourhomepartition as the boot argument

Honestly, I've never done it this way. It should work though. I've always done this by extracting the initrd, editing the fstab, and rebuilding it. This is much simpler though.

---

### Post by earthpigg on 2009-07-11
> **Psyphre said:**
> 
Am i doing something wrong?

dunno. im a noob too. anything copied to /dev/shm is simply loaded into ram, correct?

what i am doing as we speak:

-copying an ubuntu minimal .iso to /dev/shm
-creating a 1.6 gb virtual disk at /dev/shm

-installing ubuntu minimal + lxde in a VM with the virtual hard drive located at /dev/shm



will this demonstrate anything to me, or am i wasting my time?

---

### Post by earthpigg on 2009-07-11
```
ep@ep-9:/dev/shm$ df -h .
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 2.0G  1.6G  366M  82% /dev/shm
ep@ep-9:/dev/shm$ ls -Ss
total 1619704
_1607764 shm.vdi_                   100 pulse-shm-495328480    11408 mini.iso
    420 pulse-shm-2690479870       12 pulse-shm-823686063
ep@ep-9:/dev/shm$ 

```

shm.vdi is my 1.6gb virtual disk.

yes/no?

---

### Post by toupeiro on 2009-07-12
Don't be deceived that because RAM is fast that its necessarily better. For some things, its great, but understand that CACHE is as vital to a hard drive as RPM's if not more.  Its the fastest memory in your entire system, and end user partitioned RAM disks do not have access to it.

---

### Post by aysiu on 2009-07-12
Doesn't Puppy Linux do this? I think it has an option to load into RAM.

---

### Post by earthpigg on 2009-07-12
> **aysiu said:**
> Doesn't Puppy Linux do this? I think it has an option to load into RAM.

i know the live cd does.

after you boot from the live cd, you can remove the live cd and, for example, put a dvd in and watch it.

---

### Post by michaelzap on 2009-07-12
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)

---

### Post by toupeiro on 2009-07-12
Something I've actually done to increase SSD performance is have /var/log dumped to a ram drive.  Not the best server practice, but for standalone workstations its great because it reduces total write overhead to the solid state disk.  If you absolutely want them backed up then you can do a very periodic sync to something else in cron or something in an init level when your machine shuts down.  Thats about the only case I can think of where I actually wanted to use a ram drive on a regular basis.

---

### Post by monsterstack on 2009-07-12
> **uljanow said:**
> You can [already do that]("https://wiki.ubuntu.com/BootToRAM"). There used to be an option or still is to pass an argument like toram to the Ubuntu Live cd. Only changes are written to disk (cow).


What I do like to see is an initramdisk (max 8MB) that supports different hardware and boots in 3 seconds and is similar to Splashtop.

> **toupeiro said:**
> Something I've actually done to increase SSD performance is have /var/log dumped to a ram drive.  Not the best server practice, but for standalone workstations its great because it reduces total write overhead to the solid state disk.  If you absolutely want them backed up then you can do a very periodic sync to something else in cron or something in an init level when your machine shuts down.  Thats about the only case I can think of where I actually wanted to use a ram drive on a regular basis.

Why not switch logging off completely? If you ever encounter a persistent problem that requires you to look at them, you can turn logging back on and simply wait for the problem to happen again. I've never once had to look at anything in /var/log.

---

### Post by toupeiro on 2009-07-12
> **monsterstack said:**
> Why not switch logging off completely? If you ever encounter a persistent problem that requires you to look at them, you can turn logging back on and simply wait for the problem to happen again. I've never once had to look at anything in /var/log.

I don't really think that's the greatest idea..

Turning logging off completely is like flying blind, no thanks.  Just because I don't see any value in keeping logs historically on this machine doesn't mean I have absolutely no use for them. I've tailed logs plenty of times while tweaking apps and databases that I could care less about once they're working properly. I'm good with my solution.

---

