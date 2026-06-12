---
title: "Xubu 12.04 Needs More Room than Lucid!"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Peripheral Visionary on 2012-03-15
I'm a newcomer who probably has no business testing a Beta OS. I "inherited" a 10-year-old Dell desktop, very modest hardware by today's standards. It had Xubuntu 10.04 installed on it and it ran wonderfully. The previous owner had these disk partitions set up:

[COLOR=Blue]**/Linux swap**[/COLOR] was 1 gb (2X the machine's RAM)
[COLOR=Blue]**/**[/COLOR] (I guess root or boot) was 20 gb in size, and
[COLOR=Blue]**/home**[/COLOR] took the remainder of the 80-gb drive.

I've been experimenting with Xubu 12.04 for the past couple of days and I found a couple of things that may help others:

[COLOR=Sienna]**[SIZE=3]1_st_[/SIZE]**[/COLOR], Xubu really needs more room than 20 gb anymore. Updates to Precise couldn't finish because "not enough disk space." I created some by removing unwanted applications and doing the "sudo apt-get clean" thing, but really. In another week or month, I would have to remove more stuff to make room anyway. Maybe letting Xubu have the whole drive would have been easier, but I've read that having a separate [COLOR=Blue]**/home**[/COLOR] or [COLOR=Blue]**/data**[/COLOR] partition is better when upgrading. So I resized them using GParted from the LiveCD. 

**[COLOR=Sienna]2_nd_[/COLOR]**, Xubu 12.04 gets slower with "up time." I don't know why. But over the course of a few hours, Xubu Precise needs a reboot in order to get back the snappy speed and responsiveness it has right after boot-up. Is there anything I can do to prevent Xubu from slowwwwwing dowwwwnnnnn over a few hours' time? 

[COLOR=Sienna]**3_rd_**[/COLOR], I was warned by the previous owner that if Xubu wants to install something called "PulseAudio," I should say "No way" and remove it completely. I'm pleased to report that PulseAudio does not cripple the sound in Xubu Precise the way it apparently did in Xubu Lucid. Shhhh, don't tell on me... but I left PulseAudio alone since nothing is broken.

[COLOR=Red]**Edit:**[/COLOR]
**SOLVED** by reinstalling and letting Xubu have the whole drive. I messed up partitions somehow, unless the installer did that when it replaced 10.04 with 12.04, *saving /home*. That's what I get for downloading the Beta from Softpedia instead of the daily build!

---

### Post by dino99 on 2012-03-15
here / is less than 9 Gb on i386

---

### Post by kansasnoob on 2012-03-15
> **Peripheral Visionary said:**
> I'm a newcomer who probably has no business testing a Beta OS. I "inherited" a 10-year-old Dell desktop, very modest hardware by today's standards. It had Xubuntu 10.04 installed on it and it ran wonderfully. The previous owner had these disk partitions set up:

[COLOR=Blue]**/Linux swap**[/COLOR] was 1 gb (2X the machine's RAM)
[COLOR=Blue]**/**[/COLOR] (I guess root or boot) was 20 gb in size, and
[COLOR=Blue]**/home**[/COLOR] took the remainder of the 80-gb drive.

I've been experimenting with Xubu 12.04 for the past couple of days and I found a couple of things that may help others:

[COLOR=Sienna]**[SIZE=3]1_st_[/SIZE]**[/COLOR], Xubu really needs more room than 20 gb anymore. Updates to Precise couldn't finish because "not enough disk space." I created some by removing unwanted applications and doing the "sudo apt-get clean" thing, but really. In another week or month, I would have to remove more stuff to make room anyway. Maybe letting Xubu have the whole drive would have been easier, but I've read that having a separate [COLOR=Blue]**/home**[/COLOR] or [COLOR=Blue]**/data**[/COLOR] partition is better when upgrading. So I resized them using GParted from the LiveCD. 

**[COLOR=Sienna]2_nd_[/COLOR]**, Xubu 12.04 gets slower with "up time." I don't know why. But over the course of a few hours, Xubu Precise needs a reboot in order to get back the snappy speed and responsiveness it has right after boot-up. Is there anything I can do to prevent Xubu from slowwwwwing dowwwwnnnnn over a few hours' time? 

[COLOR=Sienna]**3_rd_**[/COLOR], I was warned by the previous owner that if Xubu wants to install something called "PulseAudio," I should say "No way" and remove it completely. I'm pleased to report that PulseAudio does not cripple the sound in Xubu Precise the way it apparently did in Xubu Lucid. Shhhh, don't tell on me... but I left PulseAudio alone since nothing is broken.

I hope this helps in some little way.

I'm really curious about the disc space usage. Would you please post the output of:

```
df -H
```

Please use code tags if possible (it makes the output a bit easier to read).

---

### Post by Peripheral Visionary on 2012-03-15
> **kansasnoob said:**
> I'm really curious about the disc space usage. Would you please post the output of:

```
df -H
```Please use code tags if possible (it makes the output a bit easier to read).

Sure thing:
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        44G   25G   17G  61% /
udev            240M  4.0K  240M   1% /dev
tmpfs            99M  760K   99M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            247M   80K  247M   1% /run/shm
/dev/sda3        30G  1.4G   27G   5% /home
robin@robin-Dell-DE051:~$ 
```

Is this a good setup? And can anyone explain why the greater the uptime, the slower my Xubu?

Thanks!

---

### Post by meborc on 2012-03-15
Did you do a fresh install of Xubuntu 12.04 daily, or did you upgrade an older one?

I am using a full blown Ubuntu 12.04 with a lot of programs and my usage is around 16 G for the root partition

You might want to remove older kernels that you don't use any more

---

### Post by TunaCanTommy on 2012-03-15
I did a fresh install of Xubuntu 12.04, Beta 1 onto a Asus EeePC 701 using the alternate CD. Before the install I partitioned the SSD as: 150mb and 3.5Gb. I put /boot on the 150MB partition and / (root) on the 3.5 partition.  Then put a 16-GB SDHC (Cat4) in the card reader and used it for /home and 'swap' - don't really think I need a swap-drive though. I have FireFox and Thunderbird installed - not a lot of additional stuff other than that.  I keep the apt/cache cleaned out and use locale-purge.

Here are the numbers I'm seeing now:

SSD /boot Size: 150MB USED: 54.75MB Unused: 92.25MB
SSD / (root) Size: 3.58GB USED:2.38GB Unused: 1.20GB
SDHC /home 11.54GB Used:796.96mb Unused:10.76GB
SDHC /swap 2.89GB

I'm faily happy with the performance of this little critter so far.

---

### Post by Peripheral Visionary on 2012-03-15
> **meborc said:**
> Did you do a fresh install of Xubuntu 12.04 daily, or did you upgrade an older one?
You might want to remove older kernels that you don't use any more

A fresh install of 12.04 on existing partitions, then resized to double the space given to "/". Doesn't
```
sudo apt-get clean
```
remove old kernels?

---

### Post by TunaCanTommy on 2012-03-15
Nope, gotta go into Synaptic and dig them out.
But be very careful what you remove.

---

### Post by kansasnoob on 2012-03-15
> **Peripheral Visionary said:**
> Sure thing:
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        44G   25G   17G  61% /
udev            240M  4.0K  240M   1% /dev
tmpfs            99M  760K   99M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            247M   80K  247M   1% /run/shm
/dev/sda3        30G  1.4G   27G   5% /home
robin@robin-Dell-DE051:~$ 
```

Is this a good setup? And can anyone explain why the greater the uptime, the slower my Xubu?

Thanks!

That blows my mind, 25GB used for "/" (aka: root) is beyond odd. I suspect you must have more than one desktop environment (aka: DE) installed.

I'd like to know just exactly what is installed but DE-wise even with U-X-L-K and maybe myth or "edu" I can't imagine exceeding 8 to 10GB :)

You'll notice there's almost nothing in /home, only 1.4GB but it is mounted so fstab must be OK. I'm guessing someone installed everything they possibly could.

Since this was a hand-me-down how much have you done with it?

With only 512MB of RAM (guessing a bit) I'd personally back up anything important and do a full disk install of either Xubuntu or Lubuntu using the daily images:

[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

But I'm guessing a lot :D

I'm a bit reminded of someones sig from the past that said something like:; Q: "what did you install from synaptic?" A: "everything" :lolflag:

---

### Post by Elfy on 2012-03-15
> **kansasnoob said:**
> That blows my mind, 25GB used for "/" (aka: root) is beyond odd. I suspect you must have more than one desktop environment (aka: DE) installed.

I'd like to know just exactly what is installed but DE-wise even with U-X-L-K and maybe myth or "edu" I can't imagine exceeding 8 to 10GB :)

You'll notice there's almost nothing in /home, only 1.4GB but it is mounted so fstab must be OK. I'm guessing someone installed everything they possibly could.

Since this was a hand-me-down how much have you done with it?

With only 512MB of RAM (guessing a bit) I'd personally back up anything important and do a full disk install of either Xubuntu or Lubuntu using the daily images:

[http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)

But I'm guessing a lot :D

I'm a bit reminded of someones sig from the past that said something like:; Q: "what did you install from synaptic?" A: "everything" :lolflag:
I remember that sig - I also remember the user telling me they'd done it:)

To the case in hand - got a 12.04 here - WITH no seperate /home - I do clear out the old archives quite regularly but keep the current apt packages and root here is 

/dev/sda7        15G  5.8G  8.1G  42% /

I'd be inclined to wonder exactly what was installed here - it's certainly not as simple as xubuntu 12.04


When this was a fresh clean install it took a bit less than 4Gb

---

### Post by Peripheral Visionary on 2012-03-15
Hmmmm. Sounds like I should've wiped the drive and let Xubuntu have the whole thing instead of separate /home then.

I loaded the Xubu 12.04 iso from Softpedia, and the installer offered to either "upgrade" the previous 10.04 (letting me keep pics, tunes, settings, etc) or wipe it all away. I chose "upgrade." The previous installation had this partition scheme:

Linux-swap, 1 gb (twice my computer's 412 mg of RAM
"/" was 20 gb
"/home" was the remainder of the 80-gb drive.

I assume that the installer preserved "/home" and left the partitions the same size as before.

So imagine my surprise when the second update couldn't complete because there was "insufficient space on the drive!" I deleted a bunch of unused applications, ran
```
sudo apt-get clean
```, and gained about 20 mb of space - enough to complete that update. But not the next update. Same issue: Insufficient drive space.

Determined not to run out of space on that partition again, I used the LiveCD to run GParted and give Xubu at least double its former space on the drive. That's why "/" is huge now. Was that not the right thing to do?

The only other stuff I have installed is Xournal, LibreOffice Impress, Xubuntu-restricted-extras, and PCManFM in place of Thunar.

Y'all are making me think that separate partitions are not such a good idea, lol.

Thanks for helping!

---

### Post by kansasnoob on 2012-03-15
> **Peripheral Visionary said:**
> Hmmmm. Sounds like I should've wiped the drive and let Xubuntu have the whole thing instead of separate /home then.

I loaded the Xubu 12.04 iso from Softpedia, and the installer offered to either "upgrade" the previous 10.04 (letting me keep pics, tunes, settings, etc) or wipe it all away. I chose "upgrade." The previous installation had this partition scheme:

Linux-swap, 1 gb (twice my computer's 412 mg of RAM
"/" was 20 gb
"/home" was the remainder of the 80-gb drive.

I assume that the installer preserved "/home" and left the partitions the same size as before.

So imagine my surprise when the second update couldn't complete because there was "insufficient space on the drive!" I deleted a bunch of unused applications, ran
```
sudo apt-get clean
```, and gained about 20 mb of space - enough to complete that update. But not the next update. Same issue: Insufficient drive space.

Determined not to run out of space on that partition again, I used the LiveCD to run GParted and give Xubu at least double its former space on the drive. That's why "/" is huge now. Was that not the right thing to do?

The only other stuff I have installed is Xournal, LibreOffice Impress, Xubuntu-restricted-extras, and PCManFM in place of Thunar.

Y'all are making me think that separate partitions are not such a good idea, lol.

Thanks for helping!

Well I help maintain about 35 to 40 PC's with some flavor of Ubuntu ...... mostly Ubuntu itself, and I've never seen a root partition larger than 8GB - NEVER!

I no longer use a separate /home on my own stuff because I multi-boot too much:

 [ATTACH]214382[/ATTACH]

I honestly think there just had to be ton of stuff installed .... 25GB worth to be exact ;)

---

### Post by cariboo on 2012-03-15
Check your directory tree, it wouldn't surprise if you had two home directories. Open a terminal and type:

```
cd /
```

then

```
ls -l
```

the directory tree should look like the screen shot, if you have a /home,  /HOME or /Home directory, that's your problem.

---

### Post by Peripheral Visionary on 2012-03-15
Output of
```
cd /
ls -l
```is:

lrwxrwxrwx   1 root root    37 Mar 12 09:14 initrd.img -> /boot/initrd.img-3.2.0-18-generic-pae
lrwxrwxrwx   1 root root    36 Mar 12 08:24 initrd.img.old -> boot/initrd.img-3.2.0-17-generic-pae
drwxr-xr-x  20 root root  4096 Mar 14 21:03 lib
drwx------   2 root root 16384 Sep 12  2011 lost+found
drwxr-xr-x   2 root root  4096 Mar 15 22:11 media
drwxr-xr-x   2 root root  4096 Jan 27 14:01 mnt
drwxr-xr-x   3 root root  4096 Feb 28 02:14 opt
dr-xr-xr-x 126 root root     0 Mar 15 22:10 proc
drwx------  15 root root  4096 Feb 28 02:19 root
drwxr-xr-x  20 root root   760 Mar 15 22:10 run
drwxr-xr-x   2 root root  4096 Mar 14 21:03 sbin
drwxr-xr-x   2 root root  4096 Dec  2 06:01 selinux
drwxr-xr-x   2 root root  4096 Feb 28 02:14 srv
drwxr-xr-x  13 root root     0 Mar 15 22:10 sys
drwxrwxrwt   8 root root   200 Mar 15 22:17 tmp
drwxr-xr-x  10 root root  4096 Feb 28 02:14 usr
drwxr-xr-x  13 root root  4096 Mar 15 21:11 var
lrwxrwxrwx   1 root root    33 Mar 12 09:14 vmlinuz -> boot/vmlinuz-3.2.0-18-generic-pae
lrwxrwxrwx   1 root root    33 Mar 12 08:24 vmlinuz.old -> boot/vmlinuz-3.2.0-17-generic-pae
robin@robin-Dell-DE051:/$ 

Have no idea what it means.

But **it's no longer relevant.** I downloaded, burned, and installed today's daily build and gave it the entire drive. Everything's new. *NOW* if it slows down I'll know it isn't my fault!  :D

---

### Post by ranch hand on 2012-03-16
I have an install of Xubuntu 12.04-testing on my test platform.  It has been there for a while and has extra images and a good bit of music on it.

2 partition install just because it is the best way to install anything.

Root is 10gig with 3.90 used.

Home is 15gigs with 2.92 used.

Have no idea what you are putting on there or doing but something is not right if it will not fit on 40gig.

Take an awful lot of kernels to do that.  Maybe if this was an upgrade along the line of 11.04-testing>11.10-testing>12.04-testing you would be approaching half or two thirds full.

Now, mind you, that I am a guy with a 40gig / on my production OS that is pretty full so I do know how to fill up an install.

On a fairly recent testing installation that is just really impressive.  You should let us in on just how you did this,

---

### Post by jerrylamos on 2012-03-16
```
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda9        6119520 1937616   3871048  34% /
```

Not much on the 1937616 Lubuntu except I replace Chromium with Firefox.

This is a 40 GB hard drive on a 2005 IBM Thinkpad.  I've got four partitions of about 6 GB each: a Lucid for recovery and three pangolin's - this lubuntu, a unity-2D Beta, and a unity-2D Alpha.  I'll install on the Alpha when there's a significant Daily Build update - down to 701 MB now, soon 700 MB? 

Enjoy,

Jerry

---

### Post by ranch hand on 2012-03-16
Have no idea where you get the idea that 2 partitions are bad.  This is the best way to protect your data for one thing.

For another the permission system works better on 2 partitions.  You will discover this if you change a 1 partition install to a 2 partition install with out reinstalling.  There are some interesting and basic differences even if they are not large.

On a testing release it is nice to have more than one install.  With a separate /home you can have several, all using the same /home.

I currently have an install of Debian Wheezy Xfce sharing a /home with Debian Sid Ldxe.  Also Zenix (Debian Squeeze based) upgraded to Debian testing sharing a /home with Zenix upgraded to Sid  and straight Debian Squeeze with OpenBox (Zenix is an OB OS).

That is a total of 5 installs on 100gigs and that is only that big because I like them big,  Using about 20gigs total with all 5 / and 2 /home.

Take some time and study partitioning.  This is not rocket science.

---

### Post by cariboo on 2012-03-16
> Take some time and study partitioning. This is not rocket science.

Many people on the forum seem to think it is. :) :)

