---
title: "Inadyn doesn't work"
date: 2011-07-30
forum: Server Platforms
---

### Post by mulanee on 2011-07-30
Hi,
My dyndns.org account is not automatically updated despite using inadyn.
It works nevertheless when I launch  inadyn in console mode.

My cron:
> @reboot /usr/sbin/inadyn>/tmp/log_inadyn


My /etc/inadyn.conf:

> # Basic configuration file for inadyn
#
# /etc/inadyn.conf
update_period_sec 600 # Check for a new IP every 600 seconds
username toto
password toto
dyndns_system [email]dyndns@dyndns.org[/email]
alias toto.com

How to configure for working?

Thank you.

---

### Post by Toz on 2011-07-30
Is there anything in the /tmp/log_inadyn file? Is the inadyn process running when you log in? 

What says:
```
cat /var/log/syslog | grep inadyn
```

As an alternative, you might want to consider adding the command **/usr/sbin/inadyn>/tmp/log_inadyn** into **/etc/rc.local** just before the **exit 0** command. It will also be run at every startup.

---

### Post by mulanee on 2011-07-31
In the /tmp/log_inadyn file, there is only the result of the last time I launched inadyn manually, and only this one.

Result of ```
cat /var/log/syslog | grep inadyn
```


> root@box:~# cat /var/log/syslog | grep inadyn
root@box:~#

Partial result of ps-ax command:
>   738 ?        Ss     0:09 cron
  739 ?        Ss     0:00 atd
  749 ?        S      0:00 CRON
  757 ?        Ss     0:00 /bin/sh -c /usr/sbin/inadyn>/tmp/log_inadyn
  758 ?        S      1:20 /usr/sbin/inadyn

---

### Post by Toz on 2011-07-31
Hmm - it is running. Try changing the command to:
```
@reboot /usr/sbin/inadyn>/tmp/log_inadyn>2>&1
```
and see if any more info shows up in the log file.

Have you tried putting the command in your /etc/rc.local file?
```
/usr/sbin/inadyn>/tmp/log_inadyn>2>&1
exit 0
```

---

### Post by mulanee on 2011-07-31
I changed cron
> @reboot /usr/sbin/inadyn>/tmp/log_inadyn>2>&1
and /etc/rc.local
> /usr/sbin/inadyn>/tmp/log_inadyn>2>&1
exit 0
Result is no log file available and inadyn is not launched.
I came back to initial cron and rc.local (without >2&1)
After reboot inadyn is launched, log file is:
> root@box:~# cat  /tmp/log_inadyn
INADYN: Started 'INADYN version 1.96.2' - dynamic DNS updater.
I:INADYN: IP address for alias 'ebgy.ath.cx' needs update to 'xx'
I:INADYN: IP address for alias 'ebgy.dyndns.info' needs update to 'xx'
I:INADYN: Alias 'ebgy.ath.cx' to IP 'xx' updated successful.
I:INADYN: Alias 'ebgy.dyndns.info' to IP 'xx' updated successful.
Result inside dyndns.org website:
> ebgy.ath.cx 	Host 	xx 	Jul. 31, 2011 3:11 AM
ebgy.dyndns.info 	Host 	xx 	Jul. 31, 2011 10:15 AM

I don't understand anything.

---

### Post by Toz on 2011-07-31
EDIT: removed - double post

---

### Post by Toz on 2011-07-31
Sorry, command should have been:
```
/usr/sbin/inadyn>/tmp/log_inadyn 2>&1
```
but not important now because it looks like its working.

Remove the cron entry and leave the entry in /etc/rc.local. Since you've posted your ip address, **I suggest you reboot immediately**. This will also allow you to test again with the entry only in /etc/rc.local.

After reboot, check to see if everything is working. Also, do not post your ip address, replace the ip address with xxx.xxx.xxx.xxx for privacy purposes.

---

### Post by mulanee on 2011-07-31
Not sure it works.
Ok, now when I reboot inadyn is launched.
But it seems again no update is done to dyndns.org.
This is an inadyn problem.
I will try ddclient

---

### Post by Toz on 2011-07-31
Compare the ip address returned from this site: [http://checkip.dyndns.com/]("http://checkip.dyndns.com/") with the address from your log file. If they match, then the dyndns ip entry is correct and inadyn is working.

---

