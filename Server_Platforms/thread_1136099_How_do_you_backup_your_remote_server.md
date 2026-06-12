---
title: "How do you backup your remote server?"
date: 2009-04-24
forum: Server Platforms
---

### Post by botfish on 2009-04-24
Please comment on my remote server backup method. I have created a Bash scrip to back up a remote server to my home computer. It uses rsync to exclude all directories with the exception of /backup, /etc, /home, /root, /var/www, and /var/log

I have decided that I just want to backup files that can't be restored by reinstalling the OS or a package manager.

Installed applications are apache2, postfix, courier-pop, mysql
The remote server does a daily mysqldump of all databases into /backup.
My web root is /var/www

I am concerned that I may have excluded important information I am not aware of.

> 
/usr/bin/rsync -vv \
-e "ssh -i $PRIVATE_KEY" \
--archive \
--delete-excluded \
--delete \
--filter='exclude /bin' \
--filter='exclude /boot' \
--filter='exclude /dev' \
--filter='exclude /initrd' \
--filter='exclude /lib' \
--filter='exclude /lib64' \
--filter='exclude /media' \
--filter='exclude /mnt' \
--filter='exclude /opt' \
--filter='exclude /proc' \
--filter='exclude /sbin' \
--filter='exclude /srv' \
--filter='exclude /sys' \
--filter='exclude /tmp' \
--filter='exclude /usr' \
--filter='exclude /fastboot' \
--filter='exclude /q\n' \
--filter='exclude /aquota.group' \
--filter='exclude /aquota.user' \
--filter='exclude /.rnd' \
--filter='exclude /var/backups' \
--filter='exclude /var/cache' \
--filter='exclude /var/lib' \
--filter='exclude /var/lib/mysql/' \
--filter='exclude /var/local' \
--filter='exclude /var/lock' \
--filter='exclude /var/mail' \
--filter='exclude /var/opt' \
--filter='exclude /var/run' \
--filter='exclude /var/spool' \
--filter='exclude /vartmp' \
$REMOTE_USER@$REMOTE_HOST:/ \
$BACKUP_DIR/


---

