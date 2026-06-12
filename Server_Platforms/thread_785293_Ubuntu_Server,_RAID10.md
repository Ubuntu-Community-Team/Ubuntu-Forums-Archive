---
title: "Ubuntu Server, RAID10"
date: 2008-05-07
forum: Server Platforms
---

### Post by TheGameAh on 2008-05-07
Howdy guys.

Been messing with Fedora.  I notice that their installer has builtin support for setting up RAID10 arrays.  I was wondering if the server edition of Ubuntu had this support, or if it had to be manually done.

Also, as a side note, plan on setting this server up as a file server / VM hosting box.  It will host 2 relatively small VMs, as well as about a simple file share.  Anyone see any problems with that?  I wouldn't think so, but admit I'm kinda new to software RAIDs.

I'd rather use Ubuntu for VM hosting as I've had nightmares getting VMware running on Fedora.

---

### Post by tribaal on 2008-05-07
Well as far as I know there is no install option for that.
You can however format disks as "linux RAID" and then use "mdadm" to set up your actual array?
I use it to have software raid1 and raid0 (on different machines), never tried setting up a RAID10 array however.

Of course the easiest is to have a hardware RAID controller :)

- Trib'

---

### Post by songshu on 2008-05-07
it is supported, just not via the installer.

i personally did it like this on a debian etch setup
[http://doku.songshu.org/doku/doku.php?id=host.cipar.net](http://doku.songshu.org/doku/doku.php?id=host.cipar.net)

---

### Post by TheGameAh on 2008-05-07
Yeah I used to be a hardware RAID guy.  Still have most of my servers with it.  But read a lot of good things about Linux software RAID, enough to make me think it was worth giving a shot as something as simple as VMs and file shares.  

Also had a bad experience with hardware RAID.  A controller died on me.  And I didn't have a spare (dumb, I know).  So had to buy a new controller and rebuild the array, obviously the complete opposite of a RAIDs intended purpose  :)

However, had a motherboard die in a RAID1 linux box once.  Just moved the drives to another Intel board, and away it went.  I like reducing another single  point of failure.

---

### Post by songshu on 2008-05-07
i use linux raid only.

for exactly the reasons you describe and the days that processors were so slow it actually did matter in performance are long gone in my opinion.

mdadm has not failed me yet for the last 5 years on various set ups.

just spend some extra money on a decent processor and still save a lot of not having to buy a controller.

---

### Post by TheGameAh on 2008-05-07
Okay guys, roadblock time.

I followed the link above, but I'm afraid it's just a little beyond me.

I see their installer doesn't support RAID 10 (trying it on a test box).  So how exactly do you even get started during the install?

I installed /boot to a 100MB partition, RAID1, but what next?  In order to install the root system (/), you need to put it on a non-RAID partition.

Can you convert the non-RAID partition to a RAID partition AFTER install?  I would assume it would wipe your data?

---

### Post by songshu on 2008-05-07
mmmm i know the place you are at, one of the reasons i wrote everything down in the link mentioned, afterwards it all makes sense so don't worry ;)

i can also recomend reading [http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch)

that i used as a guide, its is for raid1 but the same concept applies.

the trick is simply as follows.

install on /dev/sda (disk1)
boot from disk1
make disk 2 3 and 4 /dev/md
copy disk 1 to /dev/md
reboot and boot from /dev/md
add /dev/sda to /dev/md

it would be easier if it was included in the installer but at least its a great way to learn how to manage mdadm....wich you wil enjoy someday if you really really need it, namely if one disk actually does break in real life.

---

### Post by TheGameAh on 2008-05-07
Ah now I see exactly what you mean  :)  Let me give it a shot.

---

### Post by songshu on 2008-05-07
let me know if any problems.

in case you follow my notes let me know if i missed something or made a typo or anything ;)

---

