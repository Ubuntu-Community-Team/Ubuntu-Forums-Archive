---
title: "locking up last couple days"
date: 2015-03-15
forum: Ubuntu Development Version
---

### Post by buzzmandt on 2015-03-15
I am experiencing the boots to terminal, login and use systemctl start sddm thing.

however

I am now getting a complete lock up on my computer after just a few minutes of running.

Failsafe doens't lock up, so I used failsafe to install e17 (just as a small window manager for a back up purpose). e17 also locks up just after a few minutes of running.  I have tried normal login and disable kwin, to no avail.  Right now the only thing that doesn't lock up is failsafe.

Any suggestions?

---

### Post by ventrical on 2015-03-24
It's an absolute mess after todays update/upgrade.  Has even blown out the network after update. This goes for systemD and upstart.  Also .. goes back several kernel upgrades. This on nVidia graphics . I will switch to Intel adapter.

---

### Post by ventrical on 2015-03-24
Switching that hdd with kubuntu install on it to a machine with Intel graphics did the trick.  It is like the nVidia adpater card (nouveau) blocked a bunch of updates that were waiting .. and it even re-installed the kernel headers. Now I have full desktop once again.  Either there is somthing terribly wrong with nouveau nvidia drivers or my hardware is bad .. yet everything else works on that one machine. 

```

       [FONT=monospace][COLOR=#000000]ventrical@ventrical-desktop:~$ uname -a [/COLOR]
Linux ventrical-desktop 3.19.0-10-generic #10-Ubuntu SMP Mon Mar 23 16:25:20 UTC 2015 x8
6_64 x86_64 x86_64 GNU/Linux 
ventrical@ventrical-desktop:~$  


[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by buzzmandt on 2015-03-24
Actually had my other do that about 4 weeks ago with ati graphics+drivers. very similar anyway. but my original post in this thread is on my laptop with intel video. fully up to date and will lock up in 30sec-minute.  odd. I'm just waiting it out before i do a reinstall..... still waiting lol

---

### Post by gunksta on 2015-03-25
I reinstalled upstart. Relying on systemd made it impossible for me to test other aspects of the system, so I gave up.

This isn't a snipe against systemd, but it isn't really working very well on my hardware yet. Seems to be a Ubuntu thing though. I can boot Fedora just fine.

---

