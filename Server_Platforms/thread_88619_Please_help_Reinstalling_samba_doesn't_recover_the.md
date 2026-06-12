---
title: "Please help: Reinstalling samba doesn't recover the original /etc/samba/smb.conf"
date: 2005-11-10
forum: Server Platforms
---

### Post by Akhran on 2005-11-10
I accidentially overwrite the /etc/samba/smb.conf with swat before I did a backup of the original. Doing a 'aptitude purge samba' followed by 'aptitude -r install samba' doesn't recover the original /etc/samba/smb.conf. In fact, with the purge option, /etc/samba/smb.conf wasn't even removed. Isn't purge option suppose to remove all configuration files? If I manually remove /etc/samba/smb.conf and reinstall samba, samba can't even start up, cos of the missing smb.conf in /etc/samba(reinstalling samba doesn't recreate the /etc/samba directory even).

Please advise.

Thanks!
PS. Of cos, the easier way would be to install samba on another machine and copy the file over, but I'm curious why the aptitude purge option doesn't remove the configuration file and the install option doesn't recreate the original smb.conf file.

---

### Post by Cyril on 2005-11-15
Try reinstalling sama-common.  Worked for me.

---

