---
title: "Curious behavior..."
date: 2010-05-06
forum: Server Platforms
---

### Post by mslovette on 2010-05-06
I have 9.10 server installed and all patches up-to-date. For some reason, the O/S is constantly reloading the **smb.conf** for smbd. This activity appears to be at random intervals averaging 6 reloads during every 12 hour period. Do I need to be concerned? Do I need to "tweak" something?
 
/vr,
 
mslovette

---

### Post by uberlinuxnerd on 2010-05-06
> **mslovette said:**
> I have 9.10 server installed and all patches up-to-date. For some reason, the O/S is constantly reloading the **smb.conf** for smbd. This activity appears to be at random intervals averaging 6 reloads during every 12 hour period. Do I need to be concerned? Do I need to "tweak" something?
 
/vr,
 
mslovette

Polling for changes maybe?

---

### Post by capscrew on 2010-05-06
> **mslovette said:**
> I have 9.10 server installed and all patches up-to-date. For some reason, the O/S is constantly reloading the **smb.conf** for smbd. This activity appears to be at random intervals averaging 6 reloads during every 12 hour period. Do I need to be concerned? Do I need to "tweak" something?
 
/vr,
 
mslovette

Are you using DHCP to provide your server with an IP address (i.e. a static lease (reserved))?

---

### Post by mslovette on 2010-05-06
> **capscrew said:**
> Are you using DHCP to provide your server with an IP address (i.e. a static lease (reserved))?
 
I recently (within the last week), converted the IP assignment from DHCP-provided (by my router) to a static IP.

---

### Post by capscrew on 2010-05-06
> **mslovette said:**
> I recently (within the last week), converted the IP assignment from DHCP-provided (by my router) to a static IP.

Frequently users have your complaint when they are using a DHCP served IP (fixed IP or random IP).  This is because every time the interface changes the smbd daemon reloads to be sure it is up to date.  Samba can't tell that the dhcp lease is only being renewed.

In your case I would modify the syslog reporting to be more verbose.  You can do that by editing the /etc/samba.smb.conf file.  See below for the proper section.  I would increase the reporting to 3
```

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0  [COLOR="Red"]**<--make this 3**[/COLOR]


```

You can then monitor what causes your reloading.

---

### Post by mslovette on 2010-05-07
Capscrew... Thx...
 
Have made the suggested mod to smb.conf and will monitor to see if there is anything else in the logs.
 
/vr, mslovette

---

