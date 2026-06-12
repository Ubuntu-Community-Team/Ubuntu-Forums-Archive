---
title: "Encrypted volume not mounted after failed upgrade to 22.04"
date: 2022-12-05
forum: Ubuntu/Debian BASED
---

### Post by mandlebrot on 2022-12-05
After trying to upgrade from ubuntu 20.04 to 22.04, an "Upgrade failed" box was displayed with the following information

```
Checking for a new neon release
There is no development version of an LTS available.
To upgrade to the latest non-LTS development releas set Prompt=normal in /etc/update-manager/release-upgrades.
```

This didn't appear normal to me, so I restarted the machine. It prompts for an encryption password and then hits grub as normal, however when selecting the default option in grub it tries to boot but fails to mount the encrypted volume group wich contains `/home` and so on. Eventually it hits a terminal with the following

```
BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3) built in shell (ash)
```

After reading some other threads about similar issues, it seems like a possible issue with initramfs, however I am no expert in this area so I am pretty clueless.

I have run the boot-repair diaagnostic tool which resulted in the following paste bin [https://paste.ubuntu.com/p/WszxHg4HxH/](https://paste.ubuntu.com/p/WszxHg4HxH/)

Do you recommend continuing with the boot repair? Or is there something else I should do?

Any help would be appreciated.
Thanks,
Jack

---

### Post by TheFu on 2022-12-06
If it has been over 45 minutes, I'd do a fresh install of the OS I want, wiping everything previously there, and restore from my backups that I made just before attempting the backup ... for the very specific files that wouldn't conflict with the new release.

If you don't know which files could/would conflict with the new release, then I'd do a fresh install of the older OS and restore my files and programs following whatever restore procedure you have already tested and 100% know will work.

That's what I'd do.

Upgrades are like replacing an engine in a car.  They are not to be taken lightly.  Always have know-you-can-restore backups BEFORE attempting any OS version change to avoid massive disappointment.

Odd thing is that, the more I have backups that can be restored, the fewer issues I have across the board.  It is like the system knows it would be a minor inconvenience, not total data loss.

BTW, if you use any encryption, you absolutely must have excellent backups.  Just a minor hardware corruption issue in the wrong blocks of storage can completely make the entire encrypted volumes useless, hence the need for excellent backups that can be restored.

---

### Post by QIII on 2022-12-06
Moved to Ubuntu/Debian BASED as a more appropriate location.  KDE Neon is based on Ubuntu, but it is an independent distribution, not an official Ubuntu flavor.

---

