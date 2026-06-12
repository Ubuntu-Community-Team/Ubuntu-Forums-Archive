---
title: "Ubuntu 13.04 upgrade possible at all?"
date: 2016-07-18
forum: Server Platforms
---

### Post by rhelroolz on 2016-07-18
I have searched high and wide through the forum and other places online and everything that I've found has not worked for me. Basically, I am new to this company and they are running a very large Couchbase cluster across six Ubuntu 13.04 servers. Recently CB has been crashing due to kernel panic errors, which is a known issue for version 2.5.2 running on Ubuntu 13.04 and they have tasked me with upgrading this environment ASAP and without data loss and minimal downtime. 

All of the other environments (non-production) have been using 12.04 and I have used Ansible to easily upgrade to 14.04 and CB 4.1.1. However, when I come across the production servers, I am unable to do it. I know that 13.04 is end of life and everything I've tried so far, is not working and I am about at the point where I think this is not going to be possible without taking down each node one by one and manually upgrading the OS, CB and putting it into the cluster. But I wanted to see if anyone may have any ideas that would possibly help me, because doing that is going to be a very big pain and cause major impact on production. (I've only been here a month, so don't blame lack of planning on me! :P )

I've tried the following:

[https://help.ubuntu.com/community/SaucyUpgrades](https://help.ubuntu.com/community/SaucyUpgrades)

Updating the /etc/apt/sources.list

Does anyone have any idea, or suggestions? It would be greatly appreciated!

---

### Post by howefield on 2016-07-18
Thread moved to the "*Server Platform*" forum.

---

### Post by rhelroolz on 2016-07-18
MAY, key word MAY, have figured a hack around it.

Copy /etc/apt/sources.list from an existing Ubuntu 14.04 distro.
sudo apt-get update && sudo apt-get dist-upgrade

System now reports as 14.04...... I will update this thread in the future if the host actually works properly.

---

### Post by MAFoElffen on 2016-07-18
Accepted answer would be that for whatever sources are present in your sourcelist, that you change/replace the distro name to trusty... Remeber to cahnge your apt.conf to lts, to kept it limited to lts release upgrades.

Another way for intrim upgrades using archived versions of the interim's repo's.

---

