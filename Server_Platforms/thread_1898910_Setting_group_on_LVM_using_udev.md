---
title: "Setting group on LVM using udev"
date: 2011-12-22
forum: Server Platforms
---

### Post by wiz561 on 2011-12-22
Hi!

I'm trying to set the permissions on a LVM volume so that a user can use it.  I've looked this up and it says to use udev rules.  I have this...


# cat /etc/udev/rules.d/99-logger.rules 
ENV{DM_NAME}="vm1-logger", OWNER="vbox", GROUP="vboxusers", MODE:="660"
#

However, when I reboot the machine, EVERYTHING in /dev belongs to vbox:vboxusers and now just the lvm volume name 'logger'.  Can anybody give any insight on what's going on here?

Thanks!

---

