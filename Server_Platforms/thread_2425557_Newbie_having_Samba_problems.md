---
title: "Newbie having Samba problems"
date: 2019-08-26
forum: Server Platforms
---

### Post by brisingre on 2019-08-26
I'm trying to use Ubuntu for a home fileserver. I have no real linux experience.

It's nothing at all fancy -- just a software raid1 on a pair of giant drives, with some shared folders I can access from the other machines (mostly Windows) on the network. 

I installed the server flavor of Ubuntu, but installed Ubuntu Desktop with apt-get since I'm a scrub and like a GUI when I can. 

I used mdadm to set up the raid1, then used the GUI "Disks" utility to format it as EXT4 and change the mount settings to mount on startup to somewhere relatively easy to type (/mnt/memory_alpha:mirror_a).

I installed samba, and set up some shares on this disk. (I set up one for the root of the disk as an experiment, and one for my video library, so far.)

I added them as network folders in windows, it connected, I started copying stuff over. Everything seemed to be working.


A few hours into the big copy, Samba died. Restarting smbd didn't fix it, but eventually rebooting the server did. Since then, it has happened several times since. I can't even keep it up for 24 hours without it breaking, usually. 


After Samba dies:
-I can still ping the server and SSH into it so it isn't the network connection dropping.
-The raid filesystem seems to be fine, it's still mounted, the files are still there, etc.
-The smbd services still seem to be running.
-Connections from windows to the share time out very slowly.
-Restarting smbd takes an unusually long time.
-Restarting smbd doesn't fix the issue, but it does kill any connections Windows is waiting for a timeout on instantly -- which suggests something we already sort of knew, that Samba is running and accepting connections, but not handling them properly. 
-Reboot hangs trying to stop samba, hangs even longer and eventually fails to unmount the software raid, eventually spits out a bunch of stuff like this: "systemd-shutdown[1]: Sending SIGKILL to PID 6109 (smbd)" and eventually "systemd-shutdown[1]: rebooting" but it never finishes shutting down or reboots. I have to use the power button.

Restarting smbd and rebooting the server both work correctly and at reasonable speeds before I lose the share, so I think it's connected to this failure. Sadly, I have no real idea what is actually failing. Until I try to reboot, there's no obvious evidence on the Ubuntu side that anything is wrong at all. And all Windows knows is that the share is no longer available.

Does anyone have any idea what might be going on? 

I freely admit I'm in a little bit over my head here -- I don't even know where Samba keeps its log files, much less how to read one, and I'm not 100% sure it's a Samba problem and not an mdadm problem, a networking problem, or even a Windows problem. 

Thanks for your help,

-Lou

---

### Post by brisingre on 2019-08-27
A little more info:

I found Samba's logs, nothing promising but I've increased the log detail to 2, maybe I'll see something when it happens again.

When Samba breaks, it is definitely broken in the same way for any machine that tries to connect. It isn't a problem with the windows machine I'm connecting from.

Once this is broken, I can't umount the drive. So it's not just reboot  that has this problem, I just can't unmount the drive at all once it is  messed up. Perhaps this is an mdadm issue or a sata driver issue or something after all.

Once this is broken, I see a bunch of different smbd processes in gnome-system-monitor, that I can't kill no matter what I do. When it is working I see only one smbd process, which appears to respond to kill normally.

---

### Post by slickymaster on 2019-08-27
Thread moved to **Server Platforms** for a better fit

---

### Post by brisingre on 2019-08-27
Thanks! 

One more detail -- if I unmount from the GUI disks utility rather than using umount it gives me "Error unmounting /dev/md127: target is busy (udisks-error-quark, 14)". This error is always thrown twice, presumably once for each physical disk in the RAID-1 Array I am trying to unmount.

It seems that error is most often caused by trying to unmount your root partition, but my root partition is on an entirely different drive, so that can't be the issue.

I can umount with -l, but I can't mount the disk again afterwards.

It's happened again, so I have some logs if anybody wants to see them. I didn't see anything obvious but I don't know what to look for.

---

### Post by LHammonds on 2019-08-27
Samba tends to be very stable on a stable system.  You might want to run diagnostics on your hard drives and array to see if you have a failure condition.

LHammonds

---

### Post by brisingre on 2019-08-27
Thanks for replying! 

Is there anything more specific I should do than unmount everything I can and fsck -A? I'll do that as soon as this copy is completed.

The physical drives are brand new but that certainly doesn't mean there couldn't be a fault. It is more likely that I screwed up the array somehow.

---

### Post by brisingre on 2019-08-27
Ran, or tried to run, fsck. Not sure if it did anything, I was expecting more output from it than I got.

Used gparted to repair it and that definitely did its thing, produced a log, etc. I don't think it found anything major but maybe it fixed it, or maybe fsck already fixed it silently and then there was nothing to fix... I'll know in a few hours if it's crashed or in a day or two if it hasn't.

---

### Post by brisingre on 2019-08-27
9 hours -- so far, so good.

---

### Post by brisingre on 2019-08-29
Had another crash today but was definitely different -- this has made a big difference to stability.

---

