---
title: "Help removing physical volume from LVM"
date: 2014-01-20
forum: Server Platforms
---

### Post by fricciardi on 2014-01-20
To all whom are kind enough to read and reply, my sincere thanks.

I have an Ubuntu 12.04.1 server in VMware. I added another HDD to it recently and expanded the Logical volume but now realize i don't need that extra space.

I have no idea how to remove that HDD without damaging the logical volume and rendering the machine unbootable.

see Gparted screen shot attached.  /dev/sda4 is not needed [ATTACH=CONFIG]249622[/ATTACH]

---

### Post by tomearp on 2014-01-20
[This page]("http://www.howtogeek.com/howto/40702/how-to-manage-and-use-lvm-logical-volume-management-in-ubuntu/") has some step by step guides for common LVM operations. There is a section near the bottom for deleting logical volumes that sounds like what you're trying to achieve.

---

