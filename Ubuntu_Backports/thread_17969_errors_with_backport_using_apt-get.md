---
title: "errors with backport using apt-get"
date: 2005-03-03
forum: Ubuntu Backports
---

### Post by Golovko on 2005-03-03
First here is my /etc/apt/sources.list:

> #############Ubuntu Hoary##############
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted


##############Ubuntu Security##############
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse


##############Backports ##############
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoarty-extras main
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoarty-extras universe
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoarty-extras multiverse
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoarty-extras restricted


Now attempts to apt-get update:

> 
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras Release.gpg
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/restricted Packages
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/main Packages
  404 Not Found
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/universe Packages
  404 Not Found
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/multiverse Packages
  404 Not Found
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/restricted Packages
  404 Not Found
Fetched 2B in 2s (1B/s)
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoarty-extras/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoarty-extras/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoarty-extras/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoarty-extras/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoarty-extras/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoarty-extras/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoarty-extras/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoarty-extras/restricted/binary-i386/Packages.gz)  404 Not Found
Reading Package Lists... Done
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoarty-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoarty-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoarty-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoarty-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoarty-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
 

Any help appreciated.

---

### Post by dcstar on 2005-03-03
[QUOTE=Golovko]First here is my /etc/apt/sources.list:
......
Any help appreciated.[/QUOTE]

##############Backports ##############
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoarty-extras main
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoarty-extras universe
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoarty-extras multiverse
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoarty-extras restricted

Shouldn't all of the "http://backports.ubuntuforums.org/backports" end with a "/"???

---

### Post by Golovko on 2005-03-04
I tried modifying portion of my sources.list to:

> ##############Backports ##############
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoarty-extras main
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoarty-extras universe
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoarty-extras multiverse
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoarty-extras restricted
 

Running apt-get update yielded the same errors.

Gol

---

### Post by Golovko on 2005-03-04
hoarty isn't a release, but hoary is..... 

Thanks,
Gol

---

### Post by Golovko on 2005-03-04
My updated sources.list

> 
#############Ubuntu Hoary##############
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted


##############Ubuntu Security##############
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse


##############Backports ##############
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras main
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras universe
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras multiverse
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras restricted
 

apt-get update:
> 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Sources
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
Get:3 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages [20B]
Get:4 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages [20B]
Get:5 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages [20B]
Get:6 [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages [20B]
Fetched 82B in 2s (35B/s)
Reading Package Lists... Done
 

And finally a directory listing of /var/lib/apt/lists:

> 
-rw-r--r--  1 root root    19876 Mar  4 09:04 archive.ubuntu.com_ubuntu_dists_hoary_Release
-rw-r--r--  1 root root      189 Mar  4 09:04 archive.ubuntu.com_ubuntu_dists_hoary_Release.gpg
-rw-r--r--  1 root root  3099830 Mar  4 08:33 archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages
-rw-r--r--  1 root root   984604 Mar  4 08:04 archive.ubuntu.com_ubuntu_dists_hoary_main_source_Sources
-rw-r--r--  1 root root   419494 Mar  1 15:06 archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages
-rw-r--r--  1 root root   222514 Feb 26 02:04 archive.ubuntu.com_ubuntu_dists_hoary_multiverse_source_Sources
-rw-r--r--  1 root root    23877 Feb 25 07:33 archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages
-rw-r--r--  1 root root     3837 Feb 22 19:34 archive.ubuntu.com_ubuntu_dists_hoary_restricted_source_Sources
-rw-r--r--  1 root root 11535235 Mar  4 06:33 archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages
-rw-r--r--  1 root root  4229132 Mar  4 06:04 archive.ubuntu.com_ubuntu_dists_hoary_universe_source_Sources
-rw-r--r--  1 root root        0 Mar  4 09:39 backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages
-rw-r--r--  1 root root        0 Mar  4 09:39 backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages
-rw-r--r--  1 root root        0 Mar  4 09:39 backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages
-rw-r--r--  1 root root        0 Mar  4 09:39 backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages
-rw-r-----  1 root root        0 Mar  4 09:39 lock
drwxr-xr-x  2 root root       48 Mar  4 09:39 partial
-rw-r--r--  1 root root    16851 Mar  4 09:04 security.ubuntu.com_ubuntu_dists_hoary-security_Release
-rw-r--r--  1 root root      189 Mar  4 09:04 security.ubuntu.com_ubuntu_dists_hoary-security_Release.gpg
-rw-r--r--  1 root root        0 Oct 27 16:03 security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages
-rw-r--r--  1 root root        0 Oct 27 16:03 security.ubuntu.com_ubuntu_dists_hoary-security_main_source_Sources
-rw-r--r--  1 root root        0 Oct 27 16:03 security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_binary-i386_Packages
-rw-r--r--  1 root root        0 Oct 27 16:03 security.ubuntu.com_ubuntu_dists_hoary-security_multiverse_source_Sources
-rw-r--r--  1 root root        0 Oct 27 16:03 security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages
-rw-r--r--  1 root root        0 Oct 27 16:03 security.ubuntu.com_ubuntu_dists_hoary-security_restricted_source_Sources
-rw-r--r--  1 root root        0 Oct 27 16:03 security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages
-rw-r--r--  1 root root        0 Oct 27 16:03 security.ubuntu.com_ubuntu_dists_hoary-security_universe_source_Sources
 

From the apt-get update it seems that the package lists downloaded are 20 bytes, but in the lists directory, none of the backport files have any info! This seems to agree with not being able to see any hoary-extra packages (like freenx) in dselect and also apt-get install freenx gives me :

E: Couldn't find package freenx

From an earlier freenx thread I used:

dselect --expert update quit

But that didn't change anything.

Gol

---

### Post by Tatsu on 2005-03-04
Hi all,

Same in my case.

Thanks in advance

---

### Post by hndrcks on 2005-03-04
Browse the backports repository - there aren't any files to apt-get at this point for hoary, except for hoary-extras-staging.

---

### Post by Golovko on 2005-03-04
That is the fix I needed. Changing hoary-extras to hoary-extra-staging in my sources.list yielded package lists that actually contained information. Like the above post says, browsing the repo just through http would have confirmed this.

I now have freenx up and working (writing this post using a freenx session from windows xp). Thanks all.

Gol

---

