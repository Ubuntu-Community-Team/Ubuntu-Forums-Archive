---
title: "Problem with SAMBA share"
date: 2009-09-10
forum: Server Platforms
---

### Post by Vegan on 2009-09-10
OK I installed a disk to /disk2 for want of a folder name

I make 2 directories for shares

so I edit samba same as for directories locally, when I try to use the share I get an error that I cannot write to it

the folders are

/disk2/chess
/disk2/music

more are planned

ideas?

---

### Post by jonabyte on 2009-09-12
you will probably need to do more editing to the smb.conf file. You can use my example from my blog post for a basic samba server;

[http://jonabyte.wordpress.com/2009/04/06/quick-and-dirty-samba-setup-reprint/]("http://jonabyte.wordpress.com/2009/04/06/quick-and-dirty-samba-setup-reprint/")

---

### Post by Vegan on 2009-09-14
I tred adding "read only = no" and that seems to allow the mounted disk to work fine. Curios that local / was not affected.

seems to be a nuisance as the disk contains no home directories.

---

