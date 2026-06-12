---
title: "MRTG not updating"
date: 2007-01-01
forum: Server Platforms
---

### Post by Enigmatic on 2007-01-01
I'm not sure what's up with my install of MRTG. I installed it, and it was updating itself perfectly. After rebooting my machine though, it is no longer updating. I'm unsure as to what could have changed. Here is the contents of crontab -e for root:

0-55/5 * * * * root if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ]; then env LANG=C /usr/bin/mrtg /etc/mrtg.cfg >> /var/log/mrtg/mrtg.log 2>&1; fi

---

### Post by gfowler on 2007-01-01
You need a mrtg directory in /var/lock/ for it to work.  Reboot will remove the directory and MRTG will fail to update.  I put mkdir /var/lock/mrtg  in /etc/rc.local and it makes the required /var/lock/mrtg on reboot.  

Jerry

---

### Post by Enigmatic on 2007-01-01
Sweet, thanks!

---

