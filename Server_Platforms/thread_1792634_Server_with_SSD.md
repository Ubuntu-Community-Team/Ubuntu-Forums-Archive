---
title: "Server with SSD"
date: 2011-06-28
forum: Server Platforms
---

### Post by jerryk1234 on 2011-06-28
Hello,

   I'm setting up an Ubuntu server to replace my aged Pentium IV Slackware box.  It's a Dell Inspiron 560 with modest core-2 duo processor, 8 gigs of ram, and a pair of good sized hard disks.

   I came upon a good deal on a couple of 40gig Intel SSDs.   I'd like to use one in the server. I'd like to use the SSD for the relatively invariant stuff, because they write
slow, and are life-limited in the # of writes.    So:

  /bin
  /usr/bin
  /boot
  /etc
  /lib
  /usr/lib
  /usr/local/lib
  /mnt
  /opt

The best way IMHO to achieve this would be to make the SSD the root, and mount
hard drive partitions/filesystems to it to places such as:
  /var
  /media  ( here you read and write giant files.  Hard disks do this just fine. One will work 
                 especially fine if one particular hard drive is dedicated to this. )
  /root
  /home
  /tmp

A quick "df" yields a list of filesystems.  There are four that are not tied to any device!
/dev
/dev/shm
/var/run
/var/lock

( df also discloses that the root filesystem is presently standing at 502megs.  Guess it'll
fit in a 40-gig SSD )

These deviceless filesystems worry me.  Are they created magically on boot?  What's required to make the system magically create them on boot?  If I copy the filesystem over to the SSD and redo the grub config, will it Just Work?  Web searches reveal subtleties
WRT mount points.

        Thanks in advance,

                                            - Jerry Kaidor

---

### Post by jerryk1234 on 2011-06-28
Looks like the root filesystem MUST have /var/run and /var/lock.
So apparently I can't mount anything directly to /var.

Slicing and dicing my ( really quite enormous ) hard drives, I get
/var/backups
/var/cache
/var/games
/var/lib
/var/local
/var/log
/var/mail
/var/opt
/var/spool   ( the biggie! )
/var/www
/var/tmp

I *really* don't like slicing and dicing my disks that fine.  This whole thing is looking fragile and easy to break down the road, with dire and hard to troubleshoot consequences.

Hindsight being 20/20, it might not have been a good idea of the Ubuntu designers to 
create magic stuff in /var, such that it can't be mounted to the root as a whole.

Or am I not understanding something?

                                 - Jerry

---

### Post by jerryk1234 on 2011-06-28
Further poking and prodding reveals that the following directories are currently empty:

/var/games
/var/local
/var/opt
/var/tmp

Leaving only 

/var/mail
/var/backups
/var/log
/var/spool
/var/cache
/var/lib

I can probably get away with token "just in case" filesystems for the top 4, and assign the bulk of the "var" disk to the bottom 6.

                                 - Jerry

---

