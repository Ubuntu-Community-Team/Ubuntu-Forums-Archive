---
title: "Remove /etc/vmware/not_configured to make VMWare Player work in Hardy"
date: 2008-07-01
forum: Virtualisation
---

### Post by scottywz on 2008-07-01
I had been having problems getting VMware Player 2.0.4 to run in Hardy.  It would install and configure OK, but when I ran it in terminal, it would say:
```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```
I saw [this post]("http://ubuntuforums.org/showpost.php?p=5131785&postcount=10") which mentioned a "vmware_not_configured" file.  At least for me, this file is /etc/vmware/not_configured and removing it solves the problem.

I really think this should be a sticky or something.

---

### Post by Andreas_DK on 2008-09-27
> **scottywz said:**
> I had been having problems getting VMware Player 2.0.4 to run in Hardy.  It would install and configure OK, but when I ran it in terminal, it would say:
```
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
```
I saw [this post]("http://ubuntuforums.org/showpost.php?p=5131785&postcount=10") which mentioned a "vmware_not_configured" file.  At least for me, this file is /etc/vmware/not_configured and removing it solves the problem.

I really think this should be a sticky or something.

I had the same problem with vmplayer 2.0.5 and Ubuntu 8.04. The "not_configured" file came again and again after reboot. It showed up, that I had two times a file vmware in rc2.d like S19vmware and S90vmware. Both linked to vmware in init.d. Removing one of them solved the problem (I removed S19vmware).
Best regards
Andreas

---

### Post by MartinG on 2008-11-15
The only trouble with this is that you lose the "safety check".  

This whole issue does all come down to start and stop scripts, it appears.  Building on the post by scananza in the following

[http://ubuntuforums.org/showthread.php?t=313362&page=2](http://ubuntuforums.org/showthread.php?t=313362&page=2)

I realized that the VMware install/configure process places K08vmware as well as S90vmware in /etc/rc2.d and for me at least this appears to be the problem.  I have now run the following two commands and that seems to sort it:

```
sudo update-rc.d -f vmware remove
sudo update-rc.d vmware defaults 90 08
```

The key difference from scananza's solution is that when/if you upgrade/reconfigure, you won't be left with K99vmware or S99vmware scripts lying around!

---

