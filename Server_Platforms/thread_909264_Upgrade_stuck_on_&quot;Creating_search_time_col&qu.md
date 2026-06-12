---
title: "Upgrade stuck on &quot;Creating search_time col&quot;"
date: 2008-09-03
forum: Server Platforms
---

### Post by xrvjorn on 2008-09-03
I'm trying to upgrade Ubuntu Server 6.06LTS to 8.04.1, using the instruction on [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades).

The last hour, the upgrade has been stuck on
```
Setting up phpbb2-conf-mysql (2.0.22-3) ...
Creating MySQL tables if they don't exist yet...
Creating phppp_sessions_keys table if it doesn't exist yet...
Creating search_time column if it doesn't exist yet...
```

No disk accesses, no network activity, no CPU load, nothing at all (my Ubuntu Server i srunning under VMWare, so I can monitor system activity). Is the upgrade supposed to sit idle and wait for so long?

---

### Post by fackamato on 2008-10-09
Same problem here when doing upgrade on 8.10 Intrepid. (sudo apt-get update && sudo apt-get dist-upgrade):

```
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up phpbb2-conf-mysql (2.0.23+repack-3) ...
Creating MySQL tables if they don't exist yet...
Creating phpbb_sessions_keys table if it doesn't exist yet...
Creating search_time column if it doesn't exist yet...

```

---

### Post by xrvjorn on 2008-10-09
Has it worked out for you? I'm afraid it didn't for me. I tried to interrupt and resume the installation at that point, and ended up with an unbootable system.

---

### Post by fackamato on 2008-10-09
> **xrvjorn said:**
> Has it worked out for you? I'm afraid it didn't for me. I tried to interrupt and resume the installation at that point, and ended up with an unbootable system.


I just removed the package.

If you got an unbootable system, it is unrelated to this error. Perhaps you got a new kernel installed and GRUB didn't get modified or something. Anyway, the upgrade should (and does on my system) continue after I ctrl+c out of the "hang".

---

