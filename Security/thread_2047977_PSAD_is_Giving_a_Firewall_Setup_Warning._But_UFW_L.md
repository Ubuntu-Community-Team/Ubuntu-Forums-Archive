---
title: "PSAD is Giving a Firewall Setup Warning. But UFW Logging is enabled."
date: 2012-08-25
forum: Security
---

### Post by THPubs on 2012-08-25
I have setup PSAD on my server. It asks me to add the following iptables rules:

```
iptables -A INPUT -j LOG
iptables -A FORWARD -j LOG
ip6tables -A INPUT -j LOG
ip6tables -A FORWARD -j LOG
```

I'm using UFW to manage iptables. So, I simply ran the command sudo ufw logging on But, whenever I restart PSAD or restart my server, I get an email saying:

message subject : [psad-status] firewall setup warning on server!

[HTML][-] You may just need to add a default logging rule to the /sbin/iptables
    'filter' 'INPUT' chain on *server*.  For more information,
    see the file "FW_HELP" in the psad sources directory or visit:

    http://www.cipherdyne.org/psad/docs/fwconfig.html

[-] You may just need to add a default logging rule to the /sbin/ip6tables
    'filter' 'INPUT' chain on *server*.  For more information,
    see the file "FW_HELP" in the psad sources directory or visit:

    http://www.cipherdyne.org/psad/docs/fwconfig.html[/HTML]

PS : The machine have Ubuntu 12.04 and the latest PSAD 2.2 (compiled from the source)

---

### Post by 2F4U on 2012-08-26
Since ufw has several log levels and the command you run turned on just the lowest log level. I guess that PSAD requires more than that and you can turn on high log levels for ufw:

[http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html)

The log levels available are off, low, medium, high and full.

---

### Post by THPubs on 2012-08-26
> **2F4U said:**
> Since ufw has several log levels and the command you run turned on just the lowest log level. I guess that PSAD requires more than that and you can turn on high log levels for ufw:

[http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/ufw.8.html)

The log levels available are off, low, medium, high and full.

Tried both high and full but still PSAD sends the warning :(

---

### Post by THPubs on 2012-08-27
No solution?

---

### Post by Doug S on 2012-08-27
Enabling logging on UFW just enables logging of some specific rules.
To me, it seems as though this PSAD thing wants you to log every single packet (oh my goodness!!!) The only thing I can think of is to toss out UFW and write your iptable rules directly so as to satify PSAD.

---

### Post by nosebb on 2012-09-26
So, do a &#8220;ufw logging on&#8221; in order for ufw to propagate several files in the /etc/ufw directory, amongst them before(6).rules & after(6).rules. Edit both of the before.rules (before and before6 .rules files) and append &#8220;-A INPUT -j LOG&#8221; & &#8220;-A FORWARD -j LOG&#8221; (on separate lines) accordingly, making sure to not append them after the COMMIT line. Reboot, then run &#8220;psad --fw-analyze&#8221; to see the problem is resolved.

---

