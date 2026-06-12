---
title: "Virtual Disk Backup Methods"
date: 2009-12-30
forum: Server Platforms
---

### Post by midwesterndirt on 2009-12-30
I currently use VirtualBox in headless mode running multiple VMs on one server because I find VMware to be too bloated and slow. I have written scripts for shutting down and starting up virtual machines and I currently have cron shut them all down twice a month, rsync the virtual disk files to a separate hard disk for backup, and then start them up again. While sort of an inconvenient method, I would have no problem doing it this way since this is just a home server setup, but cron seems to choke every time it runs the backup script. This is evidenced by the custom log files that my script writes to and the fact that the VMs never start up again after the backup. Running the backup script manually works just fine.

So the question is this: are there any better methods for backing up the virtual hard disks that anyone can suggest? Last time I checked, virtual disk backups don't work too well when the VM is running, and I feel like using snapshots or a RAID array is overkill. Any ideas?

---

### Post by BkkBonanza on 2009-12-31
The new version of VirtualBox allows for multiple concurrent snapshots. That may be the most efficient way to make backups and I think you can automate them via the command line. The snapshot files ought to be much smaller than full disk images.

---

