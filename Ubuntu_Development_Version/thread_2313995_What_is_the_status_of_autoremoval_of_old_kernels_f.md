---
title: "What is the status of autoremoval of old kernels for 16.04"
date: 2016-02-17
forum: Ubuntu Development Version
---

### Post by BlueAZ on 2016-02-17
Hi,  I'm an Ubuntu user since 2011 on a 64-bit AMD system I built.  I usually upgrade to the latest LTS version and stick with it till the next.  That means lots of kernel version updates along the way, which causes boot problems on my rig.  I found out how to search & remove old kernel, header & image versions using Synaptic.  It works great & helps a lot.  I posted a thread about whether one could/should remove old Linux-Tools versions in 'General Help' but didn't get any useful responses.  So I experimented and found I could remove older Linux-Tools in Synaptic without problems.  That is the extent of my expertise in this area.

My post here is to address the status of this issue in 16.04 development.  If it's not already too late, it would be nice if the new version's updater could contain user-specified options for automatic removal of old kernels/headers/images/tools.  Like if I could specify that all such older than the most recent two versions (current + a backup option) would be automatically, safely and completely removed from my system.

I'm not knowledgeable enough to develop this feature myself, but would like to suggest it to the real heroes!

Thanks,   BlueAZ, USA

---

### Post by deadflowr on 2016-02-17
I've moved this post to it's own thread.
As the sticky posted into is for actual development news.

---

### Post by ian-weisser on 2016-02-17
Already included in the 16.04 version of unttended-upgrades (U-A).
It defaults to on. The new feature asks aptdaemon for the list of orphans at the start and end of it's run. Any new orphans are removed by U-A before it terminates.
This is different from U-A's existing autoremove, which remains and is still off by default.

If you are not running 16.04 yet, you can simply enable U-A's existing autoremove.
If you are running 16.04, you can enable still the existing autoremove, but probably won't see it do much because of the new feature.

---

### Post by grahammechanical on 2016-02-18
> If it's not already too late,

It is. If the developers have not already decided on doing something like this, then suggesting it now is months too late and this user forum is not the place to do it.

I have been running 16.04 since the first few days of the start of its 26 week development cycle. It has received many kernel upgrades over the weeks and I think that there is at least another kernel upgrade to come. I have run autoremove once and it removed some old kernels. And apt-get upgrade right now informs me that there are 3 kernels that can be removed by running sudo apt autoremove.

I do not have a separate boot partition. So, filling up /boot is not a problem for me. And I cannot test any automatic use of autoremove in a real life situation. So, the best advice I can give to anyone with a separate /boot partition (LVM & Encrypted installs? Yes?) is to regularly run

```
sudo apt autoremove
```

Regards.

---

### Post by Cavsfan on 2016-02-18
There is a bug that goes back to Trusty as well as Utopic, Vivid, Wily and Xenial 16.04. It even affected Mint 17 about autoremoving all kernels but one.
This is wrong and 2 kernels are what is expected to be kept, one for backup.

It has been stated by a developer (Jarnos) on the bug that it will eventually try to autoremove the one kernel you have left if allowed to do this.

I filed the bug at ian-weisser's suggestion. Here is the thread where I started the discussion: [http://ubuntuforums.org/showthread.php?t=2251168](http://ubuntuforums.org/showthread.php?t=2251168)

Here is the bug about **/etc/kernel/postinst.d/apt-auto-removal wants to remove all kernels except the latest one**: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1440608](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1440608)

Then there is the issue about when manually deleting a kernel or autoremoving it and the unnecessary need to reboot your system afterwards: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1458204](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1458204)

So, if keeping 2 kernels instead of just one is important sign on to the bug. Also, if you believe a reboot is unnecessary upon any kernel removal sign on to the other one.

Also there is a cron job Jarnos added (from the bug) to perform an autoremoval at startup and a new **/etc/kernel/postinst.d/apt-auto-removal** file to replace the one you have.

It works well and will allow keeping up to 3 kernels but no more than 3 as I tested that today and it wanted to autoremove the 4th kernel.

---

### Post by BazBear on 2016-02-19
> **grahammechanical said:**
> It is. If the developers have not already decided on doing something like this, then suggesting it now is months too late and this user forum is not the place to do it.

I have been running 16.04 since the first few days of the start of its 26 week development cycle. It has received many kernel upgrades over the weeks and I think that there is at least another kernel upgrade to come. I have run autoremove once and it removed some old kernels. And apt-get upgrade right now informs me that there are 3 kernels that can be removed by running sudo apt autoremove.

I do not have a separate boot partition. So, filling up /boot is not a problem for me. And I cannot test any automatic use of autoremove in a real life situation. So, the best advice I can give to anyone with a separate /boot partition (LVM & Encrypted installs? Yes?) is to regularly run

```
sudo apt autoremove
```

Regards.Is that a valid command? I only ask because I've always run ```
sudo apt-get autoremove
``` to remove old kernels.

---

### Post by deadflowr on 2016-02-19
> **BazBear said:**
> Is that a valid command? 
Yes it is.
At least for 16.04

---

### Post by grahammechanical on 2016-02-19
> **apt-get** is the [command line]("https://en.wikipedia.org/wiki/Command_line") package management tool supplied with the Debian package **apt**. APT searches its cached list of packages and lists the dependencies that must be installed or updated.

[https://en.wikipedia.org/wiki/Advanced_Packaging_Tool](https://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

When apt-get upgrade lists packages that are no longer needed it also advises to use apt autoremove to remove them. And it works as does apt-get autoremove

Regards

---

