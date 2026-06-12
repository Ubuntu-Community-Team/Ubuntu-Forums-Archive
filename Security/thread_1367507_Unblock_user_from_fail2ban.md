---
title: "Unblock user from fail2ban"
date: 2009-12-29
forum: Security
---

### Post by R.Bucky on 2009-12-29
Ok, no laughing. I seem to have blocked myself out of my server from a remote location. I am using fail2ban. I do not have physical access to the machine for several hours, but have a mobile device to get into the server. How do I unblock myself?
Hey, I said no laughing.

---

### Post by cdenley on 2009-12-29
The only way I know of is to simply delete the iptables rule fail2ban created.

---

### Post by R.Bucky on 2009-12-29
Assuming that to be in hosts.deny. I'll check it out. Thanks.

---

### Post by FuturePilot on 2009-12-29
> **R.Bucky said:**
> Assuming that to be in hosts.deny. I'll check it out. Thanks.

No, Iptables is completely different from the tcpwrappers (hosts.deny, hosts.allow etc.)

```
sudo iptables -L -n
```
will show you all the iptables rules. See [http://bodhizazen.net/Tutorials/iptables/]("http://bodhizazen.net/Tutorials/iptables/") for more info on iptables.

---

### Post by noway2 on 2009-12-29
Seriously, no laughing.  I have done this to myself...

Doesn't fail2ban automatically release the lock after 5-10 minutes anyway?  Or did you go and put some ludicrous time frame in?  Now, that might be worth a laugh.

If applicable and do-able, you may want to add yourself to a whitelist so you won't block yourself out.

---

### Post by pannemanm on 2010-01-19
I don't know if you already solved it, but here's my suggestion:
 
First enter following command:
 
```
sudo iptables -L -n
```
This option shows all entries
 
To remove an entry, use following:
```
iptables -D fail2ban-SSH -s xxx.xxx.xxx.xxx -j DROP
```
 
Replace SSH with the correct chain name
On the x's, enter the IP adress to unblock
 
I've added a portion my fail2ban jail.local file
 
```

# The DEFAULT allows a global definition of the options. They can be override
# in each jail afterwards.
 
[DEFAULT]
 
# "ignoreip" can be an IP address, a CIDR mask or a DNS host. Fail2ban will not
# ban a host which matches an address in this list. Several addresses can be
# defined using space separator.
ignoreip = Enter the IP addresses to ignore here
 
# "bantime" is the number of seconds that a host is banned. 172800 seconds = 48 hours
bantime = 172800
 
# A host is banned if it has generated "maxretry" during the last "findtime"
# seconds.
findtime = 600
 
# "maxretry" is the number of failures before a host get banned.
maxretry = 3
 
# "backend" specifies the backend used to get files modification. Available
# options are "gamin", "polling" and "auto". This option can be overridden in
# each jail too (use "gamin" for a jail and "polling" for another).
#
# gamin: requires Gamin (a file alteration monitor) to be installed. If Gamin
# is not installed, Fail2ban will use polling.
# polling: uses a polling algorithm which does not require external libraries.
# auto: will choose Gamin if available and polling otherwise.
backend = auto
&#12288;
# This jail corresponds to the standard configuration in Fail2ban 0.6.
# The mail-whois action send a notification e-mail with a whois request
# in the body.
 
[ssh-iptables]
enabled = true
filter = sshd
action = iptables[name=SSH, port=ssh, protocol=tcp]
sendmail-whois-lines[name=SSH, dest=mailaddress, sender=sender address]
logpath = /var/log/auth.log
maxretry = 3
 
[vsftpd-iptables]
enabled = true
filter = vsftpd
action = iptables[name=VSFTPD, port=ftp, protocol=tcp]
sendmail-whois-lines[name=VSFTPD, dest=mailaddress, sender=sender address]
logpath = /var/log/vsftpd.log
/var/log/auth.log
maxretry = 3
 
[apache-iptables]
enabled = true
filter = apache-noscript
action = iptables[name=APACHE, port=http, protocl=tcp]
sendmail-whois-lines[name=APACHE2, dest=mailaddress, sender=sender address]
logpath = /var/log/apache2/error.log
maxretry = 3

```

---

