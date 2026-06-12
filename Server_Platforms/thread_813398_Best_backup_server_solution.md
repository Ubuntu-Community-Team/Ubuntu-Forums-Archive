---
title: "Best backup server solution?"
date: 2008-05-30
forum: Server Platforms
---

### Post by samosamo on 2008-05-30
I crontab'd a script I wrote that runs rdiff-backup on a few directories I need backed up.  It works flawlessly and it has saved me several times over the years.  I guess I'm just looking for a GUI to help manage it.

I tried slbackup and the webmin plugin (based on rdiff-backup) and it is kinda nice but, still I feel there is a better solution.

---

### Post by hyper_ch on 2008-05-31
what do you need a gui for when you have it already managed?

---

### Post by windependence on 2008-05-31
Try AMANDA or Bacula. I believe you can run them from webmin as well.


-Tim

---

### Post by samosamo on 2008-06-02
> **hyper_ch said:**
> what do you need a gui for when you have it already managed?

i just wanted to see if there was something better out there

---

### Post by dmatrix on 2008-06-10
apt-cache show backuppc

Set it up with ssh + rsync

---

### Post by quietas on 2008-06-10
I'll second BackupPC. Really handy file pool based backups that work. I use it at work on several of our critical laptops as well as desktops. All of the servers are using Backup Exec though and being dumped out to tape.

[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

---

