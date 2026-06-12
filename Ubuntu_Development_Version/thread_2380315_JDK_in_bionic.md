---
title: "JDK in bionic?"
date: 2017-12-15
forum: Ubuntu Development Version
---

### Post by Kris_M on 2017-12-15
sudo apt-get install software-properties-common
```
kris@kris-Z97X-UD3H:~$ java -versionopenjdk version "1.8.0_151"
OpenJDK Runtime Environment (build 1.8.0_151-8u151-b12-1-b12)
OpenJDK 64-Bit Server VM (build 25.151-b12, mixed mode)
kris@kris-Z97X-UD3H:~$ sudo apt-get install software-properties-common
[sudo] password for kris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
software-properties-common is already the newest version (0.96.24.17).
software-properties-common set to manually installed.
The following packages were automatically installed and are no longer required:
  libcdio16 libical2 libixml10 libupnp10 libx265-130
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kris@kris-Z97X-UD3H:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcdio16 libical2 libixml10 libupnp10 libx265-130
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 13.0 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 271739 files and directories currently installed.)
Removing libcdio16:amd64 (0.94-1) ...
Removing libical2:amd64 (2.0.0-4) ...
Removing libupnp10:amd64 (1:1.8.2-3) ...
Removing libixml10:amd64 (1:1.8.2-3) ...
Removing libx265-130:amd64 (2.5-2) ...
Processing triggers for libc-bin (2.26-0ubuntu2) ...
kris@kris-Z97X-UD3H:
```


sudo add-apt-repository ppa:webupd8team/javasee attached picsudo apt-get update
see attached pic
```
kris@kris-Z97X-UD3H:~$ java -versionopenjdk version "1.8.0_151"
OpenJDK Runtime Environment (build 1.8.0_151-8u151-b12-1-b12)
OpenJDK 64-Bit Server VM (build 25.151-b12, mixed mode)
kris@kris-Z97X-UD3H:~$ sudo apt-get update
Hit:1 http://archive.canonical.com/ubuntu bionic InRelease
Hit:2 http://archive.canonical.com bionic InRelease                            
Get:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease [235 kB]            
Hit:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:6 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Hit:7 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Hit:8 https://repo.skype.com/deb stable InRelease                              
Ign:9 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic InRelease        
Get:10 http://us.archive.ubuntu.com/ubuntu bionic/main i386 Packages [1,007 kB]
Hit:11 http://dl.google.com/linux/chrome/deb stable Release                    
Get:12 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1,011 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 DEP-11 Metadata [436 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64 Icons [261 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu bionic/universe i386 Packages [8,319 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [8,353 kB]
Err:18 http://ppa.launchpad.net/webupd8team/java/ubuntu bionic Release         
  404  Not Found
Get:19 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 DEP-11 Metadata [2,938 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64 Icons [8,228 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu bionic/multiverse amd64 DEP-11 Metadata [40.7 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64 Icons [197 kB]
Reading package lists... Done                                 
E: The repository 'http://ppa.launchpad.net/webupd8team/java/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
kris@kris-Z97X-UD3H:~$ java -version
openjdk version "1.8.0_151"
OpenJDK Runtime Environment (build 1.8.0_151-8u151-b12-1-b12)
OpenJDK 64-Bit Server VM (build 25.151-b12, mixed mode)



```

try anyway

```
kris@kris-Z97X-UD3H:~$ sudo apt-get install oracle-java8-installerReading package lists... Done
Building dependency tree       
Reading state information... Done
Package oracle-java8-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'oracle-java8-installer' has no installation candidate
kris@kris-Z97X-UD3H:~$ 



```

any ideas how to get around this error?

EDIT: NOTE: According to Oracle this is the latest...  Need JDK to build ROM for phone.
Thanks.

---

### Post by cariboo on 2017-12-15
Change bionic to artful:

> The repository 'http://ppa.launchpad.net/webupd8team/java/ubuntu **bionic** Release' does not have a Release file.

---

### Post by Kris_M on 2017-12-17
thanks!

---

