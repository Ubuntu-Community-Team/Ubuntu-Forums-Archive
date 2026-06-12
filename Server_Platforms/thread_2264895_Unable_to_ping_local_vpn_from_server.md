---
title: "Unable to ping local vpn from server"
date: 2015-02-11
forum: Server Platforms
---

### Post by manoj_kumar3 on 2015-02-11
Hi,

I'm using Open VPN to connect my server. I'm able to connect my Open Vpn, through that I can connect my server but when i tried to access resources of that server i am unable to access them. 

I have installed "ambari server" on server adn i have started. when I tried to access "ambari-server" in my local system browser (using "IP address : Port ") I can't connect to it. Also, I found that i'm not able to ping even the VPN Ip from server.

Anyone there to help me in resolving this issue??

Thanks in advance.

---

### Post by darkod on 2015-02-11
You are probably missing a route so that computers on your local lan know where to route traffic destined for the server.

Does the server have both public and private interface (ip address) or only public?

---

