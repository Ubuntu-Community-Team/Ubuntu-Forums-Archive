---
title: "upgrade 10.04  to 10.10 will I have to install the web sites again?"
date: 2011-01-07
forum: Server Platforms
---

### Post by Bushcraft Bill on 2011-01-07
will - sudo apt-get upgrade - to 10.10 server wipe out everything that I have on 10.04 system?

I don't want to start from scratch again just want to make sure before I upgrade any tips hints or downfalls I should know about for the upgrade?

I have run the update today for 10.04

Bill

---

### Post by sysabod on 2011-01-07
actually i never succeed to upgrade in your way,every time i tried,it just said

[HTML]root@sysabod-laptop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? [/HTML]

how can that be 0B addition disk space will be used ? It means nothing to be done.

Any thoughts ?:confused:

---

### Post by HugoSerrano on 2011-01-07
sudo apt-get dist-upgrade 

But do you need to do the upgrade? 10.04 it's LTS, that means it as support for Long Term, so it's better for servers.

Anyway, your server will be upgraded, it's not a clean install! But you may find some configurations problems... or not :-P

Regards.

---

### Post by James78 on 2011-01-07
Remember to ALWAYS backup your settings, VHosts, data, and just everything, when upgrading, because upgrading can go horribly wrong, or mess up configs, or do any variety of things; it's best to make sure you have a good backup first for peace of mind.

---

### Post by Bushcraft Bill on 2011-01-07
I think I may just hold off then as things are working very well so I guess their is no need to take the chance I will wait till their is really a need to upgrade to 10.10 and thanks again everyone for your comments...

Bill 

> **HugoSerrano said:**
> sudo apt-get dist-upgrade 

But do you need to do the upgrade? 10.04 it's LTS, that means it as support for Long Term, so it's better for servers.

Anyway, your server will be upgraded, it's not a clean install! But you may find some configurations problems... or not :-P

Regards.

---

