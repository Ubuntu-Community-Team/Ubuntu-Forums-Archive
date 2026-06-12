---
title: "bridging on lucid with openvpn server"
date: 2010-12-22
forum: Server Platforms
---

### Post by chr1sM on 2010-12-22
Hi,

I have not setup openvpn server on ubuntu before but I have done it many times on CentOS. The procedure is slightly different and I am a bit confused about bridging.

The non-bridging settings I use are 

server 10.11.0.0 255.255.0.0
push "route 10.10.2.0 255.255.255.0"
push "route 10.10.0.0 255.255.0.0"

How does this translate in a bridging setting with a local address (br0) of 10.10.1.1? I have included the lines I think I need to change

;local 172.18.100.101
;server-bridge 172.18.100.101 255.255.255.0 172.18.100.105 172.18.100.200
;push "route 172.18.100.1 255.255.255.0"

Many thanks,

Chris

---

