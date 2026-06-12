---
title: "Run Inadyn at startup"
date: 2009-07-21
forum: Server Platforms
---

### Post by damo12 on 2009-07-21
I support a server remotely through Webmin.  As the server has a dynamic IP address provided by the ISP I use Inadyn and DynDNS.

Following the guide on DynDNS I have set up a configuration file at /etc/inadyn.conf but when I restart the server I have to manually start the update client using 

```
inadyn --username test --password test --update_period_sec 600 --alias test.homeip.net
```

How do I get this to run automatically when the server boots?

Thanks in advance.

---

### Post by prshah on 2009-07-21
> **damo12 said:**
> when I restart the server I have to manually start the update client 
How do I get this to run automatically when the server boots?


Add the line to your /etc/rc.local file; don't disturb the last line.

Or create a cronjob to do it for you.

---

### Post by damo12 on 2009-07-22
> **prshah said:**
> Add the line to your /etc/rc.local file; don't disturb the last line.

Or create a cronjob to do it for you.

Thanks for the help, I knew it would be something straight forward.

---

