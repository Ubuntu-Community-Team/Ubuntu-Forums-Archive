---
title: "Backup solution needed -- offsite backups"
date: 2009-08-19
forum: Server Platforms
---

### Post by joeinbend on 2009-08-19
I know this is a subject that has been discussed in various capacities here before, but I really feel the answer has been lacking. I'm looking for a backup solution that will run on Ubuntu Server, have a browser-based interface, have the ability to store and restore backups to a FTP server, as well as other local locations if desired (external drive, network share, etc.). The two that are interesting are Bacula and Amanda, however Bacula seems to be missing a straightforward browser interface (I'm not a noob, and I haven't been able to get any of the browser add-ons to work). 

I've also tried Sbackup, and NSSbackup, and both of them are on the right track, but the lack of any sort of interactive monitoring of a backup in progress is a real deal-breaker.

---

### Post by Girya on 2009-08-19
I've used backuppc and been very happy with it. It has a browser based interface and can be configured to use rsync. also uses a pooling system to save on space.

---

