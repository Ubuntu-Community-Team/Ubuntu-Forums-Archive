---
title: "webmin and syslog-ng won't start on boot after upgrade from 8.04 to 10.04"
date: 2010-09-16
forum: Server Platforms
---

### Post by the_tazinator on 2010-09-16
I recently upgraded a Ubuntu server from version 8.04 to 10.04 and after a reboot the webmin and syslog-ng server do not start at boot anymore. I can start them manually by doing /etc/init.d/webmin start and /etc/init.d/syslong-ng start and everything works fine until I root again. Granted this machine is rarely rebooted but when it is, I don't want to have to remember to start these services.

I have tried a full removal of syslog-ng and reinstall but to no avail. The entries are in the rc directories like they should and the links are valid.

Any ideas?

---

### Post by the_tazinator on 2010-09-17
After investigation further, there was more than just webmin and syslog that were having an issue so rather than trouble shoot for hours, I wiped it out and reinstalled 10.04. All is good now.

FYI, this is why you make sure you have good backups. Fresh install and everything back up and working in less than a hour.

---

