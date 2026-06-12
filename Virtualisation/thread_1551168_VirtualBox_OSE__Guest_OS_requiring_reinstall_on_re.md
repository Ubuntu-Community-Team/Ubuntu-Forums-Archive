---
title: "VirtualBox OSE:  Guest OS requiring reinstall on restart, even after fully installed."
date: 2010-08-11
forum: Virtualisation
---

### Post by Kurtosis on 2010-08-11
I'm running Virtual Box OSE 3.1.6 from the repo on Ubuntu 10.04.  I've installed Ubuntu Server as a guest.  It was working fine until recently.

Previously I could work in the guest, then logout (of the guest) to the login prompt, then select Machine -> Close -> Power Off Machine to shut down the VM.  Then I could restart (the guest) and log back in and keep working.

Now however, every time I power down the guest that way (Machine menu -> Close -> Power off machine), the next time I start it, I get the OS installation menu instead of the login prompt.

Not sure what's changed, a recent update maybe (I tend to run Update Manager without first googling to check for regressions).  Anyone know what might be the problem?

---

### Post by Warthaug on 2010-08-12
Are you physically restarting the host?  If so, you may be having the same issue as I - the virtual box kernel manager not always starting properly.

The fix is easy; go to terminal, and type the command:
```
sudo /etc/init.d/vboxdrv start
```

Virtualbox should then run normally.

Bryan

---

### Post by Kurtosis on 2010-08-12
Thanks Bryan, though I'm not restarting the host, only the guest.  Edited original to clarify that.

And strangely, for my install it's /etc/init.d/virtualbox-ose start.  I don't have vboxdrv in init.d.  Same thing?

---

### Post by zenthanian on 2011-08-09
Try removing the ISO from the Devices menu... 
see [http://ubuntuforums.org/showthread.php?t=1716755](http://ubuntuforums.org/showthread.php?t=1716755)

---

