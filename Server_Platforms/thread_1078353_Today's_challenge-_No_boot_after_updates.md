---
title: "Today's challenge- No boot after updates"
date: 2009-02-23
forum: Server Platforms
---

### Post by mistypotato on 2009-02-23
Hi Ububtu fans!

Ok, this mornings noobie challenge is getting my server to boot after updating.
I just installed the latest updates and now I cannot boot at all.
I am not able to boot into recovery mode.

Here's what I'm getting.....

[COLOR="Red"]Alert! does not exist.  Dropping to a shell!
/init: linie 191 cannot open /dev/console: no such file
Gave up waiting for root device. Common problems:
- Boot args (Cat /proc/cmdline)
- Check root=(did the system wait long enough for the right device?)
- Missing modules (cat /proc/modules; ls /dev[/COLOR]



Then it just repeats this indefinitely.

Applications now being accepted for help with this issue :popcorn:


thx as always

---

### Post by cdenley on 2009-02-23
Boot to a livecd, mount your HD's filesystem, and run this command
```

ls -l /media/disk/dev/console

```
Replace /media/disk with the mount point for your HD's filesystem.

Are you sure those updates completed successfully and didn't have any errors? I would be cautious of hardware problems with a problem like this.

---

### Post by mistypotato on 2009-02-23
thanks cdenly.

I'll try that.  How can I display the current mount point from the command line ?

in other words....

How can I list all my hard disks partitions

---

### Post by mistypotato on 2009-02-23
> **cdenley said:**
> Boot to a livecd, mount your HD's filesystem, and run this command
```

ls -l /media/disk/dev/console

```
Replace /media/disk with the mount point for your HD's filesystem.

Are you sure those updates completed successfully and didn't have any errors? I would be cautious of hardware problems with a problem like this.


I did that, it returned....

**crw------- 1 root root 8, 1 Feb 23 10:18 /dev/sda1**

What was it supposed to do ?

---

### Post by cdenley on 2009-02-23
I  don't think you ran the right command. Try this
```

ls -l "`mount|grep /dev/sda1|cut -d \  -f 3`/dev/console"

```

---

### Post by mistypotato on 2009-02-23
hi cd,

that command results in ...........

cannot access "your command"  no such file or directory



am I typing it in wrong maybe ?

---

### Post by mistypotato on 2009-02-23
I have opted to attempt to restore my 8.10 server installation from an earlier Mondo Archive backup.

I will lose a considerable amount of configuration on my web sites but I should have made more frequent backups....but the time spent with that may be less than the time spent on repairing the broken server.

FYI.... it broke after I did updates today but I hadn't done updates for over a week so there were quite a few to be applied.

If all goes well, I will be back up and running with only the need to reconfigure Apache and my websites in about an hour.

If this fails, I will simply reinstall 8.10 server and start again.  It is a learning experience.  I only wish my server wasn't down.

Since I'm so new to Linux, and setting up a server is a complex proposition...and because I'm more familiar with Windows at this point, I'm going to go ahead and simultaneously set up a parallel WindowsXP server since I had already bought an OEM copy from Newegg anyway.

One must always have a BACKUP plan :p

I love ubuntu and this will give me more "time luxury" to take my time and carefully set up my ubuntu server which will ultimately replace the WinXP server.  Thanks for your help :KS


Oh, it's only the server that's down.  My 3 other Ubuntu PC's are doing fine.

---

### Post by mistypotato on 2009-02-23
The Mondo Restore was successful.

My loss was minimal.  I just need to set my websites back up (about 1 day) and I'm back in business.

I've mentioned before in other posts that I use MondoRescue and again, it has come through for me BIG TIME.

---

