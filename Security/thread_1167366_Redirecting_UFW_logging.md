---
title: "Redirecting UFW logging"
date: 2009-05-22
forum: Security
---

### Post by cpt_power on 2009-05-22
I have a firewall server running 9.04 and I would like to have the logging from ufw redirected to a file other than /var/log/messages by default.  Is there a line I can enter in the conf file that will make this happen, or do I have to grep it any time I need to read through the firewall logs?

Thanks!

---

### Post by lovinglinux on 2009-05-22
Open /etc/syslog.conf 

```
gksudo gedit /etc/syslog.conf 
```

Then add this line, changing iptables.log to whatever you want:

```
kern.warning                     /var/log/iptables.log
```

---

### Post by cpt_power on 2009-05-25
Won't that redirect all kernel warning messages to the iptables.log file?  I'm looking for just the iptables output to be directed to a single logfile.

---

### Post by lovinglinux on 2009-05-25
> **cpt_power said:**
> Won't that redirect all kernel warning messages to the iptables.log file?  I'm looking for just the iptables output to be directed to a single logfile.

It would redirect other warnings too. I don't know another way of doing this, but I'm not an expert.

---

### Post by lovinglinux on 2009-05-25
I guess you could run this, to grep eth0 logs instead of modifying syslog.conf:

```
sudo tail -f /var/log/kern.log | grep eth0 >> /var/log/iptables.log
```

---

