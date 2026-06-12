---
title: "Dpkg-old Query"
date: 2022-09-12
forum: Server Platforms
---

### Post by terencewklau on 2022-09-12
Hi,

Running Ubuntu Server 20.04.3 which are configured for automatic security only updates.  One of the servers had 2 files renamed with dpkg-old appended:

issue.dpkg-old
issue.net.dpkg-old

From what I understand, default action is to keep using the existing config unless someone answered Y or I, which then renames the existing config with dpkg-old.  But this I assume is only possible during a manual upgrade, not via automatic upgrades.

Based on the 50unattended-upgrades config, the "dpkg" section is commented out ...

```
// This option allows you to control if on a unclean dpkg exit
// unattended-upgrades will automatically run 
//   dpkg --force-confold --configure -a
// The default is true, to ensure updates keep getting installed
//Unattended-Upgrade::AutoFixInterruptedDpkg "true";
```

... but even if uncommented, it just forces confold which I thought is the default anyway (if my understanding of --force confold is correct).

For the record, the server was upgraded to 20.04.5 manually by one of our vendors using the following command:

```
apt full-upgrade -y
```

So any help in understanding which package upgrade caused the files to be renamed, and why the default of using existing config was not followed, would be much appreciated.

Thanks.

---

### Post by terencewklau on 2022-09-13
Looks like "apt full-upgrade -y" upgrades base-files ... which will prompt for action on:

/etc/issue
/etc/issue.net

Selecting the default "N" will create copies with "dpkg-dist" appended to it and the existing files are not touched (as expected).

Selecting "Y" will create copies with "dpkg-old" appended to it and the new config files will be used.

So looks like the perp who run the full-upgrade command selected "Y" instead of "N".

Cheers.

---

### Post by LHammonds on 2022-09-13
> **terencewklau said:**
> So looks like the perp who run the full-upgrade command selected "Y" instead of "N".
And based on their file dates, you can narrow down when this happened in case you want to comb through log files.

LHammonds

---

