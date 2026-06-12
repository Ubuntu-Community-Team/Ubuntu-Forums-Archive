---
title: "Help trying to update Ubuntu 16.04 Server"
date: 2018-07-29
forum: Virtualisation
---

### Post by Robert_Boutin on 2018-07-29
I've googled this and the commonly found solution doesn't work for me (typical is [https://ubuntuforums.org/showthread.php?t=2396814&highlight=problem+mergelist](https://ubuntuforums.org/showthread.php?t=2396814&highlight=problem+mergelist)).

I'm running six Ubuntu 16.04 Server VMs in VirtualBox.  Recently, on three of them, apt-get update returns:

```
root@share:/home/user# apt-get update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Hit:5 [http://ppa.launchpad.net/certbot/certbot/ubuntu](http://ppa.launchpad.net/certbot/certbot/ubuntu) xenial InRelease
Hit:6 [http://ppa.launchpad.net/ondrej/apache2/ubuntu](http://ppa.launchpad.net/ondrej/apache2/ubuntu) xenial InRelease
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```
apt-get dist-upgrade doesn't update any packages.  When I try the fix in the link above, apt-get dist-upgrade returns:
```
root@share:/home/rboutin# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-4.4.0-131-generic : Depends: linux-headers-4.4.0-131 but it is not installed
 linux-image-generic : Depends: linux-image-extra-4.4.0-131-generic but it is not installed
                       Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.
```

The other VMs seem to update ok.  Any other ideas on what the problem might be?  Thanks a lot.
```
root@share:/home/user# uname -r
4.4.0-130-generic
```
```
/etc/apt/sources.list
#
# deb cdrom:[Ubuntu-Server 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801)]/ xenial main restricted
# deb cdrom:[Ubuntu-Server 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801)]/ xenial main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```

---

### Post by oldfred on 2018-07-29
Moved to virtualization sub-forum where users may know servers & virtual installs.

But do all your servers have the ppas? Often a ppa is or becomes an issue.
Look for ppa in /etc/apt/sources.list.d. You can see if that is issue by commenting those out, resetting update with the suggested *sudo* *apt-get -f install.*

---

### Post by Robert_Boutin on 2018-07-30
I have these files in /etc/apt/sources.list.d:

-rw-r--r-- 1 root root 205 Jul 29 22:28 certbot-ubuntu-certbot-xenial.list
-rw-r--r-- 1 root root 205 Jul 29 22:29 certbot-ubuntu-certbot-xenial.list.save
-rw-r--r-- 1 root root 133 Jul 29 21:40 ondrej-ubuntu-apache2-xenial.list

I commented all out but unfortunately the result was the same.

---

### Post by Robert_Boutin on 2018-08-02
Does anybody have any ideas on how to fix this issue?  Commenting out the ppa's didn't seem to help.

---

### Post by oldfred on 2018-08-02
I do not know virtual installs and then what may be unique.

It looks like everything is xenial.

Did you run this to run a repair? 
*sudo* [I]apt-get -f install
[/I]
Exactly what error messages do you get?

---

### Post by steeldriver on 2018-08-02
EDIT: *n/m seems like you fixed the initial package header error with your original link*

---

### Post by Robert_Boutin on 2018-08-02
```
Here is the output after running *rm /var/lib/apt/lists/* -vf *and then [I]apt-get -f install:
[/I]
[EMAIL="root@share:/home/user"]root@share:/home/user[/EMAIL]# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-128 linux-headers-4.4.0-128-generic linux-image-4.4.0-128-generic linux-image-extra-4.4.0-128-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.4.0-131 linux-image-extra-4.4.0-131-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-131 linux-image-extra-4.4.0-131-generic
0 upgraded, 2 newly installed, 0 to remove and 26 not upgraded.
7 not fully installed or removed.
Need to get 0 B/46.5 MB of archives.
After this operation, 227 MB of additional disk space will be used.
Do you want to continue? [Y/n]Y
Use of uninitialized value $value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 65, <__ANONIO__> line 1.
Use of uninitialized value $item in hash element at /usr/share/perl5/Debconf/DbDriver/File.pm line 85, <__ANONIO__> chunk 14.
E: Invalid archive signature
E: Internal error, could not locate member control.tar.{lz4gzxzbz2lzma}
E: Prior errors apply to /var/cache/apt/archives/linux-headers-4.4.0-131_4.4.0-131.157_all.deb
debconf: apt-extracttemplates failed: No such file or directory
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'amd64-microcode' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
[EMAIL="root@share:/home/user"]root@share:/home/user[/EMAIL]#
```

---

### Post by Robert_Boutin on 2018-08-04
I have no idea where to head with this.  Any ideas on what to try next?  Thanks

---

### Post by Robert_Boutin on 2018-08-21
Well, I was able to get one of my VMs working correctly but the same fix didn't work on the others.  The only thing that I could get to work was to do a do-release-upgrade which upgraded them to 18.04 Server LTS.  They are now updating properly, although it bothers me not understanding why exactly.

---

