---
title: "Redirection loop encountered on apt upgrade in 18.04"
date: 2018-07-10
forum: Server Platforms
---

### Post by nsummy on 2018-07-10
This has been happening to me for awhile now but for the life of me can't figure it out. I have 2 machines exhibiting the same behavior and I've narrowed it down to python related upgrades as some download fine. Here is the output, any ideas?

```
nsummy@brix1:~$ sudo apt upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
apport bind9-host dnsutils libbind9-160 libdns1100 libirs160 libisc169 libisccc160 libisccfg160 liblwres160 networkd-dispatcher python3-apport python3-distupgrade ubuntu-release-upgrader-core
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 355 kB/1,894 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://192.119.223.46:80/data/00841bce733f41fb/archive.ubuntu.com/ubuntu bionic-updates/main amd64 networkd-dispatcher all 1.7-0ubuntu3.2
Redirection loop encountered
Err:2 http://192.119.223.46:80/data/008494ced7400288/archive.ubuntu.com/ubuntu bionic-updates/main amd64 libisc169 amd64 1:9.11.3+dfsg-1ubuntu1.1
Redirection loop encountered
Err:3 http://192.119.223.46:80/data/0084e3ce4b411e09/archive.ubuntu.com/ubuntu bionic-updates/main amd64 ubuntu-release-upgrader-core all 1:18.04.19
Redirection loop encountered
Err:4 http://192.119.223.46:80/data/00846bcede41c59a/archive.ubuntu.com/ubuntu bionic-updates/main amd64 python3-apport all 2.20.9-0ubuntu7.2
Redirection loop encountered
E: Failed to fetch http://192.119.223.46:80/data/00841bce733f41fb/archive.ubuntu.com/ubuntu/pool/main/n/networkd-dispatcher/networkd-dispatcher_1.7-0ubuntu3.2_all.deb Redirection loop encountered
E: Failed to fetch http://192.119.223.46:80/data/008494ced7400288/archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc169_9.11.3+dfsg-1ubuntu1.1_amd64.deb Redirection loop encountered
E: Failed to fetch http://192.119.223.46:80/data/0084e3ce4b411e09/archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-core_18.04.19_all.deb Redirection loop encountered
E: Failed to fetch http://192.119.223.46:80/data/00846bcede41c59a/archive.ubuntu.com/ubuntu/pool/main/a/apport/python3-apport_2.20.9-0ubuntu7.2_all.deb Redirection loop encountered
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by ajgreeny on 2018-07-10
What was the output of command ```
sudo apt update
``` which you must run before the **sudo apt upgrade** command

---

### Post by VMC on 2018-07-10
Odd, but if you use one of those Redirect loop links:
> [COLOR=#000000][FONT=&amp]http://192.119.223.46:80/data/00841bce733f41fb/archive.ubuntu.com/ubuntu/pool/main/n/networkd-dispatcher/networkd-dispatcher_1.7-0ubuntu3.2_all.deb[/FONT][/COLOR]
Then go [here]("http://redirectcheck.com/index.php") and post it. It looks ok.

---

### Post by nsummy on 2018-07-24
> **ajgreeny said:**
> What was the output of command ```
sudo apt update
``` which you must run before the **sudo apt upgrade** command


Believe me, I've done that many times!

---

### Post by terve2 on 2018-09-22
I had same experience when I tried to run apt-get upgrade on my Ubuntu on Windows 10. I had no experience with Ubuntu laptop. After having errors, I ran same upgrade, and a few of the error downloads came OK. Second trial of upgrade gave full download and then the upgrade succeeded. I don't know why, but it seems better to run several times.

---

### Post by terve2 on 2018-10-04
In case, I make a VPN software off while using apt-get update / apt-get upgrade (dist-upgrade), because some of my ppa lists refuse to give upgrade files with a VPN on. It made me the error "redirection loop encountered". Then I typed "upgrade" four times without elimination of this error. So I restarted a VPN again, and typed "upgrade" again, it gave the last file to be downloaded. I don't know whether this VPN (while its state is off) made something with Ubuntu 18.04 (Ubuntu 16.04 never gave me this error with same VPN softaware).

---

