---
title: "Ubuntu critical failure, how do I collect information?"
date: 2015-03-02
forum: Ubuntu Studio
---

### Post by Matthew_Johnston on 2015-03-02
Hello forum,

I had a horrible crash a few days ago and have been trying to fix it. I'll give as much info as I can, but I would like to know what I should collect so that I can get some hard hitting tech support. I mean, I could just wipe the partition and reinstall the OS, but I would like to try to fix it.

SO... here goes.

I am running Ubuntu Studio 14.10, kernel 3.16.0-31 (alternating between generic and low latency)
I have the typical problem with the nVidia driver, where when I use my touchpad, the OS completely freezes, until I [Ctl]-[Alt]-[F1-6] to a VM and back to F7 to get back to my normal workflow. The only way I know to fix THAT problem is to use the open source driver. That's not huge.
I am triple booting my system, Lenovo Y510P, with Ubuntu Studio, Lubuntu, and Windows 8.1. I am currently writing this from Lubuntu. It and Windows seem unaffected.
At the time of the crash, I was simply using Firefox. I don't remember what was open, but probably just Facebook.
The computer froze as described above, but before I could switch VM, the desktop environment reverted to CLI, and something appeared about the environment failing. I did not record this. My computer would not respond to anything, including magic Sys-rq. I think there was a kernel panic, but I did not check because I didn't know what that was at the time. I am now quite familiar. So I hard shut down my computer.
If I try to boot into Ubuntu Studio from grub, low-latency or generic kernel, I get kernel panic immediately. I can boot into the recovery mode and from there get into the GUI, but I can only access XFCE or VM, Unity fails to load.
I have tried reinstalling lightdm, XORG, and also tried substituting lightdm with gdm, all of which failed to fix anything.
I ran Memtest from a recovery disk, everything worked perfectly.
I tried repairing broken packages from dpkg in the recovery menu a few times. Nothing changed.

At this point I am probably just going to reinstall my system partition (my home directory is on a different partition) unless you wonderful people can help me fix it, but I want to know if I should save any logs or if any data I have on my bogged up system would be useful for developers.
ANY help would be useful. I am a novice-intermediate user, I learn fast and understand the concepts and language of how to use the system. I just don't know all the ins and outs of system logs and commands I may have to use to retrieve any useful data.

Thank you all in advance!

---

### Post by marseille2 on 2015-03-10
It may be a little late, but check the logs to pinpoint problems. Kernel Panic is an evil word I seriously hate, so it's always good to be sure your hardware is safe. If you can still access your files, see what's going in the kern.log and syslog:

```
 $ cd /var/log 
```

```
 $ more kern.log 
```

see beginning of the kern.log:

```
$ head kern.log
```

[INDENT=4]read first x number of lines of kern.log (just change the number after the -n switch, same for subsequent commands):

```
$ head -n 75 kern.log
```
[/INDENT]

end of kern log:

```
$ tail kern.log
```

[INDENT=4]read x amount of lines:

```
$ tail -n 75 kern.log
```

[/INDENT]
 [SYSLOG]("http://linux.die.net/man/3/syslog"):

```
 $ more syslog
```

---

