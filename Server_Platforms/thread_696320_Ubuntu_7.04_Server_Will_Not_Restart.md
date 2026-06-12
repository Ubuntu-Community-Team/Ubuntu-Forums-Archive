---
title: "Ubuntu 7.04 Server Will Not Restart"
date: 2008-02-13
forum: Server Platforms
---

### Post by funtime on 2008-02-13
I have recently installed Ubuntu 7.04 Server on my Dell PowerEdge Server at my home, and now the system will not restart. The only way for me to get it to actually restart the machine is to hold down the power button until it restarts. I originally had many problems installing the operating system on the system, and now that I have gotten it I am having this problem.

I get the following message on the screen when I attempt to restart the system.

 * Terminating all remaining processes...     [OK]
 * Sending all processes the KILL signal...     [OK]
 * Unmounting temporary filesystems...     [OK]
 * Deactivating swap...     [OK]
 * Unmounting local filesystems...     [OK]
 * Will now restart
 [9768.447849] Restarting system

After going through all this, it sits at the Restarting system message until I force a shutdown using the power button. Any ideas, or help that can be provided regarding this would be very much appreciated. Please let me know if you need any more information.

---

### Post by funtime on 2008-02-13
As an update. When I try to perform a full shutdown, I get pretty much the same problem.

 * Terminating all remaining processes...     [OK]
 * Sending all processes the KILL signal...     [OK]
 * Unmounting temporary filesystems...     [OK]
 * Deactivating swap...     [OK]
 * Unmounting local filesystems...     [OK]
 * Will now halt
 [123.614818] Power down.

It just sits there after getting this far, and never actually shuts down the system.

---

### Post by p_quarles on 2008-02-13
What commands are you using to shut down/reboot? I ask, because some commands are symlinks, and it's possible they're broken.

---

### Post by funtime on 2008-02-13
Thanks for responding. Here are the commands I have been using. They all provide the same output when trying to shutdown/reboot.

sudo init 0 - Shutdown
sudo init 6 - Reboot
shutdown -r now - Reboot

---

### Post by p_quarles on 2008-02-13
Hmm. Well, try these:
```
sudo reboot
sudo shutdown -P now
sudo poweroff
```
Dunno if those will help, but I have another idea if they don't.

---

### Post by funtime on 2008-02-13
Those didn't work either. I'm trying to upgrade the kernel, but I've never done that. Any ideas on how to do that? Thanks.

---

### Post by p_quarles on 2008-02-14
After hunting down the old thread that I had in mind (the "other idea"), I realized that was a different issue.

Upgrading the kernel should normally happen automatically via normal APT upgrades. If you want to try an alternate kernel, you would have to install it manually (again using APT). If you meant compiling the kernel, that's a bit more involved, and is rarely needed these days. If nothing else works, though, it's worth a shot.

---

