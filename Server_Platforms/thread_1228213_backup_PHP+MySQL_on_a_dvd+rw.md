---
title: "backup PHP+MySQL on a dvd+rw"
date: 2009-07-31
forum: Server Platforms
---

### Post by peladoo on 2009-07-31
we have a server that holds the code and databases. all 3 computers mount via nfs the folder that holds the source files.

so we need to backup the source files and mysql databases.

first you need:
apt-get install genisoimage
apt-get install cdrecord

then...
4 simple lines:

mysqldump -pabc --all-databases > /path/to/root/dir/dump.sql
cdrecord dev='/dev/scd0' -blank=fast
genisoimage -o /root/backup.iso /path/to/root/dir/
cdrecord -v speed=16 dev='/dev/scd0' -data /root/backup.iso

---

