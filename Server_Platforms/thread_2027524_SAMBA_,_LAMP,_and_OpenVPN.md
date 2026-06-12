---
title: "SAMBA , LAMP, and OpenVPN"
date: 2012-07-16
forum: Server Platforms
---

### Post by blakdeth77 on 2012-07-16
Hi All, Wondering if the title of this post is possible?
I have an Ubuntu 12.04 server, 4GB ram, quad core amd CPU, GB Eth, software RAID1 set up, have installed and configured SAMBA shares, installed and configured the LAMP with SugarCE on it, now I want to access those services remotely over VPN. I've looked at tutorials for the basic Routed setup and the Bridged setup too... but I don't know which one is right for this application. 

I assumed the routed config would work... but I could remotely connect over the VPN but could not access the web page on the server, or connect to the samba shares.

The example info I have below
Office LAN: 192.168.0.0/24
VPN (tun0) 10.8.0.0/24 
Remote LAN 192.168.1.0/24

/etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.11
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 208.67.222.222

```/etc/openvpn/server.conf
```

port 1194
proto udp
dev tun
ca ca.crt
cert ubuntu.crt
key ubuntu.key
dh dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.0.0 255.255.255.0"
push "dhcp-option DNS 208.67.222.222"
keepalive 10 120
comp-lzo
max-clients 10
user-nobody
group-nobody
persist-key
persist-tun
status openvpn-status.log
verb 3

```(any line not shown above is commented out.)

The client I was testing with is a Win7 box. I used the OpenVPN gui client and installed the OVPN client file like this:
```

client
dev tun
proto udp
remote (servername removed) 1194
resolv-retry infinite
nobind
persist-key
ca ca.crt
cert user1.crt
key user1.key
ns-cert-type server
comp-lzo
verb 3

```That's what I've got. The Samba and LAMP services work from the 192.168.0.0/24 subnet but as soon as I try over the VPN it says the site's not found and the hostname for the samba share is not found either. 

I thought about it and probably don't want to redirect ALL web traffic through the VPN, so I think I can set up an additional port for apache2 to listen on... but not sure because of the LAMP config. Can anyone help with this?

Thanks in advance. :-)

---

### Post by blakdeth77 on 2012-07-16
Also yes I have edited /etc/sysctl.conf
to show:
```

net.ipv4.ip_forward=1

```

---

### Post by blakdeth77 on 2012-07-16
Also in a possibly related issue... I can't get the SugarCRM to connect to the mysqld because it's not running. When I try to start it via "mysqld" at the cli I get 
```

120716 17:51:12 [Note] Plugin 'FEDERATED' is disabled.
120716 17:51:12 InnoDB: The InnoDB memory heap is disabled
120716 17:51:12 InnoDB: Mutexes and rw_locks use GCC atomic builtins
120716 17:51:12 InnoDB: Compressed tables use zlib 1.2.3.4
mysqld: Can't create/write to file '/tmp/ibiDV2Jf' (Errcode: 2)
120716 17:51:12  InnoDB: Error: unable to create temporary file; errno: 2
120716 17:51:12 [ERROR] Plugin 'InnoDB' init function returned error.
120716 17:51:12 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
120716 17:51:12 [ERROR] Unknown/unsupported storage engine: InnoDB
120716 17:51:12 [ERROR] Aborting

120716 17:51:12 [Note] mysqld: Shutdown complete


```

Any thoughts? I actually reinstalled after getting this error last time, and now it's happened again, leading me to believe it's got to do with an update? The website works fine for a while then mysteriously can't connect to the DB. 

This is getting to be enough time spent for me to just scrap the whole idea and go get a license for Windows. :-(

---

