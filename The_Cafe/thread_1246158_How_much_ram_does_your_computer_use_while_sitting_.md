---
title: "How much ram does your computer use while sitting idle?"
date: 2009-08-21
forum: The Cafe
---

### Post by blur xc on 2009-08-21
I notcied last night, thanks to my wonderful little conky, that my computer was running 45C (normally 39C or lower), running 20 - 30% cpu power, and using 1gb of ram while sitting idle.  this troubled me.

Both my wife and I were logged in, and she had FF open on an old navy flash website (store ad, hunt for coupons, kind of like a game).  So, I logged her out, killed a couple of start up apps, and logged back in- now my CPU usage was down to the 0 - 3% range (normal) and the ram usage was around 350mb.

I don't know if that's good or bad, I don't usually check my ram usage unless I'm running vbox or ripping a dvd, or some other memory intensive task.

Compiz and the Awn dock are using the most from what the system monitor is telling me, about 30-ish mb each.

BM

---

### Post by Crunchy the Headcrab on 2009-08-21
I'm using gnome 2.26+ on Fedora 11 and my RAM usage on idle is about 240MB.  CPU on a 2.26Ghz Core 2 Duo is 0-1%.  I am running compiz but none of the extra plugins like desktop cube.  I can't stand that garbage.

1 GB during idle isn't even a little close to normal.  Some program probably has a memory leak.  Not a huge issue, but it means you'll have to reboot from time to time to clear your ram.  Anyway your levels sound about right after that reboot.  :guitar:

---

### Post by bodyharvester on 2009-08-21
when no programs are running (firefox, text editors etc) its as low  as 100-200mb

but i have 2gig ram on my netbook, its a bit overkill but it only cost £21 for the 2gb stick so i figured why not, with firefox, vuze, pidgin and system monitor running, i attached a screenshot of that of about 500mb

---

### Post by giggins on 2009-08-21
I've noticed that Firefox with Flash left running for long periods of time is not very stable. I use Pandora for internet radio, and after a couple hours of having it running, Firefox + flash invariably chokes pulseaudio, and starts chewing up RAM and CPU. Even after I click the "X" to close the firefox window (and the window goes away), its still running. I end up having to open a terminal and type:

```
killall firefox
killall pulseaudio
pulseaudio &
```

Then things go back to normal. I can't complain too much, since its definitely related to Adobe Flash, which is a non-free multiverse application, so its not like Ubuntu claims it works perfect...

---

### Post by JillSwift on 2009-08-21
250-300MB with no applications running. 400-500MB with FF3.5, Thunderbird, and MPD/GMPC running. Adding Second Life can run it up to 1-1.2GB.

I have 2GB memory and 4GB swap. The swap gets lonely. ;)

---

### Post by howefield on 2009-08-21
> **blur xc said:**
> ...and she had FF open on an old navy flash website (store ad, hunt for coupons, kind of like a game).

The longer I have Firefox running, the more memory it eats, especially if using flash. It was using almost a gig last night watching Ustream. 

Opera likes memory as well, but not to the same extent, imho.

---

### Post by binbash on 2009-08-21
50MB , I am using Crunchbang with custom install.

I am also getting 90 -100mb with PCLinuxOS with Gnome custom install.

I wouldn't go for Ubuntu if system resources is important for you.

---

### Post by swoll1980 on 2009-08-21
Ahhhh! Head for the hills! Our computers are using the RAM we put in them!

---

### Post by Yes on 2009-08-21
Currently, 214 MB with Firefox and two instances of F@H runnning.  I'm on Arch with Awesome WM, I think on startup I use less than 60 MB.

---

### Post by oldsoundguy on 2009-08-21
most of the ram and 100% of the processor(s) on 7 computers that are on line .. 24/7/365 ...

and that also includes the GPU processor on the NVida card.
(which brings the processors up to 10 (two dual core + the Nvidia!)
Running items for BOINC in the background.

---

### Post by Copernicus1234 on 2009-08-21
I never need to check. Everything just runs smoothly no matter what I do. :)

---

### Post by blur xc on 2009-08-21
> **swoll1980 said:**
> Ahhhh! Head for the hills! Our computers are using the RAM we put in them!

I don't mind using the ram I put in my computer- just don't like all the ram being used when I not doing anything w/ my computer.
 
I can live w/ 300mb, but 1gig sitting idle seemed over the top.

BM

---

### Post by chrisme52 on 2009-09-16
Well mines 200meg on jaunty 64.
Same as xp.

---

### Post by misfitpierce on 2009-09-16
About 250MB tops and that running idle after I have already been uptime of over 15 hours and apps opened then all closed and IDLEing... at fresh boot idle its under 200MB... Gnome is doing very well but regardless I wouldn't care if it used more because its doing fine.

---

### Post by cartman640 on 2009-09-16
In Ubuntu I use about 300-350Mb of RAM on idle, not sure how much I'm using after a couple of days of work, 500Mb-1Gb I guess, with 8Gb of RAM it doesn't really bother me, infact I'd rather idle on 4-5Gb of RAM used and never have to wait for anything to be read of HDD. Caches can be easily cleared out if an application requires large amounts of memory. My main server (Ubuntu 64bit Server) normally runs with between 4 and 12Mb of its 4Gb free.

In Vista I was using up to 4Gb on idle without worry.

---

### Post by Paqman on 2009-09-16
> **binbash said:**
> 50MB , I am using Crunchbang with custom install.

I am also getting 90 -100mb with PCLinuxOS with Gnome custom install.

I wouldn't go for Ubuntu if system resources is important for you.

