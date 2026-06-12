---
title: "How big is your Ubuntu partition?"
date: 2009-11-08
forum: The Cafe
---

### Post by Eagles18 on 2009-11-08
I started off with a 20GB partition and ended up with a 60GB partition.

---

### Post by H2SO_four on 2009-11-08
> **Eagles18 said:**
> I started off with a 20GB partition and ended up with a 60GB partition.

+/- 80 GB (much larger than it needs to be)

---

### Post by pwnst*r on 2009-11-08
i'm assuming your numbers are because of video/music files also?

---

### Post by Eagles18 on 2009-11-08
> **pwnst*r said:**
> i'm assuming your numbers are because of video/music files also?

Actually,I store my media files in my Windows partition.But,since I hardly ever use Windows,I decided to increase the size of my Ubuntu partition.

---

### Post by The Jinx on 2009-11-08
I think you screwed up with the "> 5gb" thing you meant "< 5gb"

---

### Post by NoaHall on 2009-11-08
You're realllllly bad at making poll options :) I would expect most people to have a partition of at least 60GB/70GB

---

### Post by Eagles18 on 2009-11-08
> **The Jinx said:**
> I think you screwed up with the "> 5gb" thing you meant "< 5gb"
No,I meant ">(less than)5GB."

> You're realllllly bad at making poll options :smile: I would expect most people to have a partition of at least 60GB/70GB

I thought most people didn't make their Ubuntu,but I didn't take the fact that this is the Ubuntu forum into consideration.BTW,how do I edit the poll options.

---

### Post by pwnst*r on 2009-11-08
> **Eagles18 said:**
> Actually,I store my media files in my Windows partition.But,since I hardly ever use Windows,I decided to increase the size of my Ubuntu partition.

i actually meant to quote h2s0_four.  he said it's much bigger than it needs to be, which i don't understand.

---

### Post by SuperSonic4 on 2009-11-08
280gb

albeit / is 35

---

### Post by The Funkbomb on 2009-11-08
~200gb

---

### Post by Chronon on 2009-11-08
440 gb

---

### Post by The Jinx on 2009-11-08
> **Eagles18 said:**
> No,I meant ">(less than)5GB."

< 5gb means less than
> 5gb means greater than

---

### Post by amauk on 2009-11-08
```
tony@tony-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  5.6G   12G  33% /
/dev/sda4             342G   90G  236G  28% /home
tony-server:/roms     2.7T  2.2T  408G  85% /media/raid5/roms
tony-server:/scripts  185G  343M  176G   1% /home/tony/scripts
tony-server:/dump     2.7T  2.2T  408G  85% /media/raid5/dump
tony-server:/tony     2.7T  2.2T  408G  85% /media/raid5/tony
tony-server:/music    2.7T  2.2T  408G  85% /media/raid5/music
tony-server:/media    2.7T  2.2T  408G  85% /media/raid5/media
```

---

### Post by ViRMiN on 2009-11-08
4TB but / is 10GB, far larger than necessary.

---

### Post by Xbehave on 2009-11-08
> **Eagles18 said:**
> No,I meant ">(less than)5GB."
[>]("http://en.wikipedia.org/wiki/More_than") means more than

Not on ubuntu atm but i've let my current / grow to  6.4G (voted for >5 because that's my normal / I just let this one grow for debugging info and libraries used to compile stuff). I find a small / stops me installing too much crap. i did split up my debian install and crammed the entire thing (/,/usr,/var) into <4G

---

### Post by slakkie on 2009-11-08
8 GB root slice
2 GB swap
300 MB log dir
2 GB opt
40+ homedir

So voted for 5-10 GB

---

### Post by Paqman on 2009-11-08
/ = 11GB
/home = 31GB
swap = 3GB

Probably should shrink that swap down, since boot times these days make hibernation a bit pointless.

---

### Post by Eagles18 on 2009-11-08
> **The Jinx said:**
> < 5gb means less than
> 5gb means greater than

Whoops,can anyone tell me how to edit the poll?

---

### Post by markp1989 on 2009-11-08
my root is about 20gb 

```
mark@torrentslave:~$ df -h 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  5.4G   13G  31% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  128K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  224K  2.0G   1% /dev
tmpfs                 2.0G   19M  1.9G   1% /dev/shm
lrm                   2.0G  2.7M  2.0G   1% /lib/modules/2.6.28-11-server/volatile
/tmp                  1.0M  120K  904K  12% /tmp
vartmp                1.0M  4.0K 1020K   1% /var/tmp
varlog                8.0M  3.5M  4.6M  43% /var/log
/dev/sda5             1.4T  627G  662G  49% /media/torrents
/dev/sdb1             1.4T  547G  760G  42% /media/disk2
mark@torrentslave:~$ 

```

