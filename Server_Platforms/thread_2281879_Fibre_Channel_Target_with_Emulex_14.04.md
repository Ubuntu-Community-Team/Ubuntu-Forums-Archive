---
title: "Fibre Channel Target with Emulex 14.04"
date: 2015-06-10
forum: Server Platforms
---

### Post by seijirou on 2015-06-10
Hello

I'm attempting to replace my Solaris-based SAN with something Linux based because I want to move from ZFS to BTRFS.

I'm currently trying out Ubuntu and I've basically got everything going except for my fibre channel target.

I've got Emulex HBAs, I believe the driver for them is lpfc.

I've looked in to SCST and LIO + targetcli with the latter looking the most promising.  I think the piece that I'm missing is actually configuring the HBAS to run in target mode instead of initiator mode.

Most of the info that I've found has been regarding qlogic instead of emulex.  Is it possible to configure an emulex hba to operate in target mode?

Thank you

---

