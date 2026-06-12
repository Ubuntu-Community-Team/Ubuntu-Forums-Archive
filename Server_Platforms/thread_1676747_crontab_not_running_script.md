---
title: "crontab not running script"
date: 2011-01-27
forum: Server Platforms
---

### Post by skadoodle on 2011-01-27
Cron seems to be running the script below (According to /var/log/syslog) but I'm not receiving the email it should send. 

This does work when I invoke it manually.

checkraid (-rwxr-xr-x 1 root root)
```
#!/bin/bash

echo `/sbin/dmraid -s > /etc/check-raid/check_state`

index=0

while read line; do
        ARRAY[$index]="$line"
        index=$(($index+1))
done < /etc/check-raid/check_state

check="status : ok"
state=${ARRAY[6]}

if [ "$check" = "$state" ]; then
#       echo "Status: Good"
        var="good"
else
#       echo "Status: Bad"
        var="bad"
fi

if [ "$var" = "good" ]; then
        echo `/usr/bin/nail -s "RAID1 Status Good" some@email.net < /etc/check-raid/notification`
else
        echo `/usr/bin/nail -s "RAID1 Failed on Storage" some@email.net < /etc/check-raid/notification`
fi

```

crontab
```
PATH=/usr/sbin:/usr/bin:/sbin:/bin

# m h  dom mon dow   command
0 0 * * * /etc/cron.daily/offsiteSnJ
0 0 * * * /etc/cron.daily/checkraid


```

Any suggestions would be appreciated. Thanks!

---

### Post by Bob.Davis@wibble.net.nz on 2011-01-27
I had a similar script I couldn't get to send me an e-mail from the cron.

What I did in the end was split the notification and the process and it worked fine.

mines to send a vm backup log,  so make the log with the first script then send it to my e-mail with a second script run later. 

a bit clumsy but works well for me. perhaps this approach may work for you..

---

### Post by skadoodle on 2011-01-27
I will give that a shot and let you know how it goes. Thanks for the reply.

---

### Post by SeijiSensei on 2011-01-27
> /usr/bin/nail

I think that is at least part of the problem.

---

