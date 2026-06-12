---
title: "data recovery"
date: 2018-06-18
forum: Security
---

### Post by wilfdell on 2018-06-18
Hi 
not sure if I'm in the right forum here, I hope so... 
I've got to try to recover data from a hard disk, I accidentally installed a bootable linux installation on it instead of my USB stick. 
Can anyone help me? 

Ta
    Wilf

---

### Post by joehk2018 on 2018-06-19
try test disk 

[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2018-06-19
If testdisk finds files that can be best case as it will find full file name.
       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 

You can also try photorec, but it only finds files by scanning entire drive for file by type and then only has extension, not full file name.
       [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
    
What was partitioning before and what is it now?
sudo parted -l

---

### Post by TheFu on 2018-06-23
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) is pretty comprehensive.
There is no silver bullet and tremendous work will be installed.

1000000x easier to have backups.

---

