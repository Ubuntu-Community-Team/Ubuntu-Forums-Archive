---
title: "debconf and grub reconfigure"
date: 2012-09-20
forum: Server Platforms
---

### Post by molostoff on 2012-09-20
I have configured debconf grub2/linux_cmdline with my own value (e.g. kernel boot parameters configuration stored in debconf db backend), now after calling 'dpkg-reconfigure -f noninteractive grub-pc' a script from grub-pc package just overwrites my customisation and uses that stored in /etc/defaults/grub (e.g. wiping out debconf db values for grub2)

I wish to do the opposite - reconfigure grub and override system configuration file with values from debconf db. But it seems that the script always unconditionally overwrite debconf values in db, and I dont understand for what the purpose and why it does storing them here, while I can not use these params later, e.g. for recovering/reconfiguring?

Perhaps there is a magic way to apply imperatively debconf parameters from db to existing system configuration files? preferably with one command? possibly with creation missing config files?

---

