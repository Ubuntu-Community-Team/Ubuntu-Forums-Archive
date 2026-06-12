---
title: "Something odd I've noticed."
date: 2005-10-15
forum: The Cafe
---

### Post by PatrickMay16 on 2005-10-15
I've noticed that every time I boot Ubuntu Linux, log into GNOME and everything, and start doing my work and so on... After 15 minutes or so, something is done with my hard disks. I can tell because both of my disks make noises, as if they're being searched for something. This goes on for more or less a minute, and then stops. If I have the GNOME system monitor running while this happens, I notice the amount of used memory steadily increases until it stops.
It's not a problem for me, but I'm very curious as to what's happening. I'm guessing it's caching stuff for some reason, but I'm not sure.
Anyone know?

EDIT: Just thought I'd include this, too. It's kind of odd that it does this with both my disks. What could it possibly want with my other disk?
```

patrick@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14759   118551636   83  Linux
/dev/hdb2           14760       14946     1502077+   5  Extended
/dev/hdb5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/sda: 64 MB, 64864256 bytes
214 heads, 37 sectors/track, 16 cylinders
Units = cylinders of 7918 * 512 = 4054016 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16       63324+   6  FAT16
patrick@ubuntu:~$ 

```

---

### Post by dbott67 on 2005-10-15
After logging in, open a terminal & type in the following command:
```
top
```
```
top - 22:18:57 up 1 day, 14:20,  3 users,  load average: 0.56, 0.38, 0.38
Tasks:  86 total,   1 running,  84 sleeping,   1 stopped,   0 zombie
Cpu(s): 20.3% us,  3.9% sy,  0.0% ni, 74.2% id,  1.3% wa,  0.3% hi,  0.0% si
Mem:    256796k total,   250508k used,     6288k free,     2396k buffers
Swap:   208772k total,    43172k used,   165600k free,    63972k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6782 root      15   0 57428  43m 8552 S 12.8 17.3  81:16.19 Xorg
30556 dbott     15   0 31048  13m 8636 S  7.8  5.3   0:10.33 gnome-terminal
28539 root      15   0 22380  12m 8728 S  2.0  4.9   3:17.57 firestarter
30578 dbott     16   0  2132 1084  844 R  1.3  0.4   0:00.23 top
 6230 root      19   4     0    0    0 S  0.3  0.0   5:07.89 ktoshkeyd
 7350 dbott     16   0 23688  13m 8340 S  0.3  5.5   0:23.01 gnome-panel
 7360 dbott     15   0 18772 9712 7376 S  0.3  3.8   0:04.21 update-notifier
 7406 dbott     15   0 22516 8456 7196 S  0.3  3.3   7:31.76 clock-applet
    1 root      16   0  1560  516  460 S  0.0  0.2   0:04.17 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.62 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      10  -5     0    0    0 S  0.0  0.0   0:08.59 kacpid
   84 root      10  -5     0    0    0 S  0.0  0.0   0:00.50 kblockd/0
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.53 pdflush
  113 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
```

Then, sit, wait and watch the display.  When the hard drives start spinning, take a look at top to see which apps are running & consuming memory & CPU.

-Dave

---

### Post by PatrickMay16 on 2005-10-15
Thanks, I'll try this out. I'll edit this post once I've found the process which does this.

---

### Post by drummer on 2005-10-15
I've noticed this also, but haven't looked at the memory when it happens. I haven't noticed it happening at certain times, but when it does, my cpu graph displays about 100% 'nice' being used (not exactly sure what that is) but it doesn't slow my system down, just makes the hdd sound like it's grinding through something. I thought it might be Gnome updating a database or something but never looked into it. I'm curious too as to what it is. Any ubuntu devs that know??

---

### Post by wmcbrine on 2005-10-15
This is normal and happens in most distros I've used. It's the "locate" database being updated. It's usually scheduled to run late at night, but if your system isn't running then and you're using anacron, it will run the next time you boot.

---

### Post by az on 2005-10-15
There are a few cronjobs like logrotation and package update fetching...

---

### Post by drummer on 2005-10-15
[QUOTE=wmcbrine]It's usually scheduled to run late at night[/QUOTE]
That's probably when I notice it running, up at 1am with nothing better to do... :P

---

### Post by UbuWu on 2005-10-16
[QUOTE=wmcbrine]This is normal and happens in most distros I've used. It's the "locate" database being updated. It's usually scheduled to run late at night, but if your system isn't running then and you're using anacron, it will run the next time you boot.[/QUOTE]

And you can easily and safely disable it if you never use the locate command (don't remember how right now, I am at a windows pc here at the moment). And eve if you use locate from time to time, you can easily manually update the database after big changes to the filesystem.

---

### Post by Goober on 2005-10-16
I've yet to notice this.  I mean, I do hear the Hardrives booting up, but that is normal, since everything else is booting up as well.

No, I have never noticed this specific problem.

---

### Post by wrtpeeps on 2005-10-16
sounds interesting, but is this just GNOME?

---

### Post by wmcbrine on 2005-10-17
Nothing to do with Gnome. It's been around forever... my Slackware 3.0 system did it back in '96. (I don't think it used anacron, though, so it only happened if the system was up at index time.)

I use "locate" all the time, so I don't mind a bit.

---

### Post by kanem on 2005-10-17
If you don't want this running everyday but don't want to disable it completely you can just move it to being a weekly job instead of daily. 

By default the script (which is called slocate) resides in /etc/cron.daily. Just move it to /etc/cron.weekly (or /etc/cron.monthly) and you won't have to hear your drives grinding everytime you boot.

If your system doesn't change much from week to week the locate command should still be effective

---

### Post by alred on 2005-10-17
PatrickMay16 , maybe you can try this  qps , its a gui process viewer , works very fast and lean , rather complete if you   enable all the "features" , can peep at lots of things ...

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=qps&searchon=names&subword=1&version=hoary&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=qps&searchon=names&subword=1&version=hoary&release=all")

---

### Post by jobezone on 2005-10-17
Gnome's search file tool (Under the menu "Places") also uses locate, I think. I say this because when I use it to search a file, it imediately gives a list of good results (like it isn't actually searching in the filesystem), and thenItakes a bit longer to get a few more. in my eyes, it seems to first search with "locate", and only then doesn it use find to crawl the directories. So, I think it's a good idea to leave updatedb running.

Beagle is cooler though :)

---

