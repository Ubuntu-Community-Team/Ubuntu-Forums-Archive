---
title: "OpenVPN Configuration Issues"
date: 2012-05-30
forum: Server Platforms
---

### Post by jwright8 on 2012-05-30
I have OpenVPN installed and (I think) configured on Ubuntu 10.04 LTS.  

My server.conf is as follows:

```

local 10.1.10.70
port 56
proto udp
dev tap0
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
ifconfig-pool-persist ipp.txt
server-bridge 10.1.10.70 255.255.255.0 10.1.10.150 10.1.10.165
push "route 10.1.10.1 255.255.255.0"
push "dhcp-option DNS 10.1.10.1"
client-to-client
keepalive 10 120
tls-auth ta.key 0 # This file is secret
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3

```I followed the tutorial here:
[https://help.ubuntu.com/10.04/serverguide/openvpn.html](https://help.ubuntu.com/10.04/serverguide/openvpn.html)

When I start the service, it doesn't say failed, it says ok, leading me to believe it's up.  However, nothing is listening on port 56 that I can see.


When I try to use the OpenVPN GUI client (from OpenVPN's website, under Community), the logs show the following:

> 
Wed May 30 14:58:11 2012 OpenVPN 2.2.2 Win32-MSVC++ [SSL] [LZO2] [PKCS11] built on Dec 15 2011
Wed May 30 14:58:11 2012 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Wed May 30 14:58:11 2012 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Wed May 30 14:58:11 2012 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed May 30 14:58:11 2012 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Wed May 30 14:58:11 2012 LZO compression initialized
Wed May 30 14:58:11 2012 Control Channel MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Wed May 30 14:58:11 2012 Socket Buffers: R=[8192->8192] S=[8192->8192]
Wed May 30 14:58:11 2012 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Wed May 30 14:58:11 2012 Local Options hash (VER=V4): '13a273ba'
Wed May 30 14:58:11 2012 Expected Remote Options hash (VER=V4): '360696c5'
Wed May 30 14:58:11 2012 UDPv4 link local: [undef]
Wed May 30 14:58:11 2012 UDPv4 link remote: [24.23.50.193:56]("http://24.23.50.193:56")
Wed May 30 14:59:11 2012 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Wed May 30 14:59:11 2012 TLS Error: TLS handshake failed
Wed May 30 14:59:11 2012 TCP/UDP: Closing socket
Wed May 30 14:59:11 2012 SIGUSR1[soft,tls-error] received, process restarting
Wed May 30 14:59:11 2012 Restart pause, 2 second(s)
Wed May 30 14:59:13 2012 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Wed May 30 14:59:13 2012 Re-using SSL/TLS context
Wed May 30 14:59:13 2012 LZO compression initialized
Wed May 30 14:59:13 2012 Control Channel MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Wed May 30 14:59:13 2012 Socket Buffers: R=[8192->8192] S=[8192->8192]
Wed May 30 14:59:13 2012 Data Channel MTU parms [ L:1574 D:1450 EF:42 EB:135 ET:32 EL:0 AF:3/1 ]
Wed May 30 14:59:13 2012 Local Options hash (VER=V4): '13a273ba'
Wed May 30 14:59:13 2012 Expected Remote Options hash (VER=V4): '360696c5'
Wed May 30 14:59:13 2012 UDPv4 link local: [undef]
Wed May 30 14:59:13 2012 UDPv4 link remote: [24.23.50.193:56]("http://24.23.50.193:56")
Wed May 30 14:59:23 2012 TCP/UDP: Closing socket
Wed May 30 14:59:23 2012 SIGTERM[hard,] received, process exiting
I have my port forwarded on my router to the box.  I've also tried disabling my client's firewall.  The client system is a Windows 7 machine.

In the tutorial, it didn't tell you how to configure the .ovpn file you'd need for your Windows client machine, so I just looked at their example.conf on the OpenVPN site and modified it.

JustinDesktop.ovpn (my client file):
```

client

dev tap0

proto udp

remote 24.23.50.193 56

resolv-retry infinite
nobind

```Due to a suggestion on the forums, I've also tried with TCP.  Still won't work.

My ifconfig:

```

br0       Link encap:Ethernet  HWaddr 00:1e:90:38:25:11
          inet addr:10.1.10.70  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fe38:2511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15090609 (15.0 MB)  TX bytes:1033886 (1.0 MB)

eth0      Link encap:Ethernet  HWaddr e0:46:9a:2b:bc:ca
          inet6 addr: fe80::e246:9aff:fe2b:bcca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40832 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2895601 (2.8 MB)  TX bytes:59358345 (59.3 MB)
          Interrupt:19 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:1e:90:38:25:11
          inet6 addr: fe80::21e:90ff:fe38:2511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:82792474 (82.7 MB)  TX bytes:4728107 (4.7 MB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:88 (88.0 B)  TX bytes:88 (88.0 B)

tap0      Link encap:Ethernet  HWaddr e2:c1:2a:bd:23:b8
          inet6 addr: fe80::e0c1:2aff:febd:23b8/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)

```Any help is much appreciated; I'm at wit's end here.

EDIT: 

It might also be worth mentioning that I have the following files on the client in D:\Program Files (x86):\OpenVPn\config\ :

ca.crt
JustinDesktop.crt
JustinDesktop.key
ta.key
JustinDesktop.ovpn

On the server, my openvpn-status.log says:

> 
OpenVPN CLIENT LIST
Updated,Wed May 30 15:31:06 2012
Common Name,Real Address,Bytes Received,Bytes Sent,Connected Since
ROUTING TABLE
Virtual Address,Common Name,Real Address,Last Ref
GLOBAL STATS
Max bcast/mcast queue length,0
END

[IMG]https://mail.google.com/mail/images/cleardot.gif[/IMG]

---

### Post by spynappels on 2012-05-31
Hi there,

Is there a specific reason you used bridged mode rather than routed mode for your vpn?

The OpenVPN documentation can be found here: [http://openvpn.net/index.php/open-source/documentation/howto.html#vpntype](http://openvpn.net/index.php/open-source/documentation/howto.html#vpntype) and it explains the differences.


In any case, in your client conf file you need to allow some form of authentication, which as far as I can see is missing from yours:

```
ca ca.crt
cert client.crt
key client.key
```

You can see the sample conf files from OpenVPN here: [http://openvpn.net/index.php/open-source/documentation/howto.html#examples](http://openvpn.net/index.php/open-source/documentation/howto.html#examples) And the documentation is very good and very helpful.

If you need more help, just shout.

---

### Post by jwright8 on 2012-05-31
I used bridged mode since I have a computer connected to the eth0 out  (eth1 incoming internet connection).  The goal was to filter traffic  going through the Linux box on the way to the Windows system behind it.   Speaking of, any help you could give me to point me in the right  direction for accomplishing this via IPTables would be appreciated as  well.  I know how to block/allow IPs and ports to the box, but for some  reason it seems this doesn't apply to traffic going THROUGH the Linux  box... which frankly makes no sense.

My JustinDesktop.ovpn has what you suggested in there.  For some reason, it didn't paste, so I'll try again:

```

client
dev tap0
proto udp
remote 24.23.50.193 56
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert JustinDesktop.crt
key JustinDesktop.key
ns-cert-type server
tls-auth ta.key 1
comp-lzo
verb 3

```

Thanks for the help so far!

---

### Post by spynappels on 2012-05-31
Hmmm, the error message says that the TLS handshake failed so I guess you need to concentrate on that. 

Have you made sure there is no firewall active on the Ubuntu box and that port forwarding/NAT is working correctly on the router?

I'll be off line soon, but if you don't have this sorted by tomorrow, I'll pick it up again.

---

### Post by jwright8 on 2012-05-31
I appreciate all your quick responses.  It turns out that I'm just retarded; the configuration was actually valid.  I typed one IP number off.. still not entirely sure how I missed that, but I happened to be going over the client config for the hundredth time and found it.  

On the bright side, perhaps the configuration above will help someone that's having problems with it.

As a parting query, though, do you have any idea where I could look for the IPTables thing?

My idea is that when they connect to the OpenVPN, I would want IPTables to drop the connection (or refuse) if it wasn't an IP I explicitly allowed, no matter if the cert/auth was valid or not.  

Do you know how I'd go about doing that?

Thanks for everything so far!

---

### Post by spynappels on 2012-05-31
Ok, glad you got the VPN up anyway, could you describe what you want iptables to do in this case, and which interfaces you want it to filter, I'll certainly try and help you.

---

### Post by SeijiSensei on 2012-05-31
This code will enter rules to permit the IP addresses in VPN_ALLOW to connect to the OpenVPN port and block all other addresses.

```

# external IP of this host
MYIP="10.10.10.10"
# OpenVPN port
VPN_PORT=56
# list of allowed machines
VPN_ALLOW='10.1.1.1 10.1.1.2 192.168.33.4 172.26.33.114'

for h in $VPN_ALLOW
do
   /sbin/iptables -A INPUT -p udp -s $h -d $MYIP --dport $VPN_PORT -j ACCEPT
done
/sbin/iptables -A INPUT -p udp -d $MYIP --dport $VPN_PORT -j REJECT --reject-with icmp-host-prohibited

```

I don't know why you are using a privileged (<1024) port.  Only root and similar administrative users are supposed to be able to bind an application to that port.  Most OpenVPN connections use random high ports in the 1024-65535 range.

The VPN_ALLOW list can include subnets like 192.168.1.0/24.  If you have a really long list, it's useful to put it in a separate file, say /etc/openvpn/allow_list, one address per line, and replace the VPN_ALLOW entry above with 

```
VPN_ALLOW=$(cat /etc/openvpn/allow_list)
```

---

### Post by jwright8 on 2012-05-31
Thanks for the reply!  

I used a privileged port for the sake of simplicity.  I mapped sshd to 55 and figured I'd map the VPN to 56.  In reality, the system won't ever have anything other than that on it, so I figured it wouldn't be an issue.  If, however, it could still be an issue I don't suppose it matters if I switch it to a higher port.

---

### Post by SeijiSensei on 2012-05-31
> **jwright8 said:**
> I used a privileged port for the sake of simplicity.

Well, I don't see much in the way of simplicity here.  OpenVPN doesn't care about which port it's using, but well-designed operating systems do. So it might matter for remotes on systems like *nix that enforce standardized restrictions on ports.  I know if you tried to connect on port 56 as an ordinary user on Linux, you'd get nowhere.  Just use some high port and avoid any such problems.  I often pick a port whose numeric values matches an easy-to-remember sequence of keys on a phone.  For instance, the word "mail" on a telephone keypad maps to the port 6245.

---

### Post by jwright8 on 2012-05-31
I didn't realize it might matter that much x_x 

Thanks for the heads up.. and the interesting advice on port picking lol

---

### Post by jwright8 on 2012-05-31
Sorry for the double post, but will I be able to add that to my current IPTables script?  I have an iptables.sh file in /root/ that I execute that has all of my IPTables rules in it (it starts with -F to flush before reinitializing).  I had thought about just pasting that (after I change the port) into the script, but I'm not entire sure that will work.. will it?

---

### Post by spynappels on 2012-06-01
You should be able to paste that into your existing script, you may find a redundant rule in the "reject d-port=VPN_PORT" rule at the end if you already have a default reject traffic rule at the end of the input chain.

You could post your current script to double check though if you like....

---

### Post by jwright8 on 2012-06-01
It currently just looks something like this (I've cut parts out like other IPs blocked to make it shorter):

```

# Iptables script
#
#/bin/sh
iptables -F

## Allowed users
iptables -A INPUT -s 127.0.0.1 -j ACCEPT
iptables -A INPUT -s localhost -j ACCEPT
iptables -A INPUT -s 108.91.57.151 -j ACCEPT # Tommy
iptables -A INPUT -s 64.89.91.254 -j ACCEPT # Justin - NA NuVox
iptables -A INPUT -s 24.98.112.173 -j ACCEPT # Justin - Comcast 5/30/12

## Blocked ports
iptables -A INPUT -p tcp --dport 25 -j DROP # SMTP
iptables -A INPUT -p tcp --dport 81 -j DROP # Private
iptables -A INPUT -p tcp --dport 25 -j DROP # Rkhunter stuff
iptables -A INPUT -p tcp --dport 7950 -j DROP # Webmin
iptables -A INPUT -p tcp --dport 10000 -j DROP # Webmin
iptables -A INPUT -p tcp --dport 3306 -j DROP # MySQL
iptables -A OUTPUT -p tcp --dport 6667 -j DROP
iptables -A INPUT -p tcp --dport 1234 -j DROP # Psybnc port
iptables -A OUTPUT -p tcp --dport 1234 -j DROP # Psybnc port

## Blocked users
iptables -A INPUT -s 188.143.16.3 -j DROP #  Auth login spam - Hungary, Done 5/13/12, Added 5/14/12
iptables -A INPUT -s 117.4.179.249 -j DROP # Mail server spam - Vietnam, Done 5/13/12, Added 5/14/12
iptables -A INPUT -s 117.4.31.235 -j DROP # Mail server spam - Vietnam, Done 5/13/12, Added 5/14/12
iptables -A INPUT -s 92.85.237.190 -j DROP # Mail server spam - Romania, Done 5/13/12, Added 5/14/12
iptables -A INPUT -s 110.77.244.61 -j DROP # Mail server spam - Thailand, Done 5/13/12, Added 5/14/12
iptables -A INPUT -s 94.97.144.134 -j DROP # Mail server spam - Saudi Arabia, Done 5/14/12, Added 5/14/12
iptables -A INPUT -s 176.65.97.94 -j DROP # Mail server spam - Russia, Done 5/14/12, Added 5/14/12
iptables -A INPUT -s 2.78.203.67 -j DROP # Mail server spam - Kazakhstan, Done 5/14/12, Added 5/14/12
iptables -A INPUT -s 187.23.161.32 -j DROP # TCP Portscan - Brazil, Done 5/12/12, Added 5/14/12
iptables -A INPUT -s 78.87.123.114 -j DROP # Auth spam - Russia, Done 5/17/12, Added 5/17/12
iptables -A INPUT -s 78.140.197.50 -j DROP # Auth spam - Russia, Done 5/17/12, Added 5/17/12
iptables -A INPUT -s 120.197.249.252 -j DROP # TCP Portscan - China, Done 5/19/12, Added 5/21/12


echo Complete!

```I guess it's quite rudimentary in comparison to other IPTables scripts, but it seems to work for me.

---

### Post by spynappels on 2012-06-01
What are your default policies?

---

### Post by jwright8 on 2012-06-01
I apologize if I sound ignorant, but I'm not sure.  Most of what I've gleaned from IPTables was research I did online.  I was, apparently erroneously, under the impression that the script was all that was needed.  I wrote the script based on stuff that I read from various places.

When I do iptables -L, it just lists the IPs and such that I specified in the script I wrote, leading me to believe there are no other default policies.

At the moment, the above code is stored in iptables.sh in my /root/ dir and I just do ./iptables.sh whenever I restart the system or change the script.

---

### Post by spynappels on 2012-06-01
You can take a dump of your complete setup by running the following:
```
sudo iptables-save > /var/tmp/iptables.rules
```
You can take the resulting files, and it will tell you everything you need to know about your ruleset. It will also tell you your default policies.

If you want to, you can obfuscate the items you want to keep private and paste the output here so we can have a look.

---

### Post by jwright8 on 2012-06-01
Default Policies:
```

# Generated by iptables-save v1.4.4 on Fri Jun  1 09:59:24 2012
*filter
:INPUT ACCEPT [52485:62570003]
:FORWARD ACCEPT [140194:125452702]
:OUTPUT ACCEPT [44171:5596010]

```Various Allowed IPs

```

-A INPUT -s 127.0.0.1/32 -j ACCEPT
-A INPUT -s 127.0.0.1/32 -j ACCEPT
-A INPUT -s 64.22.103.219/32 -j ACCEPT
-A INPUT -s 74.207.230.44/32 -j ACCEPT

```Dropped ports and end of file
```


-A INPUT -p tcp -m tcp --dport 81 -j DROP
-A INPUT -p tcp -m tcp --dport 7950 -j DROP
-A INPUT -p tcp -m tcp --dport 3690 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 10000 -j DROP
-A INPUT -p tcp -m tcp --dport 3306 -j DROP
-A INPUT -p tcp -m tcp --dport 1234 -j DROP
-A INPUT -p tcp -m tcp --dport 56 -j ACCEPT
-A INPUT -p udp -m udp --dport 56 -j ACCEPT

COMMIT
# Completed on Fri Jun  1 09:59:24 2012

```For ease of reading/brevity, I took out the allowed/blocked IPs and stuff that was redundant.

EDIT: From reading it, it seems like everything is allowed incoming,forwarding, and outgoing.  Since it is behind a router, is it redundant to block all incoming ports when the router is blocking incoming traffic?

---

### Post by SeijiSensei on 2012-06-01
"iptables -L" also lists the default "policy" for each chain which is usually ACCEPT.  So if you don't set the policy to DROP, or have a catch-all DROP or REJECT rule at the bottom of the chain, you're basically accepting everything that doesn't match a rule.

The top of my iptables script looks like this:

```

# flush the filter table
iptables -F
# flush the NAT table just in case
iptables -t nat -F

# default policies
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

# INPUT rules
iptables -A INPUT ....
[rest of INPUT rules]

# residual traffic should be blocked by  policy DROP
# log any missed packets for review
iptables -A INPUT -j LOG --log-prefix=INPUT_
iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited

# FORWARD RULES
iptables -A FORWARD ...
[forwarding rules if any]

# once again log unmatched
iptables -A FORWARD -j LOG --log-prefix=FORW_
iptables -A FORWARD -j REJECT --reject-with icmp-host-prohibited

```

On a machine with a single interface that does no routing, you won't have FORWARD rules.  By default an Ubuntu machine has IP packet forwarding disabled in /etc/sysctl.conf anyway, making forwarding moot.  However if you have tunnels, then you need to consider whether to allow traffic to be forwarded between them -- whether someone connected to the tun0 interface can send traffic to someone connected to tun1.  If so, you need to enable forwarding and write FORWARD rules to control which pairs of interfaces can exchange traffic.  If all the VPN clients are simply connecting to the server to use its services, but not communicating among themselves, then you want to make sure packet forwarding is disabled in /etc/sysctl.conf.

You can add the rules I gave you before anywhere in the INPUT rules above any catchall denial rule like the ones in my example above.  If you have such a rule then, as spynappels says, you don't need the final REJECT rule I gave before:
```
[s]/sbin/iptables -A INPUT -p udp -d $MYIP --dport $VPN_PORT -j REJECT --reject-with icmp-host-prohibited[/s]
```

If you impose a default DROP policy or add a catch-all rejection rule to your list, you'll need to allow INPUT from the tun interfaces like this:

```

iptables -A INPUT -i tun0 -j ACCEPT
iptables -A INPUT -i tun1 -j ACCEPT
[...]

```

If you trust your users, a generic rule like that is fine.  If you don't trust them, you'll need to write rules specifying which ports machines connecting over the tun interfaces can use.

---

### Post by jwright8 on 2012-06-01
Okay, that makes sense.  

For curiosity's sake, if you ONLY wanted outbound traffic to be over the VPN port, could you block all other ports using IPTables?  Or do you use different ports once you're connected to the VPN and mount a network drive? 

I'd like to be able to block all outgoing traffic except traffic from remote clients connected to the VPN, which leads me to believe if you blocked all but 5556 (my new VPN port) it would work, but I don't know enough about ports to know if once connected that changes for something like, say, using mapped network drives to the machine behind the box.

EDIT:

What would be an example of when you use a forwarding rule?  Is it something like port forwarding through a router?  If so, doesn't it make forwarding through the Linux box pointless if you're already doing it through the router?

I also don't believe I have any tunnel interfaces on my machine.  Or are br0 and tap0 considered tunnel interfaces? My ifconfig:

```

br0       Link encap:Ethernet  HWaddr 00:1e:90:38:25:11
          inet addr:10.1.10.70  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fe38:2511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:85751502 (85.7 MB)  TX bytes:6577156 (6.5 MB)

eth0      Link encap:Ethernet  HWaddr e0:46:9a:2b:bc:ca
          inet6 addr: fe80::e246:9aff:fe2b:bcca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8551512 (8.5 MB)  TX bytes:184387116 (184.3 MB)
          Interrupt:19 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:1e:90:38:25:11
          inet6 addr: fe80::21e:90ff:fe38:2511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:272676657 (272.6 MB)  TX bytes:17542759 (17.5 MB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:88 (88.0 B)  TX bytes:88 (88.0 B)

tap0      Link encap:Ethernet  HWaddr ca:a1:f8:1c:98:2b
          inet6 addr: fe80::c8a1:f8ff:fe1c:982b/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:12839 (12.8 KB)  TX bytes:630 (630.0 B)

```

---

### Post by SeijiSensei on 2012-06-01
Oh, right, you're using bridging and tap.  Can't help you there, I'm afraid, but a more general answer to your question is to control traffic by IP address.  It looks like all your VPN machines will have addresses in the 10.1.10.0/24 network, so you can write a rule that permits that subnet.  

```

iptables -A INPUT -s 10.1.10.0/24 -j ACCEPT
iptables -A INPUT -j REJECT

```

In general I avoid solutions based on bridging and prefer to use routing, but that's just me.

---

### Post by jwright8 on 2012-06-01
A lot of this has to do with me just generally learning how to do it; I've learned quite a bit through all this setup and configuration process x_x.  You guys have been a huge help, and I appreciate it.

---

### Post by spynappels on 2012-06-01
No problem, I have to agree with SeijiSensei that a routed setup is much easier to work with and firewall for.

Incidentally, this is how I learned to play with OpenVPN and iptables too, I found the following link to be very helpful on the iptables stuff, it is written by one of the Mods on here, BodhiZazen:

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by jwright8 on 2012-06-01
Thank you very much for the link!  I just bookmarked it, I was looking for something just like this!

---

### Post by spynappels on 2012-06-01
No problem, glad it helped. There are a whole bunch of stickies at the top of the Security sub-forum page which you may find some "light" reading, a must for anyone running a server IMHO.

---

### Post by jwright8 on 2012-06-01
Something I'm doing is actually locking me out of SSH now >_>  

Luckily I have the system sat next to me, but does someone mind taking a look over the script I have?

```

#
# Iptables script
#
#!/bin/sh

## Flush the filter table
iptables -F
## Flush the NAT table, just in case
iptables -t nat -F

## Default policies
iptables -P INPUT DROP
iptables -P OUTPUT DROP # To drop all outgoing traffic like web browsing?
# iptables -P OUTPUT ACCEPT # Original default policy in case things go wrong
iptables -P FORWARD DROP

## Allowed users
iptables -A INPUT -s 127.0.0.1 -j ACCEPT
iptables -A INPUT -s localhost -j ACCEPT
iptables -A INPUT -s 24.30.50.193  -j ACCEPT # Local IP, NA Comcast
iptables -A INPUT -s 74.166.100.124 -j ACCEPT # Alabama
iptables -A INPUT -s 64.89.91.254 -j ACCEPT # Justin - NA NuVox
iptables -A INPUT -s 108.216.245.241 -j ACCEPT # Brandon - GA IP
iptables -A INPUT -s 24.98.112.173 -j ACCEPT # Justin - Comcast 5/30/12

## Permanent allowed users (LAN)
iptables -A INPUT -s 10.1.10.0/24 -j ACCEPT # LAN IP 
iptables -A INPUT -s 192.168.1.0/16 -j ACCEPT 


## Allowed interfaces
## this will only be uncommented if the reject rule blocks the bridge/tap
#iptables -A INPUT -i br0 -j ACCEPT
#iptables -A INPUT -i tap0 -j ACCEPT

## Allowed ports
iptables -A INPUT -p tcp --dport 5555 -j ACCEPT # SSHD port
iptables -A OUTPUT -p tcp --dport 5555 -j ACCEPT
iptables -A INPUT -p udp --dport 5556 -j ACCEPT # VPN port
iptables -A OUTPUT -p udp --dport 5556 -j ACCEPT

## Blocked ports
iptables -A INPUT -p tcp --dport 22 -j DROP # SSHD default
iptables -A INPUT -p tcp --dport 21 -j DROP # FTP default
iptables -A INPUT -p tcp --dport 25 -j DROP # SMTP
iptables -A INPUT -p tcp --dport 81 -j DROP # Private
iptables -A INPUT -p tcp --dport 25 -j DROP # Rkhunter stuff
iptables -A INPUT -p tcp --dport 7950 -j DROP # Webmin
iptables -A INPUT -p tcp --dport 3690 -j DROP # SVN
iptables -A INPUT -p tcp --dport 10000 -j DROP # Webmin
iptables -A INPUT -p tcp --dport 3306 -j DROP # MySQL
iptables -A OUTPUT -p tcp --dport 6667 -j DROP
iptables -A INPUT -p tcp --dport 1234 -j DROP # Psybnc port
iptables -A OUTPUT -p tcp --dport 1234 -j DROP # Psybnc port
iptables -A INPUT -p tcp --dport 56 -j DROP # VPN is UDP, not TCP
iptables -A OUTPUT -p tcp --dport 56 -j DROP # VPN is UDP, not TCP

## Residual traffic should be blocked by the default policy of DROP
## Log any missed packets for review
iptables -A INPUT -j LOG --log-prefix=INPUT_
iptables -A INPUT -j REJECT --reject-with icmp-host-prohibited


## Blocked users
iptables -A INPUT -s 74.171.107.175 -j DROP
iptables -A INPUT -s 98.64.13.210 -j DROP
iptables -A INPUT -s 58.211.0.12 -j DROP
# etc, cut off for brevity

echo Complete!


```
As always, thanks guys x_x

---

### Post by SeijiSensei on 2012-06-01
> **jwright8 said:**
> Something I'm doing is actually locking me out of SSH now >_>

One reason is probably because you're not allowing reply traffic.  Add the line in blue to your rules:

```

#
# Iptables script
#
#!/bin/sh

## Flush the filter table
iptables -F
## Flush the NAT table, just in case
iptables -t nat -F

## Default policies
iptables -P INPUT DROP
iptables -P OUTPUT DROP # To drop all outgoing traffic like web browsing?
# iptables -P OUTPUT ACCEPT # Original default policy in case things go wrong
iptables -P FORWARD DROP

## Allowed users
iptables -A INPUT -s 127.0.0.1 -j ACCEPT
iptables -A INPUT -s localhost -j ACCEPT
[color=blue]iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT[/color]
[etc.]

```

Even with this rule, having a blanket DROP policy for OUTPUT might still block communication with the server.  It's not just to control web browsing.  Having a default OUTPUT policy of DROP means the server can only send traffic that has been specifically allowed.  That's pretty hard to do in advance.

If you're really concerned about OUTPUT traffic, I suggest setting the OUTPUT policy to ACCEPT, then adding a logging rule at the bottom of the ruleset to identify any residual traffic.

```

[COLOR="blue"]iptables -P OUTPUT ACCEPT[/COLOR]

[...]

[color=blue]iptables -A OUTPUT -j LOG --log-prefix OUTPUT_[/color]

```

You can browse the log and see whether you need to add some additional blocking rules.

---

### Post by jwright8 on 2012-06-01
Well the culprit seems to be this line:

```

[FONT=monospace]iptables -P OUTPUT DROP
[/FONT]
```[FONT=monospace]

So doesn't that mean I would need to change the blue line to OUTPUT instead of INPUT, or should I add a line for both? 

Adding the blue line with the OUTPUT rule enabled will still block my SSH.

EDIT:

Wait, it says that RELATED,ESTABLISHED is an invalid argument.  Maybe that's my problem?
[/FONT]

---

### Post by jwright8 on 2012-06-01
Okay, it seems like I typo'd the blue line now.  It's fine.  

To kinda get around the OUTPUT problem of just using: 

```

iptables -P OUTPUT DROP 

```

Instead, I used:

```

## Dropped outgoing ports
## For net access filtering
iptables -A OUTPUT -p tcp --dport 21 -j DROP
iptables -A OUTPUT -p tcp --dport 22 -j DROP
iptables -A OUTPUT -p tcp --dport 23 -j DROP
iptables -A OUTPUT -p tcp --dport 25 -j DROP
iptables -A OUTPUT -p tcp --dport 43 -j DROP
iptables -A OUTPUT -p tcp --dport 53 -j DROP
iptables -A OUTPUT -p tcp --dport 79 -j DROP
iptables -A OUTPUT -p tcp --dport 80 -j DROP # HTTP
iptables -A OUTPUT -p tcp --dport 110 -j DROP
iptables -A OUTPUT -p tcp --dport 115 -j DROP
iptables -A OUTPUT -p tcp --dport 119 -j DROP
iptables -A OUTPUT -p tcp --dport 143 -j DROP
iptables -A OUTPUT -p tcp --dport 389 -j DROP
iptables -A OUTPUT -p tcp --dport 443 -j DROP # HTTPS

```

Good idea?

---

### Post by SeijiSensei on 2012-06-01
If you're trying to filter your VPN users, which I'm guessing is the point of this, then it's a lot easier to deal with them by address or interface, and to control them on the INPUT side like I suggested [above](http://ubuntuforums.org/showpost.php?p=11988241&postcount=20).

From the list of ports you wanted to block, it looks like pretty much all standard services.  If that's the case then, you're better off adopting default-deny like this:
```

VPN_NET="10.1.10.0/24"
VPN_SERVER="10.1.10.70"
[color='blue']WIN_SERVER="10.1.10.50"[/color]
iptables -A INPUT -s $VPN_SERVER -d $VPN_NET -j ACCEPT
iptables -A INPUT -s $VPN_NET -d $VPN_SERVER -j ACCEPT
[COLOR='blue']iptables -A INPUT -s $WIN_SERVER -d $VPN_NET -j ACCEPT
iptables -A INPUT -s $VPN_NET -d $WIN_SERVER -j ACCEPT[/color]
iptables -A INPUT -s $VPN_NET -j REJECT --reject-with icmp-host-prohibited

```

That lets machines on the VPN talk to the VPN server at 10.1.10.70 but not to each other or anywhere else.  If there are particular services you wish to allow your VPN users to reach, then add port-specific exemptions like this one which would enable SSH to remote hosts:

```
iptables -A INPUT -p tcp -s $VPN_NET --dport 22 -j ACCEPT
```

Place any exemptions above the REJECT rule in the list above.

> The goal was to filter traffic going through the Linux box on the way to the Windows system behind it.

I went back and read the first post.  You'll want to add an exemption for the Windows machine(s).  I've added it (in blue) above.

---

### Post by jwright8 on 2012-06-01
The actual idea for the output rules were to deny users on the LAN behind the VPN server those services (mostly web browsing, the rest was just an afterthought).  

I still want the people on the VPN, once they connect, to be able to access other computers on the LAN (not by name, but by IP, hence no WINS server necessary).  That's why I enabled the client-to-client in the server.conf for OpenVPN.  Sorry I didn't explain myself very well in that last post.

---

### Post by jwright8 on 2012-06-01
I get the following error from it:

```


Bad argument `10.1.10.0/24'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `ACCEPT'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `10.1.10.0/24'
Try `iptables -h' or 'iptables --help' for more information.


```


EDIT:

Never mind, I put it in without the variables (just typing in the IPs/ragnes each time) and it worked.  

Thanks a lot everyone!

---

