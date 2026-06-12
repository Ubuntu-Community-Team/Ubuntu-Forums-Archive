---
title: "Ubuntuzilla CRON crashing the system?"
date: 2007-12-31
forum: Ubuntuzilla
---

### Post by habtish on 2007-12-31
Hello all,

I had installed Ubuntuzilla a while back before TB 2.x was added in the official repos, then removed it using the uninstall script. Apparently, it looks like the CRON entries for checking updates have not been cleaned up by the uninstall script, not sure... am just a novice user.
My system has been freezing recently when going into screen saver mode and gets stuck in a non responsive mode. I had previously thought it might have been a conflict with Compiz-fusion and the gnome screen saver and turned off Compiz.... but this issue is still around, and sporadic. This just happened to me a while ago and the last entries I got from the syslog point to ubuntuzilla. ```
 16:00:01 hb /USR/SBIN/CRON[15731]: (abc) CMD (/usr/local/bin/ubuntuzilla.py -p thunderbird -a checkforupdategui 2>&1 | logger -p user.notice -t "UBUN
TUZILLA" -- )
Dec 31 16:00:02 hb UBUNTUZILLA: /bin/sh: /usr/local/bin/ubuntuzilla.py: not found
Dec 31 18:22:33 hb syslogd 1.4.1#21ubuntu3: restart

```Could this free be caused by the above? Any known issues? ideas?

TIA & Happy New Year to all!!

---

### Post by nanotube on 2008-01-08
> **habtish said:**
> Hello all,

I had installed Ubuntuzilla a while back before TB 2.x was added in the official repos, then removed it using the uninstall script. Apparently, it looks like the CRON entries for checking updates have not been cleaned up by the uninstall script, not sure... am just a novice user.
My system has been freezing recently when going into screen saver mode and gets stuck in a non responsive mode. I had previously thought it might have been a conflict with Compiz-fusion and the gnome screen saver and turned off Compiz.... but this issue is still around, and sporadic. This just happened to me a while ago and the last entries I got from the syslog point to ubuntuzilla. ```
 16:00:01 hb /USR/SBIN/CRON[15731]: (abc) CMD (/usr/local/bin/ubuntuzilla.py -p thunderbird -a checkforupdategui 2>&1 | logger -p user.notice -t "UBUN
TUZILLA" -- )
Dec 31 16:00:02 hb UBUNTUZILLA: /bin/sh: /usr/local/bin/ubuntuzilla.py: not found
Dec 31 18:22:33 hb syslogd 1.4.1#21ubuntu3: restart

```Could this free be caused by the above? Any known issues? ideas?

TIA & Happy New Year to all!!

well... it's unlikely to cause a system crash, if ubuntuzilla doesn't exist, the cron job just quits. 

but if you really want, you can clean up your user crontab using "crontab -e" command and manually delete the ubunutzilla lines...

---

