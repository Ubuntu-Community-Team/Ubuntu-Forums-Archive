---
title: "Setting up a NAS to backup files from Ubuntu 14.04 LTS server"
date: 2015-08-23
forum: Server Platforms
---

### Post by c_xy on 2015-08-23
Hello,

Currently we have a Dell T710 Poweredge server with 6 TB of data running Ubuntu 14.04 LTS.

We are interested in setting up a NAS to transfer data to for backup purposes. We want to automate this process on a weekly basis.

Here is the NAS product we are interested in purchasing:

**[SIZE=4]Synology America Disk Station 4-Bay Network Attached Storage (DS415+)[/SIZE]**


[http://www.amazon.com/Synology-America-Station-Attached-DS415/dp/B00IKTSSIO/ref=sr_1_15?&s=electronics&ie=UTF8&qid=1433611192&sr=1-15&keywords=nas&refinements=p_n_feature_two_browse-bin:7817230011](http://www.amazon.com/Synology-America-Station-Attached-DS415/dp/B00IKTSSIO/ref=sr_1_15?&s=electronics&ie=UTF8&qid=1433611192&sr=1-15&keywords=nas&refinements=p_n_feature_two_browse-bin:7817230011)

Here are a few questions:

1) Memory is 2 GB with no slots for expansion for the Synology unit. Is that enough? 2 GB seems kinda small. Again, we are only uploading data onto the NAS. Is 2 GB normal for this kind of setup? Is more needed? We want to a wholesale backup of all 6TB.

2) The following Synology link describes the process of creating backups from the Linux server to the NAS:


[https://www.synology.com/en-global/knowledgebase/tutorials/613](https://www.synology.com/en-global/knowledgebase/tutorials/613)

It suggests two methods. One is creating some kind of file share and mounting the NAS as a folder. The other method is to use ssh.

We probably prefer the ssh method, but also want to automate this process on a weekly basis. Backup the 6TB data on the server, where old files are kept, and new files are updated. So, using the ssh method, wouldn't that require a password? If so, how could one automate this process? Does mounting the NAS drive cause issues. We've used NFS in the past, and we notice severe a bottleneck and slowing down of the server from copying large files from local folder to a mounted share connected by way of the network.

Any help, suggestions, feedback, etc. would be appreciated.

Thank you for your time.

c

---

### Post by mastablasta on 2015-08-24
ssh with keys and push from server via rsync or rdiff-backup or something like that.

---

### Post by TheFu on 2015-08-24
> **mastablasta said:**
> ssh with keys and push from server via rsync or rdiff-backup or something like that.

and use snapshots from LVM to freeze the data during backups, so no downtime is necessary.
[http://www.tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://www.tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)

---

