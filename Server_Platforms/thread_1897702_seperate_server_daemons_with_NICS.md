---
title: "seperate server daemons with NICS"
date: 2011-12-19
forum: Server Platforms
---

### Post by dbecker on 2011-12-19
have ubuntu server 10.04 installed. The box is used as VPN (openVPN) and web server (apache2). 

Here's the current network config. 

```
internet
|
router (192.168.1.1)
|
ubuntu server (192.168.1.2)
workstations (dhcp 192.168.1.3/55)
```

After reading about DMZ and various security issues with web servers, would it be possible to install another NIC in the ubuntu server and seperate the web/vpn traffic?

It might look like this:

```

internet
 |
 router (192.168.1.1)
 |---------ubuntu server - apache2 listening on (192.168.0.1) in DMZ
 workstations (dhcp 192.168.1.3/55)
ubuntu server - other daemons including VPN (192.168.1.2)
```

does this make sense, or is it rubbish, i.e. putting web server on seperate NIC, outside the LAN subnet, in DMZ?

---

