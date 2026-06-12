---
title: "Set up VPN on Lucid Server"
date: 2011-03-29
forum: Server Platforms
---

### Post by corkscrew on 2011-03-29
I'm a newbie to working with  server.
System
Ubuntu Lucid Server (10.04.1)
Kernel Linux 2.6.32-30-server

NoMachine NX set up
Webmin 1.53

Netgear DGN2000 ADSL Router

Mixed LAN behind router including the Server , a NAS, IP Camera, win 7 box and 2 linux Ubuntu Lucid Lynx boxes one wired one wirless.

I work in remote locations & have to go through various company networks. I have access to the internet. 
I have been able to access my server using NoMachine NX through ssh tunnel by following various how to's on the net.

However some places I work I cannot use ssh.

I would like to set up a VPN on my server machine so I can access my LAN and if possible use NOMachine NX over the connection.

I started out by following this how to set up vpn using webmin [http://www.frontiernet.net/~beakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html]("http://www.frontiernet.net/~beakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html")

Ran into a problem in the firewall section where you have to set up incoming interface to “tun0”
I have never heard of tun before and started research on the net apparently TUN/TAP is in the kernel.

If I enter ```
grep CONFIG_TUN= /boot/config
``` I get ```
No such file or directory
```
I think again from searching the net maybe need to install the bridge-utils package?

Can anyone help?

---

### Post by spynappels on 2011-03-29
The tun0 interface is there automatically when OpenVPN server (in routed mode) is running, it is a virtual network port which can be firewalled etc.
If the server you are running OpenVPN server on is behind a residential firewall, often built into routers, and only port 1194 UDP (or whatever you choose to use) is forwarded to it, you can forget the firewall section of the tutorial, but the ipv4_forward edit in sysctl is very important.

It is also important to have your home subnet very different from any subnets from which you may want to connect. Using 192.168.1.x as your home subnet will almost guarantee you problems, as this subnet is default on many SOHO routers and you will get routing conflicts. Better to have your home LAN subnet set to something like 192.168.68.x or something equally less likely to be in use elsewhere.

---

### Post by corkscrew on 2011-03-29
ok my subnet is already comprised of 198.168.xx.xx so should be ok.
I followed rest of tutorial skipping the firewall section.
When I get to the part start your VPN Server I get the following message
> Command Execution Error /etc/init.d/openvpn start Arbirlot-VPN-Server.

I dont know if this is anything to do with it not starting but one setting in the VPN set up I didn't understand was 
> Net IP assigns (option server) 10.8.0.0 255.255.255.0 I have no idea where that address comes from

---

### Post by spynappels on 2011-03-29
> **corkscrew said:**
> ok my subnet is already comprised of 198.168.xx.xx so should be ok.


That is not necessarily the case, it is the third set of numbers which is important. If your home LAN and the remote LAN from which you are connecting have the same number in this third segment, then you will have problems, which is why I suggested a relatively unused number for the third segment.


For the error message when you start OpenVPN, it is not very descriptive.
If you go to the OpenVPN directory (/etc/openvpn?) and enter the following command, you will actually get a verbose ouput as it is trying to start. Copying this to a post here would help to see where it is going wrong:
```
sudo openvpn --config 'name of config file here'
```

Also, the 10.8.0.0 is the network address of the ip subnet used by the VPN, so your server will normally be 10.8.0.1 on tun0, and clients will get IPs of 10.8.0.5, 10.8.0.9 etc on their VPN interfaces.

---

### Post by corkscrew on 2011-03-30
> **spynappels said:**
> That is not necessarily the case, it is the third set of numbers which is important. If your home LAN and the remote LAN from which you are connecting have the same number in this third segment, then you will have problems, which is why I suggested a relatively unused number for the third segment.


For the error message when you start OpenVPN, it is not very descriptive.
If you go to the OpenVPN directory (/etc/openvpn?) and enter the following command, you will actually get a verbose ouput as it is trying to start. Copying this to a post here would help to see where it is going wrong:
```
sudo openvpn --config 'name of config file here'
```

Also, the 10.8.0.0 is the network address of the ip subnet used by the VPN, so your server will normally be 10.8.0.1 on tun0, and clients will get IPs of 10.8.0.5, 10.8.0.9 etc on their VPN interfaces.

Sorry I misunderstood you the third segment of my LAN is 25 is that ok?


I ran the following commands
```
cd /etc/openvpn
```
```
sudo openvpn --config Arbirlot-VPN-Server

Options error: In [CMD-LINE]:1: Error opening configuration file: Arbirlot-VPN-Server
Use --help for more information.
```
 Dont know if this helps here is directory listing of openvnc
 ```
ls
Arbirlot-VPN-Server.conf
clients
keys
openvpn-ssl.cnf
servers
update-resolv-conf
```

---

### Post by CraigGibbon on 2011-03-30
> **corkscrew said:**
> I'm a newbie to working with  server.
System
Ubuntu Lucid Server (10.04.1)
Kernel Linux 2.6.32-30-server

NoMachine NX set up
Webmin 1.53

Netgear DGN2000 ADSL Router

Mixed LAN behind router including the Server , a NAS, IP Camera, win 7 box and 2 linux Ubuntu Lucid Lynx boxes one wired one wirless.

I work in remote locations & have to go through various company networks. I have access to the internet. 
I have been able to access my server using NoMachine NX through ssh tunnel by following various how to's on the net.

However some places I work I cannot use ssh.

I would like to set up a VPN on my server machine so I can access my LAN and if possible use NOMachine NX over the connection.

I started out by following this how to set up vpn using webmin [http://www.frontiernet.net/~beakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html]("http://www.frontiernet.net/%7Ebeakmyn/vpn%20howto/Complete%20Home%20VPN%20Howto%20Guide.html")

Ran into a problem in the firewall section where you have to set up incoming interface to “tun0”
I have never heard of tun before and started research on the net apparently TUN/TAP is in the kernel.

If I enter ```
grep CONFIG_TUN= /boot/config
``` I get ```
No such file or directory
```I think again from searching the net maybe need to install the bridge-utils package?

Can anyone help?


 Please refer ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html

---

### Post by spynappels on 2011-03-30
try the following:

```
sudo openvpn --config Arbirlot-VPN-Server.conf
```

the .conf is important from memory.

If this does not work, can you post your conf file (suitably anonymised of course) so we can look at it and see why OpenVPN cannot open it.

And using the 192.168.25.0 network should be fine, anything other than 192.168.0.0 or 192.168.1.0 networks should be less likely to cause hassle.

Dont worry, that fact that OpenVPN is starting is a good sign, it generally means we just have to tweak your conf file.

---

### Post by corkscrew on 2011-03-30
> **spynappels said:**
> try the following:

```
sudo openvpn --config Arbirlot-VPN-Server.conf
```

the .conf is important from memory.

If this does not work, can you post your conf file (suitably anonymised of course) so we can look at it and see why OpenVPN cannot open it.

And using the 192.168.25.0 network should be fine, anything other than 192.168.0.0 or 192.168.1.0 networks should be less likely to cause hassle.

Dont worry, that fact that OpenVPN is starting is a good sign, it generally means we just have to tweak your conf file.

ok same result 
```
> sudo openvpn --config Arbirlot-VPN-Server.conf
Options error: In [CMD-LINE]:1: Error opening configuration file: Arbirlot-VPN-Server.conf

Here's the conf file
[CODE]port 1194
proto udp
dev tun0
ca keys/arbirlot/ca.crt
cert keys/arbirlot/serverkey.crt
key keys/arbirlot/serverkey.key
dh keys/arbirlot/dh2048.pem
server 10.8.0.0 255.255.255.0
crl-verify keys/arbirlot/crl.pem
ifconfig-pool-persist servers/Arbirlot-VPN-Server/logs/ipp.txt
tls-auth servers/Arbirlot-VPN-Server/ta.key 0
cipher DES-CFB
user nobody
group nogroup
status servers/Arbirlot-VPN-Server/logs/openvpn-status.log
log-append servers/Arbirlot-VPN-Server/logs/openvpn.log
verb 2
mute 20
max-clients 3
keepalive 10 120
client-config-dir /etc/openvpn/servers/Arbirlot-VPN-Server/ccd
tls-server
comp-lzo
persist-key
persist-tun
ccd-exclusive
push "route 198.168.**.** 255.255.255.0
push "redirect-gateway"
```

not sure what I was supposed to anonymise.... so just starred out the ip of my server

---

### Post by spynappels on 2011-03-30
Ok, its been a long day, so the only thing I can think of just now is to remove the 0 from dev tun0 so it only says dev tun and to use absolute paths for the certs and keys, e.g. /etc/openvpn/easyrsa/keys/arbirlot/ca.crt etc.
Try that and see.

I will have another look tomorrow when I've had a chance to catch some shuteye.

---

### Post by corkscrew on 2011-03-31
> **spynappels said:**
> Ok, its been a long day, so the only thing I can think of just now is to remove the 0 from dev tun0 so it only says dev tun and to use absolute paths for the certs and keys, e.g. /etc/openvpn/easyrsa/keys/arbirlot/ca.crt etc.
Try that and see.

I will have another look tomorrow when I've had a chance to catch some shuteye.

ok changed config as per your instructions same result I'm afraid
```
port 1194
proto udp
dev tun
ca etc/openvpn/keys/arbirlot/ca.crt
cert etc/openvpn/keys/arbirlot/serverkey.crt
key etc/openvpn/keys/arbirlot/serverkey.key
dh etc/openvpn/keys/arbirlot/dh2048.pem
server 10.8.0.0 255.255.255.0
crl-verify etc/openvpn/keys/arbirlot/crl.pem
ifconfig-pool-persist servers/Arbirlot-VPN-Server/logs/ipp.txt
tls-auth etc/openvpn/servers/Arbirlot-VPN-Server/ta.key 0
cipher DES-CFB
user nobody
group nogroup
status servers/Arbirlot-VPN-Server/logs/openvpn-status.log
log-append etc/openvpn/servers/Arbirlot-VPN-Server/logs/openvpn.log
verb 2
mute 20
max-clients 3
keepalive 10 120
client-config-dir /etc/openvpn/servers/Arbirlot-VPN-Server/ccd
tls-server
comp-lzo
persist-key
persist-tun
ccd-exclusive
push "route 198.168.**.** 255.255.255.0
push "redirect-gateway"
```

A few stabs in the dark here...
there are to NIC's in the box the active 1 is eth1 (m/board card) non active eth0 (pci card) don't suppose that has anything to do with it?

Also I have ssh server set up and running for NXNoMachine

Do I not need to install bridge-utils package?

Many thanks for the effort you are putting in here

---

### Post by corkscrew on 2011-03-31
> **spynappels said:**
> Ok, its been a long day, so the only thing I can think of just now is to remove the 0 from dev tun0 so it only says dev tun and to use absolute paths for the certs and keys, e.g. /etc/openvpn/easyrsa/keys/arbirlot/ca.crt etc.
Try that and see.

I will have another look tomorrow when I've had a chance to catch some shuteye.

OK ignore my last post success!!!! I think...
When I was looking at directory structure to change paths to absolute as per your suggestion I came across this log file in the /etc/openvpn/servers/
found an error message
```
Options error: No closing quotation (") in /etc/openvpn/Arbirlot-VPN-Server.conf:27
Use --help for more information.
```

Added the closing quotation and now when I click the red start link in the VPN server list the screen refreshes and and link changes to blue stop.
So I guess the that means the server is now running.

One thing though when I go back to same log file to have a look now there are several WARNINGS listed I wondor if there is something else I need to fix?

```
Thu Mar 31 08:06:36 2011 Linux ip addr del failed: external program exited with error status: 255
Thu Mar 31 08:06:37 2011 SIGTERM[hard,] received, process exiting
Thu Mar 31 09:45:06 2011 OpenVPN 2.1.0 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Thu Mar 31 09:45:06 2011 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Thu Mar 31 09:45:06 2011 WARNING: file 'keys/arbirlot/serverkey.key' is group or others accessible
Thu Mar 31 09:45:06 2011 /usr/bin/openssl-vulnkey -q -b 2048 -m <modulus omitted>
Thu Mar 31 09:45:06 2011 WARNING: file 'servers/Arbirlot-VPN-Server/ta.key' is group or others accessible
Thu Mar 31 09:45:06 2011 Control Channel Authentication: using 'servers/Arbirlot-VPN-Server/ta.key' as a OpenVPN static key file
Thu Mar 31 09:45:06 2011 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Mar 31 09:45:06 2011 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Thu Mar 31 09:45:06 2011 TLS-Auth MTU parms [ L:1539 D:166 EF:66 EB:0 ET:0 EL:0 ]
Thu Mar 31 09:45:06 2011 TUN/TAP device tun0 opened
Thu Mar 31 09:45:06 2011 /sbin/ifconfig tun0 10.8.0.1 pointopoint 10.8.0.2 mtu 1500
Thu Mar 31 09:45:06 2011 Data Channel MTU parms [ L:1539 D:1450 EF:39 EB:135 ET:0 EL:0 AF:3/1 ]
Thu Mar 31 09:45:06 2011 GID set to nogroup
Thu Mar 31 09:45:06 2011 UID set to nobody
Thu Mar 31 09:45:06 2011 UDPv4 link local (bound): [undef]
Thu Mar 31 09:45:06 2011 UDPv4 link remote: [undef]
Thu Mar 31 09:45:06 2011 Initialization Sequence Completed
Thu Mar 31 09:47:33 2011 event_wait : Interrupted system call (code=4)
Thu Mar 31 09:47:33 2011 TCP/UDP: Closing socket
SIOCDELRT: Operation not permitted
Thu Mar 31 09:47:33 2011 ERROR: Linux route delete command failed: external program exited with error status: 7
Thu Mar 31 09:47:33 2011 Closing TUN/TAP interface
Thu Mar 31 09:47:33 2011 /sbin/ifconfig tun0 0.0.0.0
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
Thu Mar 31 09:47:33 2011 Linux ip addr del failed: external program exited with error status: 255
Thu Mar 31 09:47:33 2011 SIGTERM[hard,] received, process exiting
```

Thanks for or your help

---

### Post by spynappels on 2011-03-31
Some of those warnings are just telling you that the permissions on your cert and key files are set so anyone can access them, if you start OpenVPN at boot, they only need to be accessible by root, so you can adjust the permissions to suit.

Glad it seems to be working for you, if you have any more questions, just shout and I'll try to help.

---

### Post by corkscrew on 2011-03-31
> **spynappels said:**
> Some of those warnings are just telling you that the permissions on your cert and key files are set so anyone can access them, if you start OpenVPN at boot, they only need to be accessible by root, so you can adjust the permissions to suit.

Glad it seems to be working for you, if you have any more questions, just shout and I'll try to help.

So if if I go into the modify VPN server there are two drop down menus one for User and one for Group currently they are set as User = nobody and Group set as nogroup the same menus and settings are in the  client key settings

Do i set them both User = Root? and Group = Root ?

---

