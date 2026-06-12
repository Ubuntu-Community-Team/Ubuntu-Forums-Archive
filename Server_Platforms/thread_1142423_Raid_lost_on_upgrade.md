---
title: "Raid lost on upgrade"
date: 2009-04-29
forum: Server Platforms
---

### Post by badrunner on 2009-04-29
I had a LTS server setup with a software raid 0 setup according to this guide: [http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)

Everything was working fine, however on updating to Jaunty /dev/md0 no longer exists on boot. Im not familiar enough with this stuff to have any idea where to begin, any ideas?

Thanks

---

### Post by badrunner on 2009-04-29
> **badrunner said:**
> I had a LTS server setup with a software raid 0 setup according to this guide: [http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)

Everything was working fine, however on updating to Jaunty /dev/md0 no longer exists on boot. Im not familiar enough with this stuff to have any idea where to begin, any ideas?

Thanks

Problem solved, i kept searching and eventually tripped over [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/330298) which details how to sort it out.

---

