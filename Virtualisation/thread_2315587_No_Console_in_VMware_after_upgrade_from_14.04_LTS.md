---
title: "No Console in VMware after upgrade from 14.04 LTS"
date: 2016-02-29
forum: Virtualisation
---

### Post by Travis_DeLong on 2016-02-29
I have a VMware ESXi machine.
One of the vitual machines is Ubuntu 14.04 LTS.
I have been using Ubuntu inside ESXi for some time now.

About a week ago there was an update to the Linux kernel.  But I have been unable to install it.

In order to keep this machine updated it wants to install about 65 MB of packages related to Linux Kernel 3.19.0

If I install this I will soon have to revert back to a snapshot before this update.
After the update I can no longer Console into the VM.  All I get is a black screen.
The Ubuntu VM does continue to work and it looks like it is actually running ok.  But I have no way to "remote desktop" into it so it is kinda useless like that.

ESXi 5.5
Ubuntu 14.04 LTS desktop
vSphere 5.5

I can use "apt-get" to keep the VM updated with no problem.  But I can not update the Kernel.

Any ideas?

---

### Post by Travis_DeLong on 2016-02-29
Never fails.

I have been trying to figure this out for about a week.
Then today I decided to make this post.

Not a problem anymore.  And I have no idea what fixed it.
But now it works and Ubuntu is fully updated.

---

### Post by howefield on 2016-03-01
Hope it stays working for you.

Moved to the "*Virtualisation*" forum.

---

### Post by MAFoElffen on 2016-03-03
(It was a kernel update...)

---

