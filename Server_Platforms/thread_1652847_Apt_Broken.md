---
title: "Apt Broken"
date: 2010-12-25
forum: Server Platforms
---

### Post by ask21900 on 2010-12-25
I am in desperate need of some help from the community.  Hopefully somebody can help fix whatever I messed up!

When moving files over to a new server, a flaw in my script caused the entire /var to be moved.  Immediately after, I tried installing samba using apt.  I got the following errors:

```

/var/lib/dpkg/info/samba.postrm: 21: update-inetd: not found
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 21: update-inetd: not found
dpkg: error processing /var/cache/apt/archives/samba_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 21: update-inetd: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Processing triggers for man-db ...
/usr/bin/mandb: can't create index cache /var/cache/man/18532: No such file or directory
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/samba_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I then followed the instructions on several different threads/sites explaining how to fix this error.  I won't post everything that I did and the results because that would be too lengthy of a post, but in short, nothing changed.  Most suggestions had to do with deleting the samba threads in rc2.d and rc3.d and using ```
apt-get -f install
```

Trying to install anything via apt now yields:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-power-manager: Depends: devicekit-power (>= 011) but it is not installable
  usplash-theme-ubuntu: Depends: usplash (>= 0.5.30) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Following these instructions yields:

```

 sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fuse-utils gnome-power-manager indicator-application libappindicator0
  libblkid1 libdevmapper1.02.1 libfuse2 libntfs10 libparted0debian1 ntfsprogs
  samba udisks
Suggested packages:
  libparted0-dev libparted0-i18n openbsd-inetd inet-superserver smbldap-tools
  ldb-tools xfsprogs reiserfsprogs mdadm cryptsetup
The following packages will be REMOVED:
  usplash-theme-ubuntu
The following NEW packages will be installed:
  indicator-application libappindicator0 libntfs10 libparted0debian1 ntfsprogs
  udisks
The following packages will be upgraded:
  fuse-utils gnome-power-manager libblkid1 libdevmapper1.02.1 libfuse2 samba
6 upgraded, 6 newly installed, 1 to remove and 1162 not upgraded.
5 not fully installed or removed.
Need to get 0B/8,718kB of archives.
After this operation, 3,035kB of additional disk space will be used.
Do you want to continue [Y/n]? 
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
(Reading database ... 141347 files and directories currently installed.)
Preparing to replace samba 2:3.4.0-3ubuntu5.6 (using .../samba_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb) ...
 Removing any system startup links for /etc/init.d/samba ...
Unpacking replacement samba ...
/var/lib/dpkg/info/samba.postrm: 21: update-inetd: not found
dpkg: warning: old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 21: update-inetd: not found
dpkg: error processing /var/cache/apt/archives/samba_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 21: update-inetd: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Processing triggers for man-db ...
/usr/bin/mandb: can't create index cache /var/cache/man/18684: No such file or directory
Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/samba_2%3a3.4.7~dfsg-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I have tried EVERY solution that google had to offer over the past 3 days with no progress.  Please help!!  It is also worth noting that the server /var came from had ubuntu-desktop installed, and the server it went to (the one with this issue) is headless.  I should also mention that I have no physical access to this box, so I am trying to solve via ssh.  My datacenter charges quite a bit for anything that they do physically, so it is possible if required, but I would like to prevent that route.

Thanks in advance!

---

### Post by furlabs on 2010-12-26
> /var/lib/dpkg/info/samba.postrm: 21: update-inetd: not found

This tells you that you are missing a binary called update-inetd. Try specifying this as a solution:
```
apt-get -f install update-inetd
```
If that doesn't improve things, then remove samba with:
```
dpkg --remove samba
```
And then again run:
```
apt-get -f install
```
And see if you are still getting error messages.

---

### Post by ask21900 on 2010-12-26
That did not solve the problem.  Same errors occur.

---

### Post by ask21900 on 2010-12-27
Although this issue has not been solved, in order to get everything back up and running before my deadline, I did a clean install.

---

### Post by karthick87 on 2010-12-27
Try,
```
sudo apt-get autoclean
```
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ask21900 on 2010-12-27
> **karthick87 said:**
> Try,
```
sudo apt-get autoclean
```
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update && sudo apt-get upgrade
```

For those who find this thread in the future, I had already performed these steps with no result.

---

### Post by siriusdane on 2013-02-15
Just so you know I was having this problem and solved it the following way:

1) I tried to install update-inetd, but it said it was already installed.
```
sudo apt-get install update-inetd
```

2) I looked for it
```
sudo dpkg --search /usr/sbin/update-inetd
```

3) Went and actually looked for it
```
ls -l /usr/sbin/update-ine*
```

4) That showed me that a file called update-inetd.real was there, but no update-inetd, so I just made a symbolic link and it was done
```
sudo ln -s /usr/sbin/update-inetd.real /usr/sbin/update-inetd
```

---

