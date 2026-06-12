---
title: "ZFS and boot-repair"
date: 2014-07-05
forum: Server Platforms
---

### Post by daniel163 on 2014-07-05
Hi all! I know I'm new here, so please take pity on me!

I'm running Ubuntu Server 12.04 LTS Server where I was running a NAS off this box on two separate from the boot drive 2TB ZFS drives successfully for over a year. Recently I did an update, and didn't check any compatibility before performing them like a novice. Upon restart I had some VERY funky behavior. Half the services on the box would not run!

I tried manually restarting one more time after about 20 minutes, and suddenly my 1024x768 monitor was telling me that whatever was being displayed was "Out of Range" and I had 0 functionality out of the machine! :(

I tried booting to a live disk, installed boot-repair, and selected to run the recommended suggestion before removing my ZFS drives like an idiot. I saw the window hit SDB after SDA (the legitimate boot device), and immediately panicked and closed the window. Hopefully stopping the process before it hit SDC. I ran the process again with both ZFS drives removed and manually selected SDA. Walla! I could get back into my install of Ubuntu Server on restart after plugging all drives in again!

Except.... uh oh, now I'm getting no pools found from "zfs list", "zpool list", and "zfs status"! $41T!!! The only command that would respond was to force import the zpool by name only, telling me it failed! In a failed attempt to gather knowledge on the problem I think I further complicated the problem by exporting the disk.. successfully, for whatever reason that worked.

Somebody please tell me I did not lose years of work and backups! Help, please! What can I do to restore the data! I did some sort of ZDB command that seemed to claim my data was intact, but... how can I get to it?! What information can I give to you to help me?

---

### Post by lukeiamyourfather on 2014-07-07
Try reinstalling ubuntu-zfs as there was recently an update rolled out. From there it will be easier to troubleshoot. Also what is the configuration of the pool?

---

