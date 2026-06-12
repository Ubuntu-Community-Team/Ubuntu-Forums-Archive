---
title: "Clients can't access other subnets connected to a bridged OpenVPN"
date: 2015-07-14
forum: Server Platforms
---

### Post by Luke_Higgs on 2015-07-14
I am running Ubuntu server 14.04 and have configured an OpenVPN server running in a bridged configuration. My clients can connect and obtain the public IP address of the VPN server, can browse the internet etc. I can SSH into the OpenVPN server from the client (that is the only device on the same subnet as clients), however I cannot access other subnets from the client. From the server I can ping devices on other subnets and I've confirmed that the firewall between the other subnets is not blocking traffic from the client assigned IP. Since I can see data from the client I suspect that the problem is there is no route back to the client.

Output from my syslog:

```
Jul 14 09:31:14 VPN001 ovpn-server[2647]: 1.2.3.4:49153 [laptop01] Peer Connection Initiated with [AF_INET]1.2.3.4:49153Jul 14 09:31:14 VPN001 ovpn-server[2647]: MULTI: new connection by client 'laptop01' will cause previous active sessions by this client to be dropped.  Remember to use the --duplicate-cn option if you want multiple clients using the same certificate or username to concurrently connect.
Jul 14 09:31:14 VPN001 ovpn-server[2647]: MULTI_sva: pool returned IPv4=192.168.3.50, IPv6=(Not enabled)
Jul 14 09:31:16 VPN001 ovpn-server[2647]: laptop01/1.2.3.4:49153 PUSH: Received control message: 'PUSH_REQUEST'
Jul 14 09:31:16 VPN001 ovpn-server[2647]: laptop01/1.2.3.4:49153 send_push_reply(): safe_cap=940
Jul 14 09:31:16 VPN001 ovpn-server[2647]: laptop01/1.2.3.4:49153 SENT CONTROL [laptop01]: 'PUSH_REPLY,route 192.168.3.254 255.255.255.0,route 192.168.2.254 255.255.255.0,redirect-gateway def1 bypass-dhcp,dhcp-option DNS 8.8.8.8,dhcp-option DNS 8.8.4.4,route-gateway 192.168.3.253,ping 10,ping-restart 120,ifconfig 192.168.3.50 255.255.255.0' (status=1)
Jul 14 09:31:17 VPN001 ovpn-server[2647]: laptop01/1.2.3.4:49153 MULTI: Learn: 00:ff:c9:73:7e:9a -> laptop01/1.2.3.4:49153
Jul 14 09:32:49 VPN001 ovpn-server[2647]: laptop01/1.2.3.4:49153 PID_ERR replay-window backtrack occurred [2] [SSL-0] [00_0036>>>>EEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEE] 0:517 0:515 t=1436880769[0] r=[-3,64,15,2,1] sl=[59,64,64,528]
```

UFW status:
```
root@VPN001:~# ufw status verboseStatus: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), allow (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
22                         ALLOW IN    Anywhere
1194/tcp                   ALLOW IN    Anywhere
1194/udp                   ALLOW IN    Anywhere
22 (v6)                    ALLOW IN    Anywhere (v6)
1194/tcp (v6)              ALLOW IN    Anywhere (v6)
1194/udp (v6)              ALLOW IN    Anywhere (v6)



```

OpenVPN server.conf:

```
;local a.b.c.d

port 1194


# TCP or UDP server?
;proto tcp
proto udp


;dev-node MyTap


ca ca.crt
cert VPN001.crt
key VPN001.key  # This file should be kept secret


dh dh2048.pem


;server 10.8.0.0 255.255.255.0


ifconfig-pool-persist ipp.txt


server-bridge 192.168.3.253 255.255.255.0 192.168.3.50 192.168.3.100


;server-bridge


push "route 192.168.3.254 255.255.255.0"
push "route 192.168.2.254 255.255.255.0"
;push "route 192.168.1.254 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"


;client-config-dir ccd
;route 192.168.40.128 255.255.255.248


;client-config-dir ccd
;route 10.9.0.0 255.255.255.252


;learn-address ./script


push "redirect-gateway def1 bypass-dhcp"


push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"


client-to-client


;duplicate-cn


keepalive 10 120


;tls-auth ta.key 0 # This file is secret


;cipher BF-CBC        # Blowfish (default)
;cipher AES-128-CBC   # AES
;cipher DES-EDE3-CBC  # Triple-DES


comp-lzo


;max-clients 100


user nobody
group nogroup


persist-key
persist-tun


status openvpn-status.log


;log         openvpn.log
;log-append  openvpn.log


verb 5


;mute 20
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
script-security 3
```

The subnet I'm trying to get to is the 192.168.2.0/24 subnet. I'm not sure where I need to put the route back for clients if that's the issue here. Thank you for any help!

Luke

---

### Post by Luke_Higgs on 2015-07-14
I feel silly now...The problem was not with the open vpn configuration or firewall configuration, my server firewall rules on the 192.168.2.0 network were not configured to accept traffic from the VPN network. I believe the above configuration is correct and working properly for a VPN.

---

