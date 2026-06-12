---
title: "Hdparm -y causing resync"
date: 2012-09-20
forum: Server Platforms
---

### Post by Frankincense93 on 2012-09-20
Hi guys.

I have been trying to make my home server to sleep my external hdds when it turns of (does a nightly shutdown every day). The external hdds are in a 'raid box' in clear-raid so that I can see each drive individually. To make these drive sleep i have tried lots of different commands, including sg_start, sdparm and hdparm. hdparm is the only command that seems to make a difference.
But when I use hdparm -y /dev/sdb and hdparm -y /dev/sdc myself it works fine and both drive spindown. But when I do this in a shell script only one of the drives spin down, and when the server restarts in the morning it has to completely resync one of the drives as it seems to think something terrible has happened!

Any ideas?
I can't give any syslog or dmesg messages atm as im not at home, but I can do later if necessary.

---

### Post by rubylaser on 2012-09-20
Have you tried to use hdparm's -S option?  That's the easiest way to spin down disks after a certain amount of idle time.  Like this.

```
hdparm -S 242 /dev/sdb
```

That would spin a disk down after an hour of inactivity.  If you'd like to read more, I have a pretty straight forward [tutorial]("http://zackreed.me/articles/60-spin-down-idle-hard-disks") to do this.  These directions work great with mdadm if that's what you're using to manage your RAID array.

---

### Post by Frankincense93 on 2012-09-20
Well, I don't really mind them being spin-up if they are idle, I just need them to shutup every night when the box turns off (as its in my room and the noise is a bit annoying)

So I'm not sure how useful the -S will be :/

Interestingly when I spin-down the drives, the top drive flashes red (its a sharkoon 5bay raid box) which suggests that the hdd has gone into error/something bad has happened (which may explain the resync if it thinks the drive is corrupted or w/e). 

This is very frustrating, when I get home I will see if I can get some dmesg/syslog messages that might help

---

### Post by Frankincense93 on 2012-09-21
Removed as it makes more sense to put it in this thread - [http://ubuntuforums.org/showthread.php?t=2050525](http://ubuntuforums.org/showthread.php?t=2050525)

---

