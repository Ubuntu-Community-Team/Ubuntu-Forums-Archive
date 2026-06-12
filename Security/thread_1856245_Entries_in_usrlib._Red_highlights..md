---
title: "Entries in usr/lib. Red highlights."
date: 2011-10-07
forum: Security
---

### Post by MadMax2 on 2011-10-07
11.04
I assume these are false positives?

Chkrootkit says:
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/pymodules/python2.7/.path /usr/lib/pymodules/python2.7/PyQt4/uic/widget-plugins/.noinit /usr/lib/jvm/.java-6-openjdk.jinfo


-rwsr-xr-x  1 root root         9676 2011-04-11 23:09 pt_chown


lrwxrwxrwx  1 root root           13 2011-07-23 11:43 sendmail -> ../sbin/exim4
....
I haven't got time to study this at the moment although I plan to take the time. I remember in windows you would search for a suspicious file and look up it's properties to see if it was authenticated by microsoft and if not google it then search for all the entries and delet (or whatever).
Thanks

---

