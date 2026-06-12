---
title: "WoW"
date: 2020-09-30
forum: Ubuntu, Linux and OS Chat
---

### Post by xinuzi on 2020-09-30
Very satisfied about the automatic install of Ubuntu with Lubuntu LXQT 20.04 over the existing Lubuntu version on one of my laptops.

The only thing I really had to set back was my previous personal desktop background.

I sometimes wonder how you excellent programmers put it all together :-)

---

### Post by ActionParsnip on 2020-09-30
It is prety spectacular. All disparate teams efforts being brought together to make a functional whole

---

### Post by howefield on 2020-09-30
Thread moved to the "*Ubuntu, Linux and OS Chat*" forum.

---

### Post by xinuzi on 2020-10-01
Of course such a big install almost never goes without a minor afterfix here and there.

Like the recurring 'system program error - send report' popup after each start up, reboot.
Even if you send the report the alert keeps appearing.

Fix with: 

> sudo rm /var/crash/*

The next reboot after that the 'system program error' disappeared, but a bluetooth error alert appeared instead.

The solution here was to disable 'ShowConnected' (at startup) in the system tray.

I had kept the former /etc/sysctl.conf file. Maybe it had sth to do with that. Or not.

---

### Post by guiverc on 2020-10-01
Hopefully you'll continue to not have problems.

The Lubuntu team are aware that some issues can occur with certain packages, thus why the [Lubuntu 20.04 releases notes]("https://lubuntu.me/focal-released/") say

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. **Doing so will result in a broken system.** If you are on 18.04 or below and would like to upgrade, please do a fresh install.

They (Lubuntu team) did write documentation for upgrades in the 18.04 -> 18.10 cycle, but these weren't even published (*you need to use a search engine to find them*) as problems varied on the changes made by users to their systems, plus packages added, resulting in the upgrade-process being *unsupported*.

I'm glad it worked for you :)

---

