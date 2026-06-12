---
title: "increasing disk space usage"
date: 2009-12-13
forum: The Cafe
---

### Post by SpriteSODA on 2009-12-13
Hi guys,

I have the same system installed on my PC for more than a year now, was Ubuntu 8.10 and was upgraded two times, finishing at 9.10 .

I'm now in a situation that my 22GB partition is out of space, and I wonder - HOW THE HELL!?, my user folder is 900MB, cant seem to understand WHY the OS takes so much space? I haven't got that much of packages installed, its crazy.

Any suggestions before I format the whole thing and start over?

---

### Post by CharlesA on 2009-12-13
You can run df -h in a terminal to see where the majority of the space is being used.

Also, there is a disk space analyzer in Gnome (not sure if there is one in KDE)

Also it might be worth noting that upgrades can leave traces of old stuff behind.

---

### Post by GeneralZod on 2009-12-13
See how much space

/var/cache/apt/archives/

take up, first.

---

### Post by orlox on 2009-12-13
Why not check the space used by the main folders under /
that might give some light unto what has happened here. Also, try running the system janitor.

---

### Post by koleoptero on 2009-12-13
Install ubuntu-tweak and do a package, config, and cache cleanup first.

---

### Post by SpriteSODA on 2009-12-13
> **GeneralZod said:**
> See how much space

/var/cache/apt/archives/

take up, first.

it takes 4KB, I think i emptied it using apt-get clean..

as for the computer janitor - that thing is insane, offers to remove packages I'm definitely using.

---

### Post by NoaHall on 2009-12-13
Check out your log sizes. If you have something like bootchart, it can use up a lot of space.

If you want to just delete everything there - (I don't recommend it) -
```
rm -rf /var/log/
```

---

### Post by SpriteSODA on 2009-12-13
the whole /var folder takes 180MB :S

---

### Post by drs305 on 2009-12-13
Three common causes of 'lost' disk space are undeleted trash (including root's), large log files, and backups which were supposed to be made to a backup partition but ended up on the wrong one.

Here is a link to analyzing and correcting disk space issues:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by CharlesA on 2009-12-13
> **drs305 said:**
> Three common causes of 'lost' disk space are undeleted trash (including root's), large log files, and **backups which were supposed to be made to a backup partition but ended up on the wrong one.**

Done that when I screwed up mounting by UUID. Having 300 gigs of data on a 320gb hard drive is bad news. :o

---

### Post by SpriteSODA on 2009-12-13
> **drs305 said:**
> Three common causes of 'lost' disk space are undeleted trash (including root's), large log files, and backups which were supposed to be made to a backup partition but ended up on the wrong one.

Here is a link to analyzing and correcting disk space issues:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

Thanks, looks very informative.

---

### Post by sdowney717 on 2009-12-13
root trash can build up pretty huge quickly.

sudo apt-get install trash-cli
sudo -i empty-trash

gets rid of it

[http://code.google.com/p/trash-cli/](http://code.google.com/p/trash-cli/)

interesting the ubuntu version reverses the command syntax
trash-empty becomes empty-trash
[http://www.mail-archive.com/distributions@lists.freedesktop.org/msg00282.html](http://www.mail-archive.com/distributions@lists.freedesktop.org/msg00282.html)

---

### Post by SpriteSODA on 2009-12-13
Thanks alot guys, using the guide drs305 suggested I found 6GB of virtualbox old snapshots and 4GB system backup from March 09, cleared 10GB of HD space :)

---

### Post by sdowney717 on 2009-12-13
i have a lot of big files myself

> scott@scott-desktop:~$ sudo find / -size +1G 
find: `/proc/9437/task/9437/fd/5': No such file or directory
find: `/proc/9437/task/9437/fdinfo/5': No such file or directory
find: `/proc/9437/fd/5': No such file or directory
find: `/proc/9437/fdinfo/5': No such file or directory
/home/scott/.VirtualBox/HardDisks/virtualbox_mythbuntu_8_10/disk.vdi
/home/scott/.VirtualBox/HardDisks/xppro32.vdi
/home/scott/.VirtualBox/HardDisks/mythbuntu.vdi
/home/scott/Videos/vlc-record-2009-10-28-21h02m00s-video0-.mpg
/home/scott/Videos/vlc-record-2009-10-28-20h04m17s-video0-.mpg
/home/scott/Videos/vlc-record-2009-09-28-11h00m43s-v4l2:__-.mpg
/home/scott/Videos/Tuesday-11-17-2009+18H-52m-07s.avi
/home/scott/Videos/vlc-record-2009-09-27-13h30m09s-v4l2:__-.mpg
/home/scott/Download/virtualbox_mythbuntu_8_10.tar.bz2
/home/scott/vm/vistabus.iso
find: `/home/scott/.gvfs': Permission denied
/home/scott/xpprooriginal.img
/home/scott/obamadvd.iso
/home/scott1/.config/chromium/Default/History
/home/scott1/obamadvd.iso
/var/lib/libvirt/images/ninixpkvm.img
/var/lib/libvirt/images/xpprooriginal.img
/var/lib/vmware/Virtual Machines/Windows Vista/Windows Vista.vmdk
/var/lib/vmware/Virtual Machines/UbuntuMiniJaunty/UbuntuMiniJaunty.vmdk
/var/lib/vmware/Virtual Machines/xpprooriginal (copy)/xpprooriginal-flat.vmdk
/var/lib/vmware/Virtual Machines/Windows Vista (fresh install)/Windows Vista.vmdk
/var/lib/vmware/Virtual Machines/Windows Vista (tversity+Avast)/Windows Vista.vmdk
/var/lib/vmware/Virtual Machines/xpprooriginal/xpprooriginal-flat.vmdk
/var/lib/vmware/Virtual Machines/xpprodell timer runs out?/xpprodell-flat.vmdk
/var/lib/vmware/Virtual Machines/xpprodell timer runs out?/xpprodell-000001.vmdk
scott@scott-desktop:~$ 


---

### Post by dullard on 2009-12-13
Take a look at:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

Using 8.04 here but I suspect that most, if not all, applies to 9.10 also,

---

