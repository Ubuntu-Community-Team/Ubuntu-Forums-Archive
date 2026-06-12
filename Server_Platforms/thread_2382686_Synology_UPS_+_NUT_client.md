---
title: "Synology UPS + NUT client"
date: 2018-01-16
forum: Server Platforms
---

### Post by BigYellowDog on 2018-01-16
I want to configure my ubuntu server as  NUT client with my Synology NAS with UPS.  I enabled USP server on the Synology NAS and added the IP address of my ubuntu server in the list of permitted devices.
I picked up the username and password from Synology and added it to ```
/etc/nut/upsmon.conf
```
```

MONITOR ups@192.168.1.10:3493 1 username password slave

```
I set MODE to ```
netserver 
```in```
 /etc/nut/nut.conf
```  When I start nut-client I am getting an error
```

Jan 16 10:17:39 ubuntu upsmon[15926]: Login on UPS [ups@192.168.1.10:3493] failed - got [ERR ACCESS-DENIED]

```
I can telnet to port 3493 OK so I don't think that is my problem.  Any suggestions? TIA :)

---

### Post by slickymaster on 2018-01-16
*Thread moved to **Server Platforms**.*

---

