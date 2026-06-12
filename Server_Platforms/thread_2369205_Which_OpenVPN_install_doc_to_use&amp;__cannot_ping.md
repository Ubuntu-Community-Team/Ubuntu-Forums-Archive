---
title: "Which OpenVPN install doc to use?&amp;  cannot ping server"
date: 2017-08-20
forum: Server Platforms
---

### Post by accounts0 on 2017-08-20
I see 4 of what appear to be official OpenVPN installation tutorials, so which one?

[COLOR=#000000][FONT=Consolas]Ubuntu Server OpenVPN Guide Page:[/FONT][/COLOR][https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)

[COLOR=#000000][FONT=Consolas]Ubuntu Community OpenVPN Help Page:[/FONT][/COLOR][https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

[COLOR=#000000][FONT=Consolas]OpenVPN Website HowTo Page:[/FONT][/COLOR][https://openvpn.net/index.php/open-source/documentation/howto.html](https://openvpn.net/index.php/open-source/documentation/howto.html)

[COLOR=#000000][FONT=Consolas]OpenVPN Community Wiki HowTo Page:[/FONT][/COLOR][https://community.openvpn.net/openvpn/wiki/HOWTO](https://community.openvpn.net/openvpn/wiki/HOWTO)

---

### Post by darkod on 2017-08-20
Well that depends what exactly you need to do and which document/tutorial covers it.
I have always started with that first link and that is enough for standard installation. After when needing something specific I usually google it around.

---

### Post by SeijiSensei on 2017-08-20
If you just want to set up a point-to-point tunnel between, say, a local machine and a remote server, read [https://openvpn.net/static.html](https://openvpn.net/static.html)

---

### Post by accounts0 on 2017-08-20
> **SeijiSensei said:**
> If you just want to set up a point-to-point tunnel between, say, a local machine and a remote server, read [https://openvpn.net/static.html](https://openvpn.net/static.html)
> **darkod said:**
> Well that depends... I have always started with that first link[QUOTE=accounts0;13678104]Ubuntu Server OpenVPN Guide Page:[https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)[/QUOTE]

I've been slowly going through this first one as was suggested earlier... Thx!

---

### Post by accounts0 on 2017-08-20
I've installed OpenVPN on an Ubuntu LTS server, as well as on the same LTS client side, according to the official Ubuntu Server documentation [1].

Although I no longer get error messages, I'm unable to ping the server (at 10.8.0.1) from the client. I've tried forwarding the specified port on both TCP & UDP on my LAN's router but it didn't make a difference.

Server status:
```

$ sudo systemctl status openvpn@server
&#9679; openvpn@server.service - OpenVPN connection to server                                                                                                                                                                                                                        
   Loaded: loaded (/lib/systemd/system/openvpn@.service; disabled; vendor preset: enabled)                                                                                                                                                                                     
   Active: active (running) since Sun 2017-08-20 11:23:02 UTC; 1h 11min ago                                                                                                                                                                                                    
     Docs: man:openvpn(8)                                                                                                                                                                                                                                                      
           https://community.openvpn.net/openvpn/wiki/Openvpn23ManPage                                                                                                                                                                                                         
           https://community.openvpn.net/openvpn/wiki/HOWTO                                                                                                                                                                                                                    
 Main PID: 439 (openvpn)                                                                                                                                                                                                                                                       
   CGroup: /system.slice/system-openvpn.slice/openvpn@server.service                                                                                                                                                                                                           
           &#9492;&#9472;439 /usr/sbin/openvpn --daemon ovpn-server --status /run/openvpn/server.status 10 --cd /etc/openvpn --script-security 2 --config /etc/openvpn/server.conf --writepid /run/openvpn/server.pid                                                                      
                                                                                                                                                                                                                                                                               
Aug 20 12:00:50 tappanzee ovpn-server[439]: x.x.x.x:33985 WARNING: this cipher's block size is less than 128 bit (64 bit).  Consider using a --cipher with a larger block size.                                                                                          
Aug 20 12:00:50 tappanzee ovpn-server[439]: x.x.x.x:33985 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication                                                                                                                                
Aug 20 12:00:50 tappanzee ovpn-server[439]: x.x.x.x:33985 Control Channel: TLSv1.2, cipher TLSv1/SSLv3 DHE-RSA-AES256-GCM-SHA384, 2048 bit RSA                                                                                                                           
Aug 20 12:00:50 tappanzee ovpn-server[439]: x.x.x.x:33985 [Triborough] Peer Connection Initiated with [AF_INET]x.x.x.x:33985                                                                                                                                         
Aug 20 12:00:50 tappanzee ovpn-server[439]: Triborough/x.x.x.x:33985 MULTI_sva: pool returned IPv4=10.8.0.6, IPv6=(Not enabled)                                                                                                                                            
Aug 20 12:00:50 tappanzee ovpn-server[439]: Triborough/x.x.x.x:33985 MULTI: Learn: 10.8.0.6 -> Triborough/x.x.x.x:33985                                                                                                                                                
Aug 20 12:00:50 tappanzee ovpn-server[439]: Triborough/x.x.x.x:33985 MULTI: primary virtual IP for Triborough/x.x.x.x:33985: 10.8.0.6                                                                                                                                  
Aug 20 12:00:52 tappanzee ovpn-server[439]: Triborough/x.x.x.x:33985 PUSH: Received control message: 'PUSH_REQUEST'                                                                                                                                                        
Aug 20 12:00:52 tappanzee ovpn-server[439]: Triborough/x.x.x.x:33985 send_push_reply(): safe_cap=940                                                                                                                                                                       
Aug 20 12:00:52 tappanzee ovpn-server[439]: Triborough/x.x.x.x:33985 SENT CONTROL [Triborough]: 'PUSH_REPLY,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.6 10.8.0.5' (status=1)                                                                    
wetyourself@tappanzee:~$

```

Client status:
```

$ sudo systemctl status  openvpn@client
&#9679; openvpn@client.service - OpenVPN connection to client
   Loaded: loaded (/lib/systemd/system/openvpn@.service; disabled; vendor preset: enabled)
   Active: active (running) since Sun 2017-08-20 08:00:48 EDT; 34min ago
     Docs: man:openvpn(8)
           https://community.openvpn.net/openvpn/wiki/Openvpn23ManPage
           https://community.openvpn.net/openvpn/wiki/HOWTO
  Process: 13989 ExecStart=/usr/sbin/openvpn --daemon ovpn-%i --status /run/openvpn/%i.status 10 --cd /etc/openvpn --script-security 2 --config /etc/openvpn/%i.conf --writepid /run/openvpn/%i.pid (code=exited, status=0/SUCCESS)
 Main PID: 13991 (openvpn)
   CGroup: /system.slice/system-openvpn.slice/openvpn@client.service
           &#9492;&#9472;13991 /usr/sbin/openvpn --daemon ovpn-client --status /run/openvpn/client.status 10 --cd /etc/openvpn --script-security 2 --config /etc/openvpn/client.conf --writepid /run/openvpn/client.pid


Aug 20 08:00:52 Triborough ovpn-client[13991]: OPTIONS IMPORT: --ifconfig/up options modified
Aug 20 08:00:52 Triborough ovpn-client[13991]: OPTIONS IMPORT: route options modified
Aug 20 08:00:52 Triborough ovpn-client[13991]: ROUTE_GATEWAY 192.168.1.1/255.255.255.0 IFACE=wlp2s0 HWADDR=2c:6e:85:1a:8a:1a
Aug 20 08:00:52 Triborough ovpn-client[13991]: TUN/TAP device tun0 opened
Aug 20 08:00:52 Triborough ovpn-client[13991]: TUN/TAP TX queue length set to 100
Aug 20 08:00:52 Triborough ovpn-client[13991]: do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Aug 20 08:00:52 Triborough ovpn-client[13991]: /sbin/ip link set dev tun0 up mtu 1500
Aug 20 08:00:52 Triborough ovpn-client[13991]: /sbin/ip addr add dev tun0 local 10.8.0.6 peer 10.8.0.5
Aug 20 08:00:52 Triborough ovpn-client[13991]: /sbin/ip route add 10.8.0.1/32 via 10.8.0.5
Aug 20 08:00:52 Triborough ovpn-client[13991]: Initialization Sequence Completed
cb@Triborough:~$

```

Client networking:
```

$ ifconfig tun0
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.6  P-t-P:10.8.0.5  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:17828 (17.8 KB)


cb@Triborough:~$


$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlp2s0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 enp3s0
10.8.0.1        10.8.0.5        255.255.255.255 UGH       0 0          0 tun0
10.8.0.5        0.0.0.0         255.255.255.255 UH        0 0          0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 virbr0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlp2s0
192.168.122.0   0.0.0.0         255.255.255.0   U         0 0          0 virbr0
cb@Triborough:~$

```



[1]
[https://help.ubuntu.com/lts/serverguide/openvpn.html](https://help.ubuntu.com/lts/serverguide/openvpn.html)



EDIT:
I tried setting it up in the Network Manager GUI, telling the WiFi connection to connect through the VPN connection I added. But when I activate it I lose access to the internet, & the WiFi tray icon turns blue [2].

[2]
[https://imgur.com/a/Zs9Bn](https://imgur.com/a/Zs9Bn)

---

### Post by accounts0 on 2017-08-20
I've finished the steps outlined, but can't ping the server.

Started a new thread: [https://ubuntuforums.org/showthread.php?t=2369218&p=13678156#post13678156](https://ubuntuforums.org/showthread.php?t=2369218&p=13678156#post13678156)

---

### Post by darkod on 2017-08-20
1. Is the firewall on the server allowing ping requests over the vpn tunnel?

2. I haven't used NM to connect to openvpn, I simply use text conf files in /etc/openvpn on the client side. For me it works much better.

---

### Post by darkod on 2017-08-20
Why did you open a new thread, you should have continued here... You can ask an admin to merge it to this one.

---

### Post by accounts0 on 2017-08-20
> **darkod said:**
> Why did you open a new thread, you should have continued here...
 Since the title of this thread no longer applies. Seems a whole new thing.

---

### Post by wildmanne39 on 2017-08-20
I went ahead and merged the two threads.

---

### Post by darkod on 2017-08-20
Well it is still more or less the same topic, plus we don't even now right now if the issue is with networking or not. So, please check what is now my post #7 in this thread and give us more info.

---

