---
title: "Best way to check smart stauts?"
date: 2010-06-16
forum: Server Platforms
---

### Post by seanstar12 on 2010-06-16
I am wanting a daily script to check the smart status of the drives and email me if any fail. Is this the best way to go about it, or is there something better?

```

#!/bin/sh
# Script to check smart status of drives
        
        smartctl /dev/sdb -H | grep -e 'overall-health' | awk '{print "sdb " $6}' > /scripts/smart_status
        smartctl /dev/sdc -H | grep -e 'overall-health' | awk '{print "sdc " $6}' >> /scripts/smart_status
        smartctl /dev/sde -H | grep -e 'overall-health' | awk '{print "sde " $6}' >> /scripts/smart_status
        smartctl /dev/sdf -H | grep -e 'overall-health' | awk '{print "sdf " $6}' >> /scripts/smart_status
        smartctl /dev/sdg -H | grep -e 'overall-health' | awk '{print "sdg " $6}' >> /scripts/smart_status
        smartctl /dev/sdh -H | grep -e 'overall-health' | awk '{print "sdh " $6}' >> /scripts/smart_status
        smartctl /dev/sdi -H | grep -e 'overall-health' | awk '{print "sdi " $6}' >> /scripts/smart_status
        smartctl /dev/sdj -H | grep -e 'overall-health' | awk '{print "sdj " $6}' >> /scripts/smart_status
        smartctl /dev/sdk -H | grep -e 'overall-health' | awk '{print "sdk " $6}' >> /scripts/smart_status
        smartctl /dev/sdl -H | grep -e 'overall-health' | awk '{print "sdl " $6}' >> /scripts/smart_status
        smartctl /dev/sdm -H | grep -e 'overall-health' | awk '{print "sdm " $6}' >> /scripts/smart_status

*edit* some if command in here (haven't written it yet, but soon will)*
cat /scripts/smart_status | grep -E 'FAILED' > /tmp/failed_smart_status
if
mailx -s "Failed Smart Status" $EMAIL < '/tmp/failed_smart_status'
fi

```

---

### Post by hictio on 2010-06-16
Have you checked this one yet? [Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by seanstar12 on 2010-06-16
> **hictio said:**
> Have you checked this one yet? [Smartmontools](https://help.ubuntu.com/community/Smartmontools)
Wow, I completely looked over that page but I didn't think it was what I needed. I think it's going to do the trick. Thanks!

By the way..
I edited the /etc/smartd.conf
DEVICESCAN -m [email]myemailaddress@domain.com[/email] -M exec /usr/share/smartmontools/smartd-runner

services smartmontools restart

---

