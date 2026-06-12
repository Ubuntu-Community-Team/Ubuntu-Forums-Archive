---
title: "Listening connections on my server"
date: 2020-11-18
forum: Security
---

### Post by sniper8752 on 2020-11-18
I did a netstat -tulpn, and got the following:
```
[FONT=monospace][COLOR=#000000]Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    [/COLOR]
[/FONT]udp        0      0 <my-public-ip>:68        0.0.0.0:*                           722/systemd-network 
udp        0      0 0.0.0.0:51820           0.0.0.0:*                           -  
```
Does port 68 really need to be listening on the outside interface?  And any ideas on the second line, what it is/doing?

EDIT: I am running Ubuntu Server 20

---

### Post by The Cog on 2020-11-18
Port 68 is bootpc - it is normal, and listens for DHCP responses.
Port 51820 appears to be the kernel listening rather than a process. The only time I have seen this is when wireguard is configured and listening. Do you have wireduard configured? If it's not that then I have no idea.

---

### Post by sniper8752 on 2020-11-18
Yup!  Thank you.

---

