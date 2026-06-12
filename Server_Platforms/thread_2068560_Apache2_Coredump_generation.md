---
title: "Apache2 Coredump generation"
date: 2012-10-09
forum: Server Platforms
---

### Post by atz6975 on 2012-10-09
Hi, 
I use Ubuntu Server 12.04.1 with Apache2 & mod_php from distribution.Nothing special.

I'm struggling to have coredumps produced on segfaults.
I've setup the Coredumpdirectory (outisde tmp, with rights to www-data) apache directive but no dump is produced

My understanding of documentation is that Apache2 simply requires this directive to create a coredump.

Do I also need to change ulimit for www-data?
In that case I would assume (as root):
su www-data
ulimit -c unlimited <-----change 0 coredump(blocks) to unlimited
exit
service apache2 restart <----do I need this

Thanks for your help.

---

