---
title: "Mysql - ibdata1 deleted, how to recover ?"
date: 2006-05-02
forum: Server Platforms
---

### Post by mpa on 2006-05-02
Hi guys, I moved to a new apartment which yet to have an internet connection, so before I moved out I downloaded wikipedia xml dump so I can have an offline encyclopedia. After using mediawiki's phpdump, I found out that I didnt have enough freespace, so I deleted the database and was thinking about symlinking /var/lib/mysql to another drive which has enough space.

Unfortunately, deleteing wikipedia database did not free up the now unused space. Since I really need the occupied space, I deleted the ibdata1 file in /var/lib/mysql (I am not sure if I spelled it right, dont have my boxen with me). I thought I could just delete everything in /var/lib/mysql and then use mysql_install_db to start a fresh mysql database. Unfortunately, ever since then, I can no longer start mysql daemon.

I've been in this situation before and back then reinstalling mysql easily fixed it, but right now I have no internet. Any ubuntu user know how to fix this ? 

I am using Ubuntu Dapper Beta, last updated two days ago.

---

### Post by LordHunter317 on 2006-05-02
If the mysql packages are in /var/cache/apt/archives, you can purge and reinstall them.

Failing that, I'll come up with the proper steps later, when I find them.

FWIW, the only way to get that space back would have been to rebuild the cluster:[list][*]On an InnoDB system, the database files don't contain actual data, 'ibdatax' does.[*]You cannot shrink that file once it's expanded[*]There is an option to use a single file per table, but it has performance ramifications and was broken in previous versions of MySQL.  I'd persume it's fixed in 5.0, but I don't actually know.[/list]

---

### Post by mpa on 2006-05-02
Yep, I tried searching the cache for mysql package, unfortunately it isnt there. Also, I asked people in #mysql at freenode if there is a way to free up the space  taken by the wiki database and since they said the file size cannot be shrinked and I REALLY need the space (its the root partition) I decided to delete the then -huge- ibdata1 file. Rebooted the system and got my space back.


PS
After I read mysql docs (bless $deity theres internet at work), it looks like I can edit the variable in mysql.cnf to specify a new location for innodb so it give the right permission, mysql server can build a new db. Gonna try that when I got home.

---

