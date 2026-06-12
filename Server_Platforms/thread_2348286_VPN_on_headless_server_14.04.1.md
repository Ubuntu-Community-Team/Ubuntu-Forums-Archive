---
title: "VPN on headless server 14.04.1"
date: 2017-01-02
forum: Server Platforms
---

### Post by fredfillis on 2017-01-02
Am pretty much a noob to this topic, so please excuse my ignorance.

I have a small home network behind a router. Most of my machines are Windows based but I have one machine that I set up a few years ago with ubuntu server 14.04.1 which acts purely as a media server for the other machines on my network. I would like to employ a VPN client on that machine only while still being able to stream media files to my home network. In theory, that sounds easy enough. My previous experience with VPN has been that a "tunnel" is set up through the existing internet connection. In this case, my router is connected to the internet, the router allocates an IP address to my ubuntu server, say 192.168.1.100. Other machines on the network are able to stream files from that IP address. 

However, I've read some other sites where it is clear that some users have issues with this set where local machines can't find the "server" after the vpn connection was established on the server machine. If I install a VPN client on the ubuntu server machine, I don't see why any other machines on my home network would not be able to see the ubuntu server IP address any longer. I don't want all my machines on the VPN for various reasons, not the least of which is being able to connect to my workplace.

The VPN service I was looking at using is ExpressVPN which uses OpenVPN. 

Am I likely to have issues with clients on my network finding my media server IP address if the media server is running a VPN connection at the same time?

---

### Post by darkod on 2017-01-02
Do you plan the vpn tunnel to become default internet gateway for the server? I agree with you in that establishing a vpn connection should not prevent your other LAN clients to reach your server on its LAN private IP.

However I am not sure if that is true in the scenario where all traffic is routed through the vpn. In such case there might be issues because the server might send traffic destined for the LAN out through the vpn tunnel. But even in this case you should be able to sort that out easily with a static route telling to server to route 192.168.1.0/24 on its standard interface, not the vpn tunnel.

I guess you will have to give it a shot and try... :)

---

### Post by fredfillis on 2017-01-02
Hey darkod, thanks for taking the time. No, I don't plan on routing all traffic through the VPN. If I wanted to do that, I would just implement the VPN on my router. My "server" is just another client on my LAN that happens to have Ubuntu server installed. 

I will give it a try. Seems to me that with my router handling DHCP this should work with no impact on other clients :)

---

### Post by darkod on 2017-01-03
Well, you can still have your LAN using standard internet through the router but a specific machine/server in your home to be connected over vpn and route all its traffic through it. That's the scenario I was referring to. :)

Because that depends on the setup on the vpn server. So when the client connects it does not have a choice really if the vpn server sends an order routing to be changed making the vpn tunnel default.

---

