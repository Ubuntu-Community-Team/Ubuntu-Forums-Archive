---
title: "Removed auth.log"
date: 2010-11-01
forum: Server Platforms
---

### Post by qjmoss on 2010-11-01
Now I'm running Debian lenny, but i thought that i'd try asking her.

Now, I'm dinkin' around in my auth.log file, and I managed to remove it.

I created a new auth.log file, but I'm wondering on how to restore it to the previous state so it is actually taking logs.

Any help would be great.

Thank you.

](*,)

---

### Post by TSJason on 2010-11-03
If debian uses the same user and group as ubuntu (possibly) then you'll probably want to:

```

sudo chown syslog.adm /var/log/auth.log
sudo chmod 640 /var/log/auth.log
sudo /etc/init.d/rsyslog restart

```

or, if you're not using rsyslog

```

sudo /etc/init.d/syslog restart

```

HTH

---

