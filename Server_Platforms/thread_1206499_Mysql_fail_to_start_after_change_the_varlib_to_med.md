---
title: "Mysql fail to start after change the /var/lib to media/disk"
date: 2009-07-07
forum: Server Platforms
---

### Post by rlimpin on 2009-07-07
i just follow the instruction on this link

[http://www.ubuntugeek.com/how-to-change-the-mysql-data-default-directory.html](http://www.ubuntugeek.com/how-to-change-the-mysql-data-default-directory.html)

after sudo /etc/init.d/mysql restart

fail to start

then i type tail /var/log/messages

root@ubuntuserver:/media/disk# tail /var/log/message
tail: cannot open `/var/log/message' for reading: No such file or directory
root@ubuntuserver:/media/disk# tail /var/log/messages
Jul  7 06:37:03 ubuntuserver kernel: [  973.766146] ata1.00: configured for UDMA/33
Jul  7 06:37:03 ubuntuserver kernel: [  973.766172] ata1: EH complete
Jul  7 06:55:28 ubuntuserver kernel: [ 2077.574179] ata1.00: qc timeout (cmd 0xa0)
Jul  7 06:55:28 ubuntuserver kernel: [ 2077.574203]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
Jul  7 06:55:28 ubuntuserver kernel: [ 2077.574204]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
Jul  7 06:55:33 ubuntuserver kernel: [ 2082.613881] ata1: port is slow to respond, please be patient (Status 0xd0)
Jul  7 06:55:38 ubuntuserver kernel: [ 2087.588648] ata1: device not ready (errno=-16), forcing hardreset
Jul  7 06:55:38 ubuntuserver kernel: [ 2087.588654] ata1: soft resetting link
Jul  7 06:55:38 ubuntuserver kernel: [ 2088.132352] ata1.00: configured for UDMA/33
Jul  7 06:55:38 ubuntuserver kernel: [ 2088.132374] ata1: EH complete

Can you help me thanks

---

