---
title: "Primary drive filling randomly"
date: 2014-08-24
forum: Server Platforms
---

### Post by Edward_Collinson on 2014-08-24
Hi,

My file server keeps filling up the primary drive for no reason. The drive that is filling is 250GB and the file server part is saved on a 1tb software raid 1 array mounted to the primary disk.

I tried uninstalling things but Dkpg wont run because it can't save the auth file due to it being full :(

Any ideas?

~Ed

---

### Post by Edward_Collinson on 2014-08-24
This is the second time this has happened

---

### Post by Bashing-om on 2014-08-24
Edward_Collinson; Well;

2 things pop to mind.
1) /boot partition is full
2) Log files are run-a- muck with error reports .

So where is the space being consumed ?
```

df -h
df -i
cd /
sudo du -sx * | sort -n

``` 
If you need to drill down further, or around use 'cd' to move to a directory of interest then repeat the 'du' command.
The results are in megabytes.

Will relate a lot as to what is going on.

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

