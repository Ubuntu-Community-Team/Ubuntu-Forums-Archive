---
title: "Ideas for projects to do with an Ubuntu home server?"
date: 2009-08-24
forum: Server Platforms
---

### Post by nerr on 2009-08-24
Hey everybody, I've been tweaking my home server a lot lately and before I head off to college in a week or so here, I'd like to find another project or two to set up on it, for learning experience, or even just for fun.

I currently run on my server:
rsync (with bash scripts for network backup/sync of Windows machines)
Samba
CUPS
apcupsd
rTorrent
irssi
ClamAV
Subsonic
OpenSSH
Apache + PHP

That's all I can think of at the moment, but again, I'm always looking for something new to play around with, and if it could possibly be very beneficial to me, why not?  I'm basically just looking for some ideas to toy around with.  Some I have in my head include:

Domain Controller via Samba
OpenVPN
folding@home
Squid proxy server

But I'm sure there's more out there than just that.  Surprise me!  I'd really appreciate some ideas, and possibly some guides to help me along!  Thanks!

---

### Post by aesis05401 on 2009-08-24
Is your server going to be staying up at your house, going with you, or going dark?

---

### Post by nerr on 2009-08-24
Staying home, online as much as possible.  Probably 24/7 since I won't be screwing around with it too much since I won't have physical access to the box when I break my SSH server. :)

---

### Post by doas777 on 2009-08-24
openVPN would be very useful for hitting your resources from school. or route through your home network, should the need arise.
if you don;t do the samba domain controler, perhaps bind. I use a local bind server to resolve local machines, and forward to internet queries.

---

### Post by nerr on 2009-08-24
I'm not entirely sure how a VPN works, but I can grasp the concept of what it does by what the name implies: Virtual Private Network.  The last time I attempted to set one up using a guide in the community documentation, it broke my eth0 interface, which is bad news for a box with no video out, hahaha.  Is there a surefire way to get a VPN running, even if the guide is a little lengthy?  I'd like to experiment with it.

---

### Post by TaBaScO77 on 2009-08-25
This gives some good instructions on setting up OpenVPN:

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

That would be great if you want to access your home network remotely and securely.

---

### Post by aesis05401 on 2009-08-25
I don't know about OpenVPN specifically, but the number one thing you will want VPN for is piping any traffic that is being shaped, blocked,  or logged on your university network.

---

### Post by smeerbartje on 2009-08-25
You can also install SABNZBD, for usenet downloading...

---

### Post by FakeOutdoorsman on 2009-08-25
Here's a similar thread where SSH tunneling, Tor relaying, and virtualization are mentioned:

[Looking for more awesome things to do with ubuntu server](http://ubuntuforums.org/showthread.php?t=1214849)

---

### Post by doas777 on 2009-08-25
a vpn is a lot like a tunneled ssh connection, except that it operates at a lower layer of the protocol stack. a vpn connection makes your remote terminal look like it is a host on the local lan itself. 
If you have an ssh box, you can remote into it but you really just have a session on that server. you would not be able to hit any other resources on the private network unless you use the ssh server as a proxy. 

a VPN connected terminal actually appears to be on the local network (though it is not) so you can access all network resources directly.  

hope that helps

---

### Post by nerr on 2009-08-25
EDIT: OpenVPN is up and running, and I can connect to it using Windows Vista x64 using OpenVPN 2.1 rc19. :) Hurray!  Now to get out of my own house and test it!

---

### Post by nerr on 2009-08-25
Okay, now I can't seem to access any local services, even with the VPN connected.  iptables shouldn't be getting in the way, nor should my router since I'm connected via VPN to my server.  Any idea what the problem could be?  I just used the configurations specified in the Community Documentation for OpenVPN.

---

### Post by doas777 on 2009-08-25
> **nerr said:**
> Okay, now I can't seem to access any local services, even with the VPN connected.  iptables shouldn't be getting in the way, nor should my router since I'm connected via VPN to my server.  Any idea what the problem could be?  I just used the configurations specified in the Community Documentation for OpenVPN.

at work, if you connect to our network, and then vpn into the gateway as though you were in the feild, you loose all connectivity. it causes a serious loop in your network topology so it freaks out and exits. that should only happen if the vpn is connected though. naming resolution can also be a pain with dual homed hosts (as a vpn client naturally is). how are you trying to connect to what?

---

### Post by nerr on 2009-08-25
I'm using the OpenVPN client for Windows to connect to my Ubuntu Server box at home, and it's assigning me an IP address that I normally use on my home network for this machine.  The problem is that it doesn't seem to be forwarding any services such as Samba to me, and I'm not sure why.  Maybe it's because the remote network I'm on at the moment also has a Linksys router with similar features?  Could my traffic be getting lost with the traffic here?

---

### Post by doas777 on 2009-08-26
I think your client will have to be on another network (a router between both devices) from the network that your server is on. is that what your doing?

---

### Post by andrew.46 on 2009-09-02
Hi nerr,

> **nerr said:**
> I'm always looking for something new to play around with, and if it could possibly be very beneficial to me, why not?  I'm basically just looking for some ideas to toy around with. 

Have you though of running a proxy NNTP server such as leafnode-2? I run this one at home and once it is set it requires zero maintenance:

[Howto] Setup and use Leafnode-2 with the newsreader slrn
[http://ubuntuforums.org/showthread.php?t=676837](http://ubuntuforums.org/showthread.php?t=676837)

Just ignore all the slrn stuff :-).

Andrew

---

