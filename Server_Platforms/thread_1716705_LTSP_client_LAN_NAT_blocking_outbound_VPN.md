---
title: "LTSP client LAN NAT blocking outbound VPN?"
date: 2011-03-28
forum: Server Platforms
---

### Post by InterpreDemon on 2011-03-28
Hi - Fairly new to Linux/Ubuntu, but have set up a nice LTSP network for the home (tired of hearing "my computer froze" with the Gates boxes) using Maverick on an IBM x346 server and multiple diskless Dell SX260's for the clients. I also run my own legacy XP box on the LTSP LAN for legacy apps like Quickbooks, etc., as well as to service some clients. It is slick, and definitely a bullet-proof way to keep the wife and kids out of trouble.

While I thought the router and NAT on the server were working perfectly gaining Web access for my XP box, browsing, mail, ssl banking, etc., I just discovered I cannot complete a Windows client VPN connection via the LTSP LAN... no problem connecting from the other side of the server, no problem pinging the remote VPN server from the LTSP LAN, in fact when I attempt the connection it sees and initiates the connection to the remote VPN server but just hangs at validation. Plug into the higher level LAN (the internet router) and no problem at all. Firewall not running in the server, so ports should not be an issue.

So the question is does anybody have any experience with encapsulation or port blocking issues in the double-interface LTSP DHCP/NAT environment? I could understand the head-scratching if I was trying to set up IpSec, but Windows VPN server/client is generally the least sensitive to router/firewall issues and I just cannot figure out why this one ain't working. It definitely smells like an encapsulation issue to me... sees the server, authenticates but cannot build the tunnel.

TIA

---

### Post by InterpreDemon on 2011-03-31
***[COLOR=Red][SIZE=4]Anybody??[/SIZE][/COLOR]***

---

