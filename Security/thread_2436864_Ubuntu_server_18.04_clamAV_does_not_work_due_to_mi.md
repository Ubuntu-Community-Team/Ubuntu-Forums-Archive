---
title: "Ubuntu server 18.04: clamAV does not work due to missing /var/run/clamav/clamd.ctl"
date: 2020-02-14
forum: Security
---

### Post by erotavlas on 2020-02-14
Hi,
I have a problem with ubuntu server 18.04. I have clamAV that can be reached by the other processes via unix socket domain (/var/run/clamav/clamd.ctl). ClamAV works well for a while, then the file clamd.ctl disappears from the previous path and I need to manually create it or to restart the system.
I already tried with sudo apt-get install clamav-daemon.

This is my file /etc/clamav/clamd.conf
```

LocalSocket /var/run/clamav/clamd.ctl
FixStaleSocket true
# TemporaryDirectory is not set to its default /tmp here to make overriding
# the default with environment variables TMPDIR/TMP/TEMP possible
User root
ScanMail true
ScanArchive true
ArchiveBlockEncrypted false
MaxDirectoryRecursion 15
FollowDirectorySymlinks false
FollowFileSymlinks false
ReadTimeout 180
MaxThreads 12
MaxConnectionQueueLength 15
StreamMaxLength 10M
LogFileMaxSize 0
LogSyslog false
LogFacility LOG_LOCAL6
```

This is a script run with crontab

```
#!/bin/bash

# update
#freshclam

FILETODOWNLOAD="main.cvd daily.cvd bytecode.cvd";

for F in ${FILETODOWNLOAD}; do
 sudo rm -f /var/lib/clamav/$F
 wget http://database.clamav.net/$F -P /var/lib/clamav
 sudo chown clamav:clamav /var/lib/clamav/$F
 sudo chmod 644 /var/lib/clamav/$F
done

# scan
LOGFILE="/var/log/clamav/clamav-$(date +'%Y-%m-%d').log";
#EMAIL_MSG="Please see the log file attached.";
#EMAIL_FROM="clamav-daily@domain";
#EMAIL_TO="webmaster@domain";
DIRTOSCAN="/var/www /home/master/";

for D in ${DIRTOSCAN}; do
 DIRSIZE=$(du -sh "$D" 2>/dev/null | cut -f1);

 echo "Starting a daily scan of "$D" directory.
 Amount of data to be scanned is "$DIRSIZE".";

 clamscan -ri "$D" >> "$LOGFILE";

 # get the value of "Infected lines"
 MALWARE=$(tail "$LOGFILE"|grep Infected|cut -d" " -f3);
done
```

Any idea?

P.S. I already tried with [this solution]("https://askubuntu.com/questions/1170774/clamav-clamd-ctl-file-is-not-getting-created-on-ubuntu").

---

### Post by DuckHook on 2020-02-14
*Thread moved to **Security** as the more appropriate forum.*

---

