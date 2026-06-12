---
title: "ssh logged port in auth.log is different than 22"
date: 2010-10-22
forum: Server Platforms
---

### Post by tapas_mishra on 2010-10-22
As far as I understand ssh runs on port 22 but in my /var/log/auth.log I see 
> Oct 22 11:14:51 somedomain sshd[28588]: Accepted publickey for user from 192.168.0.17 **port 48504** ssh2
why is this logged 48504 different than ssh port 22?

---

### Post by CharlesA on 2010-10-22
That's the source port. It is usually a random high port.

The destination port is always going to be 22 (or whatever one you change it to), but that's not logged.

---

### Post by tapas_mishra on 2011-03-07
Thanks for clearing that out.

---

