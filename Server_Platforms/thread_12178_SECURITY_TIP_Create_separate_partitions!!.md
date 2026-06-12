---
title: "SECURITY TIP: Create separate partitions!!"
date: 2005-01-22
forum: Server Platforms
---

### Post by jdong on 2005-01-22
Just learned an important lesson in server security. On the new Ubuntu Backports server, I just noticed that the /var partition was filled to the brim! Cause? Misbehaving Prelude logs not being rotated -- there was 10+GB of random packet captures! Had we not created a separate /var partition, I would've noticed 1 month later that the entire hard drive was full!


The same applies to /tmp and /home -- on a server, never let one constantly changing filesystem crowd out everything else!!

---

### Post by dataw0lf on 2005-01-24
This isn't just a security based idea, either; good design promotes separating partitions for a variety of reasons.  I've gotten into the habit of _always_ partitioning, at the very least, /usr, /var, and /home.  Obviously, on a much used server, you might want to partition /usr/local and /tmp as well, and consider implementing quotas for your user.  
dataw0lf

---

### Post by jdong on 2005-01-24
I'm just starting to learn about LVM's, and their flexibility. I want to start using them on my new system setups, too.

---

### Post by Buffalo Soldier on 2005-01-24
Before I started using GNU/Linux, most website that I go through would directly/indirectly suggest that /var is to be put in its own partition.

[http://www.linux.org/lessons/beginner/l4/lesson4e.html](http://www.linux.org/lessons/beginner/l4/lesson4e.html)> /var is a directory for certain files that may change their size (ie. variable size) For example, there are a few excellent databases for Linux. One is called MySQL. Normally, MySQL keeps its data in a subdirectory of /var called /var/mysql/. If I had an e-commerce website, I would have a database to register purchases. That database would obviously grow in size. And if it didn't then I'd be in trouble. It is also the normal place where email servers store their incoming mail. Again, email varies in size as well.

---

### Post by dataw0lf on 2005-01-24
The flexibility of LVM's is astounding.  I currently use LVM on both my servers and my workstation.
dataw0lf

---

### Post by jdong on 2005-01-24
What **really** sucks is when I used Gentoo, I thought /var would hold logs, a bit of local e-mail, and a few static webpages and a small database, so I gave 5GB to /var.


Then, I realized Portage did all its compiling in /var/tmp/portage.... Boy, was that a surprise when I unpacked OOo's source!

---

### Post by nocturn on 2005-01-25
Another good security tip if you have seperate partitions.

Set /tmp sticky so users can not delete other people's files (does not require a sep. part.)
Mount  everything but root with nodev.
Add nosuid and noexec to /tmp and at least nosuid to /home and /var.

---

### Post by Elotemuygrande on 2005-01-27
[QUOTE=jdong]What **really** sucks is when I used Gentoo, I thought /var would hold logs, a bit of local e-mail, and a few static webpages and a small database, so I gave 5GB to /var.


Then, I realized Portage did all its compiling in /var/tmp/portage.... Boy, was that a surprise when I unpacked OOo's source![/QUOTE]

You probably know this, but portage respects a number of environment variables that let you put it anywhere. But I would agree that /var is a bad default.

From man make.conf:
> PORTAGE_TMPDIR = [path]
              Defines the location of the temporary build directories.
              Defaults to /var/tmp.

---

