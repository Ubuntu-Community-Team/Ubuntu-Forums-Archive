---
title: "Suddenly major server issues and offline"
date: 2012-01-17
forum: Server Platforms
---

### Post by DarkSnake-Kobra on 2012-01-17
We got some major issues with our server running Ubuntu 11.10 x32 Server edition. Was working fine just a few hours ago then a spammer got into our forum and posted somethings then got some mysql errors then upon rebooting the whole thing went down.

> login as: darksnake-kobra
darksnake-kobra@192.168.1.2's password:
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-14-generic-pae i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue Jan 17 09:09:20 CST 2012

  System load:  0.0               Processes:           79
  Usage of /:   8.3% of 35.21GB   Users logged in:     0
  Memory usage: 40%               IP address for eth0: 192.168.1.2
  Swap usage:   0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)
Last login: Tue Jan 17 09:09:21 2012 from 
darksnake-kobra@SERVER:~$ sudo su
[sudo] password for darksnake-kobra:
sudo: Can't open /var/lib/sudo/darksnake-kobra/1: Read-only file system
root@SERVER:/home/darksnake-kobra# apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages/DiffInde                                                                             x
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.167 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources
  404  Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources
  404  Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages
  404  Not Found [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
  404  Not Found [IP: 91.189.92.177 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release)  re                                                                             name failed, Read-only file system (/var/lib/apt/lists/us.archive.ubuntu.com_ubu                                                                             ntu_dists_oneiric_Release -> /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dis                                                                             ts_oneiric_Release).

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main)                                                                             /source/Sources  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/univ](http://security.ubuntu.com/ubuntu/dists/oneiric-security/univ)                                                                             erse/source/Sources  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main)                                                                             /binary-i386/Packages  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/univ](http://security.ubuntu.com/ubuntu/dists/oneiric-security/univ)                                                                             erse/binary-i386/Packages  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/mai](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/mai)                                                                             n/source/Sources  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/uni](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/uni)                                                                             verse/source/Sources  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/mai](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/mai)                                                                             n/binary-i386/Packages  404  Not Found [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/uni](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/uni)                                                                             verse/binary-i386/Packages  404  Not Found [IP: 91.189.92.177 80]

E: Some index files failed to download. They have been ignored, or old ones used                                                                              instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock
root@SERVER:/home/darksnake-kobra# apt-get upgrade
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@SERVER:/home/darksnake-kobra# reboot
root@SERVER:/home/darksnake-kobra#
Broadcast message from darksnake-kobra@SERVER
        (/dev/pts/1) at 15:41 ...

The system is going down for reboot NOW!



This is the last login through putty.

---

### Post by volkswagner on 2012-01-17
Is /var full?

```
df
```

```
sudo du /var --max-depth=1 -h
```

---

### Post by DarkSnake-Kobra on 2012-01-17
> **volkswagner said:**
> Is /var full?

```
df
```

```
sudo du /var --max-depth=1 -h
```


I wouldn't think so. I can't even mount the file system as the picture shows so I'm not sure how to even run this. Plus sudo is having problems like I posted.

---

### Post by volkswagner on 2012-01-17
You may want to try booting a live cd to check your log files and hard drive to see if any partitions are full.

---

### Post by DarkSnake-Kobra on 2012-01-17
Right now I'm running Caine 2.5(based on Ubuntu 10.04) and checking things. If I do find anything odd how would I go about issuing the commands or cleaning var?

---

### Post by DarkSnake-Kobra on 2012-01-17
I'm having a heck of a time mounting an LVM volume. I was able to do it once, but now I just can't mount it. I've lvm2, but no luck.

---

### Post by volkswagner on 2012-01-18
See if this link helps.  It is rather old, but it is for LVM2.

[http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

---

### Post by DarkSnake-Kobra on 2012-01-18
That didn't work. 

> mount: wrong fs type, bad option, bad superblock on /dev/SERVER/root,
missing codepage or helper program, or other error

---

### Post by DarkSnake-Kobra on 2012-01-19
I was able to get it working.  Had to go under /dev/mapper/SERVER-root and run sudo mount SERVER-root which worked fine. Unfortunately I ended up switching to CentOS as I haven't been overly happy with Ubuntu Server as it seems to break easily.

---

### Post by CharlesA on 2012-01-20
> **DarkSnake-Kobra said:**
> I was able to get it working.  Had to go under /dev/mapper/SERVER-root and run sudo mount SERVER-root which worked fine. Unfortunately I ended up switching to CentOS as I haven't been overly happy with Ubuntu Server as it seems to break easily.
Use what works for you.

It sorta sounds like they used SQL injection or something. Hard to tell unless you had access to the logs.

---

### Post by DarkSnake-Kobra on 2012-12-27
I know this is old, but I ended up replacing that computer. The hard drive went bad. It's also a lot of work running a web server so I ended up not using it anymore as I don't seem to have what it takes to run one. Thanks for the help and all.

---

### Post by OliverHaslam on 2012-12-27
> **DarkSnake-Kobra said:**
> I know this is old, but I ended up replacing that computer. The hard drive went bad. It's also a lot of work running a web server so I ended up not using it anymore as I don't seem to have what it takes to run one. Thanks for the help and all.
 
Curious what you're doing for hosting now, or is the site no longer live?

---

### Post by DarkSnake-Kobra on 2012-12-27
I'm just doing a blog right now and using weebly for some of my projects. :)

---

