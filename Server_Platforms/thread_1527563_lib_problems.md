---
title: "lib problems"
date: 2010-07-09
forum: Server Platforms
---

### Post by michellez on 2010-07-09
I am trying to install some UPS software from [http://www.liebert.com/servicesupport_pages/ServiceSupport.aspx?x=multilink_download_lin](http://www.liebert.com/servicesupport_pages/ServiceSupport.aspx?x=multilink_download_lin)

```

$ sudo ./ML_40_004_Linux_x86.bin
Using /tmp for temporary storage.
Unpacking to /tmp/ML.tar...
Checksumming...
Extracting...
pwd=/tmp/ML

Please wait while the MultiLink installation starts...

./Setup install
* Checking kernel version (2.4.18 or later required)...
* Checking for glibc...
* Checking for libstdc++-libc6.2-2.so.3...

This product requires the GNU C++ Runtime Library (libstdc++-libc6.2-2.so.3)
or later. Your system must be upgraded before installation can proceed.

```

If I check what is present it seems correct as the following exists /usr/lib/libstdc++.so.6.0.13

But if I do the following, which surely this should mean newer is installed...? I'm confused :(

```
$ sudo apt-get install libstdc++6-4.4-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
libstdc++6-4.4-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

```

Thank you for your help!
Shell

---

### Post by Devi1903 on 2010-07-09
You also need to run
> sudo apt-get install libc6
to check libc6 is the latest version.
Also run
> sudo apt-get install libstdc++6
instead of
> sudo apt-get install libstdc++6-4.4-dev
to make sure libstdc is up to date and all libstdc packages are installed.

---

### Post by michellez on 2010-07-10
Hi and thanks

I did the following:

```
user@host:~/Downloads$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libc-bin libc-dev-bin libc6-dev libc6-i686
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc-bin libc-dev-bin libc6 libc6-dev libc6-i686
5 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
Need to get 10.8MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

```

which completed fine.

I then (I did what I did before because I thought it would help "show" the version installed exactly as the below doesn't show what version it thinks it is):

```
user@host:~/Downloads$ sudo apt-get install libstdc++6
Reading package lists... Done
Building dependency tree
Reading state information... Done
libstdc++6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

```

Back to the same again though:

```
user@host:~/Downloads$ sudo ./ML_40_004_Linux_x86.bin
Using /tmp for temporary storage.
Unpacking to /tmp/ML.tar...
Checksumming...
Extracting...
pwd=/tmp/ML

Please wait while the MultiLink installation starts...

./Setup install
* Checking kernel version (2.4.18 or later required)...
* Checking for glibc...
* Checking for libstdc++-libc6.2-2.so.3...

This product requires the GNU C++ Runtime Library (libstdc++-libc6.2-2.so.3)
or later. Your system must be upgraded before installation can proceed.

```

Thanks
Shell

---

### Post by michellez on 2010-07-12
Sorted!

```
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb        

sudo dpkg -i libstdc++2.10glibc2.2_2.95.4-24_i386.deb   
```

---

