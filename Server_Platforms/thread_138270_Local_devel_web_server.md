---
title: "Local devel web server"
date: 2006-03-01
forum: Server Platforms
---

### Post by hardbop200 on 2006-03-01
Hello everyone!

To begin, my name is Josh and I am currently running Ubuntu 5.10 on a PIII 700 Mhz laptop, running fluxbox to stay light.  :)   I would like to run a local web and database server on my laptop to develop on.  I would like something that can support php, mysql, etc.  Initially, I thought that Apache would be the default way to go, but there may be other options out there that I'm not aware of that would be less resource-intensive on my measly devel laptop.  I don't mind getting my hands dirty, but I would like to have something that is easily acquired via the standard, universe or multiverse repositories.  This would, at the very least, save me a little time with the installation.

Just for frame of reference, my goal is to have 2 or 3 websites running on my laptop:

1.  A copy of my website that I can mess up, delete, and reinstall.  Also good for backups.
2.  A "documentation" site, probably a wiki, for personal use.
3.  A blank site for messing around with learning new things.

So to sum up, what webserver would you recommend?  Obviously I would have to have mysql (this is what my website uses now, which is hosted by someone else).

Thanks for your time!

Josh

---

### Post by suRoot on 2006-03-01
Just use Apache - it'll work fine on your system.  I ran Apache 1.x on a 486 for a long long time.

---

### Post by majikstreet on 2006-03-01
I don't see any issues with apache, but I have tried cherokee before.. it's very light :D

---

### Post by jezjones on 2006-03-02
My dev server at home is a AMD k6 266 with 256mb ram.
It is running Apache 2.0, php 5, mysql 4.0, perl.

If you want to save resources then don't install an X server, just use the command line.

Good luck.

---

### Post by majikstreet on 2006-03-02
oh yeah, I ran apache on a system of unknown cpu speed or cpu type, with 128mb RAM :D

---

