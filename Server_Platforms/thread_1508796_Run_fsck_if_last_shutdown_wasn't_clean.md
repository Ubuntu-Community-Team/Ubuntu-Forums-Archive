---
title: "Run fsck if last shutdown wasn't clean"
date: 2010-06-13
forum: Server Platforms
---

### Post by fox_cream on 2010-06-13
Hi - 

I have a file server that has a raid array with a jfs file system attached.  Whenever there is a power cut (quite frequently in our house), and the server is not shutdown cleanly, then the raid array is not automatically mounted since ubuntu doesn't know if the journal is clean.  I have to then manually run fsck and remount the partition by hand which is a bit annoying.  

Basically, does anybody know if fsck can be set to run if a non-clean shutdown has been detected, or failing that, on every boot?  Thanks in advance.

---

### Post by dapperdanny77 on 2010-06-13
check /etc/fstab
if the 6th column of the given filesystem is set to 0 then fsck is skipped during startup

this value defines the order fs are being checked during boot
the root fs usually is set to 1 - so you can set your fs to 2

---

### Post by cariboo on 2010-06-13
If you live in an area with frequent power problems, a ups could solve your problem. I recommend APC, as there is a utility in the repositories to control it. I have mine setup to shut the server down after 5 minutes with no power. Here in Canada you can get a 350W ups for under $60CDN. I have a 900W unit, as I have 2 systems connected to it.

I got mine several years ago as I was getting tired of having to fsck the raid array after every power bump. Since then except for a 22 hour outage due to an ice storm 2 years ago, my power has been very reliable.

---

