---
title: "Ubuntu Home Server Upgrade Advice Needed"
date: 2012-08-28
forum: Server Platforms
---

### Post by mitanc on 2012-08-28
Hey All,

I currently running an Ubuntu Home Media Server which responsibilities are:

[LIST]Filesharing (mainly for videos which can be watched on iOS devices and XBMC hooked up two different TVs in the house)[/LIST]
[LIST]NZB Downloading (sabnzb & sickbeard)[/LIST]
[LIST]dyndns resolution[/LIST]
[LIST]AirVideo Server[/LIST]
[LIST]Websever (very small footprint, one or two functions I am the only user)[/LIST]
[LIST]Any other random thing I can come up with Linux to do for me.[/LIST]

The server is running on Ubuntu 10.04 (Lucid) 32 Bit.  Here is the output of my df -h command:
```
sysadmin@mediaserver:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              4.6G  4.3G   94M  98% /
none                  986M  248K  985M   1% /dev
none                  990M     0  990M   0% /dev/shm
none                  990M  372K  990M   1% /var/run
none                  990M     0  990M   0% /var/lock
none                  990M     0  990M   0% /lib/init/rw
/dev/sdb3              92G  1.8G   86G   3% /backup
/dev/md1              276G  226G   36G  87% /home
/dev/sda4             634G  541G   61G  90% /mediafiles
/dev/sdb4             546G  514G   32G  95% /oldmediafiles

```

To summerize, I have /dev/sda & /dev/sdb both are 1 TB hard drives.  

I have the following partitions under software raid:
/dev/md0 /         4.6 GB
/dev/md1 /home     276 GB

The rest is free space in both the sda and sdb drives which are dedicated mainly to videos which I download.  

Now, the issue I am having is my sdb hard drive is about to fail.  This is the output of smartctl -Hc /dev/sdb

```
sysadmin@mediaserver:~$ sudo smartctl -Hc /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
Failed Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   002   002   036    Pre-fail  Always   FAILING_NOW 4015

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 ( 600) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 195) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

```

Lastly, I have no space left on my / parititon so its becoming difficult to do upgrades and even install new software on the ubuntu system.  

I have now decided the hard drives need to be replaced so I purchased 2 x 3 TB Hard Drives which I want to put into RAID 1 configuration.  Instead of paritioning of the space I was going to put everything on partition and have it all mirrored.  This way if one ever fails I can always replace the drive and still be up and running.  

Since I was doing this, I was going to plan on reinstalling the newest ubuntu version but I'd like to keep my settings for sabnzb, sickbeard, and all those other things I setup for this computer.  

Can any of you guys offer some advice as to how to go about doing this?  What would be the best way without the most problems.

Appriciate all your help, thanks!

---

### Post by CharlesA on 2012-08-28
You could try cleaning out / but a 5GB partition is probably a bit too small if you are going to be installing a ton of stuff.

I run my server VMs with 15GB drives, usually, but sometimes with drives as large as 50GB.

---

### Post by mitanc on 2012-08-29
> **CharlesA said:**
> You could try cleaning out / but a 5GB partition is probably a bit too small if you are going to be installing a ton of stuff.

I run my server VMs with 15GB drives, usually, but sometimes with drives as large as 50GB.

I ended up doing the following:

I purchased two 3 TB Drives and loaded them in LVM in Ubuntu server 12.04.

I then made logical partitions for the following
```
/
/boot
/media/datafiles  # Other files
/media/mediafiles  ## All the videos
/media/TimeMachine ## Time Machine server for my mac
/media/SnapRaid  ## SnapRaid parity directory
```

After making all the space for these I have about 1 TB to spare, and since its LVM I think it will give me the options for resizing if the time comes.  

Any recommendations or thought?

Thanks!

---

### Post by CharlesA on 2012-08-29
That sounds about right. I haven't used LVM, so I am not 100% sure on it.

I would rather go with the largest possible partition from the start instead of messing with it later, but that is just me. :)

---

### Post by mitanc on 2012-08-29
> **CharlesA said:**
> That sounds about right. I haven't used LVM, so I am not 100% sure on it.

I would rather go with the largest possible partition from the start instead of messing with it later, but that is just me. :)

I agree on that, but depending on the situation this leaves me more flxible.  I currently have 2 TB dedicated to my media files (thats only downloaded TV, Movies, etc.) and 500 GB for my datafiles.

I kept 500 GB for TimeMachine for my iMac which will hold my photos and music in iTunes (I prefer that kind of media kept sorted on this)

Lastly, some space for the snap raid setup which may or may not need to grow in the future.  Leaves me flexible to figure it out as it gets bigger.

Anyways, always love to hear about other configs.

Thanks!

---

### Post by LHammonds on 2012-08-29
> **mitanc said:**
> 
Any recommendations or thought?

I would definitely recommend organizing it so it can grow in the future rather than consuming everything now.  You can take a look in my sig for how I setup an Ubuntu Server with LVM.

I initially create and separate everything with very small partitions...just enough to get up-and-running.  I then increase the volume to where I think I need it for the immediate future with a little bit extra room.  I then expand the file system in each to where I need them but leave room in the volume for additional growth in the future.

Having this extra room in the volume will allow you to easily increase the file system whenever you need it...and as a matter of fact, I use a script to watch the usage and auto-increase the file system as needed...and then it emails me to let me know it increase the space a little bit...thus allowing me time to determine if I need to expand the volume some more or even add additional drives.

It is always easier and safer to expand a file system than shrinking it.  You can expand any file system while the system is online and running but to shrink, you MUST dismount the file system or corruption will occur.  Shrinking can also destroy data if you mess up and shrink it too much.  And with file systems used by the OS (such as the root or usr), you must take the server offline and boot a LiveCD to shrink them (you cannot take a file system offline if it is used by the OS!)

LHammonds

---

