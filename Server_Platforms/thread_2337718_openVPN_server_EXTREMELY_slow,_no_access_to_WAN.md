---
title: "openVPN server EXTREMELY slow, no access to WAN"
date: 2016-09-21
forum: Server Platforms
---

### Post by David_Goguen on 2016-09-21
Hi everyone,


So this is going to be quite the long explanation. First of all, all the servers in question are running the latest version of Ubuntu Server 16.04.1 LTS. I successfully configured an openVPN server on the network at my parent's house a little while ago. The server is configured to run over UDP port 50, because most ports are blocked by my university, but this one is not. Everything works great: remote access to the network, access to the WAN appearing as if I'm surfing from the server's network's external IP, and I get full bandwidth (they have a connection with 20 Mbps upload and I'm able to transfer files between the server and a client remotely at a full 20 Mbps. Running a browser speed test also reveals full 20 Mbps bandwidth). On their network, I run two servers: the one hosting the VPN (which also acts as a file server, media server, and bind9 DNS server) at 192.168.1.100 and another server acting as a backup bind9 DNS server at 192.168.1.130. This is my configuration file, which as I said before, works perfectly:


```

port 50
proto udp
dev tun
ca ca.crt
cert gogudaserver.crt
key gogudaserver.key
dh dh2048.pem
server 192.168.35.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.1.0 255.255.255.0"
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 192.168.35.1"
push "dhcp-option DNS 192.168.1.130"
push "dhcp-option DOMAIN gogudanetwork.com"
client-to-client
keepalive 10 120
cipher AES-256-CBC
comp-lzo
comp-noadapt
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3

```


My iptables configuration is also as follows (output of iptables -S):


```

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -i p4p1 -p udp -m state --state NEW -m udp --dport 50 -j ACCEPT
-A INPUT -i tun+ -j ACCEPT
-A FORWARD -i tun+ -j ACCEPT
-A FORWARD -i tun+ -o p4p1 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i p4p1 -o tun+ -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -o tun+ -j ACCEPT

```


Now, here's the weird part. Now that I'm living away from my parents for school, I wanted to host another openVPN server at my apartment to give me access to my network at my apartment. Unlike at my parent's, I only have one server that acts as the openVPN server, file server, media server, bind9 DNS server and DHCP server at 192.168.2.100. I have literally copy and pasted the openVPN server config file from the other server to this one, along with the iptables rules, and modified as necessary. However, I just can't get the clients to use the VPN the way they're supposed to! They'll connect (Tunnelblick on OS X connects very slowly and often hangs at "authenticating", but the openVPN app on my phone connects within 3-5 seconds, so I think the connection is being made successfully and the Tunnelblick issue is a problem with my Mac or config file on the Mac, which I'll look into later), but then network traffic will slow to an almost halt no matter the client, judging by bytes in and bytes out. I'm then able to see other computers on the network and browse network shares (VERY slowly), but I have absolutely no access to the WAN. I thought that it might be a DNS issue (not sure if the openVPN daemon likes having the DNS server on the same server; this issue was probably avoided at my parent's house by also pushing the backup server to clients so the backup server can resolve WAN addresses), so I tried pushing 8.8.8.8 as a DNS server to the clients, at which point websites will attempt to load, but hang and bytes in/bytes out comes to almost a complete stop. I also tried pushing the route 192.168.35.0/24 to the clients with no success. I don't know what I'm doing wrong... everything works so perfectly on my parent's server with the EXACT SAME CONFIGURATION! These are my current config file and iptables rules on my server:


```

port 50
proto udp
dev tun
ca ca.crt
cert jupiterserver.crt
key jupiterserver.key
dh dh2048.pem
server 192.168.35.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.2.0 255.255.255.0"
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 192.168.35.1"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DOMAIN jupiternetwork.com"
client-to-client
keepalive 10 120
cipher AES-256-CBC
comp-lzo
comp-noadapt
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3

```


```

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -i p2p1 -p udp -m state --state NEW -m udp --dport 50 -j ACCEPT
-A INPUT -i tun+ -j ACCEPT
-A FORWARD -i tun+ -j ACCEPT
-A FORWARD -i tun+ -o p2p1 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i p2p1 -o tun+ -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -o tun+ -j ACCEPT

```


The config files for the clients were also made using the same one used for clients of my parent's network. I've also tried changing the port with no luck. The syslog doesn't show anything weird either (there was previously an error about TLS handshakes, but I remade all the certificates and it seems to have gone away). This just doesn't make sense to me... We both have the same ISP, even the same internet plan even, and we're even both using the same router (ASUS RT-AC55U) with port 50 forwarded correctly on the exact same firmware version. I'm absolutely stumped by this... hopefully someone else has some sort of idea as to what might be going on.

---

### Post by darkod on 2016-09-21
Why are you using the same 192.168.35.0/24 subnet for OpenVPN on both locations? It shouldn't matter unless you try to connect the same client to both sites. When you try to do that, it won't work correctly because it will not know to which 192.168.35.0/24 to refer to.

Golden rule with vpn: Always use different subnets on all sites.

That being said, you seem to have done the config correctly (although I only quickly glanced over it), I have no idea why the speed would be low. Do you also have good upload speed on your apartment internet connection? Don't forget that when pulling something from your home server that is actually upload from its point of view. If the connection upload is low (as with most ADSL for example), the connection will be terrible.

---

### Post by David_Goguen on 2016-09-21
> **darkod said:**
> Why are you using the same 192.168.35.0/24 subnet for OpenVPN on both locations? It shouldn't matter unless you try to connect the same client to both sites. When you try to do that, it won't work correctly because it will not know to which 192.168.35.0/24 to refer to.

Golden rule with vpn: Always use different subnets on all sites.

That being said, you seem to have done the config correctly (although I only quickly glanced over it), I have no idea why the speed would be low. Do you also have good upload speed on your apartment internet connection? Don't forget that when pulling something from your home server that is actually upload from its point of view. If the connection upload is low (as with most ADSL for example), the connection will be terrible.

I originally did have it on 192.168.36.0/24 but changed it to 192.168.35.0/24 to closer mimic the server at my parents house just in case it had something to do with that (I know the subnet most likely wasn't the reason, but I thought I'd try changing it because I was desperate, haha). Either way, I never plan on connecting to both networks at the same time, so it shouldn't be an issue.

My upload speed is exactly the same as my parents': 20 Mbps. And I get that when running a speed test from my network at the apartment, so I know it's not anything to do with a lack of upstream bandwidth.

---

### Post by darkod on 2016-09-21
I would drop the redirect-gateway and the DNS 192.168.35.1 options and restart openvpn on the server.

The redirect-gateway for me is a special use scenarios when you need the client to go out through the vpn server public IP. Do you really need this? Otherwise routing ALL traffic through the vpn will always introduce more latency and delays. Stick to only necessary traffic over the vpn.

The DNS 192.168.35.1 (or pushing any dns over the openvpn for that matter) is pointless unless you really need to use that private DNS servers of yours. And in such case push the server private IP in the 192.168.2.x range, not it's point-to-point vpn IP. It should work either way, but it's just one of the things you could try.

As for your iptables rules at the home server, you first set all policies to ACCEPT (INPUT, FORWARD and OUTPUT), so any rules after that are pointless. You never have a drop rule. Which is OK because you are on private LAN behind your home router/firewall. I'm just saying that those rules don't do anything in fact if all policies are ACCEPT.

However, what you do need is a MASQUERADE rule in the nat iptables table. Do you have that? You can check with:
```
sudo iptables -t nat -L -n -v
```

Also, have you enabled ipv4 forward in /etc/sysctl.conf? I assume you did, otherwise vpn shouldn't even work. You can check that also with:
```
cat /etc/sysctl.conf | grep forward
```

---

