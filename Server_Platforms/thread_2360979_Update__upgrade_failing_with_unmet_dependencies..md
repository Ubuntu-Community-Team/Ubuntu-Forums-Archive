---
title: "Update / upgrade failing with unmet dependencies."
date: 2017-05-10
forum: Server Platforms
---

### Post by nethfel on 2017-05-10
Hi,

I've got an older Ubuntu server (12.04.5) that I would at some point like to upgrade to 14, but right now I'm stuck with a dependency problem doing an update/upgrade cycle.

uname -r:

```
3.2.0-126-generic-pae
```

Here's what I get for upgrade (update already run):

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.122.137) but 3.2.0.126.141 is installed
                     Depends: linux-headers-generic-pae (= 3.2.0.122.137) but 3.2.0.126.141 is installed
E: Unmet dependencies. Try using -f.

```

So I do an apt-get -f install:
```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-119-generic-pae linux-image-3.2.0-119-generic-pae
  linux-image-3.2.0-116-generic-pae linux-headers-3.2.0-113-generic-pae
  linux-image-3.2.0-111-generic-pae linux-headers-3.2.0-113
  linux-headers-3.2.0-120 linux-headers-3.2.0-118 linux-headers-3.2.0-119
  linux-headers-3.2.0-118-generic-pae linux-image-3.2.0-118-generic-pae
  linux-headers-3.2.0-120-generic-pae linux-image-3.2.0-115-generic-pae
  linux-image-3.2.0-120-generic-pae linux-image-3.2.0-113-generic-pae
  linux-image-3.2.0-110-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic-pae
The following packages will be upgraded:
  linux-generic-pae
1 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,724 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.122.137); however:
  Version of linux-image-generic-pae on system is 3.2.0.126.141.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.122.137); however:
  Version of linux-headers-generic-pae on system is 3.2.0.126.141.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

As you can see it's still complaining.  I used dpkg to remove a few old kernels (including 3.2.0.122 as the system is running 126) and still get the same error.

Any tips on how to clear this?  I've tried clearing the apt cache as well and that didn't change anything.

---

### Post by ian-weisser on 2017-05-10
Fixing this is trivial...if you are running a supported version of Ubuntu (you are not, anymore).

The upgrade error message tells you everything you need to know: Your kernel metapackage is out of date. This is a well-known byproduct of letting your /boot run out of space - you missed that upgrade.

All you need to do is apt-get --reinstall the kernel metapackage.
But wait...that will reinstall the obsolete metapackage, since you probably have the old deb sitting in your package cache.

So delete the old deb from your package cache first. You probably did this already when you were "clearing the apt-cache" (not sure what that means).
Then reinstall the kernel metapackage.

---

