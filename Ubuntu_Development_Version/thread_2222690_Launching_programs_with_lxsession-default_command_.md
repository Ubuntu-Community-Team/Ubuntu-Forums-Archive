---
title: "Launching programs with lxsession-default command causes system log-out"
date: 2014-05-07
forum: Ubuntu Development Version
---

### Post by DogMatix on 2014-05-07
Here's a good one for you that affects my 14.10 Lubuntu install and so far I have replicated this bug on a 14.04 Lubuntu install on the same machine and another machine with a 14.10 Lubuntu install.

It came to light when I enabled the right-click Openbox menu. Choosing any selection that has a lxsession-default command attached to it such as:
```
<item label="Calculator">
<action name="Execute"><command>lxsession-default calculator</command>
<startupnotify><enabled>yes</enabled></startupnotify>
</action>
</item>
```
causes a system log-out.

Also issuing the command, in a Terminal:
```
lxsession-default calculator
```
causes a system log-out.

This seems to apply to any program associated to lxsession-default

Launchpad:[ Bug 1316832](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1316832)

Ubuntu Forums: [Hardware thread addressing the same issue](http://ubuntuforums.org/showthread.php?t=2219915)

Anyone else getting this?

---