### Post by TheGameAh on 2008-05-08
Well, messed with it off and on all day yesterday.  A little this morning.  Having all kinds of issues, so I started bare minimum.  No RAID10, just a RAID1 system with 2 disks.

Everything is happy.  Installed GRUB on both disks.  I unhook one, and the system will not boot.  After some research, seems to actually be an Ubuntu bug, where both disks need to be present to boot.  A little irritating.

On Fedora, the RAID setup installed and operated flawlessly, but installing VMWare is a complicated chore.

On Ubuntu, VMWare is in the repos, but can't get the RAID setup right.

---

### Post by songshu on 2008-05-08
> **TheGameAh said:**
> 

 both disks need to be present to boot.  A little irritating.
right.

thats not irritating, thats inexcusable..

which bug wouold that be?

---

### Post by TheGameAh on 2008-05-08
Check out this link:

[https://bugs.launchpad.net/ubuntu/+bug/120375](https://bugs.launchpad.net/ubuntu/+bug/120375)

A very long post.  Includes a bunch of workarounds that worked for some people, not for others.  This mostly revolved around Feisty/Gutsy, but I can confirm the same symptoms for Heron as well.

In short, in Ubuntu, a RAID1 system will not boot if all array members are not present (kinda the opposite of RAID really :) )

So that does it for this Ubuntu VM/file server idea.  I didn't try the workarounds or hacks, cause to be honest I'm not 100% comfortable with them. Last thing I need to do during a crash is lookup a bunch of workarounds to get things running.  :)

So I'll maybe try getting VMware working on Fedora once again, or perhaps try Debian (that bug report says that Debian has no trouble).  Only thing is I'm not sure how difficult/easy it is to install VMWare on Debian.

---

### Post by songshu on 2008-05-08
that basically disqualifies the ubuntu development cycle for a server OS IMHO

i have tried VMware on debian i think about a year ago..no real problems that i can recall.

but then again i wasn't impressed with vmware so i went with xen and vserver

the install would be pretty straight forward
[http://howtoforge.com/debian_etch_vmware_server_howto](http://howtoforge.com/debian_etch_vmware_server_howto)

---

### Post by TheGameAh on 2008-05-09
I'm at the part now where I'm trying add /dev/sda3 (the old / partition) to /dev/md1 (the current RAID10 degraded / partition).  But mdadm is reporting that /dev/sda3 is busy.  I'm not sure why.  As far as I can tell, everything is running off of the arrays now (/dev/md0, which is boot; and /dev/md1, which is /   -did not RAID the swaps-).

Any idea why /dev/sda3 might be busy?

---

### Post by songshu on 2008-05-09
eeuuuhhh no ;)

what does your 
cat /proc/mdstat and df -h say?

---

### Post by TheGameAh on 2008-05-09
I deleted /dev/sda3 just to see what would happen.  System could not log the root partition.  Guess that means I didn't copy it over right.

However, fstab has no mention of sda3, nor does df -h.  Gonna try to set it up again.

---

### Post by TheGameAh on 2008-05-12
Okay, I'm once again in the spot where I'm trying to add /dev/sda3 to the RAID 10 array.

Running df -h  shows everything as I think it should (/boot is on /dev/md0; / is on /dev/md1).  I assume this means that /dev/sda3 should be available for adding.

However, running "mdadm --add /dev/md1 /dev/sda3" says that sda3 is busy.  I assume that means that / is still on sda3 somehow.

---

### Post by songshu on 2008-05-12
can you paste the outcome of 

df -h
cat /proc/mdstat
fdisk -l

---

### Post by songshu on 2008-05-12
here is mine by the way for comparison

```
host:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              9.0G  1.0G  7.6G  12% /
tmpfs                 4.0G     0  4.0G   0% /lib/init/rw
udev                   10M  128K  9.9M   2% /dev
tmpfs                 4.0G     0  4.0G   0% /dev/shm
/dev/md0               92M   44M   43M  51% /boot
/dev/md3              907G  154G  708G  18% /VSERVERS
/dev/md4              917G  146G  725G  17% /BACKUP

```



