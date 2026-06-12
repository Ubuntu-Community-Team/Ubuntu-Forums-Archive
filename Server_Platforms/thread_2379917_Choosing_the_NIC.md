---
title: "Choosing the NIC"
date: 2017-12-11
forum: Server Platforms
---

### Post by steve keating on 2017-12-11
Hello

I have loaded Ubuntu 16.04 on a server with two on board NICs. The first NIC has the public IP so I can RDP to the server. The second NIC has a private IP, so I can access the other equipment on the network. When I open the browser I can access the internet. But if I try to go to the private network, the browser will only take me to the public IP. Is there a way to get the browser to go to the private IP network? I have tried configuring with the private IP on the first NIC, and the public on the second, but that will not allow me to access the server.

Thanks.

Stephen Keating

---

### Post by howefield on 2017-12-11
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2017-12-11
I don't understand. Which browser are you talking about, web browser?

Routing traffic to public or private networks does not depend on the browser at all. Can you also post the output of:
```
cat /etc/network/interfaces
```

and also give us the IP of the resources you are trying to access on the private LAN?

---

### Post by SeijiSensei on 2017-12-11
Can you browse sites on the local network via IP address, like [http://192.168.1.1/](http://192.168.1.1/) ?

---

