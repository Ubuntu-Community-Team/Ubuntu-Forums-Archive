---
title: "Perl modules not installing"
date: 2007-04-03
forum: Server Platforms
---

### Post by jsaumer on 2007-04-03
Hello,

I am running Ubuntu Server 6.10.  I am getting the following error for every perl module I try to install:

```

Writing Makefile for File::HomeDir
 -- NOT OK

```

I do have make installed.  Do I need to check somewhere to make sure that it is looking at the right path for make?

Thanks in advance
jsaumer

---

### Post by Antarell on 2007-04-23
I am having the same problem on 7.04, I have googled my fingures to the bone with no joy... HELP!!!!

---

### Post by llamakc on 2007-04-23
This doesn't solve the problem you're having compiling but you're aware that many perl modules are available via apt, right?

```

root@llamakc:/etc/postfix# apt-cache search perl | grep home
libfile-homedir-perl - Get the home directory for yourself or other users in Perl

```

This installs (on Feisty)

```

root@llamakc:/etc/postfix# apt-cache policy !$
apt-cache policy libfile-homedir-perl
libfile-homedir-perl:
  Installed: 0.56-1.1
  Candidate: 0.56-1.1
  Version table:
 *** 0.56-1.1 0
        500 http://archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```

---

