---
title: "cpu usage in 10.04"
date: 2010-05-09
forum: System76 Support
---

### Post by stewpac on 2010-05-09
I just did the upgrade to lucid (upgrade not fresh install) and I am experiencing a large amount of cpu usage. I run top and the offending processes seem to be udisks-daemon, gvfs-gdu-volume-manager, and udevd. I've had the udevd problems before ([http://ubuntuforums.org/showthread.php?t=1154175&highlight=cpu+usage](http://ubuntuforums.org/showthread.php?t=1154175&highlight=cpu+usage)) and been able to downgrade udev in synaptic. This got rid of the high cpu usage but also resulted in needing to manually mount usb drives and cd/dvds as well as having to restart to get usb keyboards to work. I cannot do this now (or at least I don't know how now) as the upgrade seems to have removed the option to force the version number for udev to an earlier one.

I have also tried:
```
$ sudo killall udevd

```
and not really experienced a difference in the cpu usage so this problem may be related to gvfs and udisks more than udev itself.

The proposed repo seems to contain some upgrades to gvfs but I don't like to do things that I don't know for sure how to reverse so I haven't installed them.

I should say that keyboards and usb drives appear to work the way they're supposed to (just as they did with high cpu usage in the previous version of ubuntu).

I have a panp4n pangolin and I'm up to date and have also run the system76 driver and restarted.

---

### Post by thomasaaron on 2010-05-10
I'm not seeing this across the board, or with our shop panp4n, so it's probably something unique to your particular install.

You might check to see if it occurs from a live CD (I'm betting it won't). If not, you might want to try a fresh install. I hate suggesting that, but almost to a case, whenever I see one issue in an online upgrade, there are others not far behind. I'm just sayin'...

---

### Post by stewpac on 2010-05-10
If you are not seeing it then it does seem likely that there is something particular about my install. I'm reluctant to do a fresh install as I have made a lot of changes to my installation and I don't want to spend the time reproducing them. I also see it as a bit of a cop-out. I will check to see if it happens with a liveCD though that will take me a couple days. Do you have any other suggestions?

---

### Post by stewpac on 2010-05-11
Ummmm....ok. So I started poking around and found out through udisks --monitor that /org/freedesktop/UDisks/devices/sr0 was constantly being polled. Since this is the dvd drive I decided to see if mounting a disk there would stop the polling. It did...and the cpu usage is normal now.

So now that we know the problem...what do I do to fix it (besides keeping a dvd in the drive all the time)?

---

### Post by isantop on 2010-05-11
Does removing the DVD cause the CPU usage to jump back up? If not, then what happens after a reboot? This may have fixed the problem entirely.

---

### Post by stewpac on 2010-05-11
> **isantop said:**
> Does removing the DVD cause the CPU usage to jump back up? If not, then what happens after a reboot? This may have fixed the problem entirely.

Well, removing the dvd does make the usage go back up. In terms of rebooting (or in general) all that matters is whether a dvd is in the drive or not. Can you tell me why you thought it would have fixed it? I don't understand. Maybe I said something incorrect?

---

### Post by isantop on 2010-05-12
Just a diagnosis question.

When you upgraded, did you previously upgrade from 9.04 to 9.10? Sometimes, you can get simple errors with multiple upgrade cycles. The upgrade tool is really not exactly where it should be. 

Also keep in mind that a fresh install and re-setting up your computer may take less time than figuring out and fixing the problem. I don't want to make it seem like we're forcing you to just upgrade; I will continue to help you out if you'd rather, but this could be an upgrade problem, and it may be unlikely that we can fix this in a reasonable amount of time.

---

### Post by stewpac on 2010-05-12
> **isantop said:**
> Just a diagnosis question.

OK.

> **isantop said:**
> When you upgraded, did you previously upgrade from 9.04 to 9.10? Sometimes, you can get simple errors with multiple upgrade cycles. The upgrade tool is really not exactly where it should be. 

Yes I did. It does appear that the upgrade tool isn't where it should be. CPU usage was the only problem in the previous upgrade (I cannot say that this is the same problem however) and is one of two problems in this upgrade. (The other is the battery is not reporting correctly.)

> **isantop said:**
> Also keep in mind that a fresh install and re-setting up your computer may take less time than figuring out and fixing the problem. I don't want to make it seem like we're forcing you to just upgrade; I will continue to help you out if you'd rather, but this could be an upgrade problem, and it may be unlikely that we can fix this in a reasonable amount of time.

Yeah, I understand that if this takes a long time it may take more time but I'm willing to invest the time if it helps me learn what's going on. I also think that it's a little much to ask people to do a fresh install every 6 months. I mean, that's part of why I left windows. 

So ... any ideas?

---

