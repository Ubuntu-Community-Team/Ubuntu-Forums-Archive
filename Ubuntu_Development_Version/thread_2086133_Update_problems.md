---
title: "Update problems"
date: 2012-11-19
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2012-11-19
Unable to apt-get update most of today with amd64 on Acer 5253 notebook.  I've got it plugged into an external keyboard and monitor, and usually have a wired network and wireless both active since sometimes I do live boots and don't want to bother setting hidden wireless WPA security.  Been doing this for a year O.K.

Today apt-get update gets all screwed up trying to resolve the sources.list entries.  Then even screwed up Firefox accessing this forum.  Refresh failed.

Tried disabling the wireless no help.  So shut down altogether.

Booted up, disabled wireless first, then apt-get update running O.K., forum O.K., and Firefox has no problem accessing tabs.

?

Of course when both are active and I've got the problem, network is screwed up, hence can't do a ubuntu-bug network-manager since it can't log onto launchpad.....

---

### Post by cariboo on 2012-11-19
Moved to a thread of it's own, as this post had nothing to do with the thread it was in.

---

### Post by jerrylamos on 2012-11-20
amd64 Kernel 3.7 either wireless or wired worked, but not both together.  First Ubuntu kernel that has had that problem since I bought the Acer 5253.  The kernel/network manager must be getting screwed up on what it is doing with which.  I don't know how to submit an ubuntu-bug if the network isn't working.  Catch 22.

---

### Post by zika on 2012-11-20
> **jerrylamos said:**
> amd64 Kernel 3.7 either wireless or wired worked, but not both together.  First Ubuntu kernel that has had that problem since I bought the Acer 5253.  The kernel/network manager must be getting screwed up on what it is doing with which.  I don't know how to submit an ubuntu-bug if the network isn't working.  Catch 22.Maybe this procedure from another thread could help You...
[http://ubuntuforums.org/showpost.php?p=12361375&postcount=17](http://ubuntuforums.org/showpost.php?p=12361375&postcount=17)

---

### Post by jerrylamos on 2012-11-20
amd64 Kernel 3.7 either wireless or wired worked, but not both together.  First Ubuntu kernel that has had that problem since I bought the Acer 5253.  The kernel/network manager must be getting screwed up on what it is doing with which.  I don't know how to submit an ubuntu-bug if the network isn't working.  Catch 22.

---

### Post by zika on 2012-11-20
> **jerrylamos said:**
> amd64 Kernel 3.7 either wireless or wired worked, but not both together.  First Ubuntu kernel that has had that problem since I bought the Acer 5253.  The kernel/network manager must be getting screwed up on what it is doing with which.  I don't know how to submit an ubuntu-bug if the network isn't working.  Catch 22.#1 is with wired and #3 is with wireless... ? ;)

---

### Post by cwsnyder on 2012-11-20
I take it that you are running Ringtail, since you are running the 3.7 Linux kernel?  Or did you add it to your previously working package?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070993](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070993) looks like where you should add your report.

You may also want to look at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1077822)
and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1078984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1078984)

---

