---
title: "Upgrading Gutsy to Hardy Question"
date: 2009-02-04
forum: Server Platforms
---

### Post by Barry53 on 2009-02-04
Hi,

I want upgrade a Gutsy server to Hardy server mainly because Hardy is LTS. I have read

[https://help.ubuntu.com/community/HardyUpgrades]("https://help.ubuntu.com/community/HardyUpgrades")

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/249340]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/249340")
 
Can I simply do
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

or do I still need to woory about the bug mentioned in the launchpad link above.

Thanks for your help

---

### Post by Barry53 on 2009-02-24
I answered my own question. I used update-manager-core which was already installed on my Gutsy server. I used 
```
sudo do-release-upgrade
```
and all went well. My Gutsy server was using kernel 2.6.14 not the reported 2.6.15 kernel that caused the update problems.

I did backup up my system first using sysrescuecd from [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page").

Hope this helps someone,

---

