---
title: "imap login problem"
date: 2007-08-25
forum: Server Platforms
---

### Post by b06dqn on 2007-08-25
have a problem with imap,
in ssh if i "telnet localhost imap2" the login works, but if i "telnet office.idz.ro imap2" it connects but the login fails. 
i use courier imap.

the problem is that i can't use the webmail (roundcube), the login fails also on the login page.

---

### Post by 505 on 2007-08-25
Check the file /etc/courier/imapd to see if connection are limited to localhost (127.0.0.1)

---

### Post by b06dqn on 2007-08-25
```
##NAME: ADDRESS:0
#
#  Address to listen on, can be set to a single IP address.
#
# ADDRESS=127.0.0.1

ADDRESS=0

```

is this the problem? what do i have modifiy?

---

### Post by MrHorus on 2007-08-26
> **b06dqn said:**
> have a problem with imap,
in ssh if i "telnet localhost imap2" the login works, but if i "telnet office.idz.ro imap2" it connects but the login fails. 
i use courier imap.

the problem is that i can't use the webmail (roundcube), the login fails also on the login page.

This is a DNS issue.

"telnet localhost imap2" simply asks telnet to connect to localhost (127.0.0.1) on the IMAP2 port - telling it to telnet to "office.idz.ro" - this step is failing as the DNS does not seem setup for this.

billy@winky:~$ nslookup office.idz.ro 
Server:         212.159.6.10
Address:        212.159.6.10#53

** server can't find office.idz.ro.mshome.net: NXDOMAIN

---

