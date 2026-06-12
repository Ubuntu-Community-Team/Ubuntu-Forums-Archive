---
title: "Network backup software?"
date: 2007-06-04
forum: Server Platforms
---

### Post by MatthewMetzger on 2007-06-04
Hello,

I'm doing research in preparation to building a server to do automated network backups of mainly OS X clients, but I also have a few Windows and Linux machines. There are less than thirty clients in my organization and I'd like disk-based backup as I don't think we require the extra expense of a long term tape backup.

I have a bit of experience maintaining unix based servers, but I'm not an expert. I've looked up the backup software packages** Amanda**, **Bacula**, and **BackupPC** (also the **FreeNAS** distribution). All of them look fairly complicated from a beginner's perspective, but I'm confident that I can learn and implement whatever solution I end up choosing.

Do any of you have experience with automated network backups using ubuntu server? Any suggestions? **Warnings?** Bad experiences or good experiences with a particular backup software package?

Any help would be greatly appreciated.

-Matthew Metzger

---

### Post by craigp84 on 2007-06-05
Whatever you go with (it doesn't matter which one you go with - go with what makes your life easier), make sure you practice the recovery at least once.

Think how absolutely insanely frustrating it would be to go to all this hassle, but not test it, only to find out when you need to depend on the backups, some error in the setup prevents restoration.

I've seen *way* too many people suffer this. If you've not actually proven it works - then it absolutely does not work.

Automated backups are fairly trivial. If you can arrange for automated restores, then your setup really is the mutt's cahoonas.

-c

---

### Post by MatthewMetzger on 2007-06-06
Thanks for your reply Craig. I will take your advice and test restoration of data thoroughly. I'm leaning toward **rsnapshot** because it seems easy to implement and minimizes backup storage size.

thanks again.

-Matthew

---

### Post by MatthewMetzger on 2007-06-06
I'm again reconsidering which software to use. BackupPC looks very good with web interface and automated restores (I'm interested in the details of this).

I've purchased a book on backup and recovery published by Norton. ISBN-10: 0596102461. It won't arrive for a while. I will take my time planning this backup system.

-Matthew

---

### Post by kaneda74 on 2007-06-07
i looked into using rdiff-backup on the osx side and also looking into webmin's plug in for skokelinux backup or shorelinux backup as its know.

for now i am running Ubuntu 7.04 with samba turned on and the mac clients are using stuffit to automatically create a backup on the smb shares.

its working but i had to use stuffit since the utf-16 support doesnt work on my build yet.
im looking into using netatalk 2.0 or newer since its supposed to support large files as well as wierd file names allowed by osx.

im still considering using rdiff-backup since i can have versioning and the backup time would be faster if it only copied the changes files.

Michael Crabtree
Director of Consulting Services
Carlin IT

---

### Post by craigp84 on 2007-06-07
rsnapshot++

It's trivial to setup, is very reliable, can be locked down and secured a lot easier than most other solutions, and end users can restore their own data saving the admin time.

-c

---

### Post by MatthewMetzger on 2007-06-07
> **craigp84 said:**
> rsnapshot++ . . . and end users can restore their own data saving the admin time.

I've been looking fairly closely at rsnapshot and backupPC. Are you sure that you didn't mean backupPC in your last post? It doesn't seem like end users can do their own restore with rsnapshot, but maybe I haven't read closely enough.

thanks for your time and tips,

Matthew

---

### Post by craigp84 on 2007-06-07
Definitely meant rsnapshot :)

But, as i said before: it doesn't matter which one you go with - go with what makes your life easier

Hope this helps,

-c

---

