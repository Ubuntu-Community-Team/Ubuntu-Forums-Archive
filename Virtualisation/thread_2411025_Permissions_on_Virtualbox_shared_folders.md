---
title: "Permissions on Virtualbox shared folders"
date: 2019-01-23
forum: Virtualisation
---

### Post by two4two on 2019-01-23
I have Ubuntu host with VirtualBox.  I have ubuntu guest.  I have defined an NTFS vbox shared folder of a large partition different from where the host is and from where the virtual disk file is located.  I have no problem, when logged into the VM, to read, write create, delete, etc folders and files on the vbox shared folder.  

This VM has Odoo on it.  It is an out-of-the box all-in-one deb package and it creates the Postgres datastore inside the VM -- on the virtual disk file.  I tried to use pgadmin3 to create a tablespace on the vbox shared folder because it is large enough to hold all my data, but it doesn't work due to a permissions problem.  

So four questions:  

1.)  does it matter, regards permissions, that this vbox shared folder is an NTFS file system?  

2.) which level are the permissions enforced, Host, VM or both?  

3.) even though my VM user account has full access to the vbox shared folder why can't pgadmin create the datastore folders and files?  

4.)  how do I change permissions on NTFS file systems and at what level, Host, VM or both?  Maybe it would be easier to use an EXT4 file system?

---

### Post by #&amp;thj^% on 2019-01-23
Did you add your user to the group with
```

sudo usermod -G vboxsf -a myusername
```
change **"myusername"** to your login user name.
Also>> is guest additions installed,
You may try a log out and back in again, but a reboot should kick it in gear. (That's not saying this will solve your problem)
**EDIT:** Sorry i have problems when a post is just one long paragraph. (Just Me)
This may help a little also: [https://ubuntuforums.org/showthread.php?t=2306825](https://ubuntuforums.org/showthread.php?t=2306825)

---

### Post by two4two on 2019-01-24
Yes, it was easier to use an EXT4 file system.

CREATE TABLESPACE dontest
  OWNER postgres
  LOCATION '/media/sf_LinWork5/test-tablespace';

Works fine.  I had to pre-create the folder test-tablespace.  And then the create worked OK.  

Note that it is a vbox shared folder.  And in that folder it creates another folder called PG_9.5_201510051.  In the VM, I go to /var/lib/postgresql/9.5/main/pg_tblspc and find a folder called 263215. This is actually a symlink to /media/sf_LinWork5/test-tablespace.  If (in nautilus) I open that symlink I sure enough see the PG_9.5_201510051 folder, which is empty.  Makes sense so far.  

So, execute CREATE DATABASE:

CREATE DATABASE "recurring_docs_plus_automation_linwork5"
  WITH OWNER = odoo
       ENCODING = 'UTF8'
       TABLESPACE = dontest
       LC_COLLATE = 'en_US.UTF-8'
       LC_CTYPE = 'en_US.UTF-8'
       CONNECTION LIMIT = -1;

and get:

ERROR: could not fsync file "pg_tblspc/263215/PG_9.5_201510051/273398": Invalid argument
SQL state: XX000

I have no idea what this means -- yet.  

Sorry if this is more a PostgreSQL problem, or a VirtualBox problem.  I've been looking around on many forums and it seems I'm the only person in the world who tries to run PostgreSQL in a VirtualBox Ubuntu VM and is trying to put a datastore (tablespace) in one of the vbox shared folders I've defined for that VM (so that my data is not kept in a VirtualBox vdi file, but rather is kept on a real hard drive partition).  

Or at least the only one who has had a problem doing it.  All due to lack of knowledge in Linux, VirtualBox and PostgreSQL.  It'd be really cool if someone out there knew how to do this and would teach me (and the world) how.  Thanks.

---

### Post by SeijiSensei on 2019-01-25
I suggested a solution for a similar issue the other day.  I never heard back from the poster so I don't know if this worked or not.

Basically I suggested using NFS to export the filesystem from the host and mount it on the guest.  That assumes both host and guest are running Linux.

[https://ubuntuforums.org/showthread.php?t=2410667&p=13831939&viewfull=1#post13831939](https://ubuntuforums.org/showthread.php?t=2410667&p=13831939&viewfull=1#post13831939)

Unless you are forced to use NTFS for some reason, you should always choose ext4 or a similarly compatible filesystem for Linux. NTFS is not fully-compatible.

---

### Post by two4two on 2019-01-28
OK, I did some research on VirtualBox forum.  There is a thread that explains that by default vbox does not allow VMs to create symlinks on shared folders.  But that there is a way to enable it:  [https://forums.virtualbox.org/viewtopic.php?f=15&t=90390&p=433668&hilit=symlink#p433668](https://forums.virtualbox.org/viewtopic.php?f=15&t=90390&p=433668&hilit=symlink#p433668)

I will try it and reply after I've worked with it.

---

### Post by TheFu on 2019-02-08
I've had issues with vboxsf locking not actually working correctly on Windows hosts.  This would be a huge issue for a DBMS.
Trying to run a Linux DBMS on NTFS is a bad idea.  Trying to run a Linux DBMS through any file sharing method, with an NTFS disk as the underlying data store is a really, really, bad idea.  I would expect data corruption.

---

### Post by SeijiSensei on 2019-02-08
I believe VB folder sharing uses a version of CIFS so *nix primitives like permissions and symlinks don't work.

I'd run the Postgres server on the host. If you need to access it from the guest, use a network connection.  If you use NAT, you'd connect to the host's NAT address, often something like 10.0.8.1. If you use a bridged adapter, use its address. You'll need to enable connections to the PostgreSQL server from that address in pg_hba.conf. 

Once you've got everything set up you should be able to issue a command from the guest like

```
psql -h 10.0.8.1 mydatabase
```

---

### Post by TheFu on 2019-02-08
SeijiSensei - excellent idea.   If it is an option at all, running any DBMS on native hardware is a good idea.

---

