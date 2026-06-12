---
title: "Edgy sources.list woes."
date: 2007-01-16
forum: Repositories &amp; Backports
---

### Post by abzolutxero on 2007-01-16
this is kind of the culmination of a few different threads that i have posted, and haven't heard much on.

first, i attempted to install banshee from the deb file provided [HERE]("http://ubuntuforums.org/showthread.php?t=329260").

I receive the following error:

```
Error: Dependency is not satisfiable: boo
```

so i was recommended to run "sudo aptitude install boo" to install the dependency, however when i do run it, i get the following: 

```
abzolutxero@FreeSpirit:~$ sudo aptitude install boo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for boo
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

which i assume to mean that i don't have the correct repos installed.  so i stumbled my way onto the source-o-matic page, and created the following sources.list file, with my CD's added as  sources, as well as the repo listed for banshee (because i figured it would install the dependencies with it):

```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu edgy main restricted 
deb http://us.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

deb-src http://us.archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu edgy universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

deb-src http://us.archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://seveas.imbrandon.com edgy-seveas all 

deb-src http://seveas.imbrandon.com edgy-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse 

deb-src http://us.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

# Upstream Wine
deb http://wine.budgetdedicated.com/apt edgy main 

deb-src http://wine.budgetdedicated.com/apt edgy main

# Upstream Opera
deb http://deb.opera.com/opera etch non-free 

deb-src http://deb.opera.com/opera etch non-free

# bzr nightly snapshots
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./ 

deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Upstream Beryl
# GPG key: ed8a569e
deb http://www.beerorkid.com/compiz edgy main-edgy 

deb-src http://www.beerorkid.com/compiz edgy main-edgy

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ edgy free non-free 

deb-src http://medibuntu.sos-sts.com/repo/ edgy free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com edgy-commercial main 

deb-src http://archive.canonical.com edgy-commercial main


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://apebox.org/badgerexplosion ./

```

So there is problem 1.... what repos am i missing that i need?  

Problem 2 has to do with the repos i have.  when i run "sudo aptitude update" or "sudo apt-get update" i get alot of IGN's.   so i run synaptic, and get the following error... 

```
http://apebox.org/badgerexplosion/./Packages.gz: 301 Moved Permanently
http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz: Sub-process gzip returned an error code (1)
http://deb.opera.com/opera/dists/etch/non-free/source/Sources.gz: 404 Not Found

```

and 

```
W: GPG error: http://deb.opera.com etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
```

i know how to fix the latter problem, but i cant find the key for that repos.... however, i have no idea how to fix the upper set of issues....

I know this is alot, but i figured that it would be easier to post the whole story and see if i got any responses than to post 4 threads.... Any help will be appreciated!!

Regards,

Brad

---

### Post by HercuLeeZ on 2007-01-16
I seem to be having a the same problem since doing my first 'apt-get upgrade' after the initial install last night.  I have been trying to install 'eskuel', and can't seem to find it in the repositories.

Are their alternative mirrors that we should/could be downliading our binaries from?

---

### Post by abzolutxero on 2007-01-17
bump, hopefully someone in the know will see this.

---