### Post by thomasaaron on 2010-05-13
Hey, stewpac.

> Well, removing the dvd does make the usage go back up. In terms of rebooting (or in general) all that matters is whether a dvd is in the drive or not. Can you tell me why you thought it would have fixed it? I don't understand. Maybe I said something incorrect?

A couple years ago, I ran into a similar problem on a Darter Ultra 1 and our old Gazelle Performances. Ultimately, the problem turned out to be an incompatibility between Ubuntu and the firmware on the DVD drive.

Whenever no disk was in the drive, CPU usage would go out of control and eventually render the machine unusable. If you put a disk in the drive, this did not happen. 

Eventually, we found a firmware upgrade for the *dvd drive*, which fixed the problem. This is *not* something I'd want to try with your machine, as we're not seeing this across the board; your issue seems to be a one-off anomaly.

> Yeah, I understand that if this takes a long time it may take more time but I'm willing to invest the time if it helps me learn what's going on. I also think that it's a little much to ask people to do a fresh install every 6 months. I mean, that's part of why I left windows.

While you're correct that it isn't fair to ask people to do a fresh install every six months, it's also true that the last three Ubuntu upgrades have been riddled with support issues because of corruption occurring during the upgrade. Hosed upgrades go a bit beyond typical support scenarios in that there may be little or no solid community-wide leads to follow up on. But we'll do what we can.

My hunch is that something broke the way Ubuntu interacts with the firmware in your DVD drive.

I'll have Ian keep looking into it.

---

### Post by isantop on 2010-05-13
> **stewpac said:**
> (The other is the battery is not reporting correctly.)

Actually, these two problems may be one and the same. The way Ubuntu interacts with the CPU and the Battery are actually closely related through a special system called proc. My guess is that, somewhere along your upgrade path, some error occurred and caused a problem with your proc system, specifically the power management section of it.

---

### Post by stewpac on 2010-05-14
Ok. how do I go about investigating these options (proc or firmware)? I have heard of people solving this problem with a firmware upgrade to the dvd drive as well. I don't know if it's a good idea or not but I know I don't know how to upgrade the firmware for a device in linux.

---

### Post by thomasaaron on 2010-05-14
> I don't know if it's a good idea or not but I know I don't know how to upgrade the firmware for a device in linux.

In your case, this would not be a good idea. Since you have a one-off problem, it isn't a good idea to mess with the firmware. Also, I'm not even sure if there is a firmware upgrade for that dvd drive. So, it may not be *an* option anyway.

We'll continue looking into it a little bit more.

---

### Post by stewpac on 2010-05-28
So is there any news on this? I should say that the battery applet reports just fine but whatever conky uses to poll it isn't working. Also when logging in I get a notification that the battery may not be working.

---

### Post by thomasaaron on 2010-05-28
No. We're not able to duplicate your problem.

I'd advise re-imaging.

---

### Post by zitch on 2010-07-05
I had just updated to 10.04 this weekend from 8.10 (both 64-bit, with a fresh install onto a new harddrive) on my last-gen Serval Pro (serp5) and I'm seeing the same symptoms here.  When idling, there is a pretty constant 30-40% usage across all CPUs.  Work-around include inserting a disc into the DVD drive or shutting down udev ('sudo stop udev').  

This also occurs on the live CD!  I boot up the 10.04 64 bit Desktop live cd, open up a terminal, run top, then remove the CD from the drive and I see the same processes (gvfs-gdu-volume, udisks-daemon, dbus-daemon, udevd, and other) taking up 30%-40% of the cpu.  

For now, I've simply stopped udev until I need to plug in a USB device or insert a CD.  I'll probably make a couple of panel scripts to do this for now.

---

### Post by zitch on 2010-07-09
If it helps any, Here's the output of *cdrecord -scanbus* on my serp5:

```
$ cdrecord -scanbus
scsibus1:
	1,0,0	100) 'Optiarc ' 'DVD RW AD-7560S ' 'SX01' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *

```

I've also attached the output of *sudo udevadm monitor --property* while there's no CD in the drive.  Here are some related links for this little problem:

[http://ubuntuforums.org/showthread.php?t=1475029&highlight=udevd](http://ubuntuforums.org/showthread.php?t=1475029&highlight=udevd)
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/578180](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/578180)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=581791](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=581791)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=582903](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=582903)

The latter report seems to show that this was fixed in Debian, and the first link does show that a firmware upgrade of the drive did fix this for one person.

UPDATE:

My particular problem seems to related to this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379780](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379780).  I'm currently reading through it to see if there's any better way of working around this than disabling udev.

UPDATE 2:

Well, the suggestion by AmadeuS in [post 82](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379780/comments/82) did not work for me (I guess this was a fix for Karmic?), but the suggestion by [Mark Fernandes in post 78]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379780/comments/78") to run *hal-disable-polling --device /dev/sr0* as root did seem to work.  

