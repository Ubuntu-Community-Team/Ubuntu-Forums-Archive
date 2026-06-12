---
title: "how to configure wlan0 for internet connection eth0 for my network dhcp"
date: 2014-03-05
forum: Server Platforms
---

### Post by Erdem on 2014-03-05
hello 
i have a ubuntu 12.04.04 server
i want to give ip address and let them reach to internet over dhcp server while using eth0 but my server using wlan0 to connect internet.

how can i configure them?

---

### Post by nerdtron on 2014-03-05
Post the contents of the server's /etc/network/interfaces file.

---

### Post by Iowan on 2014-03-05
A couple of questions:
Is the 12.04 machine supposed to be the DHCP server?
What are results of:
```
route -n
```

---

### Post by SeijiSensei on 2014-03-06
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

