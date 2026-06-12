---
title: "Server Backup"
date: 2007-06-13
forum: Server Platforms
---

### Post by TheGameAh on 2007-06-13
Just added an Ubuntu LAMP server to our mix of Windows 2003 servers.  With the Windows boxes I just backup everything to a tape library through Backup Exec.  What options are there for Ubuntu backup?  Doesn't necessarily have to go right to the tape library, but need a backup of some kind.

---

### Post by prezbedard on 2007-06-13
I use Backup Exc myself to backup our windows servers. I do believe it either comes with or you can get a remote backup agent for unix/linux. I just checked my materials and there is a cd for the unix/linux remote agent which I guess comes with it as it was not ordered specifically.

---

### Post by netlogic on 2007-06-13
I use two methods. I use Mondo to create an ISO that I can reinstall all the applications within  few minutes. I use Backuppc for data backup. Mondo helps me quickly recover from administrative mistakes when the machine won't boot.

---

### Post by Swab on 2007-06-13
I use rdiff-backup, it's in the repos.

I have a nightly backup to an external HD, and a weekly backup to a NAS in another building.   Also the server has a RAID 1 array.

---

