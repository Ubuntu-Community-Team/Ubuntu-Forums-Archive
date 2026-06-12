---
title: "Removing with apt-get"
date: 2009-07-26
forum: Server Platforms
---

### Post by brunoskrebs on 2009-07-26
Hi there,

I just removed proftpd from my server using "apt-get remove proftpd".

Then I searched for files/foldes containing proftpd in the name and it returned this small list:

> 
/etc/cron.monthly/proftpd
/etc/default/proftpd
/etc/init.d/proftpd
/etc/pam.d/proftpd
/etc/proftpd
/etc/proftpd/ldap.conf
/etc/proftpd/modules.conf
/etc/proftpd/proftpd.conf
/etc/proftpd/sql.conf
/etc/proftpd/tls.conf
/etc/rc0.d/K50proftpd
/etc/rc1.d/K50proftpd
/etc/rc2.d/S50proftpd
/etc/rc3.d/S50proftpd
/etc/rc4.d/S50proftpd
/etc/rc5.d/S50proftpd
/etc/rc6.d/K50proftpd
/var/cache/apt/archives/proftpd_1.3.1-6ubuntu1_i386.deb
/var/lib/dpkg/info/proftpd.list
/var/lib/dpkg/info/proftpd.postrm
/var/log/proftpd
/var/log/proftpd/controls.log
/var/log/proftpd/proftpd.log


can I remove all these files without facing trouble??

Thanks!

---

### Post by wojox on 2009-07-26
Yes some are directories, but yes you can remove all instances of proftpd.
Next time try 

```
sudo apt-get --purge remove <application>
```

It removes all including conf files

---

