---
title: "Iptables help"
date: 2018-01-26
forum: Server Platforms
---

### Post by batta-daniel91 on 2018-01-26
Hi!

I want to run openvpn on my home server. I configured the openvpn server and now it's work.
But I don't have access to the 80 port from my LAN network.

I'm using [THIS]("https://linode.com/docs/networking/vpn/tunnel-your-internet-traffic-through-an-openvpn-server/") tutorial to configure my iptables.

Anyone can help me how can I access my web server and tunnel my internet traffic through vpn?

Thank!
Daniel

---

### Post by darkod on 2018-01-26
That tutorial is for the openvpn server to serve as gateway for the openvpn client machine.

Are you trying to access port 80 of the openvpn server, or just browse any internet website using the server as your gateway?

---

### Post by batta-daniel91 on 2018-01-29
I try to access the 80 port of the OpenVPN server from LAN or from VPN

---

### Post by darkod on 2018-01-29
In that case you need a rule allowing port 80 for traffic coming into the vpn tunnel tun0. At the moment you have no such rule. Something like:
```
-A INPUT -p tcp -i tun0 --dport 80 -j ACCEPT
```

---

### Post by batta-daniel91 on 2018-01-29
Thanks!

I tried it, but I still get connection refused message.

What does this part in the mean? What if I don't want limited HTTP access?

[COLOR=#228B22]# Allow DNS resolution and limited HTTP/S on eth0.
[/COLOR][COLOR=#A61717]-[/COLOR][COLOR=#658B00]A[/COLOR] INPUT -i eth0 -p tcp -m state --state ESTABLISHED --sport [COLOR=#B452CD]80[/COLOR] -j ACCEPT
[COLOR=#A61717]-[/COLOR][COLOR=#658B00]A[/COLOR] OUTPUT -o eth0 -p tcp -m state --state NEW,ESTABLISHED --dport [COLOR=#B452CD]80[/COLOR] -j ACCEPT
[COLOR=#A61717]-[/COLOR][COLOR=#658B00]A[/COLOR] INPUT -i eth0 -p tcp -m state --state ESTABLISHED --sport [COLOR=#B452CD]443[/COLOR] -j ACCEPT
[COLOR=#A61717]-[/COLOR][COLOR=#658B00]A[/COLOR] OUTPUT -o eth0 -p tcp -m state --state NEW,ESTABLISHED --dport [COLOR=#B452CD]443[/COLOR] -j ACCEPT

---

### Post by darkod on 2018-01-29
The rules in that tutorial are very restrictive. I suggest to use less restrictive rules unless you have good experience with iptables.

Even the OUTPUT traffic is blocked unless you allow it specifically. But looking at the rules again, tun0 traffic seems permitted (notice the section titled "Allow traffic on the TUN interface"). You just have to make sure your tunnel interface is really tun0.

Also access to the server from the LAN is another thing. You have to add other rules for that too. The access from/to the openvpn tunnel seems to be permitted though. So if you try accessing your openvpn server from a conected client (using the vpn IP, not LAN IP), it should work...

---

### Post by batta-daniel91 on 2018-01-29
I double check it and I can use the HTTP server from OpenVPN network. But from LAN side not. How can I make less restrictive the rules?
Now I see I'm unable to ssh from this server to another server on the LAN. 

If I use NEW state instead of ESTABLISHED it will be helping? Or I just don't need to use -m state --state NEW,ESTABLISHED?

---

### Post by darkod on 2018-01-30
Well, first I would start by setting ACCEPT policy to OUTPUT. I could never understood using REJECT for OUTPUT because in that case you have to have excellent overview which outgoing traffic you are using and allow it. Otherwise it is blocked by the REJECT.

That is why you cannot ssh from that server to another one. Even outgoing traffic is blocked.

If you want ao access anything on the server from any other LAN interface that is not eth0, you will need adequate rule for that interface.

Here is an example of basic rules I use on openvpn servers. You will need to add any specific rules that you want.
```
*filter
:INPUT DROP [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]

-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p udp --dport 8451 -j ACCEPT
-A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i tun0 -s 10.8.200.0/24 -j ACCEPT
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --set --name SSH
-A INPUT -i eth0 -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 4 --rttl --name SSH -j DROP
-A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT

COMMIT

*nat
:POSTROUTING ACCEPT [0:0]

-A POSTROUTING -o eth0 -s 10.8.200.0/24 -j MASQUERADE

COMMIT
```

---

### Post by batta-daniel91 on 2018-02-05
Thanks! Thats solve all my problems!

---

### Post by darkod on 2018-02-05
I'm glad it helped you. Please mark the thread as Solved. You can do that in Thread Tools above the first post.

---