this is my only pc with ubuntu rest are running arch.

---

### Post by ZankerH on 2009-11-08
/home -  80GB
/ - 20GB
/boot - 512 MB
/var,/tmp - 10 GB each
/media/stuff - 1TB minus everything listed above

---

### Post by CharlesA on 2009-11-08
```
charles@thor:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             283G   88G  181G  33% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  1.9M  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  144K  2.0G   1% /dev
tmpfs                 2.0G  1.5M  2.0G   1% /dev/shm
lrm                   2.0G  2.5M  2.0G   1% /lib/modules/2.6.28-16-server/volatile
/dev/sdb1             3.6T  1.3T  2.2T  36% /array
/dev/sdc1             1.4T  1.3T   64G  96% /sync

```

/ is 88GB but it has a 84GB disk image sitting on my desktop. >.>

---

### Post by sports fan Matt on 2009-11-08
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G  3.8G  427G   1% /
udev                 1002M  248K 1002M   1% /dev
none                 1002M  124K 1002M   1% /dev/shm
none                 1002M   92K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
none                 1002M     0 1002M   0% /lib/init/rw

---

### Post by lovinglinux on 2009-11-08
Wow, some people have really big Ubuntu partitions.

This is my partition scheme:

sdb1 - swap - 2 Gb
sdb2 - root - ext4 - 12 Gb
sdb3 - home - ext4 - 8 Gb (for settings only)
sdb4 - personal data - ext4 - 125 Gb (with symlinks inside home)

sda1 - personal data - 40 Gb (with symlinks inside home)
sda2 - root (for beta testing) - ext4 - 8 Gb
sda3 - windows - ntfs - 25 Gb

---

### Post by jollysnowman on 2009-11-08
6gB... I store my data in another partition.

---

### Post by kio_http on 2009-11-08
50 Gb

---

### Post by CharlesA on 2009-11-08
Heh I just chose "use entire disk" when I installed Ubuntu.

All my data is stored on a RAID array mounted to /array. :p

---

### Post by gnuvistawouldbecool on 2009-11-08
This computer, about 10GB since it's not only my computer/want to leave room for games in windows.

My laptop has a 17GB /, 25GB /home.  Computer I built from recycled/reused parts (which runs Mandriva), has 36GB /, 50GB /home, 155GB /mnt/windows.

/ generally I make rather large since I usually end up installing a lot of compiling stuff, or install things I don't really need and never clean it out.

---

### Post by xpod on 2009-11-08
My main Ubuntu installation on my desktop is about 20G / with 200G /home.
This laptop, with lubuntu, has the whole 40G drive given to / with no separate /home partition at the moment. 

The first time i ever installed Ubuntu(6.06) was on a 3.2G slave drive i`d stuck in the desktop i was using at the time, purely for fear of damaging the main 40G drive that i`d only recently managed to re-install XP on.
The updates soon took their toll though and it was only a week later that my 3.2G drive was sacked, as was Windows, and the whole drive was given to Ubuntu.

---

### Post by Zoot7 on 2009-11-08
```
mark@mark-xps:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              73G   22G   48G  31% /
udev                 1006M  336K 1006M   1% /dev
none                 1006M  4.0M 1002M   1% /dev/shm
none                 1006M  212K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
/dev/sda3             146G   76G   63G  55% /home
/dev/sda2             242G  127G  115G  53% /media/Windows
```

70 gigs for the system and 150 gigs for /home. I probably should resize the system and make it smaller as most of the stuff I accumulate over time goes in my home directory anyway.

On my homebuilt desktop, Ubuntu occupys a 750Gb Hard Drive - 100 gigs for the system and the remainder of the Hard Drive for /home.

---

### Post by lovinglinux on 2009-11-08
> **Zoot7 said:**
> 70 gigs for the system and 150 gigs for /home. I probably should resize the system and make it smaller as most of the stuff I accumulate over time goes in my home directory anyway.

On my homebuilt desktop, Ubuntu occupys a 750Gb Hard Drive - 100 gigs for the system and the remainder of the Hard Drive for /home.

Why do you need 70-100Gb for system files? How much of that are you using, not considering home?

---

### Post by Zoot7 on 2009-11-09
> **lovinglinux said:**
> Why do you need 70-100Gb for system files? How much of that are you using, not considering home?
I don't need it. TBH little enough of it is used with me, generally somewhere in or around the 30GB mark, I've been meaning to resize it for some time now.

