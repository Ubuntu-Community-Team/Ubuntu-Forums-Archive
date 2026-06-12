---
title: "fstab and manual mount command"
date: 2010-01-31
forum: Server Platforms
---

### Post by fishcc on 2010-01-31
Seeking confirmation:   

If I have various options like noatime in the fstab (for an xfs file system - not sure if that is relevant)  

and 

I 'manually' mount  that filesystem (actually from a script) using 

mount /dev/xxx    /mnt/somedirectory

Will the 'manual' mount read the options from the fstab or do I have to put the options (with -o?) into the script to make the manual mount happen with those options?

Thanks!

---

### Post by SuperSonic4 on 2010-01-31
I believe you have to put them as options as only mount -a refers to fstab

---

### Post by falconindy on 2010-01-31
If your device and mount point match that of an entry in /etc/fstab, the mount command will read the options given in the fstab. Otherwise, you'll need to pass the options as an argument to the -o option via a comma delimited list.

For example:
```
mount /dev/sdd1 /mnt/music -o noatime,nobarrier,nodev
```

Note that you actually only need to match the mount point **or** the device in /etc/fstab if you're not specifying the entire mount manually.

---

### Post by fishcc on 2010-02-03
Thanks for that - the script actually states 

#mount  /dev/xxx  /mnt/directory 

-- so I guess it **would** read the fstab(?)   

On the other hand, I discovered that on this server, it's not actually in that particular fstab (by design or error, not sure) -- so will go for putting it in the script.

On last thing... does it matter if the -o option goes before or after the device and dir e.g.

#mount -o option /dev/xxx  /mnt/directory
or 
#mount /dev/xxx  /mnt/directory -o option

unfortunately -- live systems, so I can't just try it..:o

Cheers for your help guys!

---

