---
title: "Quota Errors w/ (Ubuntu 10.10 / Webmin 1.520)"
date: 2010-11-04
forum: Server Platforms
---

### Post by Kaigeos on 2010-11-04
First I install "quota" from webmin.

Then I go to System/Disk and Network Filesystems and edit Root Filesystem to use Quota.

Finaly I go to System/Disk Quotas to "Enable Quotas", and I get the following error.

quotaon: cannot find //quota.user on /dev/disk/by-uuid/d56b04cb-c0b1-46d6-ab2e-818a145ee895 [/]

---

### Post by greenmuh on 2010-11-07
Im having the same problems:

# quotacheck -avugm
quotacheck: Scanning /dev/disk/by-uuid/xxxxx [/] done
quotacheck: Checked 4817 directories and 52700 files

# quotaon -avug
quotaon: using //aquota.group on /dev/disk/by-uuid/xxxxx [/]: No such process
quotaon: Quota format not supported in kernel.

is this an ext4 / quota problem or a ubuntu 10.10 problem?

---

### Post by psusi on 2010-11-07
The volume must be mounted with quotas enabled, so you need to add the quota option to the /etc/fstab line and remount.

---

### Post by James78 on 2010-11-08
My line in /etc/fstab:
```
UUID=<uuid>  /  ext4  grpquota,errors=remount-ro,usrquota,rw 
```

To bypass all these insane problems, I just got Ubuntu 10.04.1 LTS (which is grade A supported), and installed on there, then upgraded. Since 10.04.1 LTS is grade A supported, then problems like these are very unlikely to occur when installing on a fresh 10.04.1 system. You can always upgrade afterward. Staying on LTS releases for servers is the best option though, while you won't be able to upgrade to new versions of software until the next LTS (don't worry about security updates, those are supported), you won't have to upgrade very often, will get long term support, and will have a guaranteed upgrade to the new LTS, not so much for regular release upgrades. And besides all that, most server software supports LTS releases, and other releases are secondary or at the bottom; it eases their development cycle, as LTS is much more trusted overall, which would be an indication as to why there was a problem with the Webmin installs on 10.10, but not 10.04.1.

---