I'll change my scripts to run this and *hal-disable-polling --enable-polling --device /dev/sr0*, though I want to try post 82's suggestion one more time, but with a reboot.

UPDATE 3: That's a negative on trying to disable polling in udev and reboot.  The *hal-disable-polling* scripts do work though.  And CDs still mount even with polling disabled!  Again, I'm running 10.04 with the serp5.  I'll work around with this script a bit longer 

Sorry for the many updates as I try to work through this problem.  As it is, it seems I can simply run *hal-disable-polling --device /dev/sr0* as root and the following processes: udevd, udisks-daemon, gvfs-gdu-volume, dbus-daemon, and several other processes do not constantly occupy 30% of my CPUs **and** I can still auto-mount CDs and attach USB devices.

---

### Post by thomasaaron on 2010-07-12
Please try booting from a live USB flash drive (which you can create via System > Admin > Startup Disk Creator) and see if the problem still exists. We've not been able to duplicate this one in the shop, and it doesn't appear to be happening across the board. So, it seems more like an upgrade-related data corruption.

If you don't get the problem via the flash drive (10.04 64-bit), then I'd recommend a fresh install.

---

### Post by zitch on 2010-07-12
Created a boot Flash drive from the 10.04 64-bit desktop cd (Connecting to the forums in it now), and here's what top is showing on boot:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ top

top - 00:39:57 up 2 min,  8 users,  load average: 1.52, 0.86, 0.34
Tasks: 204 total,   3 running, 201 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.2%us, 13.1%sy,  0.0%ni, 62.2%id,  0.0%wa,  0.5%hi,  0.0%si,  0.0%st
Mem:   4055676k total,   993008k used,  3062668k free,   104628k buffers
Swap:  8002552k total,        0k used,  8002552k free,   400516k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4626 ubuntu    20   0 63916 3736 2784 S   12  0.1   0:11.57 gvfs-gdu-volume    
 4671 root      20   0 57352 3444 2584 S   10  0.1   0:07.97 udisks-daemon      
 2332 messageb  20   0 24376 1980  772 S    7  0.0   0:05.27 dbus-daemon        
 5433 ubuntu    20   0  172m 8228 6248 S    7  0.2   0:06.28 gdu-notificatio    
 9648 ubuntu    20   0  199m  12m 9636 S    6  0.3   0:03.26 update-notifier    
 2824 root      18  -2 17716 1472  348 S    5  0.0   0:05.49 udevd              
 2323 root      20   0 16896  884  636 S    3  0.0   0:01.37 upstart-udev-br    
 2885 root      20   0  163m  33m 8880 R    3  0.8   0:08.73 Xorg               
    1 root      20   0 23816 2008 1292 S    1  0.0   0:01.65 init               
  266 root      20   0     0    0    0 S    1  0.0   0:01.08 scsi_eh_1          
 7428 ubuntu    20   0  207m  14m  10m S    1  0.4   0:00.57 gnome-terminal     
 4652 haldaemo  20   0 46864 5040 3916 S    1  0.1   0:00.58 hald               
 2337 root      16  -4 17720 1524  396 S    0  0.0   0:00.41 udevd              
 7226 ubuntu    20   0  510m  72m  29m S    0  1.8   0:07.05 firefox-bin        
 8699 ubuntu    20   0 19216 1468 1052 R    0  0.0   0:00.35 top                
13436 root      18  -2  4008  692  540 D    0  0.0   0:00.01 cdrom_id           
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           

```

It's still showing the same 30-40% CPU usage as when I re-enable polling on my installed system and when I boot the LiveCD then remove the CD after it boots.

After running *sudo hal-disable-polling --device /dev/sr0*:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ top

top - 00:43:40 up 6 min,  9 users,  load average: 0.71, 0.95, 0.49
Tasks: 174 total,   1 running, 173 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  0.0%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4055676k total,  1013992k used,  3041684k free,   104908k buffers
Swap:  8002552k total,        0k used,  8002552k free,   413448k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 8699 ubuntu    20   0 19216 1468 1052 R    1  0.0   0:01.30 top                
    1 root      20   0 23816 2008 1292 S    0  0.0   0:03.66 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.04 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.05 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.19 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr          
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                 
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers        

```

As you can see, the CPU usage practically drops to zero.

Re-enabling polling using *sudo hal-disable-polling --enable-polling --device /dev/sr0* gives:
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ top

