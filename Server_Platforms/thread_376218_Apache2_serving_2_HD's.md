---
title: "Apache2 serving 2 HD's"
date: 2007-03-04
forum: Server Platforms
---

### Post by pseif1 on 2007-03-04
Ok, so I have set up a torrentflux server on an old small box to see how it works.  It works great.... but the hard drive it is on only has 4gb of space 2 of which are already taken. SO I want to put another hard drive in place of the cd rom for space (like a 40gb).  How do I tell apache to run off of hda but store on hdb, any help would be great. 

paul

---

### Post by kidders on 2007-03-04
Hi there,

The simplest thing to do would be to put /var/www on hdb. Don't forget to shut down Apache before you make the switch though!

---

### Post by SuSUntu on 2007-03-04
The DocumentRoot directive in your httpd.conf file (the Apache configuration file) is where you set the path for served pages / content.

You can set it to anything you want, whether it's 

```

DocumentRoot "/var/www/html"

```

or

```

DocumentRoot "/im/the/best/webmaster/httpdocs"

```

---

### Post by Mr. C. on 2007-03-04
> **pseif1 said:**
> Ok, so I have set up a torrentflux server on an old small box to see how it works.  It works great.... but the hard drive it is on only has 4gb of space 2 of which are already taken. SO I want to put another hard drive in place of the cd rom for space (like a 40gb).  How do I tell apache to run off of hda but store on hdb, any help would be great. 

paul

The other's have answered your question, but just for clarity.  Apache and other programs use file systems, not raw disk - ie. it knows nothing about hda, hdb, etc.

Once the disk is formatted into partitions, and a partition has a file system on it, you can mount that file system anywhere under the root file system you desire.

The, to programs, its just another directory.

This is a common enough confusion to beginners that it bears mentioning.

See Week 4 Notes at:
   [http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

MrC

---

