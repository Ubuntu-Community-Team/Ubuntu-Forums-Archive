---
title: "udevd daemon is working my cpu like crazy"
date: 2009-05-09
forum: System76 Support
---

### Post by stewpac on 2009-05-09
My Panp4n has been cranking the cpu for a couple days now. I got around to looking up why and it seems there's been a bit of an issue with the udevd daemon which does event handling. I'm having this problem as when I kill udevd the cpu usage drops to basically nothing (as opposedto consistently 33% or 50% when I'm not doing anything intensive). 

I'm not happy to just kill it as the most important event for me is turning on my bluetooth radio (for my mouse). This doesn't work if udevd isn't running.

Any suggestions? 

At this point I'm very much regretting this 'upgrade' to jaunty which has far too many regressions for my taste.

---

### Post by gila_monster on 2009-05-09
I'm seeing the same thing. CPU is hovering around 25% usage. This isn't a killer for me, but it's annoying. I doubt there's a workaround, so let's hope that an update soon fixes things.

---

### Post by thomasaaron on 2009-05-10
I'm wondering if it is this tracker bug...

We have an ongoing forum post going on it. Please see...
[http://ubuntuforums.org/showthread.php?p=7225556#post7225556](http://ubuntuforums.org/showthread.php?p=7225556#post7225556)

Here is a link with a workaround. I've not tried it yet, as I've not been able to duplicate the problem in my shop...
[http://ubuntuforums.org/showthread.php?t=1138029](http://ubuntuforums.org/showthread.php?t=1138029)

Running these commands fixed it for one customer...
sudo apt-get install tracker-utils
tracker-processes -r 

Tracker sucks a lot of cpu time with this bug. Try running those commands and see if it corrects the problem.

---

### Post by stewpac on 2009-05-12
Thanks for the thought Tom but those fixes seem unlikely to me. I'm not even running tracker and I don't get the error messages listed in the posts you linked to.

It genuinely looks like udevd is the bad process - when I kill it my cpu usage goes back to normal. I don't know if tracker and udevd are related though. I've just been using

sudo /etc/init.d/udev restart 

when I want to connect my mouse or a drive or something and

sudo killall udevd

afterward to get the cpu down again. This is *really* annoying though so any other help you can give would be enormously appreciated.

---

### Post by thomasaaron on 2009-05-12
I'm not seeing any bugs reported on this. I also am not sure if udev is related to tracker. 

Try creating logs via System > Admin > System76 Driver > Support > Create while the cpu usage is high. Attach them to this thread, and I'll have a look.

---

### Post by MysticGold04 on 2009-05-18
I'm seeing 30-40% usage on both cores for udevd.  I think this started happening with the last round of updates.  I am not running the tracker, so I don't think that the tracker is involved. If I kill the udevd daemon, cpu usage goes down to 1-2% idling. I know that udevd is a required part of the system, so I restarted it after verifying it was the culprit.

EDIT: I'd like to add that my Acer laptop is the one affected.  This does not seem to be tied to System76 specifically.

---

### Post by thomasaaron on 2009-05-18
gila_monster and mysticGold04, 

I'm guessing that both of you guys upgraded, as opposed to doing a fresh install?

---

### Post by MysticGold04 on 2009-05-18
Mine was a fresh install.  I left my /home intact as ext3, and reformatted my / as ext4.  I attempted an upgrade from 8.10, but had issues because I didn't remove manually installed .debs and some other dependencies got messed up, so at that point I just rebooted and did a fresh install.  Everything seemed normal up until a week or so ago I started to notice my cpu hovering around 30-40% just idling.

The only reason I noticed is I run Conky. That only uses about 1-2% while the rest of the system is idle.

---

### Post by thomasaaron on 2009-05-18
My guess is that some configuration left over in your home dir, or the ext4 filesystem (which still has a lot of open bugs on it), has something to do with the problem. 

This has been a really bad upgrade. I've seen more hosed computers than in any other upgrade.

---

### Post by stewpac on 2009-06-28
Sorry it took so long to do but I've attached a log file as you suggested. I'm still having issues with it. I wouldn't mind it so much but I think it affects battery life negatively and my fan is running more often.

For the logs, I produced them from the sys76 driver and restarted the system just before producing them.

By the way, I did try doing the tracker commands which didn't result in any difference. I also still have the ext3 file system so I don't think it has to do with a bug in ext4. Though maybe it has something to do with my not having ext4.

Hope it helps figure out what the problem is.

---

### Post by thomasaaron on 2009-06-29
Try running...

sudo apt-get remove evms

...and then rebooting.

---

### Post by stewpac on 2009-06-30
I tried it, but it doesn't seem to be installed. Any other ideas?

Here was my output

stew@venture:~$ sudo apt-get remove evms
[sudo] password for stew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package evms

---

### Post by thomasaaron on 2009-06-30
Could you please post the output...

cat /etc/fstab

Also, you might have a look at this thread. Seems to be the same problem...
[http://ubuntuforums.org/archive/index.php/t-450206.html](http://ubuntuforums.org/archive/index.php/t-450206.html)

---

### Post by stewpac on 2009-06-30
Sure. I'll check out the thread too.

stew@venture:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	defaults	0	0
# /dev/sda1
UUID=6c814527-5db0-4129-b3bc-f41a16213147	/	ext3	relatime,errors=remount-ro	0	1	# /dev/sda1
# /dev/sda3
UUID=5aea32d9-f557-461a-958a-011fe718ac27	/home	ext3	relatime	02	# /dev/sda3
# /dev/sda2
UUID=3d13dcef-1b8c-41d9-bada-a585b4022a2d	none	swap	sw	0	0# /dev/sda2
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

---

### Post by thomasaaron on 2009-06-30
OK. After looking at your fstab, I don't think that you have the same issue. Back to the drawing board...

Go to System > Administration > Synaptic Package Mangaer. Search for udev, and tell me what version you are running.

You are on Jaunty, too, right?

---

### Post by stewpac on 2009-06-30
I'm using udev version 141-1.1.

Yes, I'm on Jaunty and this started occurring after I upgraded (not a clean install).

---

### Post by thomasaaron on 2009-06-30
OK. In Synaptic Package Manager, search for it again and highlight it. Then go to Package > Force Version in Synaptics Menu. In the resulting window, select 141-1 (Jaunty) and lock that version in.

Does that fix the problem? If not, go ahead and repeat the procedure and go back to the other version.

---

### Post by stewpac on 2009-06-30
Ok. I did that and it does appear to have fixed the problem. I guess there's a bug in udev 1.1. 

Thanks for the help!

---

### Post by Spike-X on 2010-02-06
> **thomasaaron said:**
> OK. In Synaptic Package Manager, search for it again and highlight it. Then go to Package > Force Version in Synaptics Menu. In the resulting window, select 141-1 (Jaunty) and lock that version in.

Does that fix the problem? If not, go ahead and repeat the procedure and go back to the other version.

Bumping this thread because this fixed the problem I was having with udev following the latest upgrade.

---

### Post by Spike-X on 2010-02-06
...at least, I thought it had fixed the problem until I turned the computer back on and found it was still happening.

---

### Post by thomasaaron on 2010-02-08
Spike-X, what System76 model do you have?

---

