---
title: "Disk check every time I boot"
date: 2012-10-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by charlescarroll1 on 2012-10-08
I'm running Ubuntu 12.04 with Gnome 3 and every time I power on my system, there is always a disk check which is getting kind of annoying. I am dual booting with Windows 7 and also have a second hard drive in my laptop that is replacing the CD drive. The only thing I've found was [this post]("http://askubuntu.com/questions/60249/why-does-ubuntu-ask-to-check-my-hard-drives-every-so-often"), which hasn't worked.

Any thoughts?

---

### Post by Crafty Kisses on 2012-10-08
I'm aware the instructions were on tune2fs, but have you tried
```

sudo tune2fs -c 0 /dev/sdXY
```

---

### Post by GeForce 9500GT on 2012-10-08
[Check here, tip no. 2]("https://sites.google.com/site/tipsandtricksforubuntu/tips-and-tricks").

---

### Post by overdrank on 2012-10-08
Moved to Ubuntu +1 (Quantal Quetzal)

---

### Post by funicorn on 2012-10-08
try to fsck the problematic disk, when it's [COLOR="Red"]unmounted[/COLOR]

---

### Post by VinDSL on 2012-10-08
Ran into this problem on the last cycle (PP).

Might want to peruse this thread, for clues...

[INDENT][http://ubuntuforums.org/showthread.php?t=1927438]("http://ubuntuforums.org/showthread.php?t=1927438")[/INDENT]

---

### Post by charlescarroll1 on 2012-10-10
> **Crafty Kisses said:**
> I'm aware the instructions were on tune2fs, but have you tried
```

sudo tune2fs -c 0 /dev/sdXY
```

This is the error message I get
```
tune2fs 1.42 (29-Nov-2011)
tune2fs: No such file or directory while trying to open /dev/skXY
Couldn't find valid filesystem superblock.

```

---

### Post by charlescarroll1 on 2012-10-10
> **GeForce 9500GT said:**
> [Check here, tip no. 2]("https://sites.google.com/site/tipsandtricksforubuntu/tips-and-tricks").

This is the error message I get:
```
sudo: tune2fs-c: command not found

```

I don't know what this tune2fs command is, but it apparently isn't working :(

---

### Post by GeForce 9500GT on 2012-10-10
> sudo: tune2fs-c: command not found
 
There must be a space between tune2fs and -c. It should be:
[B]sudo tune2fs -c # # # / dev / ***
[/B]
Where:
###  is the interval of checking
***   is the partition which has to be checked/changed
 
 
 
 
> I don't know what this tune2fs command is, but it apparently isn't working :(
 
Read these sites:
[http://oreilly.com/linux/command-directory/cmd.csp?path=t/tune2fs](http://oreilly.com/linux/command-directory/cmd.csp?path=t/tune2fs)
[http://linux.about.com/library/cmd/blcmdl8_tune2fs.htm](http://linux.about.com/library/cmd/blcmdl8_tune2fs.htm)
[http://www.unixtutorial.org/commands/tune2fs/](http://www.unixtutorial.org/commands/tune2fs/)
[http://www.commandlinefu.com/commands/using/tune2fs](http://www.commandlinefu.com/commands/using/tune2fs)

---

### Post by charlescarroll1 on 2012-10-10
> **GeForce 9500GT said:**
> There must be a space between tune2fs and -c. It should be:
[B]sudo tune2fs -c # # # / dev / ***
[/B]
Where:
###  is the interval of checking
***   is the partition which has to be checked/changed
 
 
 
 

 
Read these sites:
[http://oreilly.com/linux/command-directory/cmd.csp?path=t/tune2fs](http://oreilly.com/linux/command-directory/cmd.csp?path=t/tune2fs)
[http://linux.about.com/library/cmd/blcmdl8_tune2fs.htm](http://linux.about.com/library/cmd/blcmdl8_tune2fs.htm)
[http://www.unixtutorial.org/commands/tune2fs/](http://www.unixtutorial.org/commands/tune2fs/)
[http://www.commandlinefu.com/commands/using/tune2fs](http://www.commandlinefu.com/commands/using/tune2fs)

I cut & pasted the command you posted and it worked. This is the output:
```
chuck@5P4C3:~$ sudo tune2fs -c # # # / dev / ***
[sudo] password for chuck: 
tune2fs 1.42 (29-Nov-2011)
tune2fs: option requires an argument -- 'c'
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
	[-i interval[d|m|w]] [-j] [-J journal_options] [-l]
	[-m reserved_blocks_percent] [-o [^]mount_options[,...]] [-p mmp_update_interval]
	[-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
	[-M last_mounted_dir] [-O [^]feature[,...]]
	[-E extended-option[,...]] [-T last_check_time] [-U UUID]
	[ -I new_inode_size ] device

```

I hate to sound like a jackass, but what did I just do here?


Thanks for the sites, too!

---

### Post by charlescarroll1 on 2012-10-10
I restarted my system and it is still running a disk check.

BTW, thanks for helping a guy out.

---

### Post by GeForce 9500GT on 2012-10-10
Explaination:
**sudo tune2fs -c # # # /dev/ *****
**Where:**
**### is the interval of checking**
***** is the partition which has to be checked/changed**
 
### indicates the interval after how many restarts a partition should be checked. If you change ### into 100, this means that after every hundredth boot a check will be performed. You must fill in a number here higher than 30. The higher the number, the more boots/restart before performing a check.
 
*** indicates the partiton of which the interval must be changed. Here you fill in sda1 or sdb1 or sdb2 or sda2 depending of how your disk is partitioned. 
 
So if you want to change the interval of your first partition of your first disk to 500, the command should be:
**sudo tune2fs -c 500 /dev/sda1**

---

