---
title: "I can connect as anonymous, but as a local account!"
date: 2013-11-07
forum: Server Platforms
---

### Post by thishalll on 2013-11-07
I installed Ubuntu server and vsftpd.

vsftpd.conf

local_enable=YES
write_enable=YES
chroot_local_user=YES



Then I restarted vsftpd.

I can connect to as anonymous through Cyberduck or FileZilla, but I cannot use a local account.

Firewall is off and port 21 is open.

What is the problem??

I am trying to figure this out for three days, but I still stuck here.

---

