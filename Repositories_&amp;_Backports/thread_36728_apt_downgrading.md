---
title: "apt downgrading?"
date: 2005-05-24
forum: Repositories &amp; Backports
---

### Post by benplaut on 2005-05-24
is there any way to downgrade a package with apt? i installed the newest kernel update and now (yeah, the can't boot problem) i can only access the system by chroot'ing from the LiveCD. 

is there a (hopefully easy) way to downgrade with apt?  ](*,)

---

### Post by Xian on 2005-05-24
You just need to properly pin that package in your /etc/apt/preferences (if it doesn't exist then create it in a text editor). Here is a How-To that was written for Debian, but is applicable in Ubuntu as well. You will be interested in the section that is titled, 'HOW APT INTERPRETS PRIORITIES'.

[Apt Preferences](http://ccrma.stanford.edu/planetccrma/man/man5/apt_preferences.5.html)

---

### Post by mendicant on 2005-05-25
% sudo aptitude install <pkgname>=<version>
% sudo aptitude hold <pkgname>

This installs a particular version of the package, downgrading if necessary.  For instance, there are two versions of bzip2 available: 1.0.2-2ubuntu0.1 and 1.0.2-2.  To install the latter, you would use:
% sudo aptitude install bzip2=1.0.2-2

To check what versions are available, use apt-cache show <pkgname>

---

### Post by benplaut on 2005-05-25
thanks  :) 

solved my problems through the power of 










[SIZE=7]GUI!!![/SIZE]

 :twisted:

---

