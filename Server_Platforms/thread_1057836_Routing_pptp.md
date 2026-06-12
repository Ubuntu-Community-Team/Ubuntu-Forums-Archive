---
title: "Routing pptp"
date: 2009-02-02
forum: Server Platforms
---

### Post by lucaspr on 2009-02-02
Hello,

I'm tryin to setup a pptp connection for my friends, so we can play a game together and share files if needed (mods for the game)

What I've got so far:

LAN <-> Server (Zimbra) **<-** Router <-> internet <-> pc friend 1
                                               <-> pc friend 2

explation of this figure :) and a little more detailed info :

- LAN : My lan network IP-range and subnet: 192.168.7.0/24

- Server: Configured Zimbra server (with Bind DNS) 192.168.7.254/24
 
On this server (hostname: luukserver) I configured a pptp-server which is working for the server, so no problem there. They can login and connect to this server fine. (webmin and pptpd)
Assigning IP addresses: 192.168.6.10/24 - 192.168.6.20/24

The problem is they cannot browse the network for obvious resons. The IP-range is differend, but if I configure to use the same IP-range as my LAN the connection can no longer be established.

I'm busy learning MCSA so I know a little about routing and routing tables. But how can I configure the routing table on my server in such a way my pptp clients can connect to the network?
And how can I make that route or that routes persistent?

**Found what I was looking for in another thread and reply below! Changes IP-ranges of the PPTP-clients.**

> 
Re: adding a persistent route
Hi there!

I was looking for the same thing and I think I found a better solution!
```

sudo vi /etc/network/interfaces

```

add your command here at the end of the file, eg

```

up route add -net 192.168.0.0 netmask 255.255.0.0 gw 10.0.0.1 dev eth0

```

Notice the 'up' part, it is important to include it before your command.

Thats it! Now you can restart the network to activate the changes
```

sudo /etc/init.d/networking restart

```

Client1: 

Now for my question.. 

This setup:

Client 1:  Remote LAN (192.168.1.0/24) <-> Draytek 2900 <-> IPSec VPN Tunnel <-> Zyxel NBG460N my LAN (192.168.7.0/24)
Client 1 can connect to my pc fine! (ping and game are no problem.) Lan-to-Lan tunnel!!

Client 2: Remote LAN (192.168.1.0/24) <-> Speedtouch 780 <-> PPTP VPN Tunnel <-> Zyxel <-> Server(192.168.7.241)
Client 2 can connect to the server but not to my pc..

So no network connection to my lan. IP-Range for my pptp clients are 192.168.7.60-70/24 

Which gateway should I use for the pptp routing. And does it matter that I already have a 192.168.1.0/24 remote LAN in my VPN connections? 
 
Is my assumption correct that I should add this to my networking interfaces file:
```

up route add -net 192.168.7.0 netmask 255.255.255.0 gw 192.168.7.241 dev ppp0

```

Any info on this one?

---

### Post by koenn on 2009-02-02
I thought that with pptp it would be common to assign the clients addresses in the LAN range. Then there would be no routing problems. Strange that this doesn't work, all pptp I've seen so far work this way. 

To solve the problem through routing, the client config of pptp (on your friends pc's) needs to contain a statement that your LAN 192.168.7.0/24 is reachable through the tunnel (or manually add a route through the ppp interface)

---

### Post by lucaspr on 2009-02-02
Well if it should work then  I must have done something wrong.. 

Guess I'll try again.. As I am installing multiple servers in VMWare Server 2 as part of my 'renewing' process. 

Which means no more then deleting my old server and installing 2 fresh virtual servers. One for Zimbra and the other for my filesharing, DNS, pptp, etc...

So new installation new chances of screwing things up :). But this time I'll have Snapshots to revert to if anything goes wrong!

But thanx for your info about the ranges! The IP-ranges of my friends are different (192.168.1.0/24 and 192.168.0.0/24) so that shouldn't be a (or the) problem. I'll try again and will let you know!

---

### Post by lucaspr on 2009-02-04
> **koenn said:**
> I thought that with pptp it would be common to assign the clients addresses in the LAN range. Then there would be no routing problems. Strange that this doesn't work, all pptp I've seen so far work this way. 

To solve the problem through routing, the client config of pptp (on your friends pc's) needs to contain a statement that your LAN 192.168.7.0/24 is reachable through the tunnel (or manually add a route through the ppp interface)

Ok, so I setup the pptp-server again and indeed the range is within my LAN IP-range! Thanks for the info!

Now the IP-range works but how to setup a persistent tunnel. 

One pptp-client has dropped, still a friend though :) , but I've got my Zyxel NBG460N to setup a IPsec VPN tunnel to a draytek 2900 router \\:D/. 

So only one left.. Is it possible to setup the routing only when the client connects? I certainly not a script-kiddy.. The only scripts I use I copy and paste from this forum ;).

Nevermind... Found another thread which I will look into first.. 
[http://ubuntuforums.org/showthread.php?t=38621](http://ubuntuforums.org/showthread.php?t=38621)

---

### Post by lucaspr on 2009-02-17
So as I am the only one replying in my thread...

I will give the answer to my problem.. (Thanks to this page [http://pigtail.net/nicholas/pptp](http://pigtail.net/nicholas/pptp)

It is a simple solution to my 'big' problem. Just edit the file /etc/sysctl.conf

Now find in /etc/sysctl.conf 
```

#net.ipv4.conf.default.forwarding=1

```

**And just delete the #**

That was all, problem solved. Now as I am a newbee/rookie/starter whatever you like to call it... This was something I didn't search for, or how can I better explain it, I didn't know what to search for until I accidentally came on the page mentioned above. 

So big thanks to the author !! Maybe this will help others in their search.

ps. Didn't anyone know this, except the author of that page? ;)

---

