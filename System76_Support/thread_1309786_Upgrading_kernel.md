---
title: "Upgrading kernel"
date: 2009-11-01
forum: System76 Support
---

### Post by jmwink on 2009-11-01
Hi all,

I know that I could probably find numerous threads out there in the general discussion, but I appreciate the helpfulness of the Sys76 community, so I'm going to start a thread here. 

I'd rather not do a complete upgrade to 9.10, feeling like things are working fine, and not worth risking any possible breakage. But, I would like to use the 9.10 kernel. I know there must be a way to just upgrade the kernel, but I don't really understand how to go about doing that. Any help would be much appreciated.

---

### Post by HotShotDJ on 2009-11-01
> **jmwink said:**
> I'd rather not do a complete upgrade to 9.10, feeling like things are working fine, and not worth risking any possible breakage. But, I would like to use the 9.10 kernel. I know there must be a way to just upgrade the kernel, but I don't really understand how to go about doing that. Any help would be much appreciated.I don't recommend doing this.  I tried it myself and it really messes things up due to some kernel level changes between Jaunty and Karmic.  You can, however, get many of the benefits of the 2.6.31.* kernel in the 2.6.30.* kernel, which is compatible with Jaunty.  BUT, if you decide to do that, you will lose automatic security upgrades as well as AppArmor.  Its really not worth it.  Consider doing a full upgrade to Karmic.  Give it a test using the LiveCD to make sure there is no major breakage.  I also recommend a fresh install, rather than an in-place upgrade.  Many people have reported no problem with in-place upgrades while some others claim that it has hosed their systems.  Also, with an in-place upgrade, you do not get the benefits of the ext4 file system (and those benefits alone are worth the upgrade! ext4 is FAST!).  As long as you have a full backup of your /home directory and your evolution settings (if you use evolution), then a fresh install is a rather painless procedure.  But as with ALL major upgrades with any software, the key words are "test, test, test!"  LiveCD's are a life-saver in this regard.

---

### Post by jmwink on 2009-11-01
Thanks for the reply. I actually spent all day demoing out a variety of ubuntu flavors, and I think I've learned my lessons about my computing needs and my computing priorities. The number of fresh installs of this and that are enough to make my eyes spin like pinwheels. 

I demoed 9.10 today, and ran into the ubiquitous power management bug. It was indeed, lightning fast, so I look forward to upgrading at a future date, when I have far fewer deadlines and other things to get done. For now I'll stick to the kernel I have; with Openbox, it runs plenty fast.

Thanks again!

---

### Post by Lee_Machine on 2009-11-02
If there is a kernel feature or functionality that is considered important then the Ubuntu Kernel maintainers will backport it. Meaning they will add it to an earlier kernel, and it will show up via Update Manager.

Make sure you have backports on if you want them.

System >> Administration >> Software Sources

In the updates tab check off Unsupported Updates (karmic-backports)

More than often kernel backports are new firmwares, and drivers that were added to the newer kernel. 

Backports also apply to all packages installed, not just the kernel.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)


[https://lists.ubuntu.com/mailman/listinfo/ubuntu-backports](https://lists.ubuntu.com/mailman/listinfo/ubuntu-backports)


Hope this helps :D

---

