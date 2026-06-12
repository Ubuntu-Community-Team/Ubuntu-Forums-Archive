---
title: "i get this pureftp mysql fail"
date: 2020-08-19
forum: Server Platforms
---

### Post by math492m on 2020-08-19
root@comasys_backup:/home/server# cp /etc/pure-ftpd/db/mysql.conf /etc/pure-ftpd/db/mysql.conf_orig
root@comasys_backup:/home/server# cat /dev/null > /etc/pure-ftpd/db/mysql.conf
root@comasys_backup:/home/server# vi /etc/pure-ftpd/db/mysql.conf
root@comasys_backup:/home/server# vi /etc/pure-ftpd/conf/ChrootEveryone 
root@comasys_backup:/home/server# vi /etc/pure-ftpd/conf/CreateHomeDir 
root@comasys_backup:/home/server# vi /etc/pure-ftpd/conf/DontResolve 
root@comasys_backup:/home/server# service pure-ftpd-mysql restart
Job for pure-ftpd-mysql.service failed because the control process exited with error code.
See "systemctl status pure-ftpd-mysql.service" and "journalctl -xe" for details.
root@comasys_backup:/home/server# 

pls help

---

