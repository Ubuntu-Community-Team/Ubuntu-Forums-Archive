---
title: "untar saving permissions and owners"
date: 2011-03-04
forum: Server Platforms
---

### Post by ZenMasta on 2011-03-04
I backed up a website

tar –cvzf tarfilename myfolder
The permissoins/groups were
drwxrwxrwx 14 robbieb www-data       4096 Feb 28 10:08 myfolder


When i try to untar using root user it extracts like so.

drwx------  5 root    root           4096 Mar  4 10:53 myfolder

I have tried both with 
tar -xvzf myarchive.tar.gz
or
tar -xvzpf myarchive.tar.gz

they both do the same.

---

### Post by hawkmage on 2011-03-04
If you do a "tar ztvf myarchive.tar.gz" do the files listed have the correct ownership?

---

### Post by ZenMasta on 2011-03-04
It appears so. It's a big archive so obviously I can't check everything manually but the first few results I checked and they are the same.

---

### Post by ZenMasta on 2011-03-04
Actually let me correct that. It looks like the sub folders have the correct ownership and permissions. The foot folder does not.

---

### Post by hawkmage on 2011-03-04
So the issue is on the extract.

Very odd, I just tested it on Ubuntu 10.10 and it works perfectly for me.

---

### Post by ZenMasta on 2011-03-04
It's fine now. I don't know what I did different. But obviously I was doing something wrong before.

Thanks anyway Hawkmage

---

### Post by SeijiSensei on 2011-03-05
> **ZenMasta said:**
> It's fine now. I don't know what I did different. But obviously I was doing something wrong before.

You should to use the "p" option when creating archives with tar to "preserve" all the ownerships and permissions.  Create the archive with

```
tar cjvpf file.tar.bz2 /path
```

---

