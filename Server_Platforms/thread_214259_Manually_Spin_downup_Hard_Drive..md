---
title: "Manually Spin down/up Hard Drive."
date: 2006-07-12
forum: Server Platforms
---

### Post by eldaria on 2006-07-12
Hey guys.

I have a server set up in my house, it has a total of 4 hard drives.
3 of them are nice and Silent, and can hardly be heard..
The fourth one is very noisy.

The thing is this drive is only used for backup so I want to spin it down when not used.

Basically I want to make a script that runs once every day.

Spin up harddrive.
Mount partition.
Run backup.
Unmount partition.
Spin down drive.

I figured how to do all steps except the spin down/up, i can only find software like hdparm and noflushd, but they are both timer based.

is there a utility that can flush cache to drive and then spin it down?

Regards.
Brian

---

### Post by jurkki on 2006-07-12
i'd say hdparm does the trick, not sure though..

```
hdparm --help

```
```

 -f   flush buffer cache for device on exit
 -y   put IDE drive in standby mode
 -Y   put IDE drive to sleep


```

---

### Post by MJN on 2006-07-12
What's wrong with the spindown function being timer based? Just set it to 1 minute, or whatever, and your backup will wake it up, do it's stuff, and then the drive will go back to sleep 1 minutes after.

This also has the advantage that should anything else wake it, e.g. you accessing it, updatedb doing its daily scan etc, it'll then go back to sleep again.

Or am I missing something?

Mathew

---

### Post by eldaria on 2006-07-12
Oh I missed those features of hdparm.
It works perfectly, when mounting the drive it spins up.
Just what I needed.

The reason i do not want to use timer is to avoid too much spin up/down, since it will shorten the life time of the drive.

Also it should be used only for backup, therefore it will not even be in fstab, only manual mount.

---

