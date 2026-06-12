---
title: "Dual boot 2 Ubuntu Versions"
date: 2017-04-28
forum: Server Platforms
---

### Post by jingo_man on 2017-04-28
I have an existing system for my home server. It has many components installed already (DNS, DHCP, MySQL Server, Apache, Seafile, TVHeadend, Wordpress, and probably many more I have since forgotten!). The big consideration is the MDADM & LVM partition scheme I have for my large media library, as well as the userdata for some of the above applications as well, i.e. MySQL databases and Seafile documents (but the binaries and config are on the O/S partitions). It runs an end-of-life version of Ubuntu (14.10) which I wasnt confident of upgrading, and now is so far behind I have even less confidence!

I would now like to upgrade, but with the above, the most sensible approach will be to create a new partition on the SSD drive and dual boot a second Ubuntu installation. Or possibly considering Debian, as it has a less aggressive upgrade cycle.

What I need is the ability for either / both Ubuntu instances to be able to use the MDADM & LVM partitions, mount them in the same place, and applications (such as MySQL) to both point to these locations.

Is this possible? Are there good guides / walkthroughs / tutorials / videos people can recommend?

There are plenty of Ubuntu & Windows dual boot guides, but they do not have the final "partition sharing" aspect that I need.

Thanks

---

### Post by howefield on 2017-04-28
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

