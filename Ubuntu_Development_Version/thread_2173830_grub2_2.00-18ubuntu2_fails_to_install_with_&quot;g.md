---
title: "grub2 2.00-18ubuntu2 fails to install with &quot;grub-probe: error: failed to get canonica"
date: 2013-09-11
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2013-09-11
I've been bitten by this. There's already a bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1223959](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1223959)

More specifically in my case it was the update to grub-pc. I don't actually have grub2 installed. It seems to be a meta-package. I haven't needed it anyway.

```
paul@lubuntu-64:~$ aptitude show grub2
Package: grub2                           
New: yes
State: not installed
Multi-Arch: foreign
Version: 2.00-18ubuntu2
Priority: extra
Section: universe/admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Uncompressed Size: 32.8 k
Depends: grub-pc (= 2.00-18ubuntu2), grub-common
Conflicts: grub2
Provides: grub2
Provided by: grub2
Description: GRand Unified Bootloader, version 2 (dummy package)
 This is a dummy transitional package to handle GRUB 2 upgrades.  It can be safely removed.
Homepage: http://www.gnu.org/software/grub/

paul@lubuntu-64:~$
```

---

### Post by Cavsfan on 2013-09-11
> **paul_in_london said:**
> I've been bitten by this. There's already a bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1223959](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1223959)

More specifically in my case it was the update to grub-pc. I don't actually have grub2 installed. It seems to be a meta-package. I haven't needed it anyway.

```
paul@lubuntu-64:~$ aptitude show grub2
Package: grub2                           
[COLOR=#ff0000]New: yes[/COLOR]
State: not installed
Multi-Arch: foreign
Version: 2.00-18ubuntu2
Priority: extra
Section: universe/admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Uncompressed Size: 32.8 k
Depends: grub-pc (= 2.00-18ubuntu2), grub-common
Conflicts: grub2
Provides: grub2
Provided by: grub2
Description: GRand Unified Bootloader, version 2 (dummy package)
 This is a dummy transitional package to handle GRUB 2 upgrades.  It can be safely removed.
Homepage: http://www.gnu.org/software/grub/

paul@lubuntu-64:~$
```

That's odd I show about the same thing exept the red.
```
cavsfan@cavsfan-MS-7529:~$ aptitude show grub2
Package: grub2                    
State: not installed
Multi-Arch: foreign
Version: 2.00-18ubuntu1
Priority: extra
Section: universe/admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Uncompressed Size: 32.8 k
Depends: grub-pc (= 2.00-18ubuntu1), grub-common
Conflicts: grub2
Provides: grub2
Provided by: grub2
Description: GRand Unified Bootloader, version 2 (dummy package)
 This is a dummy transitional package to handle GRUB 2 upgrades.  It can be safely removed.
Homepage: http://www.gnu.org/software/grub/

```

And yet it is installed:
```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy grub-pc
grub-pc:
  Installed: 2.00-18ubuntu1
  Candidate: 2.00-18ubuntu1
  Version table:
 *** 2.00-18ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/main amd64 Packages
        100 /var/lib/dpkg/status

```

```
cavsfan@cavsfan-MS-7529:~$ grep -e "menuentry " -e "submenu" /boot/grub/grub.cfg | sed 's/^[ \t]*//' | cut -d "'" -f1,2 | nl --starting-line-number=0
     0    menuentry "Precise Pangolin 12.04" {
     1    menuentry "Precise Pangolin 12.04 (Recovery Mode)" {
     2    menuentry "Quantal Quetzal 12.10" {
     3    menuentry "Quantal Quetzal 12.10 (Recovery Mode)" {
     4    menuentry "Raring Ringtail 13.04" {
     5    menuentry "Raring Ringtail 13.04 (Recovery Mode)" {
     6    menuentry "Saucy Salamander 13.10" {
     7    menuentry "Saucy Salamander 13.10 (Recovery Mode)" {
     8    menuentry "Linux Mint 13 Nadia" {
     9    menuentry "Linux Mint 13 Nadia (Recovery Mode)" {
    10    menuentry "Linux Mint 15 Olivia" {
    11    menuentry "Linux Mint 15 Olivia (Recovery Mode)" {
    12    menuentry "Windows 7" {
```

---

### Post by paul_in_london on 2013-09-11
Like me, you have gub-pc and (presumably) grub-common installed.

I think maybe you meant to post the output of:

```
paul@lubuntu-64:~$ apt-cache policy grub2
grub2:
  Installed: (none)
  Candidate: 2.00-18ubuntu2
  Version table:
     2.00-18ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ saucy-proposed/universe amd64 Packages
     2.00-18ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
paul@lubuntu-64:~$
```

Anyway, a fix is apparently in the pipeline. :)

---

### Post by jfernyhough on 2013-09-11
Just a quick one-liner as a workaround for now:

```
sudo apt-get install grub-common=2.00-18ubuntu1 grub-pc=2.00-18ubuntu1 grub-pc-bin=2.00-18ubuntu1 grub2-common=2.00-18ubuntu1
```

---

### Post by Cavsfan on 2013-09-11
> **paul_in_london said:**
> Like me, you have gub-pc and (presumably) grub-common installed.

I think maybe you meant to post the output of:

```
paul@lubuntu-64:~$ apt-cache policy grub2
grub2:
  Installed: (none)
  Candidate: 2.00-18ubuntu2
  Version table:
     2.00-18ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ saucy-proposed/universe amd64 Packages
     2.00-18ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
paul@lubuntu-64:~$
```

Anyway, a fix is apparently in the pipeline. :)

You are right! :) grub2 is not installed.
```
cavsfan@cavsfan-MS-7529:~/Downloads$ apt-cache policy grub2
grub2:
  Installed: (none)
  Candidate: 2.00-18ubuntu1
  Version table:
     2.00-18ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages

```

I try to keep my grub installed on a healthy Ubuntu like 13.04 because I hate seeing grub rescue and believe me I have seen it a "couple" of times. :)
Another reason I like to have more than one install. Today's updates borked my flashback session - no panels and weird errors.

Hopefully this too will be fixed. :)

---

### Post by paul_in_london on 2013-09-11
Fixed now with latest updates.

---

### Post by paul_in_london on 2013-09-11
```
paul@lubuntu-64:~$ apt-cache policy grub2
grub2:
  Installed: (none)
  Candidate: 2.00-18ubuntu3
  Version table:
     2.00-18ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ saucy-proposed/universe amd64 Packages
     2.00-18ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
```

---

### Post by Cavsfan on 2013-09-11
Not too sure about that grub2 file I am in Raring 13.04

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy grub2
grub2:
  Installed: (none)
  Candidate: 2.00-13ubuntu3
  Version table:
     2.00-13ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ raring/universe amd64 Packages

```

---

