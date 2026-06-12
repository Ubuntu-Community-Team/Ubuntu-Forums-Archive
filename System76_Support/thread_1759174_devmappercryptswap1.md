---
title: "/dev/mapper/cryptswap1"
date: 2011-05-15
forum: System76 Support
---

### Post by cfrancoec on 2011-05-15
Hello guys! thanks for the attention :)
Okay, this is my problem:
was normally booting when the start up splash screen goes black and nothing happens.
I reboot the pc and when it's rebooting the splash screen of Ubuntu appears with a text down there that says:
> /dev/mapper/cryptswap1 is not ready You can skip or manually mount it. Pressing s or mI pressed S & M while the screen was black, but nothing happens.
I read in this thread [http://j.mp/kUKZM1](http://j.mp/kUKZM1) that the only way its to reinstall it. It's true? :confused:
Now I'm running in failsafe mode, or something like that :tongue:
Please help!
Sorry about my bad English, im from Argentina :)

---

### Post by Morbius1 on 2011-05-15
This thread might be applicable to your situation - not sure: [http://ubuntuforums.org/showthread.php?t=1754867](http://ubuntuforums.org/showthread.php?t=1754867)

---

### Post by cfrancoec on 2011-05-15
> **Morbius1 said:**
> This thread might be applicable to your situation - not sure: [http://ubuntuforums.org/showthread.php?t=1754867](http://ubuntuforums.org/showthread.php?t=1754867)
No =/
Thanks, i will format =/

---

### Post by Dave_L on 2011-05-15
[Ubuntu 10.04]

When I get that message, I wait. After a few seconds, booting continues normally, and /dev/mapper/cryptswap1 seems to mount properly:

```
$ sudo swapon -s
Filename				Type		Size	Used	Priority
/dev/mapper/cryptswap1                  partition	1952480	0	-1
```

```
$ sudo parted /dev/mapper/cryptswap1 unit co print unit s print
Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 1999MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  1999MB  1999MB  linux-swap(v1)

Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 3904979s
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End       Size      File system     Flags
 1      0s     3904978s  3904979s  linux-swap(v1)
```

It doesn't show up in /etc/mtab, but I figured that's normal for the swap file.

---

### Post by isantop on 2011-05-16
I think your fasted option right now would be to reinstall. I would recommend against encrypting your home partition as well unless you absolutely need it, as it causes a lot of issues and leads to even more.

---

### Post by thunderriver on 2011-05-28
Well, when it fails to mount, are you actually experiencing issues?
Even in Natty, I see it all the time, and I have no trouble saving files.
Encrypting home directory is a must for me, so to say that the easiest fix is to lower your standard on security is...by disabling home dir encryption... well, not for me.

But I have to say, if it is truly a bug, it should be fixed. That's why we support open source in the first place. If security has to be compromised, we all should just go back to Windows. Plain and simple

---

