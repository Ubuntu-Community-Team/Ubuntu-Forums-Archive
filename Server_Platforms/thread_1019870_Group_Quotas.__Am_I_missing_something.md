---
title: "Group Quotas.  Am I missing something?"
date: 2008-12-23
forum: Server Platforms
---

### Post by eyd on 2008-12-23
I've followed the various HOWTO's on setting up quotas in linux on a new install of 8.04 server.  I've got user quotas working fine, but can't seem to get the group quotas working properly for the life of me.  They work as the default group, but not as a custom group.  For example, I have a user on the system, eyd, that has his own group eyd.  I can edit the quota for the group and user eyd fine.  I added the user eyd to the group 5gigs and set it's quota, but it doesn't seem to take.  

(as root, checking the quota for 5gigs.  This stays when I change it.)
```
Disk quotas for group 5gigs (gid 1002):
  Filesystem                   blocks       soft       hard     inodes     soft$
  /dev/sda3                         0        500       1000          0        0$
```

(as eyd, checking the quotas via `quota -g`)
```
Disk quotas for group eyd (gid 1001): 
     Filesystem  blocks   quota   limit   grace   files   quota   limit   grace
      /dev/sda3     104     550    5550              86       0       0        
Disk quotas for group 5gigs (gid 1002): none
Disk quotas for group test (gid 1006): none
```

I've even changed the group for eyd from eyd to 5gigs in /etc/passwd, but that doesn't seem to matter.  I removed all quota support, then readded it after the groups were built, but that also didn't work.  

My ultimate plan is to have different groups, 5gigs, 10gigs, etc, and users in those groups only able to save that much data to their home folder.  Anyone have an idea on what my problem is?   Thanks alot!

eyd

---

### Post by eyd on 2008-12-29
bump

---