```
host:~# cat /proc/mdstat
Personalities : [raid1] [raid10] 
md3 : active raid10 sdb6[0] sdf6[3] sde6[2] sdd6[1]
      966020352 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      
md2 : active raid10 sdb5[0] sdf5[3] sde5[2] sdd5[1]
      979712 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      
md1 : active raid10 sdb3[0] sdf3[3] sde3[2] sdd3[1]
      9574528 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      
md0 : active raid1 sdb1[0] sdd1[3] sde1[2] sdf1[1]
      96256 blocks [4/4] [UUUU]
      
md4 : active raid1 sda1[0] sdc1[1]
      976759936 blocks [2/2] [UU]
      
unused devices: <none>

```



```
host:~# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sdb2             609       60801   483500272+   5  Extended
/dev/sdb3              13         608     4787370   fd  Linux raid autodetect
/dev/sdb5             609         669      489951   fd  Linux raid autodetect
/dev/sdb6             670       60801   483010258+  fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sdd2             609       60801   483500272+   5  Extended
/dev/sdd3              13         608     4787370   fd  Linux raid autodetect
/dev/sdd5             609         669      489951   fd  Linux raid autodetect
/dev/sdd6             670       60801   483010258+  fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sde2             609       60801   483500272+   5  Extended
/dev/sde3              13         608     4787370   fd  Linux raid autodetect
/dev/sde5             609         669      489951   fd  Linux raid autodetect
/dev/sde6             670       60801   483010258+  fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sdf2             609       60801   483500272+   5  Extended
/dev/sdf3              13         608     4787370   fd  Linux raid autodetect
/dev/sdf5             609         669      489951   fd  Linux raid autodetect
/dev/sdf6             670       60801   483010258+  fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/md4: 1000.2 GB, 1000202174464 bytes
2 heads, 4 sectors/track, 244189984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md4 doesn't contain a valid partition table

Disk /dev/md0: 98 MB, 98566144 bytes
2 heads, 4 sectors/track, 24064 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 9804 MB, 9804316672 bytes
2 heads, 4 sectors/track, 2393632 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 1003 MB, 1003225088 bytes
2 heads, 4 sectors/track, 244928 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md3: 989.2 GB, 989204840448 bytes
2 heads, 4 sectors/track, 241505088 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md3 doesn't contain a valid partition table

```

---

### Post by TheGameAh on 2008-05-12
df-h shows the following:

Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              7.4G  606M  6.4G   9% /
tmpfs                1006M     0 1006M   0% /lib/init/rw
udev                   10M   84K   10M   1% /dev
tmpfs                1006M     0 1006M   0% /dev/shm
/dev/md0               92M   19M   69M  22% /boot


cat /proc/mdstat shows the following:

Personalities : [raid1] [raid10] 
md1 : active raid10 sdb3[1] sdd3[3] sdc3[2]
      15631104 blocks 64K chunks 2 near-copies [4/3] [_UUU]
      
md0 : active raid1 sda1[0] sdd1[2](S) sdc1[3](S) sdb1[1]
      96256 blocks [2/2] [UU]


fdisk -l shows the following:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sda2              13         136      996030   82  Linux swap / Solaris
/dev/sda3             137        1109     7815622+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sdb2              13         136      996030   82  Linux swap / Solaris
/dev/sdb3             137        1109     7815622+  fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sdc2              13         136      996030   82  Linux swap / Solaris
/dev/sdc3             137        1109     7815622+  fd  Linux raid autodetect

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sdd2              13         136      996030   82  Linux swap / Solaris
/dev/sdd3             137        1109     7815622+  fd  Linux raid autodetect

Disk /dev/md0: 98 MB, 98566144 bytes
2 heads, 4 sectors/track, 24064 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 16.0 GB, 16006250496 bytes
2 heads, 4 sectors/track, 3907776 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md1 doesn't contain a valid partition table