---

### Post by kansasnoob on 2012-03-16
> **cariboo907 said:**
> Many people on the forum seem to think it is. :) :)

+1!

I like Ranch Hand but that's a (c)rude comment. Partitioning is easy to some of us but others don't even understand the difference between a drive and a partition, largely because of Windows drive A, drive C, baloney :mad:

I don't consider myself stupid but I'm having a horrible time trying to figure out how to perform a netboot install with a live CD in a chroot. I've found three different guides and I'm still stumped :confused:

We should always be polite to each other ;)

---

### Post by Peripheral Visionary on 2012-03-16
I *like* having separate partitions! I *wanted* to have separate partitions. The first install was supposed to overwrite [COLOR=Black]**/**[/COLOR] and leave my [COLOR=Black]**/home**[/COLOR] partition alone. 

While it did preserve the **/home** partition (and all my data), it did *not* properly overwrite my existing Lucid **/** partition. Instead it apparently *shared* that partition with Lucid, which is why I had all those issues. That was a problem with GParted or with the installer, I don't know which.

Rather than risk a repeat of that, I simply gave Xubu Precise the entire drive. It solved all my issues.

I don't think I'll bother creating a separate /home partition until Precise is fully ready and at least a couple of moths old, just in case there's some bug with the installer or the new implementation of GParted.

Just say'n.

---

### Post by Gregory Lee on 2012-03-17
> **kansasnoob said:**
> That blows my mind, 25GB used for "/" (aka: root) is beyond odd. I suspect you must have more than one desktop environment (aka: DE) installed.


```
:~# df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       524G   41G  458G   9% /
udev            4.0G  4.1k  4.0G   1% /dev
tmpfs           1.6G  938k  1.6G   1% /run
none            5.3M  4.1k  5.3M   1% /run/lock
none            4.0G  287k  4.0G   1% /run/shm
/dev/sda6       524G   20G  479G   4% /user
/dev/sda7       444G  258G  164G  62% /extra
```As you see, I have 41G in root, and that is all the 12.04 stuff.  The other partitions, sda6 and sda7 are leftovers from my previous computer.  What I have is from the alpha2 install, then updating and installing just a few extras.  When I installed Gnome 3, I asked for all the optional desktop environments that were listed with it (KDE Plasma, etc.), and it took a while to download, so it's probably taking an appreciable amount of space.  I haven't tried to clear away unused kernels or whatever.

---

### Post by cariboo on 2012-03-17
> **Gregory Lee said:**
> ```
:~# df -H
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       524G   41G  458G   9% /
udev            4.0G  4.1k  4.0G   1% /dev
tmpfs           1.6G  938k  1.6G   1% /run
none            5.3M  4.1k  5.3M   1% /run/lock
none            4.0G  287k  4.0G   1% /run/shm
/dev/sda6       524G   20G  479G   4% /user
/dev/sda7       444G  258G  164G  62% /extra
```As you see, I have 41G in root, and that is all the 12.04 stuff.  The other partitions, sda6 and sda7 are leftovers from my previous computer.  What I have is from the alpha2 install, then updating and installing just a few extras.  When I installed Gnome 3, I asked for all the optional desktop environments that were listed with it (KDE Plasma, etc.), and it took a while to download, so it's probably taking an appreciable amount of space.  I haven't tried to clear away unused kernels or whatever.

How much do you have in your /home directory? That can't all be downloaded packages. I did a fresh install when beta 1 came out, and I have updated at least twice a day since then, /var/cache/apt/archives contains 978MiB in archived packages.

---

### Post by Gregory Lee on 2012-03-17
> **cariboo907 said:**
> How much do you have in your /home directory? That can't all be downloaded packages.
Whoops.  I forgot that I put my music in my home directory (which is in the root partition).
```
greg@greg-p7-1220:~$ du -sh /home
21G    /home
greg@greg-p7-1220:~$ du -sh /home/greg/Music
19G    /home/greg/Music
greg@greg-p7-1220:~$ du -sh /var/cache/apt/archives
2.8G    /var/cache/apt/archives
```

---

### Post by Elfy on 2012-03-17
> **Gregory Lee said:**
> Whoops.  I forgot that I put my music in my home directory (which is in the root partition).
```
greg@greg-p7-1220:~$ du -sh /home
21G    /home
greg@greg-p7-1220:~$ du -sh /home/greg/Music
19G    /home/greg/Music
greg@greg-p7-1220:~$ du -sh /var/cache/apt/archives
2.8G    /var/cache/apt/archives
```

Do you ever run 

```
sudo apt-get autoclean 
```

or ```
sudo apt-get clean

```
> 
autoclean
           Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control.

clean
           clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/.

---

### Post by Peripheral Visionary on 2012-03-17
I'm not the only one who thinks that a separate /home partition is not always the best option. I found this in another subforum from a frequent helper in the community:

[http://ubuntuforums.org/showpost.php?p=11769055&postcount=5](http://ubuntuforums.org/showpost.php?p=11769055&postcount=5)

Excerpt:

> You don't need a separate /home. If you reinstall Ubuntu in the future  it will detect the existing /home folder and retain it even though it is  in the same partition.

There, just say'n.

---

### Post by kansasnoob on 2012-03-17
> **Peripheral Visionary said:**
> I'm not the only one who thinks that a separate /home partition is not always the best option. I found this in another subforum from a frequent helper in the community:

[http://ubuntuforums.org/showpost.php?p=11769055&postcount=5](http://ubuntuforums.org/showpost.php?p=11769055&postcount=5)

Excerpt:



There, just say'n.

This statement:

> You don't need a separate /home. If you reinstall Ubuntu in the future it will detect the existing /home folder and retain it even though it is in the same partition. 

is NOT 100% true! I'll try to explain a bit ;)

Beginning with Maverick the devs (under the direction of the design team) gave the live installer (aka: ubiquity) a total overhaul, no doubt that created some new bugs as would be expected, but it also introduced some new options.

Among those new options, if you have only one existing **buntu installation you should be offered the option to either upgrade or replace that installation similar to this:

[ATTACH]214458[/ATTACH]

But it is NOT bullet proof! It should retain /home and also update/reinstall the proper updated additional packages, but as with most "advanced" automatic methods things can and sometimes do go wrong!

I've tested that option a little bit and it's OK 98% of the time but some customizations seem to really bork things .......... so always back up anything important!

But if you choose "something else" (aka: manual partitioning) and choose to format "/", and it contains "/home", then the data in "/home" will be gone!!!!!!!

Nothing at all wrong with creating a separate "/home", it can be useful. I used to do it all the time, and still do in some cases ;)

Something that came to mind here is that we may be dealing with a borked daily iso image :confused:

It's possible.

---

### Post by ptn107 on 2012-03-17
Why such large / partitions?  I've always allocated 12 GB for / but honestly have never really exceeded 4-6 GB on my 3 machines.  Root on this one takes up only 3.7GB and I have tons of extra stuff installed.

---

### Post by Peripheral Visionary on 2012-03-17
> **ptn107 said:**
> Why such large / partitions?  I've always allocated 12 GB for / but honestly have never really exceeded 4-6 GB on my 3 machines.  Root on this one takes up only 3.7GB and I have tons of extra stuff installed.

I explained that in [this post]("http://ubuntuforums.org/showpost.php?p=11768460&postcount=11").

> 
I loaded the Xubu 12.04 iso from Softpedia, and the installer offered to  either "upgrade" the previous 10.04 (letting me keep pics, tunes,  settings, etc) or wipe it all away. I chose "upgrade." The previous  installation had this partition scheme:

Linux-swap, 1 gb (twice my computer's 412 mg of RAM
"/" was 20 gb
"/home" was the remainder of the 80-gb drive.

I assume that the installer preserved "/home" and left the partitions the same size as before.

So imagine my surprise when the second update couldn't complete because  there was "insufficient space on the drive!" I deleted a bunch of unused  applications, ran
 	Code:
 	sudo apt-get clean 
, and gained about 20 mb of space - enough to complete that  update. But not the next update. Same issue: Insufficient drive space.

Determined not to run out of space on that partition again, I used the  LiveCD to run GParted and give Xubu at least double its former space on  the drive. That's why "/" is huge now. Was that not the right thing to  do?


I think Lucid and Precise either *shared* the / partition or the installer created a second /.

M'kay?

---

### Post by Gregory Lee on 2012-03-17
> **forestpiskie said:**
> Do you ever run 

```
sudo apt-get autoclean 
```or ```
sudo apt-get clean

```
No, I don't.  I have plenty of room.  Is there some reason to do this clean up?

---

### Post by Elfy on 2012-03-17
> **Gregory Lee said:**
> No, I don't.  I have plenty of room.  Is there some reason to do this clean up?

None - sounded like you were 'worried' now it's not stupid o'clock in the morning here I can see you've loads of room :lol:

---

### Post by kansasnoob on 2012-03-17
> **forestpiskie said:**
> None - sounded like you were 'worried' now it's not stupid o'clock in the morning here I can see you've loads of room :lol:

It's always "stupid o'clock" at my place :lolflag:

---

### Post by TenPlus1 on 2012-03-17
I run Xubuntu on an old Compaq m2000 with a 40gb hard drive and my '/' partition is only 10gb with the rest allocated to '/home'...  I've never had a problem with this laptop slowing down or even running out of space when updating, although I think I may know why this happens for you...

Run Synaptic Package Manager and click on the Settings menu then select Preferences, under the Files tab highlight the button next to "delete downloaded packaged after installation" then click on the "Delete Cache Package Files" and finally the OK button...

This stops Xubuntu storing all the downloaded updates in a cache on your hard-drive and once the update is done it deletes all the temporary files it downloaded, this'll save you bags of space on your hard-drive and shouldn't slow anything down or make it run out of space :)

Also, install BleachBit as it helps in the cleaning up of temporary files and overgrown thumbnails :)

---

### Post by Gregory Lee on 2012-03-17
I have a question that is indirectly related to this room matter.  When I do normal upgrades, am I getting all the header .h files that are needed to compile against the libraries I'm installing?  If not, is there an easy way to get them?

---

### Post by cariboo on 2012-03-17
When downloading packages, you get essentially a compressed archive. dpkg reads a control file, and pre-installation and post-installation scripts, and places the files in the proper directories. You can open a .deb package with the archive manager, and view the contents.

if you want to compile programs for source, you can download the source files from the repositories.

This [wiki page]("https://help.ubuntu.com/community/InstallingSoftware") may explain things a little better.

---

### Post by dcstar on 2012-03-17
> **Peripheral Visionary said:**
> 
........
**SOLVED** by reinstalling and letting Xubu have the whole drive. I messed up partitions somehow, unless the installer did that when it replaced 10.04 with 12.04, *saving /home*. That's what I get for downloading the Beta from Softpedia instead of the daily build!

Then MARK the thread.

---

### Post by Gregory Lee on 2012-03-17
> **cariboo907 said:**
> You can open a .deb package with the archive manager, and view the contents.
Is this in answer to my question?  I guess I could rephrase the question to ask whether these .deb packages include header files.  I'd guess, from your answer, that they don't.
> 
if you want to compile programs for source, you can download the source files from the repositories.
Yes, I knew that.  The Fedora distributions do provide "devel" packages containing header files, so I was just curious whether Ubuntu had anything corresponding.  Apparently not.

---

### Post by cariboo on 2012-03-18
> **Gregory Lee said:**
> Is this in answer to my question?  I guess I could rephrase the question to ask whether these .deb packages include header files.  I'd guess, from your answer, that they don't.

Yes, I knew that.  The Fedora distributions do provide "devel" packages containing header files, so I was just curious whether Ubuntu had anything corresponding.  Apparently not.

That's why I suggested you open a .deb with the archive manager so you could see for yourself. If you haven't done any clean up lately, all the archived packages are located in /var/cache/apt/archives.

---