top - 00:46:29 up 9 min,  9 users,  load average: 1.31, 0.92, 0.54
Tasks: 174 total,   2 running, 172 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.8%us, 13.5%sy,  0.0%ni, 60.8%id,  0.0%wa,  1.0%hi,  0.0%si,  0.0%st
Mem:   4055676k total,  1005212k used,  3050464k free,   104908k buffers
Swap:  8002552k total,        0k used,  8002552k free,   413576k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4626 ubuntu    20   0 64040 3844 2784 S   17  0.1   0:34.68 gvfs-gdu-volume    
 4671 root      20   0 57352 3444 2584 S    9  0.1   0:25.99 udisks-daemon      
 2332 messageb  20   0 24376 1980  772 S    8  0.0   0:17.26 dbus-daemon        
 2926 root      18  -2 17716 1472  348 S    8  0.0   0:02.24 udevd              
 5433 ubuntu    20   0  172m 8308 6248 S    8  0.2   0:20.07 gdu-notificatio    
 9648 ubuntu    20   0  199m  13m 9640 S    5  0.3   0:14.24 update-notifier    
    1 root      20   0 23816 2008 1292 S    1  0.0   0:04.19 init               
 2323 root      20   0 16896  884  636 S    1  0.0   0:03.55 upstart-udev-br    
 2885 root      20   0  163m  33m 8908 S    1  0.9   0:22.85 Xorg               
  266 root      20   0     0    0    0 S    0  0.0   0:02.74 scsi_eh_1          
 2337 root      16  -4 17720 1524  396 S    0  0.0   0:01.17 udevd              
 7428 ubuntu    20   0  213m  21m  10m S    0  0.5   0:02.17 gnome-terminal     
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.05 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.05 migration/1        
        

```

And finally, inserting a CD with polling enabled on the drive:
```

top - 00:48:32 up 11 min,  9 users,  load average: 0.87, 0.92, 0.58
Tasks: 175 total,   1 running, 174 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.7%us,  1.5%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   4055676k total,  1007668k used,  3048008k free,   105168k buffers
Swap:  8002552k total,        0k used,  8002552k free,   414516k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2885 root      20   0  164m  33m 8908 S    2  0.9   0:24.24 Xorg               
 7226 ubuntu    20   0  511m  75m  30m S    1  1.9   0:28.38 firefox-bin        
 4626 ubuntu    20   0  150m 4320 3064 S    1  0.1   0:43.96 gvfs-gdu-volume    
 7428 ubuntu    20   0  213m  21m  10m S    1  0.5   0:02.74 gnome-terminal     
 4428 ubuntu    20   0  290m  14m  10m S    0  0.4   0:00.84 metacity           
 4671 root      20   0 65780 3692 2796 S    0  0.1   0:33.10 udisks-daemon      
 5433 ubuntu    20   0  172m 8392 6248 S    0  0.2   0:25.54 gdu-notificatio    
25869 ubuntu    20   0 19216 1448 1052 R    0  0.0   0:00.50 top                
    1 root      20   0 23816 2008 1292 S    0  0.0   0:05.05 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.05 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.06 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.30 events/0           

```

As it is, running *hal-disable-polling --device /dev/sr0* as root seems to persist though boot (looks like it creates a file at /etc/hal/fdi/information/media-check-disable-storage_model_Optiarc_DVD_RW_AD_7560S.fdi), so there's no need to re-run the command on every boot.  I've been running this way all weekend and yet to come across any problems.  So I guess this matter is largely solved for me (if running this command was the "correct" fix).

---

### Post by thomasaaron on 2010-07-13
OK, well, so much for that idea. Thanks for trying that. I'll put a tech on it and see what we can figure out.

---

### Post by zitch on 2010-07-13
No problem.  If you need anything else from me, feel free to ask.  I wouldn't be surprised if it's a low priority since it seems pretty specific to the hardware (especially the Optiarc DVD RW AD-7560S drive) and seems to have a pretty easy fix (one that just has to be incorporated into future updates if it's the right one).

---

### Post by JohnM1 on 2010-07-17
> **zitch said:**
> 
PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
4626 ubuntu 20 0 64040 3844 2784 S 17 0.1 0:34.68 gvfs-gdu-volume
4671 root 20 0 57352 3444 2584 S 9 0.1 0:25.99 udisks-daemon
2332 messageb 20 0 24376 1980 772 S 8 0.0 0:17.26 dbus-daemon


This problem has been bugging me for a long time - excessive CPU usage with gvfs-gdu-volume, udisks-daemon and dbus-daemon

I have had this problem on Lucid and Karmic - fresh installs.

Looks like it is down to my Optiarc ad-7640S DVD drive.

This command "fixes" the problem for me too:

```
sudo hal-disable-polling --device /dev/sr0
```

---

### Post by andres.ordonez on 2010-07-31
Works for me too.

ubuntu 10.04 64bit
optiarc dvd rw AD-7580S

---

