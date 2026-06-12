---
title: "TightVNC server permission issues"
date: 2011-06-28
forum: Server Platforms
---

### Post by timstott on 2011-06-28
Hello Ubuntu Forum!

I have installed TightVNC server via ssh on a computer (Ubuntu 10.04), configured it so that it could run as a daemon...

I have multiple hard drives in the machine and I cannot mount them, create new partitions...
I get the following message: Permission Denied : "Not Authorized"

This is strange as I could do these operations when I was physically on the computer (not via remote desktop).

I know TightVNC creates a new desktop on connection but I don't understand why it would change my access rights...

Note: I can do everything I want when I vnc login as root.

Could you please help me with what I believe is a permission problem with TightVNC ?
I've spent some time on the web and couldn't find a similar problem or a solution.

Thank you very much :D

---

### Post by doas777 on 2011-06-28
are you able to sudo/gksu from your remote session? can the user usually sudo/gksu when operating interactively?

---

### Post by timstott on 2011-06-28
Yes I am able to sudo from my remote session.

---

### Post by arrrghhh on 2011-06-28
Wait, why are you using TightVNC on a server install?

ssh should be all you need to manage the server remotely...

---

### Post by timstott on 2011-06-28
Agreed, arrrghhh, I should have never used the word server :D.

It's for collaboration work... Nothing fancy really.

---

### Post by arrrghhh on 2011-06-28
> **timstott said:**
> Agreed, arrrghhh, I should have never used the word server :D.

It's for collaboration work... Nothing fancy really.

This is in the server platform section of the forum... as in no GUI :p.

---

### Post by timstott on 2011-06-28
My bad, I didn't really know where to put it. Though my issue seems to be related to a server application.

I had no problem doing what I wanted when I had the computer in front of me. It's a TightVNC server problem.

Where should I redirect the post?

---

### Post by doas777 on 2011-06-28
so you have a desktop server. no big. I have one myself, and ain't no one gonna tell me its not a "server". its where my services live.

so when you are operating the box interactively, you can mount drives without autorization, but when on a vnc session remoted into the same user accounts session, you cannot. is that correct?

are the drives listed in your fstab, and do the folders that the mount points indicate exist already? the folders are in /media by default.

since your user is sudo-capable and you are able to use it correctly in the vnc session as well, that kinda says to me that the problem is with gfuse or one of the user-space feature enablers (stuff that lets users run certain things that traditionally only root can do, like mount partitions).

I have no particular expertise with these kinds of issues, since I'm quick to throw together a workaround (like mounting from the terminal), but I have a hunch that the user that is running the vnc process lacks the ability to mount a disk, and at some level its authorization is coming into question.

if you run:
```
ps -ef | grep vnc
```what user is the server running under?

if you run:
```
groups <usernameFromAbove>
```is 'fuse'/'plugdev' in there?
here are the defaults for a sudo-capable user:
```
adm dialout fax cdrom floppy tape dip video plugdev users fuse lpadmin admin
```

---

### Post by timstott on 2011-06-29
Hello doas777,

That is right, when I operate the box interactively, I can mount drives without autorization, but when on a vnc session remoted into the same user accounts session, I cannot.

Regarding fstab, I think it is not listing all my drives.

Here is the content of /etc/fstab
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e12a2679-678d-4223-a814-8e93e49e4c97 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f26b4fb3-4e4b-498f-9dd2-9ad542824962 none            swap    sw              0       0

```

And here is sudo fdisk -l
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea29db28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38853   312081408   83  Linux
/dev/sda2           38853       38914      487425    5  Extended
/dev/sda5           38853       38914      487424   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b012e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488386583+  ee  GPT

```

If I run the code ps -ef | grep vnc, I get user root (I have temporarily created a vnc for root) and 1000 (I don't know what that is).
I've put the output below just in case
```
1000      1032     1  0 Jun28 ?        00:01:08 Xtightvnc :0 -desktop server -auth /home/me/.Xauthority -geometry 1024x768 -depth 16 -rfbwait 120000 -rfbauth /home/me/.vnc/passwd -rfbport 5900 -fp /usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb
1000      1062     1  0 Jun28 ?        00:00:00 /bin/sh /home/me/.vnc/xstartup
root      2824     1  0 Jun28 ?        00:03:29 Xtightvnc :1 -desktop X -auth /root/.Xauthority -geometry 1024x768 -depth 24 -rfbwait 120000 -rfbauth /root/.vnc/passwd -rfbport 5901 -fp /usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/75dpi/,/usr/share/fonts/X11/100dpi/ -co /etc/X11/rgb
root      2828     1  0 Jun28 ?        00:00:00 /bin/sh /root/.vnc/xstartup
1000      4895  4861  0 14:55 pts/0    00:00:00 grep --color=auto vnc
```

So my username is not in the output above but I still did groups <me>.
Outputs a list that does include 'fuse' and 'plugdev'.
```
me adm dialout cdrom plugdev fuse lpadmin admin sambashare
```

I hope this helps and clear things up.
Thank you very much for you time and patience.

---

### Post by timstott on 2011-06-30
By the way, I have just installed vnc4server and I am having the exact same problem.

But there is a workaround for accessing the drives. It's not perfect but at least they are accessible (consists in adding fixed drives to fstab)
[http://ubuntuforums.org/showthread.php?t=635561](http://ubuntuforums.org/showthread.php?t=635561)

---

### Post by doas777 on 2011-06-30
definitely seems to be a fuse issue. I wish that info lead me to actionable conclusions.
I agree with your workaround (in fact I always try to configure my systems that way in any case), so hopefully that will address your needs. CDroms and usb drives will probably remain an issue however.

---

