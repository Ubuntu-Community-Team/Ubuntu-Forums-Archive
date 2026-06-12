---
title: "Enabling SYN cookies"
date: 2009-05-19
forum: Security
---

### Post by bugmenot2006 on 2009-05-19
Hello,

I am trying to enable SYN cookies in ubuntu but to no avail.
I have uncommented net.ipv4.tcp_syncookies=1 in /etc/sysctl.conf and restarted the PC, but syn cookies doesn't seem to be enabled.

I check this by sending a TCP SYN request to the PC and looked at the reply. The SEQ number is always 0, it should be some random numbers.

Please Help

Thanks

---

### Post by kryptoz on 2009-05-21
You can enable it run time without rebooting the server and check. Try `echo "1" > /proc/sys/net/ipv4/tcp_syncookies`

---

