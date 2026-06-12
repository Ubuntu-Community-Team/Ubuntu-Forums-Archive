---
title: "Dell T320, Ubuntu 16.04.  Hard Drive Identifiers"
date: 2018-06-11
forum: Server Platforms
---

### Post by ScatterBrain on 2018-06-11
I have a Dell T320 with a H710 RAID Controller.  Inside the T320, I've installed a 250GB SSD for Ubuntu, with the intention of using the H710 RAID as a LVM for NFS accessible storage.  All is OK, except that Ubuntu picked up the SSD as /dev/sdb and the RAID as /dev/sda.  Again, everything is working, the machine is booting and functional.  But...I'd really like to swap those identifiers.  SSD=/dev/sda; RAID=/dev/sdb.  Is this possible and what do I need to do to achieve it?

I've not done anything except install Ubuntu Server and update it.  I've not even created the LVM on the RAID yet.  A reload is not a problem.

---

### Post by volkswagner on 2018-06-12
I know this doesn't answer your question... but you may consider dropping /Dev/sdx reference. Use UUID instead. The /Dev can randomly change while the unique identifier won't.

---

