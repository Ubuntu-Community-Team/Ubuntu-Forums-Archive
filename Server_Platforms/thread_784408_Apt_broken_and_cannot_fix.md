---
title: "Apt broken and cannot fix"
date: 2008-05-06
forum: Server Platforms
---

### Post by elvar on 2008-05-06
Hello, after running 'apt-get update' and then 'apt-get upgrade' I ended up with the following...

<root@example.com:lib/dpkg>apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  update-manager-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/30.4kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 23295 files and directories currently installed.)
Preparing to replace update-manager-core 1:0.81 (using .../update-manager-core_1%3a0.81.3_i386.deb) ...
Segmentation fault (core dumped)
dpkg: warning - old pre-removal script returned error exit status 139
dpkg - trying script from the new package instead ...
Segmentation fault (core dumped)
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.81.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 139
Segmentation fault (core dumped)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager-core_1%3a0.81.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I cannot seem to uninstall that package or reinstall it either. Anyone have any suggestions on how to fix this? This is Ubuntu Server 7.10 32bit.


Kind regards,
Elvar

---

### Post by bluefrog on 2008-05-06
/var/lib/dpkg/status and info should have files you should remove.
This should give you access to apt-get again.

Eventually apt-get clean afterwards.

James Dupin

---

### Post by tamoneya on 2008-05-06
you should also perform apt-get check```
sudo apt-get check
```This will check for any broken dependancies and should fix them.

---

### Post by elvar on 2008-05-06
> **tamoneya said:**
> you should also perform apt-get check```
sudo apt-get check
```This will check for any broken dependancies and should fix them.


apt-get check does not return any errors.

---

### Post by elvar on 2008-05-06
> **bluefrog said:**
> /var/lib/dpkg/status and info should have files you should remove.
This should give you access to apt-get again.

Eventually apt-get clean afterwards.

James Dupin


I will take a look at this. Should I be removing the entries for the 'update-manager-core'?


Elvar

---

### Post by bluefrog on 2008-05-06
all entries left in those folder are subject to prevent you from running apt-get. I believe it is a bit extreme but if nothing else works...

---

### Post by elvar on 2008-05-14
Ok, here's an update. I think the reason apt is failing is because python core dumps when run. Please see below...

```
>strace python
execve("/usr/bin/python", ["python"], [/* 12 vars */]) = -1 EFAULT (Bad address)
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Process 16873 detached

```

Any ideas on how to fix this?

---

