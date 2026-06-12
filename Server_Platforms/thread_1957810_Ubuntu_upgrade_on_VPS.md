---
title: "Ubuntu upgrade on VPS"
date: 2012-04-13
forum: Server Platforms
---

### Post by tsmr on 2012-04-13
Hi all.

I've had an Ubuntu VPS for more than a year now and I would like to upgrade the system.
When I first purchased the service, I selected 10.10 to be installed. Everything works smoothly but due to the "old" version, some packages are not updating to the latest version (eg. transmission)
Now I am planning to upgrade to 11.10 (or better yet to 12.04 LTS) and I want to know if there is anything I should worry about.

I mean, I've done dozens of sys upgrades, but they all were on physical machines with GRUB, stock kernels and loadable modules.
What would be the correct upgrade procedure on a VPS?

Thanks!

---

### Post by SeijiSensei on 2012-04-13
Upgrading is often easier on a server because the vast array of GUI-based stuff isn't usually involved.  I'd wait until 12.04 is released and then follow the usual procedures for a "dist-upgrade".

If this is a production server where uptime is important, a better alternative is to rent a new VPS with the new version of the OS, then migrate any customizations from one machine to the other.  Once you're sure the new server is functioning properly, you can cancel your contract for the original one.  You'll need to change any DNS records that point to the old server's IP, of course.

---

### Post by Jonathan L on 2012-04-14
Hi tsmr 

I'd heartily endorse Seiji's advice: if you've got a way to get another instance it's easily the best way as you can compare everything as you go.  Indeed, if you leave the old one running for a month or whatever, you have an easy "uncommit" if you find something strange later.  For many servers it's more practical to simply rebuild from scratch (OS+applications+data) rather than copy and upgrade.

Per his comment about DNS, you might find that the VPS supplier has a way for you to move IP addresses from the old one to the new one.  Certainly you can with OpenStack (Rackspace etc) and Amazon.

Kind regards,
Jonathan.

---

