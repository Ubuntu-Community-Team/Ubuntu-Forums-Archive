---
title: "Connect to VPN client through VPN server."
date: 2014-11-13
forum: Server Platforms
---

### Post by Seunghyuk Choi on 2014-11-13
Hi, I will move another place where I can use shared internet. So, I will have none or limited control for top router.

Currently, I have a machine that runs ubuntu 12.04 LTS server. I am running rutorrent client and pydio on it.

I don't think that I can forward ports to my server after moving out. 

Therefore, I want to know some alternative method that allows me to connect to my server from outside.


 If I rent a dedicated server and install openvpn server on it. Then, I connect openvpn from my home server. If I do this, is there any way to forward to my home server whenever I tried to connect to a dedicated server?

 Or, is there any way to get it working without ordering an individual line?

---

### Post by nerdtron on 2014-11-13
> I don't think that I can forward ports to my server after moving out. 

Therefore, I want to know some alternative method that allows me to connect to my server from outside.


 If I rent a dedicated server and install openvpn server on it. Then, I  connect openvpn from my home server. If I do this, is there any way to  forward to my home server whenever I tried to connect to a dedicated  server?
Seems logical. Since you can't port forward from the router.
If your home server is connected to the external VPN server, then from another computer you try to connect to the VPN, you can configure the VPN server to forward you to the home server.
I'm no expert on port forwarding but what ports do you need to forward?

---

### Post by sandyd on 2014-11-13
> **Seunghyuk Choi said:**
> Hi, I will move another place where I can use shared internet. So, I will have none or limited control for top router.

Currently, I have a machine that runs ubuntu 12.04 LTS server. I am running rutorrent client and pydio on it.

I don't think that I can forward ports to my server after moving out. 

Therefore, I want to know some alternative method that allows me to connect to my server from outside.


 If I rent a dedicated server and install openvpn server on it. Then, I connect openvpn from my home server. If I do this, is there any way to forward to my home server whenever I tried to connect to a dedicated server?

 Or, is there any way to get it working without ordering an individual line?

If you have a few spare ips on the server, you can do gre tunneling.

See [http://wiki.buyvm.net/doku.php/gre_tunnel](http://wiki.buyvm.net/doku.php/gre_tunnel) for an example.

Otherwise, you can just do DNAT to forward ports from the server to your computer.

---

