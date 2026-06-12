---
title: "Analyze forced reboot"
date: 2010-09-15
forum: Server Platforms
---

### Post by ikarusX3 on 2010-09-15
Hi,

I run an ubuntu server installation on an atom platform. This has been running since 8.10 and has since been updated to the newest versions, but i intend to stop at 10.04 and upgrade to LTS releases only.

Every update has brought its own little issues, but after some slight tweaking the system has been running smoothly again.

After i experienced some reallocated sector notices from the not-24/7-certified harddisk, i replaced it with a 24/7 capable one (2.5'') and cloned the old system onto it.

This is where the problems start. I experience intermittent reboots of the machine. Before the last hardware change, the system had ~100d of uptime, already running 10.04. I wouldnt just pin it on the hard drive, since i have changed a couple of additional stuff, namely spindown scripts for the 3.5'' data drives, and my main question is:

How do i find out what caused the reboot, like a crash dump or the last run activity or system call?

And one more small question:

I mount my drives using their UUIDs, and after each reboot the drive identifier changes, e.g. my datadrive has sdc and after a reboot its sda. This is annoying since some scripts interact with the drive identifier, requiring me to change the scripts following a reboot. Can this be hard-mapped somehow?

Thanks in advance

---

### Post by CharlesA on 2010-09-15
The only way to "hard map" drives is to use UUID. What sort of scripts are you running that require the /dev/sdyx designation?

---

### Post by ikarusX3 on 2010-09-15
A script that monitors hard drive access and issues a standby command via hdparm if no such access happened for a specified amount of time.

Im currently looking how hard drive spindown behaves when let alone by itself, thus not using any of these scripts, so the mapping is not an issue. But investigating the reason for the reboots (roughly every 7 days, but at different time of day) is more important right now.

---

### Post by CharlesA on 2010-09-15
I looked into seeing if there was a log for why a machine is rebooted, but couldn't find much. If it's happening every 7 days, do you have a something running in cron that would cause a reboot?

Best thing you could do is as soon as it reboots, check the logs for around the time it rebooted.

You can check the exact time it went down by running this:

```
last -x | grep reboot
```
or
```
last -x | grep shutdown
```

As for the script, it looks like hdparm doesn't like to use the UUID, so you could try adding something like this into the script to go off a label of each drive:

```
#!/bin/bash

echo -e "Valid devices are: label1, label2, label3, label4."
read -p "Enter the device you wish to scan: " -a NAME
DEV=`blkid /dev/sd?? | grep $NAME | cut -c1-8`
echo $DEV
```

That'll grep whatever you input and strip everything but the drive designation out.

---

