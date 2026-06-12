---
title: "apt-mirror what am I doing wrong?"
date: 2017-01-09
forum: Ubuntu/Debian BASED
---

### Post by mintmag on 2017-01-09
Hey guys. Does anyone here have any experience with apt-mirror. I've been trying to use it to set up a local repository using apt-mirror but for some reason I can't get it to work. I have of course backed up my sources.list and sources.list.d 

Here are the config files

sources.list
```
deb file:/mnt/c980c639-428d-44fa-b480-9f0c0651709d/home/pepermint-mirror/mirror/au.archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb file:/mnt/c980c639-428d-44fa-b480-9f0c0651709d/home/pepermint-mirror/mirror/au.archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb file:/mnt/c980c639-428d-44fa-b480-9f0c0651709d/home/pepermint-mirror/mirror/au.archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
deb file:/mnt/c980c639-428d-44fa-b480-9f0c0651709d/home/pepermint-mirror/mirror/au.archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse

```

peppermint.list
```
deb file:/mnt/c980c639-428d-44fa-b480-9f0c0651709d/home/pepermint-mirror/mirror/ppa.launchpad.net/peppermintos/p7-release/ubuntu xenial main
```
peppermint-respin.list
```
deb file:/mnt/c980c639-428d-44fa-b480-9f0c0651709d/home/pepermint-mirror/mirror/ppa.launchpad.net/peppermintos/p7-respin/ubuntu xenial main
```

Mirror.list
```
############# config ##################
#
 set base_path    /mnt/c980c639-428d-44fa-b480-9f0c0651709d/home/pepermint-mirror
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads  50   
set _tilde 0
#
############# end config ##############
deb http://ppa.launchpad.net/peppermintos/p7-respin/ubuntu xenial main
deb http://ppa.launchpad.net/peppermintos/p7-release/ubuntu xenial main 
deb http://au.archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse

#deb-src http://archive.ubuntu.com/ubuntu xenial main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu xenial-security main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu xenial-updates main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu xenial-proposed main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse

clean http://au.archive.ubuntu.com/ubuntu

```

I just can't access any programs that aren't already installed. Please let me know what it is that I'm doing wrong. This is what the output reads [https://drive.google.com/file/d/0Bwt4rSMJWa1DSXlhRkN5OU5JTlU/view](https://drive.google.com/file/d/0Bwt4rSMJWa1DSXlhRkN5OU5JTlU/view)

---

### Post by howefield on 2017-01-09
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by mintmag on 2017-01-09
Peppermint is being used for this example. Is that why it was moved?

---

### Post by howefield on 2017-01-09
> **mintmag said:**
> Peppermint is being used for this example. Is that why it was moved?

Of course.

> General Help
All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, UbuntuGnome and Ubuntu Mate.

You are welcome to post questions regarding other distributions with the caveat that if they are not named above they get here posted to the relevant section within the "Other OS Support and Projects" section.. 

> Other OS Support and Projects
This forum is for the support of other operating systems and other Linux distros. No official Ubuntu supported distro questions should be posted here. Please be aware this is not the best place to receive tech support for these OSs/Distros and users should look for official support channels for those systems. 

---

