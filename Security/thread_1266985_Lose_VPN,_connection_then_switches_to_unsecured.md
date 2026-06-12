---
title: "Lose VPN, connection then switches to unsecured"
date: 2009-09-15
forum: Security
---

### Post by Bakoo on 2009-09-15
I'm running Ubuntu 64 bit, and I have a new VPN service I've been using for about a week for bittorrent.  About once per day, I lose the VPN and the connection automatically switches to the regular unsecure mode.  Is there any way I can prevent an unsecured connection from being started once I lose the VPN?  The service is worthless as it now stands.  Help appreciated!

---

### Post by The Cog on 2009-09-16
All I can think of is to configure iptables to only allow the VPN traffic out over your normal network connection. The easiest way is probably to block outgoing traffic to everything except your VPN server's IP address. You may need to allow UDP port 53 (DNS) queries out as well though. Just block this traffic on eth0 or wlan0 or whatever. Don't block the tunnel interface.

---

### Post by Bakoo on 2009-09-18
I never thought of the firewall option.  Thank you!

---

### Post by The Cog on 2009-09-18
Glad to be able to help.

A background task checking the interface status every minute and restarting the vpn if needed might come in handy too.

---

### Post by Bakoo on 2009-09-22
The firewall is the way to go with this.  My IP on my system will be the same with or without the VPN connection, however.  I don't really know how to do the blocking with a firewall.  I tried with my router's firewall, just blocking about everything both to and from WAN/LAN

TCP/UDP IP range 0.0.0.0 to 93.182.255.0  ports 0-65000
                     range 93.255.255.0 to 192.167.255.0  ports 0-65000
                     range 192.168.255.255 to 255.255.255.255  ports 0-65000

Nothing changed.  I don't know what I did wrong.  I can still access everything with the VPN off.  I don't understand this.  

I haven't a clue as to what to do with the Linux firewall settings.  I have Firestarter installed, but with the same IP on the computer for both the VPN and non-VPN connection, I don't know what to block.  With the router firewall, I can leave the VPN tunnel open and access to the router & modem, but with the Linux firewall, if I block specific ranges like above, I should also be blocking most access to the internet even through the VPN tunnel. 

I did some searches online for Ubuntu firewall tutorials and the like, but nothing mentions anything like this.

???

---

### Post by Bakoo on 2009-09-23
Got the router firewall working.  According to SwissVPN (I'm not subscribing yet), a router firewall, not a software firewall, is what should be used for this.

---

