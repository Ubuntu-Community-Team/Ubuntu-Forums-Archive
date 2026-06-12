---
title: "VMware 6 doesn't fully intsall in Trusty"
date: 2014-08-02
forum: Virtualisation
---

### Post by cecilieaux on 2014-08-02
After doing a clean install of Trusty Tahr, I thought I installed VMWare Player 6, but when I start to run it I first get the error

    > Before you can run VMware, several modules must be compiled and loaded into the running kernel

Then it starts compiling four things:

-- Stopping VMware services OK

-- Virtual Network Device ... gets a red ! (CRASH)

-- Running Depmod OK

-- Starting VMware services ... gets a red ! (CRASH)

Then a new error pops up

> Unable to start services. See log file /tmp/vmware-root/vmware-modconfig-5606.log for details.


This, of course, requires root and end up being a long file that is not very informative to a very pedestrian user.

Anyone have a clue about this? TIA

C

---

