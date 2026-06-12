---
title: "Error upgrade Ubuntu Server 15.10 to 16.0.4"
date: 2017-02-15
forum: Server Platforms
---

### Post by ffelicissimo on 2017-02-15
I am trying to update my Ubunto 15.10 SERVER to the Ubuntu 16.0.4 and I am not getting it, I am doing the following steps:


```
1) sudo apt-get update
2) sudo apt-get upgrade
3) sudo apt-get dist-upgrade
4) sudo do-release-upgrade

**After the "do-release-upgrade" returned me the following error:**


$ sudo do-release-upgrade
[Sudo] password for fernando:
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[Http://www.ubuntu.com/releaseendoflife](Http://www.ubuntu.com/releaseendoflife)
0% [Connecting to br.archive.ubuntu.com (200.236.31.4)] Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apt/progress/text.py", line 183, in pulse
    If worker.status:
UnicodeDecodeError: 'utf-8' codec can not decode byte 0xe7 in position 19: invalid continuation byte
Getting: 1 Upgrade tool signature [836 B]
Getting: 2 Upgrade tool [1,265 kB]
8% [2 101 kB / 1,265 kB 7%] ^ CError in function stop
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apt/progress/text.py", line 233, in stop
    Def stop (self):
KeyboardInterrupt
Traceback (most recent call last):
  File "/ usr / bin / do-release-upgrade", line 165, in <module>
    Fetcher.run ()
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 277, in run
    If not self.fetchDistUpgrader ():
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcherCore.py", line 247, in fetchDistUpgrader
    Result = fetcher.run ()
SystemError
```

---

### Post by wildmanne39 on 2017-02-15
*Thread moved to **Server Platforms**.*

That means you can not upgrade your server you missed the deadline to do so before the repository for 15.10 was archived, now you need to install a fresh Ubuntu version.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by darkod on 2017-02-15
Use only LTS releases for servers, even for home servers. They have 5 years of support while the standard releases only have 9 months.

---

