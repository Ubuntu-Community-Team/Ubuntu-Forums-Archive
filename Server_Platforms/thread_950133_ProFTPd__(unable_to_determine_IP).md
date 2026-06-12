---
title: "ProFTPd  (unable to determine IP)"
date: 2008-10-16
forum: Server Platforms
---

### Post by wgregori on 2008-10-16
I'm a newB.... (have pity)

I'm trying to get Proftpd up and running... here's what i'm getting at startup


 * Starting ftp server proftpd                                                   - warning: unable to determine IP address of 'emachine'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]


the system runs behind a NAT firewall... where should I have the IP listed?

Thanks!
Wayne

---

### Post by etechron on 2008-10-16
<meta name="robots" content="noindex, nofollow">

---

### Post by lykwydchykyn on 2008-10-16
You might want to take a look at webmin, it's got a nice proftpd configuration module.

---

### Post by wgregori on 2008-10-17
Thanks.  I had to change my hostname and hosts file so that Proftpd could find the system's ip address.

Wayne

---

