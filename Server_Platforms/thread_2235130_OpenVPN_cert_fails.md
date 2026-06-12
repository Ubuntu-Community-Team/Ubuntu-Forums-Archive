---
title: "OpenVPN cert fails"
date: 2014-07-19
forum: Server Platforms
---

### Post by Mats_BRynolf on 2014-07-19
New installation of OpenVPN on Ubuntu 14.04 and i get this error in /var/log/syslog when i start OpenVPN
```

service openvpn start

```

```

Jul 19 09:43:00, server, 5, 3, ovpn-server[20510]:,  Options error: --dh fails with 'dh1024.pem': No such file or directory
Jul 19 09:43:00, server, 5, 3, ovpn-server[20510]:,  Options error: --cert fails with 'server': No such file or directory
Jul 19 09:43:00, server, 5, 3, ovpn-server[20510]:,  Options error: --key fails with 'server': No such file or directory
Jul 19 09:43:00, server, 3, 3, ovpn-server[20510]:,  Options error: Please correct these errors.

```

```

root@server:/etc/openvpn# ls -l
total 44
-rw-r--r-- 1 root root  5537 Jul 18 21:13 server.org.crt
-rw-r--r-- 1 root root  1078 Jul 18 21:13 server.org.csr
-rw-r--r-- 1 root root  1708 Jul 18 21:13 server.org.key
-rw-r--r-- 1 root root  1659 Jul 18 21:13 ca.crt
-rw-r--r-- 1 root root   424 Jul 18 21:13 dh2048.pem
drwxr-xr-x 3 root root  4096 Jul 18 21:07 easy-rsa
-rw-r--r-- 1 root root 10339 Jul 18 21:25 server.conf
-rwxr-xr-x 1 root root  1301 Feb  4 15:37 update-resolv-conf

```

I've done the installation according to [https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html)

---

### Post by Mats_BRynolf on 2014-07-19
dh1024.pem had to be renamed in server.conf to dh2048.pem

Problem solved

---

