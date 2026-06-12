---
title: "cron grandchild error status 1"
date: 2010-12-03
forum: Server Platforms
---

### Post by inzaghi89 on 2010-12-03
Hi,

I am using ubuntu 10.10 server edition x86 and I have some kind off issue with cron and my script. It is really easy script - just only mkdir and grep, as you can see below:
```
#!/bin/bash
KOPIUJ=`date +"%b %e"`
DZIEN=`date +%d`
MIESIAC=`date +%m`

mkdir -p /home/filip/public_html/logi/"$MIESIAC"
grep "$KOPIUJ" /var/log/ufw.log | grep "UFW BLOCK" > /home/filip/public_html/logi/$MIESIAC/$DZIEN-ufw-block.log
grep "$KOPIUJ" /var/log/ufw.log | grep "UFW AUDIT" | grep -vf "/root/cron/audit" > /home/filip/public_html/logi/$MIESIAC/$DZIEN-ufw-audit.log
grep "$KOPIUJ" /var/log/ufw.log | grep "UFW ALLOW" | grep -vf "/root/cron/allow" > /home/filip/public_html/logi/$MIESIAC/$DZIEN-ufw-allow.log
```

But is has giving me allways this error (in syslog):
> Dec  3 14:41:01 Alex CRON[3369]: (root) CMD (sh /root/cron/ufw.sh)
Dec  3 14:41:01 Alex CRON[3367]: (CRON) error (grandchild #3369 failed with exit status 1)


Have you any idea, how can I solve this issue? Script is making from root cron (crontab -eu root):
```
*/30 * * * * sh /root/cron/ufw.sh
```

I want to mention that before update from 10.04 all works well. After update from 10.04 to 10.10... it has messed...

---

