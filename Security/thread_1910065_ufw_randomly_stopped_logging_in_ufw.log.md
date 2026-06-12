---
title: "ufw randomly stopped logging in ufw.log"
date: 2012-01-16
forum: Security
---

### Post by samthethe on 2012-01-16
Today ufw decided to stop logging to ufw.log - ufw.log is:
empty, blank, has no messages, 0 bytes, zero bytes, truncated

I didn't do anything!

Messages continue as normal to kern.log and syslog.

Part of the reason I choose ufw is simply so that my log messages would be clear, and isolated from the syslog.  No that's broken I'm rather annoyed :<

PLEASE how do I fix this!!

Thanks in advanced,

sam

p.s. Please no "fix this file..." or "do this...", rather "here is the exact text you need to paste, and here is the exact path you need to paste it into..." or "here is the exact command line you need to run...".

---

### Post by Dangertux on 2012-01-16
> **samthethe said:**
> Today ufw decided to stop logging to ufw.log - ufw.log is:
empty, blank, has no messages, 0 bytes, zero bytes, truncated

I didn't do anything!

Messages continue as normal to kern.log and syslog.

Part of the reason I choose ufw is simply so that my log messages would be clear, and isolated from the syslog.  No that's broken I'm rather annoyed :<

PLEASE how do I fix this!!

Thanks in advanced,

sam

p.s. Please no "fix this file..." or "do this...", rather "here is the exact text you need to paste, and here is the exact path you need to paste it into..." or "here is the exact command line you need to run...".

It's a little hard to do it the way you want since we don't know exactly why your UFW stopped logging. However here are my suggestions.

```

sudo ufw status

```Should return 

```

Status: active

```If it doesn't re-enable ufw

```

sudo ufw enable

```If that's not the issue we need to check that logging is enabled by doing the following.


```

sudo grep -i 'loglevel' /etc/ufw/ufw.conf

```It should return something like this

```

# Please use the 'ufw' command to set the loglevel. Eg: 'ufw logging medium'.
LOGLEVEL=low

```*feel free to increase the LOGLEVEL to high if you want more detailed logging. You may do so by 

```

sudo ufw logging medium

```or 

```

sudo ufw logging high

```If it is not disabled/off then try the following

```

sudo grep -i 'logging' /etc/ufw/before.rules

```Which should return the following

```

-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny

```if they are commented out as such

```

#-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
#-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny

```then 

```

sudo nano /etc/ufw/before.rules

```And remove the octothorpe (#).

Afterwards restart ufw for good measure

```

sudo ufw disable && sudo ufw enable

```Additionally make sure the logrotate daemon is correctly configured for ufw by doing the following.

```

sudo cat /etc/logrotate.d/ufw

```Which should return the following

```

/var/log/ufw.log
{
        rotate 4
        weekly
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}

```If it does not edit the contents of the file with nano so that it looks like what I posted above.

```

sudo nano /etc/logrotate.d/ufw

```

 Then

```

sudo service rsyslog restart

```If none of these are the problem a simple 

```

sudo ufw disable && sudo ufw enable

```May fix the problem. Hope this helps.

---

### Post by samthethe on 2012-01-20
Thank you very much for the reply ... I understood all of it ... I'll let you know how it goes.

---

### Post by samthethe on 2012-01-27
Thanks again.  After googling your response seems to cover the most ground, unfortunately none of it worked :(

It took me 20 mins to write the below script - much less time that continuing to troubleshoot this me thinks.

IF YOU CAN'T FIX IT - CLUDGE IT!! :D


```
#!/bin/bash

DST_LOG=/var/log/ufw.log
SLEEP_TIME=30

if [ ! -e /var/tmp/syslogSize ]; then
    stat -c %s /var/log/syslog > /var/tmp/syslogSize
fi

while : ;
do
    sleep ${SLEEP_TIME}
    SYSLOG_SIZE_OLD=`cat /var/tmp/syslogSize`
    SYSLOG_SIZE_NEW=`stat -c %s /var/log/syslog`
    NEW_DATA_LEN=`expr ${SYSLOG_SIZE_NEW} - ${SYSLOG_SIZE_OLD}`
    if [ ${NEW_DATA_LEN} -gt 0 ]; then
        tail -c${NEW_DATA_LEN} /var/log/syslog | grep UFW >> ${DST_LOG}
        echo ${SYSLOG_SIZE_NEW} > /var/tmp/syslogSize
    else
        # should use creation time really
        if [ ${NEW_DATA_LEN} -lt 0 ]; then
            SYSLOG_0_SIZE=`stat -c %s /var/log/syslog.0`
            SYSLOG_0_TAIL_BYTES_WANTED=`expr ${SYSLOG_0_SIZE} - ${SYSLOG_SIZE_OLD}`
            tail -c${SYSLOG_0_TAIL_BYTES_WANTED} /var/log/syslog.0 | grep UFW >> ${DST_LOG}
            cat /var/log/syslog | grep UFW >> ${DST_LOG}
            echo ${SYSLOG_SIZE_NEW} > /var/tmp/syslogSize
        fi
    fi
done
```

---

### Post by samthethe on 2012-02-25
Oh btw, I didn't use "tail -f" because this will only get messages once tail is started, and obv there is no easy way to ensure tail starts before iptables!!

---

### Post by Dangertux on 2012-02-25
Haha that works though you should consider filing a bug report if you are sure this isnt a configuration error.

---

