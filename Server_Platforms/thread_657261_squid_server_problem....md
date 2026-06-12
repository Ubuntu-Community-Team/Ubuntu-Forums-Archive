---
title: "squid server problem..."
date: 2008-01-03
forum: Server Platforms
---

### Post by Mia_tech on 2008-01-03
I had my squid server working and it appears to stopped, the clients are getting page not found, I restarted the server /etc/init.d/squid restart, and the service is running on port 3128, I'm able to ping the server from my client except I'm getting page not found error

any help appreciated

---

### Post by crouton on 2008-01-03
Check your log directory for errors.  Do you have enough disk-space for squid to run?  Can you still get DNS information (nslookup or dig)?

---

### Post by k_grdn on 2008-01-03
Hi,

As well as checking your logs, start squid with:

/usr/local/sbin/squid -d 1 -N

Scan the output for any significant errors.

Regards,

k_grdn

---

### Post by Mia_tech on 2008-01-03
my bad....firewall was on, and didn't realize, is working now

thanks all

---

