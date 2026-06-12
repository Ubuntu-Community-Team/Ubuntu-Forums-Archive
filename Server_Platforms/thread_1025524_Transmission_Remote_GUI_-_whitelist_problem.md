---
title: "Transmission Remote GUI - whitelist problem"
date: 2008-12-30
forum: Server Platforms
---

### Post by Jeztastic on 2008-12-30
Hi

**1.** I am getting a whitelist error message when I try to connect to my server. I have added my ip, and tried disabling the whitelist to no avail.

**2. **My settings.json file is in home/jez/.config/transmission-daemon There were some conflicting accounts of where to put it... Is that the right place?

       ```
 "blocklist-enabled": 0,
        "download-dir": "\/home\/jez",
        "download-limit": 600,
        "download-limit-enabled": 0,
        "encryption": 1,
        "max-peers-global": 200,
        "peer-port": 16868,
        "pex-enabled": 1,
        "port-forwarding-enabled": 0,
        "rpc-authentication-required": 0,
        "rpc-password": "",
        "rpc-port": 9091,
        "rpc-username": "jez",
        "rpc-whitelist": "127.0.0.1,192.168.*.*,192.168.1.65,192.168.1.73"
        "rpc-whitelist-enabled": 0
        "upload-limit": 5,
        "upload-limit-enabled": 0
```

I edited settings.json while the daemon was stopped. Please help, this is driving me barmy!

---

### Post by bsilver6 on 2009-02-09
Hi,
Been troubleshooting a similar problem myself and just found the solution - allowing port 9091 in the firewalls of both server and client(s).
Using ufw this is easy:
```
sudo ufw allow 9091
```
Hope this fixes your problem too.

---

### Post by Jeztastic on 2009-02-09
Thanks! I already found out it was me being dense - I left out a comma in the script. Doh! 

This should help someone else though...

---

