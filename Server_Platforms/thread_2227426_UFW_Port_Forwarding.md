---
title: "UFW Port Forwarding"
date: 2014-06-01
forum: Server Platforms
---

### Post by raeif169 on 2014-06-01
Hi, I'm using an Ubuntu 12.04 server as a gateway/firewall and I need to set up port forwarding using UFW. I've read the many other articles and posts with instructions and I have gotten it to work once but cannot replicate it. I could really use some help figuring out why it won't work. I'm fairly new to linux and I have a feeling I missed a step somewhere. Here is my set up:

2 public IPs, each one has a Ubuntu Server 12.04 gateway/router. They are configured exactly the same way, same packages and same patch level. There are 2 network adapters, one with the public IP (eth0), one connected to the private LAN (eth1). For now, I'm just trying to forward tcp 80 and 443 to a web server on the LAN. From the router, I can reach the internet through the public interface and I can reach the webserver through the private interface. Here are the steps I've done so far:

1. Changed /etc/default/ufw and set **DEFAULT_FORWARD_POLICY="ACCEPT"**
2. Changed /etc/ufw/sysctl.conf and added [B]net.ipv4.ip_forward=1
[/B]3. Added the following to /etc/ufw/before.rules:
```
# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]


# Forward traffic through eth0
-A POSTROUTING -s <LAN subnet>/24 -o eth0 -j MASQUERADE


# My DNAT rules
-A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination <webserverIP>:80
-A PREROUTING -i eth0 -p tcp --dport 443 -j DNAT --to-destination <webserverIP>:443


# don't delete the 'COMMIT' line or these nat table rules won't
# be processed
COMMIT

```
4. Here are the UFW rules:
```
Status: active


To                         Action      From
--                         ------      ----
<RouterIP> 22               ALLOW       <ManagementPC>
<webserverIP> 80             ALLOW       <WANIP>
<webserverIP> 443            ALLOW       <WANIP>

```

I've been fighting this for several weeks now and could really use some help. I've got one server that runs perfectly and this one just doesn't even though it is configured exactly the same, just has a different hostname and different IPs. Thanks in advance.

-Raj

---

