---
title: "strange open ports"
date: 2011-07-07
forum: Server Platforms
---

### Post by Aweks on 2011-07-07
Hi,

I have ordered a server with OS:
Ubuntu Server 11.04

after a quick nmap scan I found out a few open ports and I have no idea what is using them.

What is using these ports?

1102/tcp filtered adobeserver-1
1201/tcp open     nucleus-sand

Thanks for answer.

---

### Post by diesch on 2011-07-07
```
sudo fuser -v 1102/tcp 1201/tcp
``` shows  you the processes listening on this ports.

---

### Post by Aweks on 2011-07-10
> **diesch said:**
> ```
sudo fuser -v 1102/tcp 1201/tcp
``` shows  you the processes listening on this ports.

Thanks for the tip, but it shows nothing :(

---

### Post by CharlesA on 2011-07-10
Are you scanning localhost?

---

### Post by karlson on 2011-07-10
Simplest way:

```
netstat -apn | egrep "1102|1201"
```

This will show the processes having the ports opened or listened to.

---

