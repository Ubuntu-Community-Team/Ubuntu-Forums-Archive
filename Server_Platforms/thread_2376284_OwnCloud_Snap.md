---
title: "OwnCloud Snap"
date: 2017-11-01
forum: Server Platforms
---

### Post by johnwesley on 2017-11-01
I have Orange PI One with Ubuntu 16.04 Server installed  
I installed snapd
I tried to install owncloud snap

It gave this reply:
jwp1@orangepione:~$ sudo snap refresh
All snaps up to date.

jwp1@orangepione:~$ snap list
No snaps are installed yet. Try "snap install hello-world".

jwp1@orangepione:~$ sudo snap find nextcloud
Name               Version       Developer         Notes   Summary
nextcloudclient    2.2.4.8       ldsdevunofficial  -       Nextcloud Desktop Client
nextcloud          11.0.5snap2   nextcloud         -       Nextcloud Server - A safe home for all your data
wdl-nextcloud-pi2  16.04-0.17-1  canonical         gadget  Raspberry Pi 2 support package for WDL/Nextcloud
wdl-nextcloud      16.04-0.5-6   canonical         gadget  Raspberry Pi 3 support package for WDL/Nextcloud
spreedme           0.29.5snap1   nextcloud         -       Spreed.ME audio/video calls and conferences feature for the Nextcloud Snap
qownnotes          17.10.10      pbek              -       Plain-text file notepad with markdown support and ownCloud integration
mdns-hostname      0.0.1         welike            -       mDNS mini-daemon to published hostname.local

jwp1@orangepione:~$ sudo snap install nextcloud
error: cannot perform the following tasks:
- Run configure hook of "nextcloud" snap if present (run hook "configure": cannot open mount namespace of the init process (O_PATH): No such file or directory)

Thank You

---

### Post by Kirboosy on 2017-11-01
Alright. So I got my coffee and music. Here we go....

On 16.04 x86_64 minimal install snap install works flawlessly. I'm guessing there might be an issue with the ARM version of 16.04 or a compatibility issue with Nextcloud on ARM.

When I list my snaps I have one there called "core" I tried to remove it to see if it will break things but "core" is not removable. Perhaps if you find and install "core" that might help with the issue you are having? 

Caboose

P.S. Please look at using the [code tags]("https://ubuntuforums.org/misc.php?do=bbcode#code") in your post to make it more readable.

---

