---
title: "Server Transfer - Help moving to new box"
date: 2009-02-26
forum: Server Platforms
---

### Post by quietas on 2009-02-26
Hi all, I have a test server which has proven itself to management and needs to be moved to a new box. The old unit is using software RAID'd IDE as md0, while the new unit actually has hardware RAID'd SCSI 320. AMD Duron to Dual P3's, IDE to SCSI (new is relative, internal helpdesk site with no load, 2x P3 supports it easily.

I can reinstall and start from scratch, but is there a way to migrate everything instead?

I'm using Server 8.10 LAMP with WordPress, GLPI, OSCNG, and OrangeHRM. I can backup and reload the MySQL databases and copy the conf files, but there has to be an easier way, right?

---

### Post by koenn on 2009-02-26
> **quietas said:**
> Hi all, I have a test server which has proven itself to management and needs to be moved to a new box. The old unit is using software RAID'd IDE as md0, while the new unit actually has hardware RAID'd SCSI 320. AMD Duron to Dual P3's, IDE to SCSI (new is relative, internal helpdesk site with no load, 2x P3 supports it easily.

I can reinstall and start from scratch, but is there a way to migrate everything instead?

I'm using Server 8.10 LAMP with WordPress, GLPI, OSCNG, and OrangeHRM. I can backup and reload the MySQL databases and copy the conf files, but there has to be an easier way, right?

Backup and copy sounds like the easiest way to me, and probably the savest. You could try to clone it (rsync, dd, ...) but with the differences in hardware, especially in your disk system, I wouldn't risk it. Even if it seems to work, the system boots, all services run and all data appears to be there, I'd never be sure that somewhere down the line this transfer wouldn't cause some sort of trouble (a file getting corrupted, unexpected I/O errors, ...

An even easier way would be that while you were setting up your test server, you'd anticipate having to move it to another machine. That could be as simple as having a text file where 
a/ you write down the commands you used to install software
b/ you write copy (e.g. scp from test:/path/file to /path/file) statements for each file (conf, script, ...) you modified or created.

If you'd done something like this while setting up the test system, you'd only have to run that text file as a script to reproduce your test system on an other machine. 


The inbetween solution is to try and create such a script after the fact, eg document your test server in a script, and run it on the production server

---

### Post by quietas on 2009-02-26
It's mostly MySQL db stuff. WordPress, GLPI, OCS, and OrangeHRM are all PHP/MySQL based. I figure a back up and restore of the databases 'should' be easy enough to do from my workstation. Then it's a matter of finding the conf files which have changed off the defualt deb installed files.

---

### Post by koenn on 2009-02-26
> **quietas said:**
> It's mostly MySQL db stuff. WordPress, GLPI, OCS, and OrangeHRM are all PHP/MySQL based. I figure a back up and restore of the databases 'should' be easy enough to do from my workstation. Then it's a matter of finding the conf files which have changed off the defualt deb installed files.
the database could be as easy as dumping it to sql statements and running those statements again on the other side. But you probably already know this. 

if you roughly remember the date when you started modifying files, you could try something like

```

#create a file with given timestamp
touch -t YYMMDDhhss /etc/timestamp

# find files created/modified after given timestamp     
find /etc -newer /etc/timestamp

```
you may also have to look in /var or /usr/share or so

it's worth a try, but no guarantees.

---

