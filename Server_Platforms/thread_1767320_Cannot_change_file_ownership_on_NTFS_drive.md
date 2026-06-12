---
title: "Cannot change file ownership on NTFS drive"
date: 2011-05-25
forum: Server Platforms
---

### Post by Hugh971 on 2011-05-25
Hi,

I'm in the process of migrating my server to Ubuntu Server 11.04 after my Server 2003 installation suffered a HDD failure. All my data is on an NTFS drive (not ideal but not much I can do about that). I can currently only read the disk as a user. root has ownership of everything on the disk. Whenever I try and change ownership of a file it doesn't bring up any errors but when running ls -l it shows that nothing has actually changed.

Any ideas on how to fix this? 

Could it be something in the fstab causing issues?

I can change ownership of files outside of that disk but nothing on it.


Thanks

Hugh

---

### Post by Morbius1 on 2011-05-25
Linux cannot change ownership or permissions of a mounted NTFS partition. It can only alter them at mount time. Post your fstab so we can see what's going on:
```
cat /etc/fstab
```

---

### Post by Hugh971 on 2011-05-28
Ah, that makes sense, I ended up changing my fstab and that fixed the problem. I'll eventually get round to formatting the disk as ext4 once I've backed it up somewhere else first.

Thanks

Hugh

---

