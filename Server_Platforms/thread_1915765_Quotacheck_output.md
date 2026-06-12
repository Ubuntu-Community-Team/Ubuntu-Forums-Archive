---
title: "Quotacheck output"
date: 2012-01-26
forum: Server Platforms
---

### Post by satimis on 2012-01-26
Hi folks,

Ubuntu 1010 server
VirtualBox

ServerName ub1010ser01 (it was cloned on another VM named ub1010ser00 which hasn't been config used as base for cloning VM)


Has any folk on the forum tried following Howto:
The Perfect Server - Ubuntu 10.10 [ISPConfig 3] - Page 4
[http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3-p4](http://www.howtoforge.com/perfect-server-ubuntu-10.10-maverick-meerkat-ispconfig-3-p4)

It went through w/o problem upto:-
# mount -o remount /
# quotacheck -avugm```

quotacheck: Scanning /dev/mapper/ub1010ser00-root [/] done
quotacheck: Cannot stat old user quota file: No such file or directory
quotacheck: Cannot stat old group quota file: No such file or directory
quotacheck: Cannot stat old user quota file: No such file or directory
quotacheck: Cannot stat old group quota file: No such file or directory
quotacheck: Checked 11162 directories and 70938 files
quotacheck: Old file not found.
quotacheck: Old file not found.

```

Are they mistake?  Or it is NOT a problem because no previous quote files created?

# quotaon -avug```

/dev/mapper/ub1010ser00-root [/]: group quotas turned on
/dev/mapper/ub1010ser00-root [/]: user quotas turned on

```
Which file I have to edit changing ub1010ser00-root as ub1010ser01?

Please shed me some light.  Thanks in advance.

B.R.
satimis

---

