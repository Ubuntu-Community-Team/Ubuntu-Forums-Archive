---
title: "FAIL2BAN v0.7.6 Feisty: Configurations Problems"
date: 2007-05-02
forum: Server Platforms
---

### Post by shookone on 2007-05-02
Sup everyone...

I have used fail2ban in the past and used the /etc/fail2ban/fail2ban.conf. 

But i recently installed Feisty , fresh installation, on my machine. As i apt-get fail2ban, i noticed that the configurations are different.

Someone please help me with this ... not understanding it much.

---

### Post by shookone on 2007-05-02
Come to realize that these later versions of fail2ban have split the configuration up into two parts.

fail2ban.conf - log related
jail.conf - this is where you configure service logs to be monitored. (SSH APACHE PROFTPD)


My problem still remains. How do i configure it for proftpd. 

When i set it up... i run a /etc/init.d/fail2ban restart 

then i attempt 3 failures (threshold set to 3) and the ip address doesn't get banned.


Any insight would be appreciated.

---

### Post by shookone on 2007-05-02
Ok got it..

Here it is...

fail2ban latests releases separate the config files. fail2ban.conf and jail.conf

If you set the services to monitor in jail.conf you should be ok. In my case it was proftpd... but fail2ban did not ban as it is supposed to. 

Make sure that your proftpd system log outputs to /var/log/proftpd/proftpd.log

Some tutorials put this under /var/log/ftp.log

That would cause conflicts unless you state otherwise in the jail.conf..

This is no longer an issue and i don't mind elaborating if needed.

---

### Post by AndyD on 2007-05-10
Hi shookone (or anyone reading :)  )

I am using Ubuntu Server 6.10 and would like to have Fail2Ban protecting my Apache authentication system.

I have apt-get'd fail2get and can see using debug it is watching the correct file (/var/log/apache2/error.log) 

It doesn't seem to ban me when I create multiple authentication failures tho :(

Auth is done using auth_ldap so I have "tweaked" the [apache] section of fail2ban.con slightly "authentication failure" --> "authentication failed"

Any help would be gratefully received.

---

