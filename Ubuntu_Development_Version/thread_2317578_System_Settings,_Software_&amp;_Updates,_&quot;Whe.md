---
title: "System Settings, Software &amp; Updates, &quot;When there are security updates&quot; is grayed out"
date: 2016-03-17
forum: Ubuntu Development Version
---

### Post by unflavored on 2016-03-17
In System Settings, how do I enable automatic security updates?  I want to choose "Download and install automatically" but I can't select any option.

---

### Post by Frogs Hair on 2016-03-17
Could be a bug see linked thread. [http://ubuntuforums.org/showthread.php?t=2315649](http://ubuntuforums.org/showthread.php?t=2315649)

---

### Post by PaulW2U on 2016-03-17
> **unflavored said:**
> In System Settings, how do I enable automatic security updates?  I want to choose "Download and install automatically" but I can't select any option.
Known bug - [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1554099](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1554099) - that is being worked on by the developers.

---

### Post by unflavored on 2016-03-17
Thanks! This is the workaround that worked for me: ```
sudo rm /etc/apt/apt.conf.d/20auto-upgrades
```

---

### Post by mc4man on 2016-03-18
This is fixed in a software-properties-gtk update, package currently in proposed. The effect on current installs upon upgrade may vary.

As far as fresh installs that include the new packages it could be that the new default will be to auto download & install security updates.
If so & one prefers to manage themselves they'll have to change the option in Software & Updates > Updates, ect.

---

### Post by Brandon_MacEachern on 2017-01-22
I'm using Xenial which was installed just 2 months ago, 16.04.1..  This bug just happened, and the "fix" regarding removing 20auto-upgrades did not work for me, this option is still greyed out.

Was the official bug fix never actually backported to Xenial all this time?

---

### Post by MikeMecanic on 2017-01-23
> **Brandon_MacEachern said:**
> I'm using Xenial which was installed just 2 months ago, 16.04.1..  This bug just happened, and the "fix" regarding removing 20auto-upgrades did not work for me, this option is still greyed out.

Was the official bug fix never actually backported to Xenial all this time?

This bug is in 10periodic or migrates into 20auto-ugrades _**second line**_.  Removing the content of 20auto-upgrades (?) was never an issue here.  Not present in YY or ZZ.

```
sudo -i gedit /etc//apt/apt.conf.d/10periodic
```
or
```
sudo -i gedit /etc//apt/apt.conf.d/20auto-upgrades
```

---

### Post by aljosa2 on 2017-01-23
1)
When I click on 'Security & Privacy' icon, the entire settings window becomes unresponsive and grayed out for about 20 seconds.

2)
It seems to me that in my 'Security & Privacy' settings something is missing: 'Files & Applications'. Is this a bug?

3)
When I want to rename files or folders, I always get the following annoying notification that won't go away:

---

