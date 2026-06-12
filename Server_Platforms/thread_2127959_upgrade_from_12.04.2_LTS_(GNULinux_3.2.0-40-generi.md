---
title: "upgrade from 12.04.2 LTS (GNU/Linux 3.2.0-40-generic x86_64) to 12.10"
date: 2013-03-21
forum: Server Platforms
---

### Post by hirohitosan on 2013-03-21
Hi there.
I had on my U. server 12.04. I did ```
apt-get dist-upgrade
``` and now I have Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-40-generic x86_64). How can I upgrade to U. server 12.10?

I tried ```
do-release-upgrade
``` but it's says that no upgrade find or something like that.

Thank you!

---

### Post by Kirboosy on 2013-03-21
[LIST=1]
[*]Install update-manager-core if it is not already installed: 

sudo apt-get install update-manager-core 
[*]If and only if upgrading from an LTS release, then edit /etc/update-manager/release-upgrades and set Prompt=normal 
[*]Launch the upgrade tool: 

do-release-upgrade 
[*]Follow the on-screen instructions. 
[/LIST]

[Source for information]("https://help.ubuntu.com/community/QuantalUpgrades#Ubuntu_Servers_.28Recommended.29")

However, might I ask why you would want to perform an upgrade from LTS to a non-LTS? (Since its a server)

Good Luck!

---

### Post by hirohitosan on 2013-03-21
> **Caboose885 said:**
> [LIST=1]
However, might I ask why you would want to perform an upgrade from LTS to a non-LTS? (Since its a server)


I had no special reason. I just wanted to upgrade to latest features, but after I read a little I'll stay with 12.04.2 LTS. Anyway thank you for your reply, for make me read more about!

Cheers

---

