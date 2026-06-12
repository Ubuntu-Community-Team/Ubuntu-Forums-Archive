---
title: "mgetty does not start new_fax"
date: 2008-08-11
forum: Server Platforms
---

### Post by Juerg on 2008-08-11
After installation of mgetty, I can receive faxes. They get stored in /var/spool/fax/incoming/ as G3 files.

According to the manual, mgetty should automatically start the script /etc/mgetty/new_fax if it exists.

strings /sbin/mgetty | grep new_fax
results in /etc/mgetty/new_fax

Permissions on /etc/mgetty/new_fax are set to 777

But still mgetty does not invoke new_fax. In the log (even with increased loglevel) there is no error message.

Any help will be much appreciated.

Juerg

---

