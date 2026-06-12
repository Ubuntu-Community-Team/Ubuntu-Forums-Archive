---
title: "Hoary apt-get MD5Sum mismatch"
date: 2005-04-04
forum: Repositories &amp; Backports
---

### Post by HJB on 2005-04-04
Hi all, please help (or direct to thread) a noob
I got this whilst doing a sudo apt-get update.
Lots of stuff came down and then suddenly this:

Fetched 494kB in 3s (135kB/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  MD5Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  MD5Sum mismatch
Reading Package Lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


Once it gave this line also:
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Please help. What am I doing wrong?

Bye
H

---

### Post by TravisNewman on 2005-04-04
give it another try later and see if it still does that. It could be that they're changing something on the repos.

---

