---
title: "Wubi Upgrade from 11.10 to 12.04 fails."
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Dygear on 2012-04-04
I did a fresh install of Ubuntu 11.10 via Wubi using Windows 7 as the platform. Once installed, I reboot and go into Ubuntu. After that I do my normal upgrade routine to make sure everything is as it should be. During the upgrade process it tells me that 12.04 is available, and I opt for that. It goes through the installation process, getting lshw, where it stalls. It will not go past this point. It shows Done, in the terminal console, but will not move onto the next item to be installed. Can someone please look into this.

Screen Shot Attached.

---

### Post by bcbc on 2012-04-04
Please file a bug: [https://bugs.launchpad.net/wubi/+filebug](https://bugs.launchpad.net/wubi/+filebug)

Consider attaching your logs to it:
```
sudo zip -r logs /var/log/
```

---

### Post by philinux on 2012-04-04
I'm not surprised. Wubi is for testing ubuntu in a safe way rather than having to partition hard drive.

Upgrading from 11.10 using wubi is not what its for.

---

### Post by bcbc on 2012-04-04
> **philinux said:**
> I'm not surprised. Wubi is for testing ubuntu in a safe way rather than having to partition hard drive.

Upgrading from 11.10 using wubi is not what its for.
That is the intended purpose of Wubi, but it's still not supposed to fail, and the bug is probably unrelated to Wubi...

It's always best to file a bug and let the devs decide on its usefulness. Potentially it may solve a problem that affects non-Wubi users.

---

### Post by philinux on 2012-04-05
Sorry I should have said upgrading from 11.10 to 12.04 **Beta** might not be supported yet as 12.04 is not released.

There would be a note to that effect in the release notes for 12.04 I guess.

[https://wiki.ubuntu.com/WubiGuide#Upgrading](https://wiki.ubuntu.com/WubiGuide#Upgrading)

Although I suppose this needs testing at some point.

Thread moved to testing forum.

---

### Post by bcbc on 2012-04-05
> **philinux said:**
> Sorry I should have said upgrading from 11.10 to 12.04 **Beta** might not be supported yet as 12.04 is not released.

There would be a note to that effect in the release notes for 12.04 I guess.

[https://wiki.ubuntu.com/WubiGuide#Upgrading](https://wiki.ubuntu.com/WubiGuide#Upgrading)

Although I suppose this needs testing at some point.

Thread moved to testing forum.

I wondered about that as well: 12.04 upgrades shouldn't be offered yet through the update manager with normal settings in place.

---

