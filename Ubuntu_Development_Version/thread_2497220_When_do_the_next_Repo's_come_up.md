---
title: "When do the next Repo's come up?"
date: 2024-04-27
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2024-04-27
I know it's usually about 2-4 weeks... Just curious how long a break before starting to look for it.

I have a vested interest in my tests... In trying check the limits of some of the possibilities, and in trying to blow a few things up before then.

---

### Post by grahammechanical on 2024-04-27
What is the code name of 24.10? Two words beginning with the letter O. In the past I have changed the addresses in the sources.list file as soon as I have known the new code name. For a few days - going into a couple of weeks there is no activity. No thing to download. No packages to change. Then activity starts to pick up.

I am not sure if an installation that has the sources.list addresses changed will receive any updates going into 24.04 LTS. Perhaps they do. I ca not remember. The starting point of the next release is the code base of the new release. So, the new development release should receive the updates to noble.

Regards

---

### Post by corradoventu on 2024-04-28
What is the code name of 24.10? Two words beginning with the letter O. 
[https://discourse.ubuntu.com/t/24-10-name-proposals/44379](https://discourse.ubuntu.com/t/24-10-name-proposals/44379)

---

### Post by zebra2 on 2024-04-28
I intend to change my repos as soon as the name is announced.  I did that when Mantic released and Noble was announced and had info files next day. On the second day after I was getting updates that were not duplicated on the Mantic release. I really don't think the new development version will be getting updated from the previous since Noble will be done and not getting many updates. There was a lot of activity on the then Noble upstart especially with "Proposed" enabled. I have five laptop's and will keep two of them on Noble and one is a Windows 11 system. I have always used a development version as my primary desktop.

---

### Post by Claus7 on 2024-04-28
Hello,

FYI: [https://www.omgubuntu.co.uk/2024/04/ubuntu-24-10-codename-oracular-oriole](https://www.omgubuntu.co.uk/2024/04/ubuntu-24-10-codename-oracular-oriole)

Regards!

---

### Post by MAFoElffen on 2024-04-29
The Oracular Repo's are up now, but... They are just a copy of Noble, so far. No changes yet.

RE: [http://us.archive.ubuntu.com/ubuntu/dists/oracular/](http://us.archive.ubuntu.com/ubuntu/dists/oracular/)

---

### Post by jbicha on 2024-05-01
By the way, the Ubuntu Release Team uses public trackers. Here is the one for opening Ubuntu 24.10 development: [https://warthogs.atlassian.net/browse/RTMP-1612](https://warthogs.atlassian.net/browse/RTMP-1612)

---

### Post by corradoventu on 2024-05-01
Repos are up. You must just update;
/etc/apt/sources.list.d/ubuntu.sources
/usr/lib/os-release
/etc/lsb-release
and you are in the new release
```
corrado@corrado-n8-oo-0501:~$ inxi -Scx
System:
  Host: corrado-n8-oo-0501 Kernel: 6.8.0-31-generic arch: x86_64 bits: 64
    compiler: gcc v: 13.2.0
  Desktop: GNOME v: 46.0 Distro: Ubuntu 24.10 (Oracular Oriole)
corrado@corrado-n8-oo-0501:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=24.10
DISTRIB_CODENAME=oracular
DISTRIB_DESCRIPTION="Ubuntu 24.10"
corrado@corrado-n8-oo-0501:~$ cat /usr/lib/os-release
PRETTY_NAME="Ubuntu 24.10"
NAME="Ubuntu"
VERSION_ID="24.10"
VERSION="24.10 (Oracular Oriole)"
VERSION_CODENAME=oracular
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=oracular
LOGO=ubuntu-logo
corrado@corrado-n8-oo-0501:~$ cat /etc/apt/sources.list.d/ubuntu.sources
Types: deb
URIs: http://archive.ubuntu.com/ubuntu
Suites: oracular oracular-updates oracular-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg

Types: deb
URIs: http://security.ubuntu.com/ubuntu/
Suites: oracular-security
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
corrado@corrado-n8-oo-0501:~$ 


```

---

