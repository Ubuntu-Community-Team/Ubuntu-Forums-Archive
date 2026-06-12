---
title: "apt-get errors?"
date: 2005-05-16
forum: Repositories &amp; Backports
---

### Post by Cydo on 2005-05-16
Hi, 

I was hoping someone smarter than me could help me with this problem. I was trying to install kismet from a tutorial. When I got to the part where you install the ethereal-common client with apt, I got these errors.

```
root@Cam:/etc/apt # apt-get install ethereal-common
Reading package lists... Done
Building dependency tree... Done
Package ethereal-common is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package ethereal-common has no installation candidate

```

And I get this when I run apt-get update

```
root@Cam:/etc/apt # apt-get update
Get:1 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com hoary Release.gpg [189B]
Hit http://us.archive.ubuntu.com hoary Release
Get:5 http://security.ubuntu.com hoary-security Release [16.9kB]
Hit http://archive.ubuntu.com hoary Release
Hit http://us.archive.ubuntu.com hoary-updates Release
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit ftp://ftp.nerim.net stable Release.gpg
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Ign http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit ftp://ftp.nerim.net unstable Release.gpg
Hit http://security.ubuntu.com hoary-security/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit ftp://ftp.nerim.net testing Release.gpg
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Get:6 ftp://ftp.nerim.net stable Release [1348B]
Get:7 http://us.archive.ubuntu.com hoary/universe Packages [2853kB]
99% [7 Packages gzip 0] [6 Release 0/1348B 0%]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com hoary/universe Packages
  Sub-process gzip returned an error code (1)
Hit ftp://ftp.nerim.net unstable Release
Hit ftp://ftp.nerim.net testing Release
Hit ftp://ftp.nerim.net stable/main Packages
Hit ftp://ftp.nerim.net unstable/main Packages
Hit ftp://ftp.nerim.net testing/main Packages
Fetched 18.4kB in 4s (3739B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Any help as to what' s wrong or how I can fix this would be greatly appreciated. Thanks.

---

### Post by Xian on 2005-05-16
Something might be entered incorrectly in your sources list.
Please post the contents of the following file:

/etc/apt/sources.list

---

### Post by Cydo on 2005-05-16
I don't think I changed anything recently but you never know.

Contents of /etc/apt/sources.list

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
  deb http://us.archive.ubuntu.com/ubuntu hoary universe
  deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

  deb http://security.ubuntu.com/ubuntu hoary-security universe
  deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main
```

---

### Post by Xian on 2005-05-16
Okay, I used your source list on my box and it ran fine aside from some GPG errors on the nerim.net repos. Since I can not duplicate the error on my system using your own list file,  it is likely that you are simply encountering a network error during the download phase, which would be directly attributable to your ISP and/or current internet connection. Also, since you mentioned that you did not recall editing the source list recently this adds further credence to it being a network problem.

Short story: It will correct itself soon or perhaps your ISP is using a toady proxy.

---

