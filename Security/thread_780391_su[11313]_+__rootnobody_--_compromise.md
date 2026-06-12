---
title: "su[11313]: + ??? root:nobody -- compromise?"
date: 2008-05-03
forum: Security
---

### Post by pytheas22 on 2008-05-03
OSSEC sent a report that /var/auth.log contains the following lines from a few hours ago:

```
May  3 08:40:43 my-desktop su[11313]: + ??? root:nobody

May  3 08:40:43 my-desktop su[11313]: pam_unix(su:session): session opened for user nobody by (uid=0)
```

I am pretty worried about this.  Who is user nobody and why would he have gotten root access to my machine?  I've read some threads that say that this can related to cron jobs running, but I don't have any cron jobs scheduled to run at the time that the login occurred.

I have my ssh and http ports open to the Internet, but OSSEC shuts down brute force attacks and I use strong passwords.  Should I be worried that my system has somehow been compromised?  rkhunter and chkrootkit don't find any rootkits; is there anything else I should look for?

---

### Post by brian_p on 2008-05-03
> **pytheas22 said:**
> OSSEC sent a report that /var/auth.log contains the following lines from a few hours ago:

```
May  3 08:40:43 my-desktop su[11313]: + ??? root:nobody

May  3 08:40:43 my-desktop su[11313]: pam_unix(su:session): session opened for user nobody by (uid=0)
```

I am pretty worried about this.  Who is user nobody and why would he have gotten root access to my machine?  I've read some threads that say that this can related to cron jobs running, but I don't have any cron jobs scheduled to run at the time that the login occurred.

I have my ssh and http ports open to the Internet, but OSSEC shuts down brute force attacks and I use strong passwords.  Should I be worried that my system has somehow been compromised?  rkhunter and chkrootkit don't find any rootkits; is there anything else I should look for?

Nothing to worry about. nobody is a user on your machine. She pops into mine at about 6:25 and does a bit of housekeeping. Rotating logs, updating the locate database etc. Have a look in /etc to see what you have scheduled for 08:40.

---

### Post by pytheas22 on 2008-05-03
> Nothing to worry about. nobody is a user on your machine. She pops into mine at about 6:25 and does a bit of housekeeping. Rotating logs, updating the locate database etc. Have a look in /etc to see what you have scheduled for 08:40.

Thanks for the response.  This is reassuring, but I am still wondering why I've never seen a warning like this until today.  I've been running OSSEC on several Ubuntu machines for a while (although it's only since last weekend that one of them runs Hardy) and this is the first time I've gotten warned about nobody.  Also, as the output below indicates, I have no cronjobs scheduled for 8:40.  Can I still be confident that there's no problem?

```
$ cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
05 00 * * * root /var/ossec/bin/ossec-control restart
#
```

---

### Post by brian_p on 2008-05-03
> **pytheas22 said:**
> Thanks for the response.  This is reassuring, but I am still wondering why I've never seen a warning like this until today.  I've been running OSSEC on several Ubuntu machines for a while (although it's only since last weekend that one of them runs Hardy) and this is the first time I've gotten warned about nobody.  Also, as the output below indicates, I have no cronjobs scheduled for 8:40.  Can I still be confident that there's no problem?

OSSEC is not something I'm familiar with so can't help you with the time disparity. Have look for nobody in /var/log/auth.log and also see /etc/updatedb.conf. I still think there is no problem.

---

### Post by The Cog on 2008-05-05
FYI: The nobody account is an account with few privileges that is used by some daemons as a safety measure. As an example, OpenVPN changes to user nobody after it has finished starting so that if the daemon were to be compromised by a malformed packet exploiting a vulnerability, it still couldn't make the daemon cause any system damage. The daemon starts as root, opens the few resources it really needs and then in effect, throws away the keys. In this case I don't fully understand the log messages, but it does look like something started with root privilege and then changed to nobody, which is the direction a good daemon would be going in. 

It's odd that OSSEC picked it up though - it has never picked that up on any of the Ubuntu servers I run it on.

---

### Post by yomaoni on 2008-05-15
I remember the first time I saw this on one of the servers I managed after an upgrade and I thought that I had been hacked.  So needless to say you are not the only one who has thought that.

---

### Post by yaztromo on 2008-05-15
If you have not seen it before the job was probably part of cron.monthly. Check the scripts in /etc/cron.monthly

---

