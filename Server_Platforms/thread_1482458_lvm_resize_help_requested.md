---
title: "lvm resize help requested"
date: 2010-05-13
forum: Server Platforms
---

### Post by xkaliburx on 2010-05-13
I have server setup the way I wanted, (running u9.10 inside esxi 4) and making a redundant backup except I forgot when I partitioned so the original has a ;
/ 30GB
/80 GB for database

the new server has /110 and the DBA is all complaining (yea this was my oversight).  I forgot it was lvm, I booted the VM off gparted but it doesn't support LVM.  I am downloading the live u10 desktop live and will try to boot off that, but that d/l and move to the esx will take a while so thought I might get a faster response here.

So basically I want to shrink the 100 to 30, then make a new partution for the 80 left.  I dont think this can be done booting into the OS right?  If so how!  If not, can booting off a live server-cd have a rescue type mode again what commands to help.

lastly, if none of the above, will the u10 live cd have a nice gui I can see/mount and do the deed?

Tnx

---

