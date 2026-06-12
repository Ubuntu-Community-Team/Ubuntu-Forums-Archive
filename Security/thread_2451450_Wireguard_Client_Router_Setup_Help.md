---
title: "Wireguard Client Router Setup Help"
date: 2020-10-04
forum: Security
---

### Post by ligistx on 2020-10-04
I am attempting to set up an Ubuntu server wireguard VPN client router via a VM under ESXi in my homelab to better understand how this works; eventual deployment would be on my raspberry pi to allow devices connected to said pi to be routed through the VPN; basically a portable router that forces every device connected to it to be routed back to my server (also lives on my homelab) used when I travel for work. For current testing, I have a Ubuntu server VM set up at a family members house so I can have an alternate public IP to verify things work as expected.

Test setup:
Local LAN - 192.168.1.1
WG Server - 10.0.0.1
Virtual LAN for testing within my homelab - 10.0.0.2
Remote LAN 192.168.86.1
WG Server on an Ubuntu Server VM
WG Client on an Ubuntu Server VM

I have a wireguard connection set up, handshakes, public IP shows correct on my WG Client 

Current server setup is:
```

[COLOR=#ABB2BF][FONT=Hack][[/FONT][/COLOR][COLOR=#ABB2BF][FONT=Hack]Interface[/FONT][/COLOR][COLOR=#ABB2BF][FONT=Hack]]
[/FONT][/COLOR]PrivateKey[COLOR=#56B6C2]=[/COLOR][COLOR=#56B6C2]<[/COLOR]server[COLOR=#56B6C2]-[/COLOR]private[COLOR=#56B6C2]-[/COLOR][COLOR=#98C379]key[/COLOR][COLOR=#56B6C2]>[/COLOR]
Address[COLOR=#56B6C2]=[/COLOR][COLOR=#56B6C2]<[/COLOR]10.0.0.1[COLOR=#56B6C2]>[/COLOR][COLOR=#56B6C2]/[/COLOR][COLOR=#56B6C2]<[/COLOR]8[COLOR=#56B6C2]>[/COLOR]
SaveConfig[COLOR=#56B6C2]=[/COLOR]true
PostUp [COLOR=#56B6C2]=[/COLOR] iptables [COLOR=#56B6C2]-[/COLOR]A FORWARD [COLOR=#56B6C2]-[/COLOR]i wg0 [COLOR=#56B6C2]-[/COLOR][COLOR=#C678DD]j[/COLOR] ACCEPT; iptables [COLOR=#56B6C2]-[/COLOR][COLOR=#C678DD]t[/COLOR] nat [COLOR=#56B6C2]-[/COLOR]A POSTROUTING [COLOR=#56B6C2]-[/COLOR][COLOR=#C678DD]o[/COLOR] [COLOR=#56B6C2]<[/COLOR]eth0[COLOR=#56B6C2]>[/COLOR] [COLOR=#56B6C2]-[/COLOR][COLOR=#C678DD]j[/COLOR] MASQUERADE;
PostDown [COLOR=#56B6C2]=[/COLOR] iptables [COLOR=#56B6C2]-[/COLOR]D FORWARD [COLOR=#56B6C2]-[/COLOR]i wg0 [COLOR=#56B6C2]-[/COLOR][COLOR=#C678DD]j[/COLOR] ACCEPT; iptables [COLOR=#56B6C2]-[/COLOR][COLOR=#C678DD]t[/COLOR] nat [COLOR=#56B6C2]-[/COLOR]D POSTROUTING [COLOR=#56B6C2]-[/COLOR][COLOR=#C678DD]o[/COLOR] [COLOR=#56B6C2]<[/COLOR]eth1[COLOR=#56B6C2]>[/COLOR] [COLOR=#56B6C2]-[/COLOR][COLOR=#C678DD]j[/COLOR] MASQUERADE; 
[COLOR=#ABB2BF][FONT=Hack]ListenPort [/FONT][/COLOR][COLOR=#56B6C2][FONT=Hack]=[/FONT][/COLOR][COLOR=#D19A66][FONT=Hack]51820
[/FONT][/COLOR]
```

Current client setup is:
```

[Interface]
PrivateKey [COLOR=#56B6C2]=[/COLOR] [COLOR=#56B6C2]<[/COLOR]client[COLOR=#56B6C2]-[/COLOR]private[COLOR=#56B6C2]-[/COLOR][COLOR=#98C379]key[/COLOR][COLOR=#56B6C2]>[/COLOR]
Address [COLOR=#56B6C2]=[/COLOR] [COLOR=#56B6C2]<[/COLOR]client[COLOR=#56B6C2]-[/COLOR]ip[COLOR=#56B6C2]-[/COLOR]address[COLOR=#56B6C2]>[/COLOR][COLOR=#56B6C2]/[/COLOR][COLOR=#56B6C2]<[/COLOR]subnet[COLOR=#56B6C2]>[/COLOR]
SaveConfig [COLOR=#56B6C2]=[/COLOR] true

[Peer]
PublicKey [COLOR=#56B6C2]=[/COLOR] [COLOR=#56B6C2]<[/COLOR]server[COLOR=#56B6C2]-[/COLOR]public[COLOR=#56B6C2]-[/COLOR][COLOR=#98C379]key[/COLOR][COLOR=#56B6C2]>[/COLOR]
Endpoint [COLOR=#56B6C2]=[/COLOR] [COLOR=#56B6C2]<[/COLOR]server[COLOR=#56B6C2]-[/COLOR]public[COLOR=#56B6C2]-[/COLOR]ip[COLOR=#56B6C2]-[/COLOR]address[COLOR=#56B6C2]>[/COLOR]:[COLOR=#D19A66]51820[/COLOR]
AllowedIPs [COLOR=#56B6C2]=[/COLOR] [COLOR=#D19A66]0.0[/COLOR][COLOR=#56B6C2].[/COLOR][COLOR=#D19A66]0.0[/COLOR][COLOR=#56B6C2]/[/COLOR][COLOR=#D19A66]0
[/COLOR]
```

Once I have wireguard set up and working - which I do believe it is, its pretty easy to set up based on the above, I moved onto setup of my secondary interface which will be 10.0.0.2 and will receive DHCP and use the router I set up within the WG Client VM. I set this up via: [https://medium.com/@exesse/how-to-make-a-simple-router-gateway-from-ubuntu-server-18-04-lts-fd40b7bfec9](https://medium.com/@exesse/how-to-make-a-simple-router-gateway-from-ubuntu-server-18-04-lts-fd40b7bfec9)

With this second interface working, I spin up an ubuntu desktop VM on my homelab connected to the same virtual network as the WG Client second interface is connected to, DHCP works as expected, and I am even able to get iffy internet on the ubuntu desktop VM. I can google things, I can watch youtube, but things just don't quite work right, I can't download and install chrome for example, it tries, it hangs, it tries some more, but just doesn't really work. Speed tests do run very near line speed though...

I assume packets are not being routed through to the wireguard interface correctly, or something somewhere is not being translated. I though the "allowwedIP's being 0.0.0.0/0 would mean all traffic through the WG Client would be forced over the WG interface, but that is proving not to really work. I have tried some random iptables settings as well, but nothing really changes anything. I have seen the fact wireguard works with namespaces, but I am not quite sure how that works or how I would set that up for my needs. I know enough to know enough, but clearly not enough to get this working as intended.

Any ideas, or guides that could be followed for this exact situation? I have been at this for a couple days now and just can't get my head around it.

I am thinking this should be in the networking subthread, posted over there as well. If a mod sees this, I suppose the right thin to do is delete.

---

