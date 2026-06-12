---
title: "Is this normal?   Is this secure?"
date: 2024-08-15
forum: Security
---

### Post by skj22306 on 2024-08-15
From:
[URL="https://wiki.ubuntu.com/Security/Features"]
https://wiki.ubuntu.com/Security/Features[/URL]

> [B]Ubuntu Security No Open Ports

Default installations of Ubuntu must have no listening network services after initial install. Exceptions to this rule on desktop systems include network infrastructure services such as a DHCP client and mDNS (Avahi/ZeroConf, see ZeroConfPolicySpec for implementation details and justification). For Ubuntu in the cloud, exceptions include network infrastructure services for the cloud and OpenSSH running with client public key and port access configured by the cloud provider. When installing Ubuntu Server, the administrator can, of course, select specific services to install beyond the defaults (e.g. Apache).

Testing for this can be done with netstat -an --inet | grep LISTEN | grep -v 127.0.0.1: on a fresh install.[/B]

I get this result:
> tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN   


using sudo netstat -ltnpv 
i get this:
> Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1220/cupsd          
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      1070/systemd-resolv 
tcp        0      0 127.0.0.1:6463          0.0.0.0:*               LISTEN      17972/app.asar --no 
tcp6       0      0 ::1:631                 :::*                    LISTEN      1220/cupsd          
tcp6       0      0 :::9800                 :::*                    LISTEN      1381/fluidsynth  


Is this normal?

Is this secure?

---

### Post by currentshaft on 2024-08-15
2

---

### Post by skj22306 on 2024-08-16
Thanks!

---

