---
title: "check if a port is open for a ip?"
date: 2010-09-08
forum: Server Platforms
---

### Post by Thyagaraj on 2010-09-08
Is it possible to check if a particular port is open for a particular ip in the terminal?

---

### Post by CharlesA on 2010-09-08
Use nmap. Depending if it a local or remote machine, you could always use netstat.

---

### Post by Thyagaraj on 2010-09-08
Thanks for the reply!.
Is it possible to know if remote machine can connect to a particular port with netstat?

---

### Post by CharlesA on 2010-09-08
netstat will only show open connections and listening services, so if you want to see if the remote machine can connect to a certain port, you'd just have to try connecting to that port.

---

### Post by arrrghhh on 2010-09-08
Well... You can see which ports are 'listening' - or accepting connections... but your ISP and router or other firewalls may still block the connection - so you won't truly know if a remote machine can connect without actually connecting a remote machine...

```
netstat -a |grep http
``` for example to see if you have any services listening on http/https.

---

