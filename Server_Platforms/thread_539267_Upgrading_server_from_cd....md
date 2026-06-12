---
title: "Upgrading server from cd..."
date: 2007-08-31
forum: Server Platforms
---

### Post by macminiman on 2007-08-31
Hi,

I have a LAMP Ubuntu server (6.06 LTS) running on a dell laptop (for personal use nothing hard). It also has ubuntu-desktop installed. I was wondering whether I could download an alternative install server cd of 7.04 and somehow upgrade my current distro. I've looked around and I've only seen instructions on how to upgrade the client. Can somebody please give me step by step instructions on how to do this? 

Thanks in advance.

---

### Post by cdenley on 2007-08-31
I never tried this before, but I think you could just add the newer cd-rom in your /etc/apt/sources.list file with apt-cdrom, then...
```

apt-get update
apt-get dist-upgrade

```

---

### Post by dmizer on 2007-09-01
you cannot upgrade direct to feisty.  you must upgrade dapper to edgy, and edgy to feisty.

i strongly urge you to wait.  dapper makes a perfect server ... it's stable and i assume it's functioning properly for you.  just wait for the next LTS release feisty +2.  it's due out next april.  you'll be able to directly upgrade from dapper to the next LTS.

on a server ... wait as long as possible before doing software upgrades unless absolutely necessary.  dapper is good until 2011, there's no need to rush things.

---

