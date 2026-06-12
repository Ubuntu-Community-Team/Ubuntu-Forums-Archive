---
title: "Security for public internet connections, VPN?"
date: 2011-05-24
forum: The Cafe
---

### Post by deadimp on 2011-05-24
Is there a way that the VPN connection can be circumvented? Could someone be listening in on your network traffic as your authenticating with the VPN server and then use those credentials / receive the decryption info to continue looking at the packets passing by? And could they additionally store your credentials for the network to which you have connected?

I've been wondering about security with internet connections. I have some general paranoia, and just wanted to know if it is silly or if it is justified. I've read a few articles on the matter, and most of them state that you should try to stick to a VPN as much as possible.

---

### Post by tubezninja on 2011-05-24
It depends on the VPN connection and how it's configured

The most basic PPTP VPN connections have weak encryption or no encryption enabled at all, in which case, yes absolutely, everything being passed through the connection can be eavesdropped on.  There are also varying levels f this type of VPN connection with varying degrees of vulnerability: MSCHAPv1 and v2 are fundamentally insecure. while MPPE is rather weak.

(I realize this may be alphabet soup for you.  The bottom line is, PPTP VPN isn't all that great, though there are ways to use TLS encryption on it which makes it more secure.)

Then you have [IPSec]("http://en.wikipedia.org/wiki/IPsec") VPNs, which is Cisco's big thing.  This is a much more secure VPN, with end-to-end protection against various different types of attacks.  In this case, everything you do through your connection - even logging in to the VPN - is encrypted and secure.

One potential drawback of IPsec is that it's pretty easy for someone analyzing the data to know that you're using a VPN, and relatively easy to block this kind of traffic.  Not that they will be able to see what you're doing, but if you are trying to hide the fact that you're using a VPN at all, or if you're using a VPN to try to get around restrictions on a network (a censorship firewall, for instance),  your use of this kind of VPN will be easy to spot and block.

Personally, I like [OpenVPN]("http://www.openvpn.net/").  It's somewhat simpler than IPsec to get going once you have it set up, and you can get it going using a simple installation token.  it uses TLS/SSL encryption, and works really well in traversing NATs.  And the great thing is, if you have control of the VPN server, it's pretty straightforward to change the port it runs on.  You can even have it run on the same port (443) as an SSL website, making it difficult to ferret out or filter (unless your local network tyrant wants to block access to ALL online shopping, banking and secure webmail sites, among others).

---

### Post by CharlesA on 2011-05-24
I'm not sure about the VPN thing, but I've always tunneled my traffic over SSH if I'm using a public internet connection.

---

### Post by decoherence on 2011-05-24
ssh tunnel ftw.

---

### Post by Smilax on 2011-09-30
I use Arethusa free VPN

[http://arethusa.su/vpn.html](http://arethusa.su/vpn.html)

it uses OpenVPN TCP 

you don't have to give your details or have an account,

you can get the CA and Config files for the free server here

[http://bb.s6n.org/viewtopic.php?id=81](http://bb.s6n.org/viewtopic.php?id=81)

it's real easy to set up 


i like it, it's good

):P

---

