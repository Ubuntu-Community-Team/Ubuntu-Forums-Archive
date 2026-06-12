---
title: "Samba over Openvpn"
date: 2011-04-23
forum: Server Platforms
---

### Post by DrkMachine on 2011-04-23
Lets see if I can explain this as I am still new at ubuntu server, I have 1 ubuntu 10.10 server running both openvpn and samba. I have openvpn set to run routed as I want the client pc's to only see the server. I had everything working flawlessly (or so I thought) night before last. Yesterday I was trying to tighten the security of samba. And now I can still connect to the vpn but can't access my samba shares.

Openvpn server.conf
```
local 192.168.1.139
port 1193
;proto tcp
proto udp
;dev tap
dev tun0
;dev-node MyTap
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
;server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100
;server-bridge
;push "route 192.168.10.0 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"
;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
;client-config-dir ccd
;route 10.9.0.0 255.255.255.252
;learn-address ./script
;push "redirect-gateway def1 bypass-dhcp"
;push "dhcp-option DNS 208.67.222.222"
;push "dhcp-option DNS 208.67.220.220"
;client-to-client
;duplicate-cn
keepalive 10 120
tls-auth ta.key 0 # This file is secret
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
verb 3
;mute 20
```

Samba smb.conf
```
# Samba config file created using SWAT
# from UNKNOWN (10.8.0.6)
# Date: 2011/04/16 17:16:03
[global]
        server string = %h server (Samba, Ubuntu)
        workgroup = WORKGROUP
        map to guest = bad user
        obey pam restrictions = yes
        pam password change = yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = yes
        security = user
        hosts allow = 127.0.0. 192.168.1. 10.8.0.
        hosts deny = 0.0.0.0/0
        interfaces = 127.0.0.1/8 192.168.1.100/24 10.8.0.0/24
        bind interfaces only = yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = no
        usershare allow guests = yes
        panic action = /usr/share/samba/panic-action %d
[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = yes
        browseable = no
[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
[test]
        path = /home/mike/test
        valid users = mike
        read only = no
        guest ok = yes
[Music]
        comment = Music Folder
        path = /srv/samba/Music
        write list = mike
        browsable = yes
        guest ok = yes
        read only = yes
        create mask = 0755
```

What I had attempted was to restrict the samba connections to the openvpn ip range bye removing the 192. addresses in the interfaces and hosts allow. but it would seem that wasn't correct, and when I added them back nothing changed.

Any assistance would be greatly appreciated

---

### Post by SeijiSensei on 2011-04-24
Samba needs to be able to listen on the tunnel address.  When the tunnel is established, what address is assigned to the tun0 or tap0 interface on the server?  That's the address that must be included in the interfaces directive. The "hosts allow" directive must include the subnet of legitimate remote tunnel addresses.

There's really very little security lost by listening on 192.168.0.0/16 addresses.  They're not routed over the public internet, so they can only appear on your local network or over a tunnel.

---

### Post by DrkMachine on 2011-04-24
Thank you for the reply seijisensei. Here is the results of ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:11:09:2d:01:d5
          inet addr:192.168.1.139  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107788 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:85333332 (85.3 MB)  TX bytes:16336645 (16.3 MB)
          Interrupt:22

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:902385 (902.3 KB)  TX bytes:902385 (902.3 KB)

tap0      Link encap:Ethernet  HWaddr 72:c0:a4:41:18:6a
          inet addr:192.168.160.1  Bcast:192.168.160.255  Mask:255.255.255.0
          inet6 addr: fe80::70c0:a4ff:fe41:186a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1828 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:337215 (337.2 KB)  TX bytes:810205 (810.2 KB)
```

I see that the IP on the tap0 is incorrect as well as needing (or wanting) it to be tun0 instead. Will see if I can correct that. Neither the tun0 or tap0 are listed in /etc/network/interfaces file.

well I have removed the tap0 interface. But now cannot for the life of me remember how to get the tun0 interface up.

---

### Post by DrkMachine on 2011-04-24
Ok. I have the tun0 up now here is the ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:11:09:2d:01:d5
          inet addr:192.168.1.139  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fe2d:1d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:80349 (80.3 KB)  TX bytes:53412 (53.4 KB)
          Interrupt:22

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:1386 (1.3 KB)  TX bytes:3258 (3.2 KB)
```

---

### Post by SeijiSensei on 2011-04-24
And the machine at 10.8.0.2 still can't see the samba server, or does it work now?  What do you see in the log files, usually in /var/log/samba, when you try to connect?

If the machine at 10.8.0.2 is running Windows, what does \\10.8.0.1\ show?  If it's a Linux box, try "smbclient -L 10.8.0.1".

---

### Post by DrkMachine on 2011-04-24
there is no machine at 10.8.0.2
the server is 10.8.0.1 and my laptop (windows) is connected to openvpn at 10.8.0.18

---

### Post by SeijiSensei on 2011-04-24
According to this, you have a tunnel from 10.8.0.1 on this machine to 10.8.0.2 at the other end.

```
tun0      Link encap:UNSPEC  HWaddr -0-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255

```

What happens if you ping 10.8.0.2?

---

### Post by DrkMachine on 2011-04-24
from the ubuntu server a ping of 10.8.0.2 goes no where
from the windows system it times out after the second packet

