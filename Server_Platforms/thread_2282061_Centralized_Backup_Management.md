---
title: "Centralized Backup Management"
date: 2015-06-11
forum: Server Platforms
---

### Post by lingpanda on 2015-06-11
Hello,

   Looking for a way to centrally manage backups of several servers. I would ideally like to create full system images as well as backup individual file and folders. Can someone point me in the right direction to look? Thanks.

---

### Post by etescartz on 2015-06-11
To my knowledge Bacula would be a good candidate. Wikipedia says Bacula supports Linux, Unix, Windows, and Mac OSX backup clients, and a range of professional backup devices including tape libraries. Administrators and operators can configure the system via a command line console, GUI or web interfaces; its back-end is a catalog of information stored by MySQL, PostgreSQL, or SQLite. Have a look here : [https://help.ubuntu.com/lts/serverguide/bacula.html](https://help.ubuntu.com/lts/serverguide/bacula.html)

---

### Post by mastablasta on 2015-06-12
how about ur backup?: [http://www.urbackup.org/](http://www.urbackup.org/)

---

### Post by TheFu on 2015-06-12
> **lingpanda said:**
> Hello,

   Looking for a way to centrally manage backups of several servers. I would ideally like to create full system images as well as backup individual file and folders. Can someone point me in the right direction to look? Thanks.

Use any of the tools that will "pull" backups. Probably want to have a lvm snapshot since you'd also need to quiesce any DBs before the backup otherwise. Any of the librsync-based backup methods can work this way with a tiny bit of scripting.

But if you want a "backup system" which includes everything, backula is probably the answer. Setting it up is non-trivial.

---

### Post by LHammonds on 2015-06-16
> **lingpanda said:**
> Looking for a way to centrally manage backups of several servers. I would ideally like to create full system images as well as backup individual file and folders. Can someone point me in the right direction to look?
I don't use a "centralized" backup system that links everything together.  I simply have my servers backup their data (file level) locally to a /bak partition and remote-copy any data I need offsite as the situation requires.  I also have partition backups run to make backups of the entire server so it could be restored to a new machine...which is also copied to a remote server.

I use 7-zip and tar to archive and compress files before sending down the wire to conserve on bandwidth and preserve file permissions.

I use fsarchiver + LVM to create snapshots of my partitions.

All of this is automated and I've documented how I've done this in the link in my sig ([how I setup Ubuntu server]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=210")).  It should also be noted that when I setup my partitions, I separate them out and label each one which makes it VERY easy to identify partition files when restoring.

LHammonds

---

### Post by lingpanda on 2015-06-18
Thanks for the suggestions. I will be looking at Bacula and fsarchiver + LVM.

---

