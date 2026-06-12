---
title: "problem in security repository May 4 2005?"
date: 2005-05-04
forum: Repositories &amp; Backports
---

### Post by stepore on 2005-05-04
hi folks, 

i'll think nothing of this if someone confirms that some ubuntu repository servers are down. if not, can someone tell me what is the problem with apt-get update. here are some errors below after i run update:

Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources [2752B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Sources
99% [11 Packages bzip2 0]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages - open (2 No such file or directory)
Fetched 62.6kB in 2s (23.4kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages - open (2 No such file or directory)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

