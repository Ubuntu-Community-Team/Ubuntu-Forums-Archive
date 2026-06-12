---
title: "dpkg error occured"
date: 2009-04-28
forum: Security
---

### Post by jayashankar on 2009-04-28
i can't able to update & i can't able to use synaptic manager due to:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i try to configure manually
Then I run: sudo 'dpkg --configure -a' and I get the following:
 parse error, in file `/var/lib/dpkg/status' near line 610 package `exim4-config':

then i removed the file status using the code;
sudo rm /var/lib/dpkg/status

when i try to conf dpkg manually know its showing 

sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory

know i can't update or use synaptic manager.
what should i do know.
please guide me.

with regards,
jayashankar.m

---

