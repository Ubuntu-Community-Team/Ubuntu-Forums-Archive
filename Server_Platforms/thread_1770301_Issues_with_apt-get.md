---
title: "Issues with apt-get"
date: 2011-05-29
forum: Server Platforms
---

### Post by am6465 on 2011-05-29
I just installed a fresh version of Ubuntu Server onto an old laptop I found (10.04.2 i386). 

I'm trying to use apt-get install and it can't find the package. I've run into this problem with other installs so I figured that all I had to due was add in the repositories to /etc/apt/sources.list

I run apt-get update and I get errors. This is the error I got before I edited sources.list

>>sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
  404  Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
  404  Not Found
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


I tried editing the sources.file, restarting the computer, and reinstalling the server OS and I still get the same thing. I know it's connected to the internet because "wget google.com" works fine.

Any ideas?


Thanks In Advance

---

### Post by volkswagner on 2011-05-29
I have had an occasion with similar symptoms.  My issue was due to no reference for "network" when setting up static ip in /etc/network/interfaces file.


What does your file look like?

```
cat /etc/network/interfaces
```

What is the output of:

```
host us.archive.ubuntu.com
```

---

### Post by am6465 on 2011-05-29
/etc/network/interfaces  reads:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp




>>host us.archive.ubuntu.com
us.archive.ubuntu.com has address 10.72.0.47
Host us.archive.ubuntu.com.mit.edu not found: 2(SERVFAIL)
Host us.archive.ubuntu.com.mit.edu not found: 2(SERVFAIL)

---

### Post by am6465 on 2011-05-30
I figured it out. The network I'm on requires me to register my mac address and I couldn't tell since the server has no UI.

---

