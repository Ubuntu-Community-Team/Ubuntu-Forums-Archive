---
title: "Problem with disk quotas"
date: 2011-12-14
forum: Server Platforms
---

### Post by rugger11 on 2011-12-14
Folks,

I am having problems implementing disk quotas on Ubuntu server 10.04. I am updated to 10.04.3 LTS with package quota 3.17-6 installed. I thought I had this sorted-out at one point after updating my system from RHEL 4, but it appears not to be the case, as one user is well over quota now. :(

My entry in /etc/fstab looks like this:

++ snip
/dev/sda2               /data2                  ext3    defaults,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0        1 2
++ end snip

Note this filesystem was imported from RHEL4 (hence ext3 fs type).

I had previously run quotacheck on this filesystem, prior to installing the user. quota -v for the user shows a set quota and limit but no usage. The quota soft limit is set to around 10Gb with a hard limit of 11Gb, but the user has 42Gb of data on the filesystem shown above.

# service quota status

Shows that quotas are on

Does anyone know how I can make this work?

Rugger11

---

