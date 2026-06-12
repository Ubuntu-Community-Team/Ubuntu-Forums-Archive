---
title: "An unknown established connection to the Amazon/OpenShift server by gnome-software"
date: 2016-05-04
forum: Security
---

### Post by andrey-arapov on 2016-05-04
Hello,

does anyone have any idea about the following established connection to the Amazon/OpenShift server by gnome-software process?

```

root@carbon:~# netstat -tulpan
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
...
tcp        0      0 [redacted]:53044      54.173.79.111:443       ESTABLISHED 2709/gnome-software
...

```

Thanks anyone who has any idea why does the gnome-software establishes this connection!


This connection occurred when I boot my Ubuntu 16.04 LTS (64bit), logged into my account and run "netstat -tulpan".

The nmap port scan showed me the following towards this IP
```

Nmap scan report for ec2-54-173-79-111.compute-1.amazonaws.com (54.173.79.111)
Host is up (0.16s latency).
Not shown: 95 filtered ports
PORT     STATE SERVICE       VERSION
22/tcp   open  ssh           OpenSSH 5.3 (protocol 2.0)
80/tcp   open  http          Apache httpd 2.2.15
443/tcp  open  ssl/http      Apache httpd 2.2.15
8000/tcp open  http-alt
8443/tcp open  ssl/https-alt

```

---

### Post by Habitual on 2016-05-04
Yeah, and ?

Common Name "*.rhcloud.com
redhat cloud.
Digicert for *.rhcloud.com

gnome software may be checking for updates?

---

