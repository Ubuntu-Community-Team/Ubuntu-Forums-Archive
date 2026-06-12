---
title: "Ubuntu 18.0.4.6 install latest openssl"
date: 2022-09-20
forum: Server Platforms
---

### Post by dansss on 2022-09-20
Hello,

I've had a latest vulnerability scan and says that our openssl, libssl1.1 & libssl-dev is out of dates and needs updating

The versions we have are the following
Package                 Installed Version                                 Required Version
openssl    1.1.1j-1+ubuntu18.04.1+deb.sury.org+3     1.1.1-1ubuntu2.1~18.04.20
libssl1.1    1.1.1j-1+ubuntu18.04.1+deb.sury.org+3     1.1.1-1ubuntu2.1~18.04.20
libssl-dev    1.1.1j-1+ubuntu18.04.1+deb.sury.org+3     1.1.1-1ubuntu2.1~18.04.20

I've done all sorts of updates/upgrades but the version still does not change.

P.S I'm awful at Linux, so if you could help step by step that'll be amazing as I could probably work out the the resolution then

Thanks

---

### Post by LHammonds on 2022-09-20
The outdated factor here is not so much the individual components but the fact you are using Ubuntu Server 18.04.    Version 20.04 and 22.04 have since been released...of which have all updated sub-components including openssl

My 18.04 server (which I only have one left and scheduled for replacement with 22.04) shows the same thing you see:

```
openssl/bionic-updates,bionic-security,now 1.1.1-1ubuntu2.1~18.04.20 amd64 [installed]
```

On my 22.04 server, I see the newer components:

```
openssl/jammy-updates,jammy-security,now 3.0.2-0ubuntu1.6 amd64 [installed,automatic]
```

For someone that is not an OS programmer and not comfortable compiling code manually and resolving dependency issues (like myself), it would be unwise to try and manually patch individual sub-components without knowing how it could adversely impact other aspects of the system.

It would be best to create new servers using the current version of the OS and get the software installed and working on new system (which may mean learning config changes in the newer OS and newer applications).  Then migrate your data and make the new system replace the old.  This process is made ridiculously easy with virtualization.  It can be a bit more problematic if you only have one server and it is installed bare-metal.  In the case of a bare-metal install, I would make sure to test this upgrade path by trying it out first on my PC using virtualization (like VirtualBox) to install the new OS and see if you can get the new software working just like the old server....then you can document the steps needed to be performed on the bare-metal upgrade....thus reducing downtime and risk of not being familiar with the complete upgrade process.

LHammonds

---

### Post by dansss on 2022-09-20
Hi,

The version you posted is the latest which is what I want 
openssl/bionic-updates,bionic-security,now 1.1.1-1ubuntu2.1~18.04.20 amd64

but I have 
openssl1.0/bionic-updates,bionic-security 1.0.2n-1ubuntu5.10 amd64

It seems to be using a repo? from deb.sury.org but no idea what to do to get rid of that and install openssl from the normal way of updating

openssl version
OpenSSL 1.1.1j  16 Feb 2021 (Library: OpenSSL 1.1.1  11 Sep 2018)

---

### Post by LHammonds on 2022-09-20
Here is what I have for my repositories on my Ubuntu Server 18.04 LTS server in this file (with comment lines removed)

/etc/apt/sources.list
```

deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse

```

This is what's in my 20.04 LTS file:
/etc/apt/sources.list
```

deb http://us.archive.ubuntu.com/ubuntu/ focal main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ focal universe
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates universe
deb http://us.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
deb [arch=ppc64el,arm64,amd64] http://mirrors.accretive-networks.net/mariadb/repo/10.5/ubuntu focal main

```

This is what's in my 22.04 LTS file:
/etc/apt/sources.list
```

deb http://archive.ubuntu.com/ubuntu jammy main restricted
deb http://archive.ubuntu.com/ubuntu jammy-updates main restricted
deb http://archive.ubuntu.com/ubuntu jammy universe
deb http://archive.ubuntu.com/ubuntu jammy-updates universe
deb http://archive.ubuntu.com/ubuntu jammy multiverse
deb http://archive.ubuntu.com/ubuntu jammy-updates multiverse
deb http://archive.ubuntu.com/ubuntu jammy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu jammy-security main restricted
deb http://archive.ubuntu.com/ubuntu jammy-security universe
deb http://archive.ubuntu.com/ubuntu jammy-security multiverse

```

Don't make changes willy-nilly though.  I don't know what the consequences would be coming from whatever that repository is to a different one.  You will need to do research on changing repositories and make sure you BACKUP.

---

### Post by SeijiSensei on 2022-09-20
Also if you add repositories manually, it's best to create a separate file for each repo and place it in /etc/apt/sources.lists.d/. Give the file a ".list" extension, then run "sudo apt update". For instance, I have a file /etc/apt/sources.lists.d/google-chrome.list that has the line:
```
deb [arch=amd64] https://dl.google.com/linux/chrome/deb/ stable main
```

That method makes it easier to disable repositories. You just stick a hash mark ("#") in front of "deb" and run sudo apt update.

If you add a repository with "add-apt-repository" it will drop a ".list" file in /etc/apt/sources.lists.d/.

---

### Post by ian-weisser on 2022-09-20
> **dansss said:**
> 
Package                 Installed Version                                 Required Version
openssl    1.1.1j-1+ubuntu18.04.1+deb.sury.org+3     1.1.1-1ubuntu2.1~18.04.20
libssl1.1    1.1.1j-1+ubuntu18.04.1+deb.sury.org+3     1.1.1-1ubuntu2.1~18.04.20
libssl-dev    1.1.1j-1+ubuntu18.04.1+deb.sury.org+3     1.1.1-1ubuntu2.1~18.04.20


Your required versions are (correctly) from the Ubuntu repositories.

But your installed versions are non-Ubuntu versions. Looks like you added a PPA.

The problem is that those PPA-provided packages have a higher version number than the versions in the Ubuntu repository.

You could argue this with your auditor, but let's assume you want to revert to the Ubuntu-provided packages.

Edit your sources:
 - Disable the PPA.
 - Ensure you have "bionic-security" enabled
 - Ensure you have "bionic-updates" enabled
 - Then run "sudo apt update" because you just changed your sources

Next, specify the version you want installed.

```

sudo apt install openssl=1.1.1-1ubuntu2.1~18.04.20 libssl1.1=1.1.1-1ubuntu2.1~18.04.20 libssl-dev=1.1.1-1ubuntu2.1~18.04.20

```

Finally, remove those PPA files from your cache so your system is not tempted to reinstall them

```

sudo apt autoclean

```

---

