---
title: "HOWTO: Rotate Oracle-XE logs"
date: 2009-08-03
forum: Server Platforms
---

### Post by Waappu on 2009-08-03
Hi

Howto is how compress daily Oracle-XE log files and keep archive for seven days.

First create new file oracle-xe to /etc/logrotate.d
```
sudo nano /etc/logrotate.d/oracle-xe
```

Insert following to file
```

### Rotates listener log and also prepares/updates tar-ball for rotation.

/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log  {

firstaction

find /usr/lib/oracle/xe/app/oracle/admin/XE/adump -name '*.aud' -print | xargs tar ufp /usr/lib/oracle/xe/app/oracle/admin/XE/adump/hist_adump_aud.tar --remove-files > /dev/null

chown oracle:dba /usr/lib/oracle/xe/app/oracle/admin/XE/adump/hist_adump_aud.tar

find /usr/lib/oracle/xe/app/oracle/admin/XE/bdump -name '*.trc' -print | xargs tar ufp /usr/lib/oracle/xe/app/oracle/admin/XE/bdump/hist_bdump_trc.tar --remove-files > /dev/null

chown oracle:dba /usr/lib/oracle/xe/app/oracle/admin/XE/bdump/hist_bdump_trc.tar

find /usr/lib/oracle/xe/app/oracle/admin/XE/cdump -name '*.trc' -print | xargs tar ufp /usr/lib/oracle/xe/app/oracle/admin/XE/cdump/hist_cdump_trc.tar --remove-files > /dev/null

chown oracle:dba /usr/lib/oracle/xe/app/oracle/admin/XE/cdump/hist_cdump_trc.tar

find /usr/lib/oracle/xe/app/oracle/admin/XE/udump -name '*.trc' -print | xargs tar ufp /usr/lib/oracle/xe/app/oracle/admin/XE/udump/hist_udump_trc.tar --remove-files > /dev/null

chown oracle:dba /usr/lib/oracle/xe/app/oracle/admin/XE/udump/hist_udump_trc.tar

endscript

rotate 7
ifempty
daily
copytruncate
missingok
nocompress
}

### Instance Alert Log
/usr/lib/oracle/xe/app/oracle/admin/XE/bdump/alert_XE.log {
rotate 7
daily
copytruncate
missingok
nocompress
}

### rotates cdump trc files
/usr/lib/oracle/xe/app/oracle/admin/XE/cdump/hist_cdump_trc.tar {
rotate 7
daily
missingok
nocompress
}

### rotates adump trc files
/usr/lib/oracle/xe/app/oracle/admin/XE/adump/hist_adump_aud.tar {
rotate 7
daily
missingok
nocompress
}

### rotate udump trc files
/usr/lib/oracle/xe/app/oracle/admin/XE/udump/hist_udump_trc.tar {
rotate 7
daily
missingok
nocompress
}

### rotate bdump trc files
/usr/lib/oracle/xe/app/oracle/admin/XE/bdump/hist_bdump_trc.tar {
rotate 7
daily
missingok
nocompress
}

```

Save your file. Next time logrotate is run Oracle-XE logs are also rotated.

Logrotate script is taken here and modified for Ubuntu and Oracle-XE
[http://orac-tips.blogspot.com/2009/01/logrotate-in-oracle.html](http://orac-tips.blogspot.com/2009/01/logrotate-in-oracle.html)

---

