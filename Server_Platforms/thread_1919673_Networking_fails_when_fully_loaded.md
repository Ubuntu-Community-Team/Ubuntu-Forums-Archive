---
title: "Networking fails when fully loaded"
date: 2012-02-03
forum: Server Platforms
---

### Post by kalosh on 2012-02-03
Hi.
I have following network config in my house:
```

ISP (static, public IP)
     |
   eth0
ubuntu desktop (dns, dhcp and dlna server, NAT)
   eth1
    |
  lan1
wireless router used as access point (no NATing)
       lan2         wireless         wireless
      LG TV         xp desktop      win7 laptop

```Now, when I am watching something (1080p) on TV using DLNA, or coping big amount of data from laptop to server something fails. Even if I stop to stuffing my network by data the problem is not being fixed. After the failure is occurred I have connection between devices in my network and server but no connection outside the world. I can ping the ISP gateway but nothing more in the world even using IP (destination unreachable) and DNS name (host unreachable). When I restart the server everything is working fine again.
Do you know what can be the problem or how to find it? If you need any logs just tell me how to retrieve it and I will provide it.
Best regards, Dawid.

---

### Post by kalosh on 2012-02-05
So if none experienced the similar problem before how could you tell me please how to start to look the where is the problem?

---

