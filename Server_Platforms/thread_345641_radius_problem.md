---
title: "radius problem"
date: 2007-01-24
forum: Server Platforms
---

### Post by dr.lnx on 2007-01-24
hi, i have a problema with radius, 
i have install the server freeradius, if i try to autenticat a userlocally, it works
```

root@radius:~# radtest root sandro 127.0.0.1 1812 secret
Sending Access-Request of id 11 to 127.0.0.1 port 1812
        User-Name = "rix"
        User-Password = "*****"
        NAS-IP-Address = 255.255.255.255
        NAS-Port = 1812
rad_recv: Access-Accept packet from host 127.0.0.1:1812, id=11, length=20

```

but if i try to autenticat my pc througth an access point it dosn't work saing
```

rad_recv: Access-Request packet from host 192.168.1.250:1035, id=1, length=189
Sending Access-Reject of id 1 to 192.168.1.250 port 1035
        EAP-Message = 0x04010004
        Message-Authenticator = 0x00000000000000000000000000000000

```
how can i make this server work???

tanks

---

