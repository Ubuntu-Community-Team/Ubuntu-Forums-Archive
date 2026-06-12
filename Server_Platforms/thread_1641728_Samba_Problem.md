---
title: "Samba Problem"
date: 2010-12-09
forum: Server Platforms
---

### Post by graphic on 2010-12-09
I recently used Ubuntu+Samba+LDAP to create a PDC for a network of Windows machines. Everything is working great even roaming profiles, however I do have one issue.

For some reason when a user's home directory gets mounted in windows the capacity and free space listed are for the OS hard drive and not the RAID 5 I set up specifically to store this information. I've checked and when I save files from windows to this mount point, they save to the correct location - that is /mnt/md0/home/username. Its not a big deal but I would like to fix this, any thoughts? Thanks in advance.

---