---

### Post by TheGameAh on 2008-05-12
Ah just noticed sda3 isn't RAID ready.  I still don't think that will fix it though.

---

### Post by TheGameAh on 2008-05-12
Sure enough.  Changed /dev/sda3 to RAID auto detect.  Still "device busy" when trying to add it to /dev/md1.

---

### Post by songshu on 2008-05-12
/dev/sda3 137 1109 7815622+ 83 Linux

shouldn't his one be Linux raid autodetect?

---

### Post by songshu on 2008-05-12
i assume you did another reboot?

---

### Post by TheGameAh on 2008-05-12
Yeah rebooted.  /dev/sda3 is listed as RAID auto detect now.  Still can't add it to the array though.

---

### Post by songshu on 2008-05-12
not sure, but could it be the swap that is keeping the disk busy?

swapoff -a

just a guess

---

### Post by TheGameAh on 2008-05-12
Nah, no good there either.  :( 

At a complete roadblock I guess.  Everything seems to indicate that /dev/sda3 should be ready to add to the array.  But it isn't.

I will say on Friday I wiped out /dev/sda3 completely, just to see what effect it would have.  I didn't think anything would happen, as / was now on /dev/md1.  But the system indeed didn't boot.  I can only guess it's still on /dev/sda3.  I did use the instructions for copying it though.

---

### Post by songshu on 2008-05-12
you should be able to completely umount /dev/sda


if you issue the ```
mount
``` command then /dev/sda should not be listed

---

### Post by TheGameAh on 2008-05-12
/dev/sda3 already doesn't show up though on issuing the mount command.

---

### Post by songshu on 2008-05-12
then what is it doing?

is it listed somewhere in fstab or mtab?

---

### Post by TheGameAh on 2008-05-12
That's the kicker.  /dev/sda3 doesn't show up in mtab or fstab at all.  By all accounts it should not be in use.  However, it says busy when trying to add it to the array.

---

### Post by songshu on 2008-05-12
then there's one last thing i can think of,

i think its not mounted, you think its not mounted, mount thinks its not mounted, 

mdadm thinks its mounted

/etc/mdadm/mdadm.conf would be the last and only place to look for, what does ```
mdadm --examine --scan
``` say and what happens if you update it?

---

### Post by TheGameAh on 2008-05-12
Here is what mdadm.conf looks like.  I don't see any references to sda3 in here.

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=f6c0929e:48b3a11d:365f2ea4:ce229319
   spares=2
ARRAY /dev/md1 level=raid10 num-devices=4 UUID=468db3b5:938cf2a2:c7780c0e:bc1542$

# This file was auto-generated on Mon, 12 May 2008 12:40:05 +0000
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

---

### Post by songshu on 2008-05-12
bingo,

if i'm not mistaking its one of these, UUID=468db3b5:938cf2a2:c7780c0e:bc1542$

can you copy this file for safe keeping and make a new one?

mdadm --examine --scan >> /etc/mdadm/mdadm.conf

---

### Post by TheGameAh on 2008-05-12
Made a backup, generated a new one, and still same thing.  :)

Now /dev/sda1 is a part of /dev/md0  (I did this during install time).  Would that cause issues?

---

### Post by songshu on 2008-05-12
i think it might (please note the ? in my voice)

you might want to fool around removing sda1 from the array etc...

think its somehow an old config thats bothering you

---

### Post by songshu on 2008-05-12
mdadm --zero-superblock /dev/sda1
mdadm --zero-superblock /dev/sda2
mdadm --zero-superblock /dev/sda3

might do the trick

---

### Post by TheGameAh on 2008-05-12
Ah.  I guess that was it.

Failed /dev/sda1, and added /dev/sda3 to the array.  Thank you very much.

---

### Post by songshu on 2008-05-12
your welcome,


you see? just as easy as hardware raid ;)

---

