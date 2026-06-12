---
title: "sudden system shutdown, /sbin/init missing, unable to boot"
date: 2016-12-11
forum: Virtualisation
---

### Post by Vedhas on 2016-12-11
[http://paste.ubuntu.com/23615092/](http://paste.ubuntu.com/23615092/)

System: Ubuntu 14.04 LTS virtual machine under VMWare Player on Windows 8.
------------------
Issue started when: I was running some Tensorflow LSTM code (heavy duty for the memory perhaps) on ubuntu and the system froze. I restarted my VM ignoring the warning about such restart, and it simply failed to boot. 

First issue: Completely blank black screen, not even a BIOS welcome!

What I tried: Did a system reboot of the host (windows 8).
-------
Issue 2: Now, while there was no longer a blank black screen, I could not get to Ubuntu. '/sbin/init: No such file or directory error' and also 'mounted file system with ordered data mode'. Complete message in the image below

[ATTACH=CONFIG]272660[/ATTACH]

One thing to note, I was also not able to get to BIOS (despite trying F2 and escape key multiple times as suggested on the first screen). I would always get to grub menu, where I can try to boot (enter key), change bootparams (e key), or enter grub command console (c key)
------------------
Counter: I launched LiveCD of the ubuntu, by providing path to local ISO file as a CD drive to VMWare Player. Tried repair using boot-repair as suggested here: [https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

My log here: [http://paste.ubuntu.com/23615092/](http://paste.ubuntu.com/23615092/)

shut down command did not shut the system down for like 2-3 minutes. So I turned it off ignoring the VMWare warning, and restarted the machine. Same error ('mounted file system with ordered data mode', /sbin/init etc.) now.

Kindly help!

---

### Post by howefield on 2016-12-11
Thread moved to the "*Virtualisation*" forum.

---