---

### Post by DrkMachine on 2011-04-24
this is in my log.nmbd

```
[2011/04/24 13:09:35.510540,  0] lib/util_sock.c:880(open_socket_in)
  bind failed on port 137 socket_addr = 192.168.1.100.
  Error = Cannot assign requested address
[2011/04/24 13:09:35.510676,  0] nmbd/nmbd_subnetdb.c:104(make_subnet)
  nmbd_subnetdb:make_subnet()
    Failed to open nmb socket on interface 192.168.1.100 for port 137.  Error was Cannot assign requested address
[2011/04/24 13:09:35.510727,  0] nmbd/nmbd.c:963(main)
  ERROR: Failed when creating subnet lists. Exiting.
```

and here is my log.smbd

```
[2011/04/24 13:09:34.088892,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/04/24 13:09:34.122839,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/04/24 13:09:34.123614,  0] smbd/server.c:1169(main)
  standard input is not a socket, assuming -D option
[2011/04/24 13:09:34.172451,  0] lib/util_sock.c:880(open_socket_in)
  bind failed on port 445 socket_addr = 192.168.1.100.
  Error = Cannot assign requested address
[2011/04/24 13:09:34.172773,  0] smbd/server.c:500(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Cannot assign requested address
[2011/04/24 13:09:34.172827,  0] lib/util_sock.c:880(open_socket_in)
  bind failed on port 139 socket_addr = 192.168.1.100.
  Error = Cannot assign requested address
[2011/04/24 13:09:34.172899,  0] smbd/server.c:500(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Cannot assign requested address
```

and my log.10.8.0.1

```
[2011/04/20 23:42:42.310586,  1] ../lib/util/params.c:350(Parameter)
  params.c:Parameter() - Ignoring badly formed line in configuration file: from UNKNOWN (10.8.0.6)
[2011/04/20 23:42:42.317419,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/04/20 23:42:42.323408,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/04/20 23:43:03.256434,  1] lib/util_sock.c:1631(get_peer_name)
  get_peer_name: getnameinfo failed for 10.8.0.1 with error Temporary failure in name resolution
[2011/04/20 23:45:17.106473,  1] ../lib/util/params.c:350(Parameter)
  params.c:Parameter() - Ignoring badly formed line in configuration file: from UNKNOWN (10.8.0.6)
[2011/04/20 23:45:17.113285,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/04/20 23:45:17.119205,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/04/20 23:45:45.132461,  1] lib/util_sock.c:1631(get_peer_name)
  get_peer_name: getnameinfo failed for 10.8.0.1 with error Temporary failure in name resolution
```

---

### Post by SeijiSensei on 2011-04-24
```
bind failed on port 137 socket_addr = 192.168.1.100.
```

I don't see a 192.168.1.100 in the ifconfig output.  The server appears to have 192.168.1.139.

I think you need to look very carefully at all the addresses you think you're assigning.  It looks to me like you're using addresses that don't exist both on the server itself, and on the remote end of the tunnel.  The server clearly thinks the other end of the tunnel is 10.8.0.2.  If your client doesn't have that address, there's something wrong in the OpenVPN configuration on one end or the other.

---

### Post by DrkMachine on 2011-04-24
well the 192.168.1.100 is my laptops address on the local lan assigned by my router.

---

### Post by DrkMachine on 2011-04-24
the 192.168.1.100 address is the address of my laptop on it's local network. the server on the same network has 192.168.1.139 assigned to it's eth0. I will look at my openvpn config and see if I can find the catch.

---

### Post by DrkMachine on 2011-04-24
I have looked at everything I can think of. I just can't find anything out of place. I'm thinking the best thing for me to do right now, is to wipe the system and start from scratch. Got a Routed Openvpn setup guide you could refer me to?

---

### Post by SeijiSensei on 2011-04-25
For two machines over a point-to-point connection, I use [this]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html").  I'm running half-a-dozen tunnels between here and client sites this way.

---

### Post by spynappels on 2011-04-26
I'd recommend using the OpenVPN Howto from the developers at [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)
to get it up and running.

FYI when connecting multiple clients to a VPN server in Routed mode, they will use 4 IP block and create a separate mini subnet for each tunnel, so when your IP address at the client end is 10.8.0.18, the other end of the tunnel is actually at 10.8.0.19 with 10.8.0.17 as the network address and 10.8.0.20 as the broadcast address. 

However, the OpenVPN server will automatically route these different subnets and will always be reachable at 10.8.0.1. Whether you can ping other clients depends on whether you have the ```
client-to-client
``` line uncommented in your server conf.

---

### Post by radistao on 2012-02-09
The problem is in Samba listening options:
if you have 
```
bind interfaces only = yes
```
 - it would not listen non broadcast interfaces (which openvpn tun0 is). This is written in *man smb.conf*: 
> Note that you should not use this parameter for machines that are serving PPP or other intermittent or non-broadcast network interfaces as it will not cope with non-permanent interfaces.
.

You have 2 solutions:
1) set bind interfaces only = no. In this cases nmbd will listen all interfaces in system, which is potential problem.
2) use tap instead of tun in openvpn. It would work like bridge.

---

