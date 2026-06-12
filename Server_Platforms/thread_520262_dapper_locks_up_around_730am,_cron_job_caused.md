---
title: "dapper locks up around 7:30am, cron job caused?"
date: 2007-08-08
forum: Server Platforms
---

### Post by 95aspire on 2007-08-08
my machine if i leave it for more than 24 hours it locks up. its not heat or hardware related as i ran a mem test on it for 3 days, and had another os on it for several days, 

im looking in my logs and at the end of each log it has this```
May 17 07:30:01 localhost /USR/SBIN/CRON[7655]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
May 17 07:30:01 localhost anacron[7677]: Anacron 2.3 started on 2007-05-17
May 17 07:30:01 localhost anacron[7677]: Will run job `cron.daily' in 5 min.
May 17 07:30:01 localhost anacron[7677]: Jobs will be executed sequentially
May 17 07:30:43 localhost kernel: [17388724.764000] Inbound IN=eth0 OUT= MAC=00:04:5a:61:11:64:00:40:ca:b4:87:65:08:00 SRC=192.168.40.126 DST=192.168.40.110 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=55344 DF PROTO=TCP SPT=4291 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
May 17 07:35:01 localhost anacron[7677]: Job `cron.daily' started
May 17 07:35:01 localhost anacron[7684]: Updated timestamp for job `cron.daily' to 2007-05-17
May 17 07:36:17 localhost exiting on signal 15
```


whats going on with this??

yes i know it says may lol. machine hasnt been on since then in ubuntu cept to play with it for like 10-15 min at a time, 

so any help would be great. thanks guys

---

