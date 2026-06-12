---
title: "The following packages cannot be authenticated"
date: 2006-02-28
forum: Server Platforms
---

### Post by ashrack on 2006-02-28
recently whenever I try to install something or upgrade new packages I get the following authentication error:
```
tom@wraith:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  ubuntu-docs
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2366kB of archives.
After unpacking 426kB disk space will be freed.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  ubuntu-docs
Install these packages without verification [y/N]?

```

---

### Post by erjohan on 2007-10-19
For me it helped doing a apt-get update you can also check that you have installed the Ubuntu FTP keys with apt-key list.

* [Installing from unofficial repos](http://edseek.com/archives/2007/03/17/apt-key-gpg-key-import-on-ubuntu-and-debian/)

This is of course a very old post.. ;-)

---

