---
title: "MySQL Remote Access"
date: 2016-09-14
forum: Server Platforms
---

### Post by Wunala Dreaming on 2016-09-14
Hi. I just setup a  Linode and made a complete LAMP installation. I'm trying to access MySQL through MySQL WorkBench but I'm getting a connection error:

> Can't connect to MySQL server error 111

This is what I've tried so far:
- Commented out the "bind-address" option on the my.cnf file or just setting it to 0.0.0.0 or *
- Grant all permissions to 'root'@'%' and the user I created ('user'@'%'), and flushed privileges. 
- Restarted mysql service

Do you know what I might be missing in order to connect remotely to MySQL?

Thanks!

---

### Post by Habitual on 2016-09-14
> **Wunala Dreaming said:**
> Grant all permissions to 'root'@'%' 
Do you understand what the "%" represents?
Wildcard access from **any host.**
Gaping Security Hole.

'root'@'known_ip' is better security.
Known_ip would be your house, car, speedboat, lawnchair, toaster.wifi, or desktop  ip address.

---

### Post by SeijiSensei on 2016-09-14
First let's test the connection.  Open a terminal and enter the command "telnet your.server.name 3306" replacing "your.server.name" with the appropriate hostname or IP address.  Do you get a "connected" reply from mysqld?  (You'll see a bunch of gibberish, too.  That's normal.)  If not, then maybe there is a firewall in the way that is blocking port 3306.  If you open up the firewall, try to limit access to just the IPs of machines that you will use to connect.  With iptables it would be rules like this:
```

/sbin/iptables -A INPUT -p tcp -s 10.10.10.10 -d ip.of.your.server --dport 3306 -j ACCEPT
[more such lines for other potential clients if needed]
/sbin/iptables -A INPUT -p tcp -d ip.of.your.server --dport 3306 -j REJECT

```

---

