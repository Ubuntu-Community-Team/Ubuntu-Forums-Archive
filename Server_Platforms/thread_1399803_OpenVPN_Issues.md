---
title: "OpenVPN Issues"
date: 2010-02-06
forum: Server Platforms
---

### Post by Uiop on 2010-02-06
I've been pulling my hair out over this all day now, and I don't appear to have gotten any closer to a solution.  I am running Ubuntu 9.10 server and would like to install OpenVPN in bridged mode on it.  All of my computers are plugged into a single, generic WiFi router.  The IP address of the WiFi router is 192.168.18.1 and it gives out IP addresses (formatted like 192.168.18.x) to connected devices via Static DHCP.

I have managed to establish an OpenVPN connection between another computer on my network and the OpenVPN server (using the public IP address given to me by my ISP, with appropriate port forwarding set up).  Unfortunately, I am unable access the internet at large while connected.  I **am** able to connect to other computers within the network however.

**[irrelevant configuration files clipped for brevity]**

What am I doing wrong?  I'm getting no error messages that I can see!  Any help would be very much appreciated.

---

### Post by noway2 on 2010-02-06
In your configuration file, you have the DHCP option set push "redirect-gateway def1 bypass-dhcp".  In theory this will cause all network traffic, including basic internet to go through the VPN.  Are you sure that this is what you want?  Normally, only network directed traffic goes to the VPN and normal browsing goes to the local link?

Personally, I have tried this option, but have not gotten it to work either and have the same result - no error, no connection.  I am curious as to your solution, assuming you get one.

---

### Post by Uiop on 2010-02-06
> **noway2 said:**
> In your configuration file, you have the DHCP option set push "redirect-gateway def1 bypass-dhcp".  In theory this will cause all network traffic, including basic internet to go through the VPN.  Are you sure that this is what you want?  Normally, only network directed traffic goes to the VPN and normal browsing goes to the local link?

Personally, I have tried this option, but have not gotten it to work either and have the same result - no error, no connection.  I am curious as to your solution, assuming you get one.

One of the things that I plan to use the VPN for is secure internet connections from WiFi hotspots.  In order for that to work, I need to tunnel all network traffic over the VPN.

Could my problems be related to my testing environment?  After all, the OpenVPN software is not designed for both the server and client being on the same LAN...  How would I go about testing my VPN configuration without actually attempting to connect from another location?

---

### Post by noway2 on 2010-02-07
If your primary concern is being able to securely connect via WIFI hotspots, a much easier solution is to use SSH to create a SOCKS proxy.  To do this, simply enter the command: SSH -NCD port user@domain.  Then in your browser, set it to proxy through the SOCKS proxy on 'port'.  You can even tell it to do remote DNS lookups, so that even that information will be handled via the remote server.  In Firefox you can get to this through the about:config page.  

There will be a slight performance penalty using the proxy, but it will be far less than using the VPN method.  The C flag will also compress the data stream improving performance a little bit.

---

### Post by Uiop on 2010-02-07
> **noway2 said:**
> If your primary concern is being able to securely connect via WIFI hotspots, a much easier solution is to use SSH to create a SOCKS proxy.  To do this, simply enter the command: SSH -NCD port user@domain.  Then in your browser, set it to proxy through the SOCKS proxy on 'port'.  You can even tell it to do remote DNS lookups, so that even that information will be handled via the remote server.  In Firefox you can get to this through the about:config page.  

There will be a slight performance penalty using the proxy, but it will be far less than using the VPN method.  The C flag will also compress the data stream improving performance a little bit.

Thank you for your reply.  Secure hotspot browsing is not my only anticipated use of the VPN--I will also need to interact with computers on my local LAN.

---

### Post by noway2 on 2010-02-08
Ok, I understand.  If you do get this feature to work through the VPN, please post the solution here.  I think this is a problem that many have been banging their head against.

---

### Post by Uiop on 2010-02-09
I have managed to solve this problem.  By attempting to connect to the VPN from outside the LAN instead of inside, and by tweaking my WiFi router's firewall settings, I was able to browse the internet and access my local LAN via my very own OpenVPN server.

Thank you to noway2 for attempting to render assistance!

---

### Post by noway2 on 2010-02-09
Would you be willing to post the openvpn configuration files so that others can compare against theirs and possibly see what you got right and they got wrong?

---

### Post by noway2 on 2010-02-09
I seem to have resolved the issue through trial and error.  The problem was in the line defining the server-bridge.

I gather that the line should be as follows:
server-bridge <address of the gateway(?) or network> <net mask> <start allocated ip> <end allocated ip>

I didn't have the start of the network, which includes the gateway in this setting. I got the clue as to what the problem was when I tried pinging google.com and it said that the host was unreachable, but yet I could ping any of the PCs on my home lan.

---