I dunno. You can easily get Ubuntu down to about 80-100MB, running Gnome. Build up from a command line install and Ubuntu can be as light as you want.

---

### Post by xpod on 2009-09-16
The old HP nx6110 i`m currently using with 512MB and a default Ubuntu(9.10) is idling at 129MB. 
On my Desktop with 2G and a not-so default Ubuntu(9.04) it`s idling at around 300MB.

---

### Post by Bölvaður on 2009-09-16
I just logged in and only have firefox open on this page: 136mb
And no.. Im not using compiz or even GNOME, so I might be on a unrealisticly low ram usage, even though I know many here have much lower than me. Lowest I have experienced when sitting idle was about 80 mb with a tiling window manager.

---

### Post by matthew.ball on 2009-09-16
I usually idle at around 12% RAM usage.

I have 1gb of RAM, so just over 120mb I guess?

---

### Post by t0p on 2009-09-16
280MB RAM (14ish% of 2GB), CPU at 35-45%.

That's with Firefox open on this page, and wget downloading a file ([video of a presentation from HAR2009]("http://images1.noterik.com/har/"))

---

### Post by spupy on 2009-09-16
I have 2 gigs. Right now, under relatively normal usage, 350 MB RAM is used. Only once I barely got over 1GB. At least I bought that ram using gift coupons, since it was a somewhat pointless upgrade (512MB -> 2GB).
Maybe I should go the OS X way and not close programs, but keep them in memory.

Archlinux + Fluxbox.

---

### Post by RiceMonster on 2009-09-16
>9000 mb

> **swoll1980 said:**
> Ahhhh! Head for the hills! Our computers are using the RAM we put in them!

+1

---

### Post by ubongo2008 on 2009-09-16
[Linux 2.6.28-15-generic x86_64=>pts/0][Wed Sep 16,  23:19:41][trg@minihtpc=>~/=>(51%)]
>  free    -t -m
                      total         used         free      shared    buffers     cached
Mem:          2983        2948           35             0                 32              2478
-/+ buffers/cache:        437       2545
Swap:            0          0          0
Total:        2983       2948         35


(my linux is loaded into ram) \\:D/

[Linux 2.6.28-15-generic x86_64=>pts/0][Wed Sep 16,  23:20:26][trg@minihtpc=>~/=>(51%)]
>mount
/dev/sda1 on / type ext3 (rw,noatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
/dev/sda2 on /media/data type ext3 (rw,noatime)
/bin on /.physical_disk/bin type none (rw,bind)
/.ramdom_access_memory/bin on /bin type none (rw,bind,noatime)
/sbin on /.physical_disk/sbin type none (rw,bind)
/.ramdom_access_memory/sbin on /sbin type none (rw,bind,noatime)
/etc on /.physical_disk/etc type none (rw,bind)
/.ramdom_access_memory/etc on /etc type none (rw,bind,noatime)
/lib on /.physical_disk/lib type none (rw,bind)
/.ramdom_access_memory/lib on /lib type none (rw,bind,noatime)
/lib32 on /.physical_disk/lib32 type none (rw,bind)
/.ramdom_access_memory/lib32 on /lib32 type none (rw,bind,noatime)
/var on /.physical_disk/var type none (rw,bind)
/.ramdom_access_memory/var on /var type none (rw,bind,noatime)
/usr on /.physical_disk/usr/originalfs type none (rw,bind,noatime)
none on /.ramdom_access_memory/usr type tmpfs (rw,size=1500m)
/dev/loop0 on /.ramdom_access_memory/usr/aufs/ro type squashfs (ro,noatime)
aufs on /usr type aufs (rw,noatime,br=/.ramdom_access_memory/usr/aufs/rw:/.ramdom_access_memory/usr/aufs/ro=ro)
/home/trg on /.physical_disk/home/trg/originalfs type none (rw,bind,noatime)
none on /.ramdom_access_memory/home/trg type tmpfs (rw,size=1500m)
/dev/loop1 on /.ramdom_access_memory/home/trg/aufs/ro type squashfs (ro,noatime)
aufs on /home/trg type aufs (rw,noatime,br=/.ramdom_access_memory/home/trg/aufs/rw:/.ramdom_access_memory/home/trg/aufs/ro=ro)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)

---

### Post by misfitpierce on 2009-09-16
> **swoll1980 said:**
> Ahhhh! Head for the hills! Our computers are using the RAM we put in them!

Exactly... I wouldn't mind if mine used more. Its there for a reason and needs to be used.

---

### Post by Warpnow on 2009-09-16
300mbs with gnome-do docky and compiz using most of that.

650 with just Firefox running.

---

### Post by Icehuck on 2009-09-16
Doing absolutely nothing and sitting at idle I use 32 mb of ram.

---

### Post by K.Mandla on 2009-09-16
Running X, htop, dash shell and elinks: 10Mb, no swap.

[http://kmandla.wordpress.com/2009/09/08/a-thousand-words-10mb/](http://kmandla.wordpress.com/2009/09/08/a-thousand-words-10mb/)

After a cold boot, only 2Mb.

---

### Post by Old_Grey_Wolf on 2009-09-16
My computer is not really idle. It is running some screenlets, compiz, AWN, Firefox with this page open, and System Monitor running. It is using 354 MiB. 

If I only had 512 MB of RAM I might care; however, I have 4 GB. I have the extra RAM because I like to use Virtualization to experiment with distros and other OSes.

---

### Post by RabbitWho on 2009-09-16
345 right after restarting .

4095 all together, but 32 bit therefore 3493

---

