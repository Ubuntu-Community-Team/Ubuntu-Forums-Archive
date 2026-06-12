---
title: "Problem with bridge-utils"
date: 2010-08-11
forum: Server Platforms
---

### Post by ramelof on 2010-08-11
Hi,

I have a VPS server. Server use a openVZ technology.

I install a openvpn and configured with this tutorial [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)  without bridge.

The connection was establish, but not sharing a internet connection

Later i instal a bridge-utils and my problem was started.

When i edited a network / interfaces file and add info about br0 and restart network i have error.
> * Reconfiguring network interfaces... 
add bridge failed: Package not installed
run-parts: /etc/network/if-pre-up.d/bridge exited with return code 1
SIOCSIFADDR: No such device
br0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
br0: ERROR while getting interface flags: No such device
Failed to bring up br0.

How is wrong? What name of missing package? I must some extra package install?

Tun/Tap was enabled by VPS provider.

Bridge-utils must by enabled by VPS provider?
How do that?

---

### Post by bodhi.zazen on 2010-08-11
Sounds as if your configuration is a bit complex.

Are you trying to configure the guest (VPS) or the host ?

I do not think you can install a bridge in the guest (VPS), but I have never tried.

Can you tell me what you are trying to accomplish exactly and if you are working with the host or guest ?

I would also help if you were to post your configuration file.

---

### Post by ramelof on 2010-08-22
Well. I created a VPN once more but a use diffrent settings.
My config file look like
```

port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway"
push "dhcp-option DNS 10.8.0.1"
;push "dhcp-option WINS 10.8.0.1"
;duplicate-cn
keepalive 10 120
comp-lzo
persist-key
persist-tun
status openvpn-status.log
log         openvpn.log
log-append  openvpn.log
verb 3
#eof

```

and config file is
```
client 
proto udp 
remote XXX.XXX.XXX.XXX 1194 
dev tun 
nobind 
tun-mtu 1500 
tls-client 
ca "c:\\Program Files (x86)\\OpenVPN\\config\\ca.crt" 
cert "c:\\Program Files (x86)\\OpenVPN\\config\\client.crt" 
key "c:\\Program Files (x86)\\OpenVPN\\config\\client.key" 
ping-restart 60 
ping-timer-rem 
persist-tun 
persist-key 
resolv-retry 86400 
ping 10 
comp-lzo 
verb 4
; eof 
```

Tutorial who i use in end of part say write this
```
echo "1" >/proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```
to sharing connection

but on my VPS i don`t have ip_forward (file/folder?)
and when i write second line i have this error
```
/etc/openvpn/# iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o venet0 -j MASQUERADE
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/.
FATAL: Could not load /lib/modules/2.6.18-194.8.1.el5.028stab070.2PAE/modules.dep: No such file or directory
iptables v1.4.4: can't initialize iptables table `nat': Table does not exist (do you need to insmod?)
Perhaps iptables or your kernel needs to be upgraded.

```

Well i have a problem because i dont add modules to kernel. Only vps provider can change sam settings.


~Edit
Policy of forward iptaples is accept, but i don`t have inetnet connection. Only to server.

---

