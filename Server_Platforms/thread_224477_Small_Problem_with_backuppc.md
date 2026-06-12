---
title: "Small Problem with backuppc"
date: 2006-07-28
forum: Server Platforms
---

### Post by olemadsen82 on 2006-07-28
Hi.

 

Im trying to figure out how to change the server Backup Path ( default var/lib/backuppc/*host* ).

I would like to do this on a client basis, I mean so that different users backup to different disks. I have a lot of data being backed up so I need to mount som nas disk to ubuntu. And there fore need to be able to choose different disks.

 

Thanks a lot.

---

### Post by olemadsen82 on 2006-08-03
Is there really no way to do this?

---

### Post by denni on 2006-08-05
> **olemadsen82 said:**
> Is there really no way to do this?

> edit /usr/share/backuppc/lib/BackupPC/Lib.pm

TopDir  => $topDir || '/path/to_new_bacup_dir'

/etc/init.d/backuppc reload

---

### Post by steveM49 on 2006-08-05
The author recommends that you use a link between the default location and your desired location.

---

### Post by denni on 2006-08-07
it is another way to reach same goal

---

### Post by denni on 2006-08-07
did see this somware on the net and it did work for me

---

