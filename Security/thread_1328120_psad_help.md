---
title: "psad help"
date: 2009-11-16
forum: Security
---

### Post by cybernet on 2009-11-16
```
root@xlist:/home/cybernet# psad -S
[+] psadwatchd (pid: 8338)  %CPU: 0.0  %MEM: 0.0
    Running since: Mon Nov 16 12:23:18 2009

[+] kmsgsd (pid: 8336)  %CPU: 0.0  %MEM: 0.0
    Running since: Mon Nov 16 12:23:18 2009

[+] psad (pid: 8334)  %CPU: 0.0  %MEM: 2.1
    Running since: Mon Nov 16 12:23:18 2009
    Command line arguments: -c /etc/psad/psad.conf
    Alert email address(es): xxx,xxx,xxx

[+] Version: psad v2.1

[+] Top 50 signature matches:
        [NONE]

[+] Top 25 attackers:
        [NONE]

[+] Top 20 scanned ports:
        [NONE]

[+] iptables log prefix counters:
        [NONE]

    Total packet counters: tcp: 0, udp: 0, icmp: 0

[+] IP Status Detail:
        [NONE]

    Total scan sources: 0
    Total scan destinations: 0

[+] These results are available in: /var/log/psad/status.out

```
but apache2 and my CPU Load says otherwise

**Too many connections**
I installed psad after this tutorial - [http://www.cyberciti.biz/faq/linux-detect-port-scan-attacks/](http://www.cyberciti.biz/faq/linux-detect-port-scan-attacks/)

but i still don't know what to do with ..
```
#!/bin/bash
IPT="/sbin/iptables"
 
echo "Starting IPv4 Wall..."
$IPT -F
$IPT -X
$IPT -t nat -F
$IPT -t nat -X
$IPT -t mangle -F
$IPT -t mangle -X
modprobe ip_conntrack
 
BADIPS=$(egrep -v -E "^#|^$" /root/scripts/blocked.fw)
PUB_IF="eth0"
[....]

```

i know that the upper code is an sh executable but where do i put it :o

---

### Post by cybernet on 2009-11-17
no one ???

---

