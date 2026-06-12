---
title: "VPN server with windows clients?"
date: 2013-06-17
forum: Server Platforms
---

### Post by kevinxsalerno on 2013-06-17
Hi, I am trying to setup a VPN connection from a windows client to my Ubuntu Server 12.04 at a different location.


Basically I want Windows clients to be able to connect via the 'new VPN connection wizard' in the control panel, I don't want any special programs or anything.

Then, after creating the VPN connection, I want to be able to access my samba folders over the VPN.

Can someone please tell me what I need to install in order for this to work? openVPN access looked pretty good, except that I have to pay for each client.

I need a tutorial too, if need be.

(Kind of confused if I need to setup anything different, given that the server already accepts SSH connections.)

---

### Post by volkswagner on 2013-06-17
I don't know of any free VPN servers which will allow connections pptp or other through control panel.

As far as OpenVPN, you do not need to pay for client software, but it does need to be installed on each client.

I'm very happy with openVPN server and client software for Windows and Mac OSX.  I run the server on my router, WNDR 3800.

---

### Post by kevinxsalerno on 2013-06-17
The certificate side of the VPN stuff confuses me, how can I just set my server up so that clients can just login with a username and password and then have access to the server as if it was in a LAN?

New to VPNs, bad with the terminology.

---

### Post by volkswagner on 2013-06-17
Well this is kind of old but it may get you started.  

[http://opensourcehacker.com/2011/10/23/set-up-pptp-virtual-private-network-vpn-server-on-ubuntu-linux/](http://opensourcehacker.com/2011/10/23/set-up-pptp-virtual-private-network-vpn-server-on-ubuntu-linux/)

What version of Ubuntu Server are you running?

Certificates are good to know for making secure connections.  Check out some of the [how to's]("http://wiki.openwrt.org/doc/howto/vpn.openvpn") on openwrt.org.

---

### Post by sandyd on 2013-06-17
PPTP and MSCHAP v2 is insecure.
[http://www.net-security.org/secworld.php?id=13342](http://www.net-security.org/secworld.php?id=13342)

---

### Post by 3L33T on 2013-06-18
> **kevinxsalerno said:**
> Hi, I am trying to setup a VPN connection from a windows client to my Ubuntu Server 12.04 at a different location.  Then, after creating the VPN connection, I want to be able to access my samba folders over the VPN.


What * access * do your users require?   Do they just simply need to read files from your samba folders? or do they need both read-and-write access to your samba folders?

Either way, try this tutorial: [using samba share over SSH]("http://simonholywell.com/post/2009/04/samba-file-share-over-ssh-tunnel.html")

---

### Post by SeijiSensei on 2013-06-18
Where are these users located?  Are they in a LAN?  If so, it would be much simpler to install a copy of OpenVPN on the remote machine and drop an old PC into the local network with another copy of OpenVPN.  Then you can set up a [static-key tunnel]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") between the old PC and the remote server, and configure your router to send traffic for the remote server to the old PC for forwarding.  Unless you need to support roaming users, this is a much simpler solution than the certificates and such required to support multiple individual client machines.

I use this setup here in my home office.  I have a PC that connects via OpenVPN to my Linode server out in the cloud.  My router has a static route that forwards traffic for the Linode server to the PC.  Because the OpenVPN hosts use an entirely different network subnet from the rest of my network, this is easy to configure in the router.  I just send all packets with addresses in 10/8 to the PC.  The rest of my hosts have addresses in 192.168/16.

---

### Post by kevinxsalerno on 2013-06-18
> **3L33T said:**
> What * access * do your users require?   Do they just simply need to read files from your samba folders? or do they need both read-and-write access to your samba folders?

Either way, try this tutorial: [using samba share over SSH]("http://simonholywell.com/post/2009/04/samba-file-share-over-ssh-tunnel.html")

They need read-write access to the samba folders, that is all.

Thanks, I'll check it out.

> **SeijiSensei said:**
> Where are these users located?  Are they in a  LAN?  If so, it would be much simpler to install a copy of OpenVPN on  the remote machine and drop an old PC into the local network with  another copy of OpenVPN.  Then you can set up a [static-key tunnel]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html")  between the old PC and the remote server, and configure your router to  send traffic for the remote server to the old PC for forwarding.  Unless  you need to support roaming users, this is a much simpler solution than  the certificates and such required to support multiple individual  client machines.

I use this setup here in my home office.  I have a PC that connects via  OpenVPN to my Linode server out in the cloud.  My router has a static  route that forwards traffic for the Linode server to the PC.  Because  the OpenVPN hosts use an entirely different network subnet from the rest  of my network, this is easy to configure in the router.  I just send  all packets with addresses in 10/8 to the PC.  The rest of my hosts have  addresses in 192.168/16.

They need to access the server via roaming. They use laptops and travel very often.

---

### Post by loyhz2ayj-jeff on 2014-05-20
I'm not sure how much more clear the original poster could be.  The requirements are these:

#1 Windows Client
#2 No extra client software permitted.. just what comes with windows.

The answer is either a yes or no - Can it be done with Ubuntu or not? Are we again making the fatal mistake of thinking the customer doesn't know what he wants?

---

### Post by spynappels on 2014-05-20
Please don't resurrect nearly year old threads, the OP received some suggestions which he said he'd investigate.

---

### Post by QIII on 2014-05-20
Necromancy closure.

---

