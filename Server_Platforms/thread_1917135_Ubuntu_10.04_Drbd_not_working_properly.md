---
title: "Ubuntu 10.04 Drbd not working properly"
date: 2012-01-29
forum: Server Platforms
---

### Post by inulled on 2012-01-29
> mike-2t@mike-2t-desktop:~$ sudo /etc/init.d/drbd start
[sudo] password for mike-2t: 
/etc/drbd.conf:4: Failed to open include file 'drbd.d/*.res'.
/etc/drbd.conf:6: conflicting use of global section 'global' ...
drbd.d/global_common.conf:1: global section 'global' first used here.
 * Starting DRBD resources                                                      /etc/drbd.conf:4: Failed to open include file 'drbd.d/*.res'.
/etc/drbd.conf:6: conflicting use of global section 'global' ...
drbd.d/global_common.conf:1: global section 'global' first used here.

This is the error I get when I try and execute "sudo /etc/init.d/drbd start" in Ubuntu 10.04 Drbd. I get the same error when trying to run "sudo drbdadm create-md r0" as well. Any ideas as to why this is happening?

---

### Post by gims71 on 2013-02-13
[B]I have the same problem as inulled.I am trying to install drbd and after configuring the file "drbd.conf" and when i want to executes this command :  "drbdadm create-md r0", I have this error message: etc/drbd.conf:6: conflicting use of global section 'global ' 
drbd.d/global_common.conf:1: global section 'global' first used here.

Sorry for my english, i'm french. Please help[/B]

---

