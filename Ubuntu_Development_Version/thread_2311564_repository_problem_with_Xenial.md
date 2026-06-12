---
title: "repository problem with Xenial"
date: 2016-01-28
forum: Ubuntu Development Version
---

### Post by luca-barazzuol on 2016-01-28
Hi,

I've just installed xenial-desktop-amd6420160127.iso in a virtual box machine (on U15.10).
If I try to make an update I got this error:
```

sudo apt-get update
[sudo] password for luke: 
Get:2 http://it.archive.ubuntu.com/ubuntu xenial InRelease [227 kB]            
Get:1 http://archive.canonical.com/ubuntu xenial InRelease [11,5 kB]      
Get:3 http://archive.canonical.com/ubuntu xenial/partner amd64 Packages [1.717 B]
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:5 http://it.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Get:6 http://archive.canonical.com/ubuntu xenial/partner i386 Packages [2.120 B]
Ign:7 http://archive.canonical.com/ubuntu xenial/partner Translation-en  
Hit:8 http://it.archive.ubuntu.com/ubuntu xenial-backports InRelease     
Get:9 http://it.archive.ubuntu.com/ubuntu xenial/main Sources [1.129 kB]  
Ign:7 http://archive.canonical.com/ubuntu xenial/partner Translation-en        
Err:7 http://archive.canonical.com/ubuntu xenial/partner Translation-en        
  404  Not Found [IP: 91.189.92.150 80]
Err:9 http://it.archive.ubuntu.com/ubuntu xenial/main Sources
  Hash Sum mismatch
Get:10 http://it.archive.ubuntu.com/ubuntu xenial/restricted Sources [7.236 B]
Get:11 http://it.archive.ubuntu.com/ubuntu xenial/universe Sources [7.634 kB]
Ign:11 http://it.archive.ubuntu.com/ubuntu xenial/universe Sources             
Get:12 http://it.archive.ubuntu.com/ubuntu xenial/multiverse Sources [178 kB]  
Get:13 http://it.archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1.481 kB]
Err:13 http://it.archive.ubuntu.com/ubuntu xenial/main amd64 Packages          
  Hash Sum mismatch
Get:14 http://it.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1.477 kB]
Err:14 http://it.archive.ubuntu.com/ubuntu xenial/main i386 Packages           
  Hash Sum mismatch
Get:15 http://it.archive.ubuntu.com/ubuntu xenial/main Translation-en [854 kB] 
Get:16 http://it.archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages [15,9 kB]
Get:17 http://it.archive.ubuntu.com/ubuntu xenial/restricted i386 Packages [16,2 kB]
Get:18 http://it.archive.ubuntu.com/ubuntu xenial/restricted Translation-en [4.302 B]
Get:19 http://it.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7.219 kB]
Err:19 http://it.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages      
  Hash Sum mismatch
Get:11 http://it.archive.ubuntu.com/ubuntu xenial/universe Sources [7.634 kB]  
Err:11 http://it.archive.ubuntu.com/ubuntu xenial/universe Sources             
  Hash Sum mismatch
Fetched 22,1 MB in 1min 20s (274 kB/s)                                         
Reading package lists... Done
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/xenial/partner/i18n/Translation-en  404  Not Found [IP: 91.189.92.150 80]
W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/xenial/main/source/Sources.bz2  Hash Sum mismatch
W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/xenial/universe/source/Sources.gz  Hash Sum mismatch
W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/Packages.bz2  Hash Sum mismatch
W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/xenial/main/binary-i386/Packages.bz2  Hash Sum mismatch
W: Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-amd64/Packages.bz2  Hash Sum mismatch
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

And trying to install "mc" (never had a problem to install it on Ubuntu) I got this error:

```
sudo apt-get install mc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mc' has no installation candidate
luke@luke-uBeta:~$ 


```

Any ideas to solve the problem?

LuKe

---

### Post by zika on 2016-01-28
1. You've caught repo in state of transition. Try again.
2. Try with main repo since local (it in your case) might not be up-to date.
3. Do You have same repos at different locations enabled at the same time? That could be wrong...

---

### Post by sammiev on 2016-01-28
I just updated and all is well at this time. :)

---

### Post by philinux on 2016-01-29
> **sammiev said:**
> I just updated and all is well at this time. :)

Yep same here no issues at all. Very boring. ;)

---

### Post by luca-barazzuol on 2016-01-31
You were right. I tried today and it works fine.

Thanks

LuKe

---

