---
title: "OpenVPN with no leaks"
date: 2016-11-16
forum: Security
---

### Post by 0x656b694d on 2016-11-16
Hello,

I'm trying to setup an OpenVPN connection on a PC behind a router with custom routing to allow incoming SSH connection from the Internet.

I'm going to describe my adventures in the hope you'll spot a problem and/or suggest a solution.

If I just take the .ovpn file provided by the VPN service and import it to the Network Manager I get IPv6 and DNS leaks. Moreover I cannot provide any up and down scripts.

My PC is behind a router on which I have set up port forwarding for SSH. With no VPN I can easily access my PC from the Internet, under VPN sshd doesn't respond.

[LIST]
[*]No use of NetworkManager
[INDENT]When setting up an OpenVPN connection with NetworkManager it does not update /etc/resolv.conf. So some clients would use the default DNS set up for the principal interface (enp3s0) and not for the VPN tunnel.

Solution: automatic connection using specified configuration:

/etc/default/openvpn:
```
AUTOSTART="myvpn"

```
/etc/openvpn/myvpn.conf:
```
# ...
# vpn configuration provided by my VPN service
# ...
auth-user-pass login.conf
script-security 2
up /etc/openvpn/custom.sh
down /etc/openvpn/custom.sh

```

/etc/openvpn/login.conf:
```

username
password

```

/etc/openvpn/custom.sh:
```
#!/bin/sh

[ "$script_type" ] || exit 0

case "$script_type" in
  up)
  ip rule add from 192.168.1.10 table vpn
  ip route add table vpn to 192.168.1.0/24 dev enp3s0
  ip route add table vpn default via 192.168.1.1

  ;;
  down)
  ip rule del from 192.168.1.10 table vpn
  ip route del table vpn to 192.168.1.0/24 dev enp3s0
  ip route del table vpn default via 192.168.1.1
  ;;
esac

/etc/openvpn/update-resolv-conf "$@"

```
[/INDENT]
  
[*]IPv6 leak
[INDENT]
[http://ipv6leak.com/](http://ipv6leak.com/) shows my real address

Solution: make the IPv6 in NetworkManager "Link-Local only"
[/INDENT]
[*]DNS leak
[INDENT]
[http://dnsleak.com/](http://dnsleak.com/) still shows the VPN DNS server and the DNS server of the principal interface which I don't trust.

/etc/resolv.conf is updated by NetworkManager:
```

nameserver <VPN DNS server 1>
nameserver <VPN DNS server 2>
nameserver 127.0.1.1

```

Solution: ?

[/INDENT]

[/LIST]

So it works almost: I get OpenVPN connected automatically and the routes for ssh are put in place.
But the locally running DNS server redirects requests to the primary DNS of the principal interface.

How do I solve this? Can I reconfigure the 127.0.1.1 somehow upon OpenVPN connection?

Thanks.

---

### Post by SeijiSensei on 2016-11-16
I'm not sure how you would stop DNS queries from being "leaked." 

Let's suppose you go the route of installing BIND9 on the client machine to make it your own self-contained DNS server.  It would still need to query the root nameservers in the clear to resolve names.  The queries would exit from the remote end of the VPN connection, but after that they would be visible. 

If there are certain hosts you visit that you would like to keep private, then add them to /etc/hosts and avoid DNS queries altogether.  I assume most queries don't fit that requirement.

---

### Post by 0x656b694d on 2016-11-17
My VPN provider gives me 2 DNS servers to use and they are put into /etc/resolv.conf. If I install a local BIND9, it would just redirect the queries to the DNS of the VPN service, and not of my ISP (I suppose).
What I'm experiencing now is that by some reason some of the queries go via the 2 VPN DNS, but some others go via the third ISP DNS and the dnsleak.com can see my third DNS. Which is weird.
Thanks for the suggestion to put something to /etc/hosts, but I'm trying to find rather a generic solution.
I don't mind if the queries go out of VPN from the name of VPN's DNS server (that's the goal).

---

### Post by SeijiSensei on 2016-11-18
If you created a local DNS server, it would by default connect directly to the root name servers, not your VPN provider's or  ISP's servers.  That would happen only if the provider hijacks DNS queries or you use a "forwarders" directive in the BIND configuration.

I'm guessing the use of custom routing tables is designed to make sure all outbound traffic goes through the VPN?  Usually I just use a separate route directly to the VPN provider's IP then make the default gateway the upstream end of the VPN tunnel.  Suppose the VPN provider has public address 172.16.16.16, and the client has the address 10.10.10.10 on interface eth0 with gateway 10.10.10.1.  Let the VPN have upstream address 192.168.77.1. Then I'd add these routes
```

ip route add 172.16.16.16 via 10.10.10.1
ip route add default via 192.168.77.1

```
The first lets the traffic flow to the VPN provider out my router, while the second sends everything else through the tunnel.  I don't actually use this setup in practice because I don't care who sees my traffic.  But I have used that method and know that it works.

---

### Post by 0x656b694d on 2016-11-26
The use of my custom routes is to allow incoming connections from my router. In particular ssh: I want to be able to connect to my PC from the Internet even if it is connected to the VPN. So I'm creating a rule for outgoing traffic from my LAN IP (192.168.1.10) with two routes:
[LIST=1]
[*]for LAN connections (network 192.168.1.0/24) let's use the enp3s0 interface and not VPN
[*]use the router 192.168.1.1 as the gateway by default
[/LIST]
So now with the port forwarding I can connect to the sshd from the Internet.

I have dnsmasq automatically started by Network Manager and serving DNS queries on 127.0.1.1.

I'm still trying to understand what this dnsmasq is good for and how do I gracefully set it up to use only the DNS servers provided by the default interface (which get changed from time to time). If of course dnsmasq is actually the guilty one.

---

