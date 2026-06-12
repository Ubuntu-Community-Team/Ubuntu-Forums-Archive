---
title: "apt-get requires CD?"
date: 2005-05-07
forum: Repositories &amp; Backports
---

### Post by Gentist on 2005-05-07
Ok, so I've been experimenting with Ubuntu for a while now, and thus added and removed a lot of packages. My only problem is that when it wants to install a package that came with the install CD, it asks me to insert it into the drive each time. First of all, I deliberately messed up (changed) fstab, so now it doesn't recognize the CD even if it's in the drive (what's the original value in case need to change it back?). Secondly, is it possible to have apt-get fetch everything that isn't already on the harddrive from the 'net? Or alternatively have it fetch from the 'net and ask for the CD if that fails (or the other way around)?

I'm asking, because the install CD is a CD-RW and will not contain the Ubuntu install image for long. I'd like to be able to install applications without relying on a CD.

---

### Post by defkewl on 2005-05-07
Add online repository via synaptic or type base-config from the command line.

---

### Post by Gentist on 2005-05-07
That did the trick. Thanks. :)

---

