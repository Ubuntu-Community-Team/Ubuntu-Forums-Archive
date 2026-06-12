---
title: "WLAN: possible attack, help"
date: 2010-11-29
forum: Security
---

### Post by oefuin on 2010-11-29
Hi!
I'm using ubuntu 10.04. I need some help with Internet security. Someone is trying to break into the network 24/7, I guess, using wide range of IPs starting with 184.  and using ports 40000 to 56000.  
My Firestarter events log looks like this:
[I]Time:Nov 29 13:42:51 Direction: Unknown In:wlan0 Out: Port:39321 Source:184.105.146.17 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov 29 13:49:01 Direction: Unknown In:wlan0 Out: Port:33263 Source:184.105.146.11 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov 29 13:49:01 Direction: Unknown In:wlan0 Out: Port:33264 Source:184.105.146.11 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov 29 13:49:45 Direction: Unknown In:wlan0 Out: Port:57348 Source:184.105.146.17 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov 29 13:49:45 Direction: Unknown In:wlan0 Out: Port:57347 Source:184.105.146.17 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown[/I]
I'm using 2WIRE wireless router, and I set up ISP firewall on “Maximum protection*–*Disallow unsolicited inbound traffic”, with MAC filtering option turned on, Stealth Mode, Block Ping, Strict UDP Session Control. 
Inbound and Outbound Control was set to disallow all inbound traffic, and allow outbound traffic only for  HTTP, HTTPS, 
FTP.
I wonder what these numberless hits mean and how to deal with them.
Any help would be greatly appreciated.
Thank you.
P.S. I captured packets on several occasions, using Wireshark, just in case. Please, let me know if that would help to determine what is going on.

---

### Post by CharlesA on 2010-11-29
Logs can make you paranoid.

If they aren't getting in, they can't do any damage.

Also, I'd suggest using GUFW or ufw instead of firestarter, since firestarter isn't being maintained anymore.

---

### Post by OpSecShellshock on 2010-11-29
Well, it doesn't appear that the traffic is being stopped by the router since it's hitting your computer. If the router is set to block unsolicited incoming traffic, then that might not describe what you're seeing. It's hard to say.

The IP addresses are from a site called vtunnel, which appears to be a proxy service. Is that something you use for web browsing, by chance?

---

