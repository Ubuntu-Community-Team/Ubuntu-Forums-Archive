---
title: "NTP Server"
date: 2009-04-29
forum: Server Platforms
---

### Post by rschapman on 2009-04-29
Here at the University we have a touch control panel that will not sync time with Windows Domain Controllers. What do I need to do to setup a Ubuntu system to simply serve time to these devices? They will not sync with anything not on the LAN so it has to be a local option. Thanks.

---

### Post by koenn on 2009-04-29
```
apt-get install ntp
```
then look in /etc/ntp.conf for configurable options and modify as needed.
restart ntpd when done

---

### Post by CarlosinFL on 2009-04-29
> **koenn said:**
> ```
apt-get install ntp
```
then look in /etc/ntp.conf for configurable options and modify as needed.
restart ntpd when done

Yup - just as noted above. Make sure you point your machines to the IP / host of the NTP server.

```
/etc/init.d/ntp restart
```

---

### Post by rschapman on 2009-04-29
You guys are awesome. Thanks.

---

### Post by koenn on 2009-04-29
you're welcome.

---

