---
title: "Ubuntu Server 17.10 to 18.04 Upgrade"
date: 2018-04-30
forum: Server Platforms
---

### Post by acascianelli on 2018-04-30
Can someone help me see what I'm missing when I try to upgrade from Ubuntu Server 17.10 to 18.04?

```
root@localhost:/etc# do-release-upgrade 
Checking for a new Ubuntu release
No new release found.
root@localhost:/etc# 
```

I can get the upgrade to attempt to proceed if I add a '-d' to the end of that command to check for development releases, but why does it not see 18.04 as being a non-development release?

Update:

Waited a couple days and the do-release-upgrade found the new version available.  Upgraded without any problems.

---

### Post by darkod on 2018-04-30
I don't use non-LTS releases like 17.10 and I don't know if the upgrade path is the same like LTS to LTS. But when using LTS to LTS upgrade, the new version is available only after the first .1 is released. In other words, it might be available only after 18.04.1 is out.

---

### Post by acascianelli on 2018-04-30
Yea, I realized that building my server on a non-LTS release was a mistake too late.  If I can get it to an LTS release without rebuilding it, I'll be staying on that until the next LTS comes out.  Just trying to avoid having to rebuild my server at this point.

---

### Post by darkod on 2018-04-30
You will probably have to be patient until 18.04.1 comes out. Usually it is recommended to upgrade after the .1 because they might need to repair some faults detected in the initial release. hence the do-release-upgrade works after the .1.

---

### Post by Dennis N on 2018-04-30
Upgrading information from 18.04 release notes:

> Upgrading from Ubuntu 16.04 LTS or 17.10:
Upgrades from 17.10 will not be enabled until a few days after 18.04's release. Upgrades from 16.04 LTS will not be enabled until a few days after the 18.04.1 release expected in late July.
There are no offline upgrade options for Ubuntu Desktop and Ubuntu Server. 

---

### Post by LHammonds on 2018-04-30
Keep in mind that doing an OS upgrade from something like 16.04/17.10/etc. to 18.04 were mainly designed for the OS only and still is not 100% perfect (such as losing network config, DNS, etc.)

Applications you install on top of the OS to typically serve a specific function may not work for a great many reasons such as different libraries or PHP version compatibility issues, etc.

For this reason, I NEVER do an in-place upgrade.  I will create a new VM, install all the same software that is on the production box and see if I can get the server running just like production.  Once I get the basic software working and document how I installed/configured it, I will then perform a migration of the data from production to the test box and see if I can get the test box to run exactly like the production box.  I will then document the data migration steps to make it work.  Then I trash the test box and do it all over again and follow the documentation I created.  If it works, I then decide if I am going to swap the IP addresses and make the test server the new production server or schedule a time to do it all over again for real.

I know this sounds painful for the person doing the work (especially when there are many servers to maintain) but my goal is to never let the users of my service know an upgrade even took place outside of normal maintenance windows.

**EDIT:** For those of you who just have 1 physical server, you can still do this test by installing something like VirtualBox on your PC to run Ubuntu Server 18.04 on your PC as a VM for testing.  When you have tested everything out, you should be fairly confident about formatting your server and installing 18.04 and the applications from scratch.  This would of course require that your migrated data be copied somewhere temporarily and have a full backup of the server if you need to restore back to the original version for whatever reason (like not having a RAID driver that works with 18.04 for example).

LHammonds

---

### Post by acascianelli on 2018-04-30
> **Dennis N said:**
> Upgrading information from 18.04 release notes:

Ok so I'm thinking I just got a little to punchy in wanting to run this upgrade.  I'll sit tight for another week to see if the upgrade option will get released.

---

