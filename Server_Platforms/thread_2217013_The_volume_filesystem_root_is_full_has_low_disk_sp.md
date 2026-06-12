---
title: "The volume filesystem root is full /has low disk space error message"
date: 2014-04-15
forum: Server Platforms
---

### Post by rbenet-4 on 2014-04-15
Hello,
 
I have a server with 2TB of disk space and Ubuntu Desktop 12.04 "Precise Pangolin" LTS + x2go.
 
I am performing a big import into a database and in the middle of the import I get the infamous “filesystem root is full/has low disk space” error message (see attached screenshot).
 
When I launch the disk analyzer tool I see that indeed the ‘/’ folder is full but the ‘/home’ still has a lot of free space. The ‘/’ partition has about 0.5TB and the ‘/home’ one as 1.5TB.
 
If I abort the import, the ‘/’ partition goes back to being 75% free. So it seems as if the import would take the ‘/’ partition as a temp folder while importing the data.
 
How can I “tell” the data import command to use the ‘/home’ partition instead of the ‘/’ as temp folder? The '/home' partition has plenty of space.
 
Sorry if I said something stupid, I am new to Linux/Ubuntu.
 
Thanks

---

### Post by LHammonds on 2014-04-15
I don't know how you change that after-the-fact.  When I install a server, I use Logical Volume Manager and separate most of the key areas to ensure root is isolated from all other areas.  For example:

```

# df --block-size=m
Filesystem           1M-blocks  Used Available Use% Mounted on
/dev/mapper/LVG-root     1875M  432M     1348M  25% /
udev                      237M    1M      237M   1% /dev
tmpfs                      50M    1M       49M   1% /run
none                        5M    0M        5M   0% /run/lock
none                      246M    0M      246M   0% /run/shm
/dev/sda1                 268M   54M      200M  22% /boot
/dev/mapper/LVG-home      183M    6M      168M   4% /home
/dev/mapper/LVG-tmp       461M   21M      418M   5% /tmp
/dev/mapper/LVG-usr      3025M 1345M     1539M  47% /usr
/dev/mapper/LVG-var      1875M  463M     1317M  26% /var
/dev/mapper/LVG-srv       183M    6M      168M   4% /srv
/dev/mapper/LVG-opt       993M  773M      178M  82% /opt
/dev/mapper/LVG-bak      1984M 1109M      790M  59% /bak

```

The link in my sig shows how I configure the partitions during initial setup of an Ubuntu Server.

LHammonds

---

### Post by koenn on 2014-04-16
as a temporary workaround, you coulld mount whatever disk/or partition that is now on /home on /tmp (assuming that's where the temporary files that fill up / go to).
you'd have to backup /home to prevent the files being whiped during a cleanup of /tmp

If the disk space issue happens simply because you have insufficient space for the database's size the above is not going to work.
In that case, you need to move the database to a separate disk that has sufficient space. 
This involves installing an additional disk, mount it somewhere suitable, and copying the db files or restoring the database from a backup.
Re. the mounting, you have to options : you can mount it in an arbitrary mountpoint but then you have to reconfigure your db system to store it's files there. You can also mount it on the directory that holds the database files atm, so your current config will remain valid  but then you'll ant to move the db files out of the way first, and restore them afterwards.

It's doable, but you need to plan it well.

---