---

### Post by Exodist on 2009-11-09
LOL, my entire PC is GNU/Linux. Windows is like 20GB out of the 390+ GB I have..

---

### Post by Dai Bando on 2009-11-09
> **Xbehave said:**
> [>]("http://en.wikipedia.org/wiki/More_than") means more than

Not on ubuntu atm but i've let my current / grow to  6.4G (voted for >5 because that's my normal / I just let this one grow for debugging info and libraries used to compile stuff). I find a small / stops me installing too much crap. i did split up my debian install and crammed the entire thing (/,/usr,/var) into <4G
&#57627; means equal to or less than
&#8805;    "     "   "  "  more than

---

### Post by Bradyhawke on 2009-11-09
This should help...

[http://www.mathsisfun.com/equal-less-greater.html](http://www.mathsisfun.com/equal-less-greater.html)

Just in case anyone is still confused, hehe


:lolflag:

---

### Post by ColdFFF on 2009-11-09
> **Dai Bando said:**
> &#57627; means equal to or less than
&#8805;    "     "   "  "  more than

The underline in the post you quoted is there because it is a link...

---

### Post by Dehouston on 2009-11-09
9.10 - 68GB
9.04 - 4.6GB (getting rid of)
Windows XP - 72GB

---

### Post by Genius2999 on 2009-11-09
I'm living on a 20GB hard disk atm, only because my 1TB disk crashed and burned :(

---

### Post by jward3010 on 2009-11-09
I'm not going to go crazy over readin this whole post, but those at the start who say the poll options are crazy because they don't contain "huge" options are crazy. They obviously don't split up there Ubuntu partitions between "/" root and "/home" - they just make one enormous partition. 

I picked 5-10GB and that to be specific is for root. I will always set up a separated home partition or use a large NTFS partition for my stuff which might be enormous but install Ubuntu into nothing more than 5 or 6GB. If I ripped DVD's and encoded video or edited enormous picture files then maybe bigger but I don't need more than that.

This was an unclear poll in a way.

---

### Post by Megrimn on 2009-11-09
Karmic - 60GB
Vista - 168GB

I only had 10GB left on the karmic partition, and had wondered where all the space went... turns out, cleaning up the old ubuntu isos gave me back 10GB more :biggrin:

---

### Post by ctrlmd on 2009-11-09
40 including music and other data

---

### Post by CP1256 on 2009-11-09
20 GB on my server, 30 GB on my desktop. The rest is usually the /home partition.

---

### Post by Marlonsm on 2009-11-09
30Gb for me.
But most of my files are stored in the 130Gb Windows XP partition.

---

### Post by Foster Grant on 2009-11-09
/ partition is roughly 10.5 gigabytes. /home partition is 94.6 gigabytes. Both partitions have vast amounts of free space for expansion. Five gigs left over for swap; slightly more than I need but it's not like I'm hurting for hard drive space.

Props to the dev team for allowing users to install separate / and /home partitions instead of forcing us all to use Debian's default of throwing everything on one partition.

---

### Post by Squonk07 on 2009-11-09
My Ubuntu partition is 20 GB, but my separate /home directory is 50 GB, so combined they come out to the highest option in the poll.

---

### Post by Dougie187 on 2009-11-09
/ - 23GB
/home - 123GB
swap - 1.5GB

---

### Post by ~unknown on 2009-11-09
125GB Windows XP NTFS
125GB Ubuntu        ext4
250GB Files            NTFS

---

### Post by seeker5528 on 2009-11-09
For my personal machines, for basic use or basic +Myth TV 20 to 40 GB covers me. TV recordings go on a seperate partition that only gets used for TV or TV and Music.

For my primary machine, since I don't re-partition very often, it's closer to 60 GB so it will handle increasing sizes of games and other software, and leave me room to be lazy about getting other stuff moved off to other partitions I use for longer term storage.

Later, Seeker

---

### Post by ElSlunko on 2009-11-09
1.5 tb!

---

### Post by The Real Dave on 2009-11-09
/                  ~8GB
/home              ~38.5GB
/media/Data        ~250GB
/media/Backups     ~70GB
/media/XP          ~5GB
/swap              ~1GB
/home/An-Lar       ~600GB        (Server mounted through SSHFS)

---

### Post by Chronon on 2009-11-09
> **jward3010 said:**
> They obviously don't split up there Ubuntu partitions between "/" root and "/home" - they just make one enormous partition. 


That is not obvious at all.  In order to formulate an answer, I took the union of all partitions used in my Ubuntu system.

---

