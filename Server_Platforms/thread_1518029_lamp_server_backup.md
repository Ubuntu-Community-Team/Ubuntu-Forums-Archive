---
title: "lamp server backup"
date: 2010-06-25
forum: Server Platforms
---

### Post by grcunning on 2010-06-25
At school I am tasked with upgrading a 7.10 lamp server to 10.04.  Before I do this, I need to make sure that I have valid backups that will allow me to restore the server if the upgrade goes wrong.

The backup script that runs now tars and gzips the following directories:
/root/ /etc/ /home/ /var/www/ /var/deliver/

other than apache, php, mysql, and sshd, the server is vanilla.
if I install gutsy lamp server on another machine, and unzip this tar in /, will this be sufficient to restore the original machine? and do I really need to restore /etc? or can I just use the new /etc and make the hostname the same as the original?
I also have mysql dumps of the databases, so I really don't need to restore anything to do with mysql, I can do that manually.

---

### Post by mörgæs on 2010-06-26
If a clean install of 10.04 does not work: Is there a particular reason  you are thinking of 7.10 rather than 9.10 or 8.04?

If you really want to revert to a 7.10 vanilla server (being aware that this version is unsupported) I would recommend reinstalling rather than using a back-up.

---

### Post by grcunning on 2010-06-26
The reason it is 7.10 is that the server has been running since gutsy was new, apparently without a single problem.  As soon as I can make sure I can do a full restore, I can upgrade to 8.04 then to 10.04(as far as I know that's the only way to upgrade)
I'm a little hesitant to do a clean lucid install, unless I can make absolutely sure that I have solid backups.
The server runs a mysql database of fish capture and water quality data for the Pennsylvania Dept of Environmental Protection, and a php front end, so I can't afford any screw ups.
I would clone the drive if I could, but it's on a multiple disk RAID 5 array.
I just need to mirror the entire server onto some different hardware.

---

### Post by new_tolinux on 2010-06-26
It's possible you'll run into trouble anyway, since the MySQL and PHP-versions are different.
You should first test that part before you should think about replacing Gutsy anyway.

Besides that, hardware that runs 24/7 and has to be reliable should be replaced after about 3 years of use.

---

### Post by mörgæs on 2010-06-26
I would do the following: 

On a test machine, install a 10.04 server with LAMP and deploy the database here to verify that there is no conflict because of the versions (I would not expect any). This can be any random desktop machine.

Boot your present server, if you are allowed to take it offline for a moment, with a 10.04 live CD and see the result. What hardware are we talking of?

Given everything is going well: Then a clean 10.04 install on the server. I would not use an obsolete version like 7.10 as a base for anything, not even an upgrade. 

Backups all the way, of course.

---

### Post by new_tolinux on 2010-06-26
I don't think the databases will give the real trouble.
Probably the different mysql version and php version can give the troubles as some commands and results are slightly different. That can break a (previously working) php-script.

---

### Post by grcunning on 2010-06-26
I think I can deal with mysql and php. The important question for me is the /etc dir. I dont know whether I should copy it over or not. If I don't, will I have to recreate all the users?
I thought if the dest server is the same version as the current one that I could just copy all the files over and it would work. If I am going to restore the backups to a fresh install of lucid, which directories should I be backing up?

---

### Post by Ryan Dwyer on 2010-06-27
Set up a test machine and practice a restore. There is no substitute for hands on experience.

If I were you I'd backup:
- Everything in /var/www
- Everything in /etc/apache2, /etc/php5 and /etc/mysql (even if you don't restore all of it, at least it's there)
- Databases using mysqldump

If you have maintenance scripts in /root/ or /home, back those up as well.

I would also immediately update to a supported distro such as Lucid. If an exploit is found in any software you are using, you will not receive the fix because Gutsy is no longer supported.

---

