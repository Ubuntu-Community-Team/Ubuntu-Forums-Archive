---
title: "Ubuntu server backup"
date: 2010-12-19
forum: Server Platforms
---

### Post by Ambiorix3 on 2010-12-19
Hey everyone,

i have a home server which runs ESXi with 4 ubuntu server VM's. 
One of these servers should be my backup server which would contain the data from all other servers and desktops. 

The backups should be done automatically every night and should be backed up incrementally from monday to saturday and a full backup on sunday. After the full backup, the past incremental backups may be overwritten. 

I haven't come here to ask you for a full solution, merely the different steps to achieve this goal. I'm not a complete linux noob but i am relatively new and i would like to learn how to do this but i don't know where to begin. 

I'd appreciate it if you could help me a hand.

---

### Post by windependence on 2010-12-19
[http://www.amanda.org/](http://www.amanda.org/)
 
[http://www.bacula.org/en/](http://www.bacula.org/en/)
 
-Tim

---

### Post by spynappels on 2010-12-19
Is the reason you want to this as a learning experience, or as a "production" scenario?

The reason I ask is that the answer may have a bearing on how this can be done.

Are you using internal Datastores (HDDs) in the ESXi host, or an NFS or iSCSI storage solution? If it is internal, you need to ensure the Backup VM lives on a different datastore than the others, or mount an NFS or other external storage to the backup VM.

Then you can use the solutions suggested by Windependence or look at rsync.

I have built an iSCSI target to connect to my ESXi host for this reason, and it works well, but I use rsync in a cronjob.

---

### Post by R.Bucky on 2010-12-20
It really depends on how far you want to take it. Rsync to an external drive with a RAID1 setup is great. But, you could also go with an off site solution for disaster recovery like SpiderOak or similar.

---

### Post by Vegan on 2010-12-20
I like a storage server idea running on bare metal. Then all the VMs can use it to store backups as needed.

My small setup uses a folder to store backups, then those files are copied to the Windows machine.

I might use the DVD drive to backup as my backups are small enough.

---

### Post by samosamo on 2010-12-20
To back up my VMs I use ghettoVCB for ESXi.  I don't back up using the traditional tar/rsync/etc method.  It backs up the whole image to an iSCSI share on a separate SAN.  It's great to restore the whole VM, but to restore just a file/directory I simply mount the vmdk image on another host and copy the files out.

To back up my data on the aforementioned SAN, I am still looking for a decent solution. There aren't many. I am considering BackupPC (ignore the stupid name) which has a nice web GUI and uses native apps like rsync.

To back up my clients I use OSX's TimeMachine which is also connected to the SAN.  I have no Windows clients to worry about, thankfully.

---

### Post by HermanAB on 2010-12-21
Dervish is another one, if you don't want to make your own one line rsync script.

---

