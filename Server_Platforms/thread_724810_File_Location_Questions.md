---
title: "File Location Questions?"
date: 2008-03-15
forum: Server Platforms
---

### Post by leroy_30 on 2008-03-15
Here's my issue/problem/whatever. It is related to HDD partitioning & file locations. I've read I don't know how many posts from here, and pages & pages from searching google. Nothing that I could find directly relates to my issue.](*,)

I've setup an Ubuntu Gutsy AMD64 server. C2D 2.2-4GB Ram-4 SATA 500GB 32MB HDD. (with no Issues that I haven't been able to resolve)

My Current HDD config is this:

Drive 1 & 2 = Software Raid 1 + LVM on Each partition.
Partitioned:
/boot   200MB
/Swap   1GB
/          20GB
/var    100GB
/home 100GB
/Shared = The Rest

Drives 3 & 4 = Software Raid 1 + LVM Partitioned & added wherever, whenever needed.

At present I'm using only about 130GB Total.

I'm running LAMP, Citadel (Which I don't like at all and will be changing), VMWARE, SAMBA, going to add SFTP. I administer the whole thing either through ssh or webmin.

Now to my problem:

I'm not really sure how to explain this but here goes. Basically I would like to have all data locations /var /home /shared (and wherever MySQL data is stored) all in a single partition to make backups simpler and to keep from having to say (OK 100GB for this & XXXGB for that) and then having to chop up my other raid 1 a little at a time and dish it out to whatever partition is running low, or having a partition with more space than will ever get used etc... 

IMHO it would be much easier if I could do:
Drives 1 & 2 = Raid 1+ LVM 
/boot 200MB
/swap 1GB
/         ??GB
/Data The Rest (/home /shared /var or whatever)

Drives 3 & 4 Raid 1 + LVM with a single partition added to /Data

All data partitions (whatever ya wanna call em) would be in /Data and not in /

If this isn't possible could someone advise of a method to accomplish something similar???

Any help would be greatly appreciated. :)

---

### Post by koenn on 2008-03-15
I see 2 solutions :

1- don't partition :
join all partitions, disks, ... in LVM logical volumes. This way you never have to worry about about 1 partition being full and another being hardly used. 
I'ts not the preferred solution, cause it doesn't meet your requirement for a separate data partition, and it would be hard to implement if you already have data that you don't want t lose while setting up /reconfiguring LVM


2- don't focus on partitions, focus on data directories :
while the directories for binaries and config files are fixed, you can configure most (probably all) daemons and applications tu use a specific directory for data. in the FSH, /srv is mentioned as 'directory for data'. You could mount a large partition to /srv and e.g. configure
* apache to use /srv/www as DocumentRoot i.s.o. the default /var/www
* mysql to use /srv/databases as datadir i.s.o its default (/var/mysql ?)
* samba to share /srv/shared
* etc. 

/srv would act as your /Data directory. 
/home would still be separate, but you could make /srv/home and use that to contain user home directories. You can do this manually
(eg edit /etc/passwords, use usermod -d -m , ...), or make a script around usermod, and/or figure out where the defaults for the homedir location are kept and change that. 
However, the use of  /home is standard, maybe you don't want to change that. You'd have to look into permissions of /srv and /home to make this work for users without giving too much access to other dirs in /srv.

Likewise when you change daemons' default data location : set the file and directory modes (access permissions) to match the original


3- you can combine 1 and 2, i.e. use LVM to span (all) available disks/partitions, and move data to /srv for easy backups

---

### Post by leroy_30 on 2008-03-15
Thanx for the input. I'm not sure which way I will go, It sounds like I have some thinking to do. :)

I'm wondering if I could do something like

/boot
/swap
/
/srv or /data or whatever

Then after the install move /home to the /srv partition and symlink to it

Would that work????

I'm not really familiar with symlinks & the like :(

If anyone else has any suggestions I would be glad to hear them.

---

### Post by koenn on 2008-03-15
It would probably work. links are supposed to be transparent, so if /home is a link to a directory elsewere (say, /srv/homedirs ), programs should just write to and  read from it (and thus to/from /srv/homedirs) without being aware it's actually a link.

I haven't used links this way, so I can't guarantee it actually works.

---

### Post by barratt_sab on 2008-03-17
I'm no expert, but I have in the past mounted part of a fs into another directory:

[from man mount]

    mount --bind olddir newdir

After this call the same contents is accessible in two places. One can also remount a single file (on a single file).

This call attaches only (part of) a single filesystem, not possible submounts. The entire file hierarchy including submounts is attached a second place using

    mount --rbind olddir newdir

Stephen

---

