---
title: "MAAS custom preseeds"
date: 2014-12-22
forum: Ubuntu Cloud and Juju
---

### Post by deephack on 2014-12-22
Hello All,

I am using MAAS 1.7.0 to comission physical servers which I will be managing with Juju.  I am struggling to get custom preseeds to work correctly though.  I am finding that if I edit the general or preseed_master files in /etc/maas/preseeds my changes are picked up but the ability to run different preseeds based on node name is not working for me.  I'm trying to follow the documentation here under the heading "User-provided preseeds".

 [http://maas.ubuntu.com/docs/development/preseeds.html](http://maas.ubuntu.com/docs/development/preseeds.html)

As such I have tried creating a preseed with the name amd64_generic_trusty_db2 and yet the node in question does not run the preseed.  I have also tried just amd64_generic_trusty and this doesn't work either.

Does anyone have any information on what I'm doing wrong here?

If it's of any interest I'm doing this because some of my nodes will be database nodes and the others will be VoIP switch nodes.  As such the drives and partitioning vary between these two types.

---

### Post by rmustakos on 2015-03-17
I don't know if this will work or not, and it is very much a hack, but I know that there are different preseed files for each region.
You might make a region controller for each of the different types, and modify those.
Other than that, I can't help you with the partitions, but you could put the driver installation in the charms

---

