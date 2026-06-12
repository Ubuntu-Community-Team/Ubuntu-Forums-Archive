---
title: "Kernel/LTS Enablement Stack on Software RAID1"
date: 2014-12-22
forum: Server Platforms
---

### Post by dipeshmehta on 2014-12-22
Hello All,

I have been using Ubuntu 12.04LTS Server Edition.  Current kernel is 3.2.0-54-generic.  The server has been installed with software RAID1.  Now, I am required to upgrade kernel to minimum of v3.11 i.e. 13.10 Saucy.  Is there any precaution to be taken related to grub or RAID while upgrading kernel?

Thanks in advance.

~Dipesh

---

### Post by houstonbofh on 2014-12-22
Backups.  Which you should be doing anyway.  But a kernal change will not change the raid.  You can actually mount your raid from a new Ubuntu LiveCD with a little work. :)

---

