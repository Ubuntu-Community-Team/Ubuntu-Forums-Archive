---
title: "Accessing a protected folder in ubuntu"
date: 2011-07-04
forum: Security
---

### Post by jonners99 on 2011-07-04
I recently had to change both disks in my Synology DS209 NAS unit.

This question is about data recovery. I have managed to place both HDDs in my desktop machine and RAID them together again in ubuntu. I have then managed to get all my information off of the harddrives except for the mysql databases. The mysql folder on the RAID discs comes up and says I do not have permission to access the folder. I have tried sudo, cp, mv but none are working for me.

Its complaint is that I am not the folders creator. Which is a nice security feature except when I am.

Any ideas on how I can get at this data?

---

### Post by SeijiSensei on 2011-07-04
> **jonners99 said:**
> Any ideas on how I can get at this data?

I'm not sure why you can't copy /var/lib/mysql as root with something like rsync, but another option would be to dump the database to a text file with mysqldump, then rebuild the database on the new drives using the mysql client.

---

### Post by jonners99 on 2011-07-04
I hadn't thought of rsync, I will try tonight.

The files are in something like /media/[RAID name]/@database/mysql

I can't even look into the mysql folder (in ubuntu file manager it has a grey cross in the bottom right corner of the folder) so can't get access to the db files.

---

### Post by jonners99 on 2011-07-06
ok have tried rsync - it says "skipping directory mysql"

I tried copying again, it said "cp: omitting directory 'mysql'"

---

### Post by SeijiSensei on 2011-07-06
The only thing I can think of is that it has permissions 0000 or perhaps is marked "immutable" with "chattr -i".  Even if it were immutable, it should still be readable.

If you run "sudo su" then cd to /media/[raid name], what does "ls -lR" show?  What if you enter @database and run that command?  Any directories in this tree with 0000 permissions?  (You'll see only hyphens; no d, r, w, or x permissions.)

---

### Post by jonners99 on 2011-07-07
I managed to use chown to change the owner of the folder and its sub folders to allow me access

Now I get to put the MYD etc files into a mysql install to export the data. I can imagine that being easy enough to sort out. Any issues I will ask.

---

### Post by cariboo on 2011-07-07
I really don't recommend you change file permissions, why didn't you just use root (sudo), to copy/backup the files.

Another way of course is to use the user you originally setup when you installed mysql to run the mysqldump command.

---

### Post by jonners99 on 2011-07-07
As I said it was a RAID created by my Synology backup, it was not allowing me to sudo copy/backup... chown was the only thing that worked and I now have my databases back up and running again on my synology with two new HDDs as I originally wanted.

For reference the owner of the files was an id number 1024 (I think)

---

