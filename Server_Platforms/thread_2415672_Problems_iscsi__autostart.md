---
title: "Problems iscsi  autostart"
date: 2019-03-29
forum: Server Platforms
---

### Post by gus_zernial on 2019-03-29
I have an iscsi initiator on an (k)ubuntu 18.10 workstation. I can successfully connect, mount and use an iscsi volume/lun/target on my QNAP NAS box, using the command

sudo iscsiadm -m node --targetname "iqn....... " --portal "192.168.1.xx:3260.1" --login

and it automatically mounts to /media/myusername/targetlunuuid

But I want the login/connect/mount to happen automatically on boot, and I can't get it to work. I've tried setting

node.startup = automatic   in /etc/iscsi/iscsid.conf    and the command

sudo iscsiadm -m node --targetname iqn...... -p 192.168.1.xx:3260.1 --op update -n node.startup -v automatic

and neither does the job. After the automatic config or command, dmesg throws out: db_root: cannot open: /etc/target on subsequent boot

Ideas to further diagnose and/or fix appreciated                Gus

---

