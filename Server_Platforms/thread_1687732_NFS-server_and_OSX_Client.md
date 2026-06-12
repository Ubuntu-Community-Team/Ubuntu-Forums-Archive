---
title: "NFS-server and OSX Client"
date: 2011-02-14
forum: Server Platforms
---

### Post by JonCCrawley on 2011-02-14
I have OSX 10.6.3 and a Ubuntu 10.10 Server
OSX-10.0.1.90
Server 10.0.1.100
NFS- /home/user/crawley-server


I have successfully mounted my NFS on my mac, but in the finder when i copy in an directory i get the error. *"The operation can’t be completed because you don’t have permission to access some of the items."*


This is the code for my /etc/exports 
```

/home/user/crawley-server 10.0.1.100(rw,sync,no_subtree_check,insecure)
/home/user/crawley-server 10.0.1.101(rw,sync,no_subtree_check,insecure)
**/home/user/crawley-server 10.0.1.90(rw,all_squash,anonuid=1000,anongid=1000,insecure)**

```

how can i fix this?

---

### Post by slimjim1520 on 2011-02-14
me and you were doing the same. I found that the ONLY way i can mount the nfs on mac OS X was by the following command

```
 mount -o nolock Server-ip:/share
```

after that i never saw an "error 36" or "YOU DO NOT HAVE PERMISSION"

Also think about it tho. When you create a new folder in ubuntu server what do you have to do ??

```
sudo mkdir
```

---

### Post by JonCCrawley on 2011-02-14
thank you i spent like 2 days trying to mount it in the disk utility.

all is fixed

---

### Post by slimjim1520 on 2011-02-14
make sure you mark it as solved

---

