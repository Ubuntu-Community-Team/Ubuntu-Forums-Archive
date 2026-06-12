---
title: "apt and do-release-upgrade service questions"
date: 2022-12-10
forum: Server Platforms
---

### Post by DigiAngel on 2022-12-10
Hey all,

So...I have a backup machine...it has 2 nics.  When it's in production, eth0 is the external for internet, eth1 is internal and gets a 192.168.1 ip.  When it's backup, it's usually off...until I need to update the packages.  When I do that, I assign eth0, the nic that usually gets the external ip, a temporary internal ip just to get it online and able to update packages.

With that in mind, sometimes certain packages, like nmbd fail to upgrade because when they try and restart, they fail because they are configured for an IP that doesn't exist.  How can I tell apt NOT to restart services?  This is Ubuntu 18 Server, and the needrestart package is not installed.

Along the same vain here....I plan on doing a full do-release-upgrade....my hope was to do it as said above, with a temporary IP assigned, but will I run into the same service not restarting issues?

Thank you!

---

### Post by MAFoElffen on 2022-12-10
With servers, I'm a fan of static network addresses and network profiles. I make backups/copies of my network config files, then make whichever I want current as the active configuration. That way, nothing changes unless you want it to... I know what it is and where to find it. No unexpected surprises.

On releases, I mostly do "migrations"... Where the old data and configs are moved to a new release. I've found over the years, that if I did do-release-upgrades continuously, that I carried a lot of clutter and bloat into my present. A lot of times, it's easier and faster to migrate.

Having said that, I plan my configurations for having to replace things in pieces...

---

### Post by TheFu on 2022-12-10
nmbd has been replaced by MSFT switching to completely different technology, mDNS.  On Linux, mDNS is handled by Avahi, which isn't usually installed on a server.  So ... if your samba clients are Win10 or newer, you don't need/want nmbd at all. It doesn't do what they need anyway.   Morbius1 posted about this a few months ago. Could be worth looking for that thread.

As for moving off 18.04 ... I've been slowly moving my 18.04 servers to 20.04.  Lots of things changed, so some core things work very different in 20.04 and later than they do in 18.04.  To avoid cruft, I'm doing fresh installs, then migrating data, specific configs, over.  Takes about 45 minutes, including the frest install, but I keep huge data storage things outside the OS areas, so only the OS stuff really gets modified ... and for large data storage, I have a checklist item to compare the uids and gids for any data files.  For root-owned stuff, this isn't needed. Where it gets complex is when daemons run under a different userid and the uid/gid changed between installs .... so the www-data user/group likely need to have file and group ownership checked/corrected post-migration.

---

### Post by DigiAngel on 2022-12-11
Thanks all....maybe I added too much detail in this post :)  My question is, how do I get apt and do-release-upgrade to NOT restart services during updating?  Thank you!

---

### Post by TheFu on 2022-12-11
> **DigiAngel said:**
> Thanks all....maybe I added too much detail in this post :)  My question is, how do I get apt and do-release-upgrade to NOT restart services during updating?  Thank you!

Disable the dæmon BEFORE doing the upgrade?

---

### Post by DigiAngel on 2022-12-11
Hrmmm....I'll have to try that thank you.

---

