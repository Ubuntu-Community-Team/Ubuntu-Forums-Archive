---
title: "Setting up Software Raid without reinstalling"
date: 2006-05-27
forum: Server Platforms
---

### Post by alexroche on 2006-05-27
Hi there....

I installed Ubuntu server a few months ago. It's on a machine with two drives: 1 4GB (everything except home dirs), and 1 80GB (home dirs). I use it mainly for web hosting/DNS/mail server. 

I'd like to get another 80GB drive and set up a Raid 1 between that drive and the other 80GB drive that is used for the home directories. Is this possible without reinstalling Ubuntu?

Also, I'd like to get a new drive to replace the 4GB (it's obviously quite old). Is it possible to copy everything over from the old drive to the new drive (with another machine).... without messing anything up?

Basically I'm trying to make it so that if one of the drives goes... It don't lose everything and the server doesn't go down.

Any help is appreciated.

Thanks,
Alexandre

---

### Post by alexroche on 2006-05-30
anyone?

---

### Post by drpepper on 2007-12-14
*Bump*

I know this post is a little old, but I want to do the exact same thing, create a raid array with a harddisk (and obviously a second one) that does not contain the system, without having to format. Anyway, got any ideas?

Cheers

---

### Post by drpepper on 2007-12-14
^^^^ by format, i mean reinstall the ubuntu system.

---

### Post by umattu on 2007-12-14
Absolutely not possible using ubuntu's software RAID.

Using MDADM you need to mark the partitions as being used for a RAID array during the setup process, the RAID device is then created, and thats where the system will be installed to.

I do believe, certain hardware RAID controllers will do RAID 1 (only) on systems that are already live.

---

### Post by rsw686 on 2007-12-15
Yes you can do this without loosing data, however I recommend backing it up just in case. Here's a tutorial.

[http://www.debian-administration.org/articles/238](http://www.debian-administration.org/articles/238)

---

