---
title: "Connect phone to LAN from outside network"
date: 2016-02-24
forum: Server Platforms
---

### Post by johnnyslogan on 2016-02-24
Dear Ubuntu people,

Maybe this is not the correct forum for this, and if that is so, I apologize in advance. What is the easiest way to give my mobile phone (it's an Android) access to my local LAN from outside? I have an Ubuntu-based home server, I have a feeling I can somehow use that to make it happen? I was thinking something about OpenVPN, but not sure if that is the correct approach or even necessary. 

Best regards.

---

### Post by Bucky Ball on 2016-02-24
*Thread moved to **Server Platforms**.*

You'll probably have more luck here as you are trying to connect to your home server.

---

### Post by SeijiSensei on 2016-02-24
I run JuiceSSH on my Android phone to connect via SSH.  I forward a high port on the router back to port 22 on a machine running openssh-server.  I could set up OpenVPN, but I make these connections so infrequently that I haven't felt the need to invest the effort to get OpenVPN working on both devices.

---

### Post by johnnyslogan on 2016-02-24
> **SeijiSensei said:**
> I run JuiceSSH on my Android phone to connect via SSH.  I forward a high port on the router back to port 22 on a machine running openssh-server.  I could set up OpenVPN, but I make these connections so infrequently that I haven't felt the need to invest the effort to get OpenVPN working on both devices.

Thanks for the suggestion. However as I understand it, that would only give me SSH-access to the server. I would like complete access to the LAN, the server is on. And I think OpenVPN might be the way to go. I have found different guides, but I'm unsure whether they will actually give me access to the LAN or only reroute my Android-connection to the internet through the server. Any links/suggestions would be much appreciated.

---

### Post by SeijiSensei on 2016-02-24
OpenVPN is the right solution.  You'd need to run it on a box behind your router and forward a high port back to the OpenVPN machine.  If you have routing properly configured, you should be able to see all the machines on your network.  If you have applications that expect all the machines to be in the same subnet, like DLNA servers, then you could masquerade the phone connection so that all the traffic appears to come from the OpenVPN server even though some of it is heading back over the tunnel to the phone.

I only use OpenVPN for [simple point-to-point connections]("http://openvpn.net/static.html") between machines.  I have tunnels to my servers at Linode and to clients' networks.  I've avoided all the stuff about certificates and the like because it is overkill for my needs.  I haven't looked at the OpenVPN client for Android very closely to know whether it would work in a simple shared-key arrangement like I use with the other machines on my network.

---

### Post by johnnyslogan on 2016-02-24
Cheers, will look into it :)

---

