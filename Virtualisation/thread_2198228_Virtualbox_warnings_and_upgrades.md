---
title: "Virtualbox warnings and upgrades"
date: 2014-01-07
forum: Virtualisation
---

### Post by alphaamanitin on 2014-01-07
Hello,

I run Xubuntu 12.04 LTS AMD64 and have virtualbox, which I use to run windows 7.  I keep getting warnings about updating to 4.2 or above versions of virtualbox.  It states that updating will break the existing virtualbox package.  Seems to be a pretty common issue, and most suggest uninstalling virtualbox and reinstalling.  I cannot find a clear, 100% clear, answer so maybe some one here knows: Can I uninstall virtualbox and reinstall it, keeping my guest session of windows 7?  I have searched but most seems to be about removing the guest and virtualbox, not updating.

Thanks,

AlphaA

---

### Post by QIII on 2014-01-07
Hello!

Where did you save your virtual disk?

Yes, you can uninstall and reinstall as long as you don't delete that virtual disk.  You will have to set up a VM again, pointing to that virtual disk.

---

### Post by JKyleOKC on 2014-01-08
> **alphaamanitin said:**
> Can I uninstall virtualbox and reinstall it, keeping my guest session of windows 7?The best answer I can give you is "Maybe."

If you really mean the currently running guest **session** then it becomes "Probably not." The reason for so many of the warnings, including several that I myself have posted, is that some of the changes made in newer versions seem not to be compatible with saved sessions or snapshots.

If, however, you habitually shut down the guest and re-boot it next time you use it, then the answer becomes "Almost certainly." I have about a dozen guest VMs of WinXP and Win2K, and every one of them has survived perfectly if shut down before doing a version upgrade; on the way to discovering this, I found that I could use the "Discard" button to get rid of saved sessions when the new version refused to load my guests. I don't know yet whether this is also the case for snapshots, since most of my VMs don't use them -- but my normal operation is to save the session and thus avoid the boot-loading delay next time I need the VM.

It's **not** necessary to create new VMs for the old virtual disks, in my experience. The VMs themselves survive the process just as do the virtual disks, if they are located in the default place: a hidden subdirectory of your home directory prior to version 4.0, or a visible subdirectory in $HOME for newer versions (my own installations use both places); uninstalls and reinstalls don't erase anything from your $HOME area unless you're reformatting the entire host disk.

---

### Post by joe_beasley on 2014-01-15
uninstall the old.  install the new.  All of your VMs and settings will still be there.

---

### Post by howefield on 2014-01-15
I'm a fan of using newer software, yes sometimes there are regressions or new bugs but generally speaking I prefer newer so I would want to upgrade, however if everything is working for you it is possible to switch off/change the update notifications.

The default is to check every day, but you can alter how often the software checks for updates and what it checks for via the Virtualbox preferences.

---

