---
title: "Networking Help"
date: 2015-11-18
forum: Server Platforms
---

### Post by clalian on 2015-11-18
Hello everyone,
This question is regarding Raspberry Pis, an Ubuntu server, and Windows machines.

I help some local organizations with their computer system administration.
Altghouh I can use TeamViewer, I am looking for a different way.
Maybe you guys can help me plan it out?

I have various Raspberry Pis (rPi), which I have configured to auto-connect to a VPN server I have setup in a small VPS instance.
So if I power up the rPi, and it has internet, it connects to the VPN server.

I would like to install on-site one of the rPis, and have it connect to my VPN server.
Then, from wherever I am, I can connect to the VPN server, and then ssh into the on-site rPi.

For TeamViewer replacement, I though of installing VNC (something like TightVNC) on the Windows machines.

That's where I have doubts.
How can I... "jump" from my machine in my office to that VNC session on-site?
I can ssh into the VPN server, and from there ssh into the on-site rPi.

Yet how can I "forward" the VNC session info?
Or would you do it a different way?

Thank you!

---

### Post by TheFu on 2015-11-18
Just use ssh.

If you use any VNC server, be certain to start it with the -localhost option.  This way non-secure connections aren't allowed. ssh tunnels are pretty easy. Must be thousands of "how-to" articles on the internet.

I wouldn't bother with a vpn if only ssh is planned.  ssh with key-based authentication and fail2ban is plenty secure for government use. Running ssh through a vpn is double-encryption and it will be slow.

---

### Post by Bucky Ball on 2015-11-18
*Thread moved to **Server Platforms**.*

You'll have better luck here with those questions. Good luck. :)

---

### Post by darkod on 2015-11-19
The OP is mentioning vnc in context of connecting to windows machines. You can't use ssh for that, not unless you start playing with cygwin and that is not full windows administration either...

One way to do it would be to connect the windows machines to the vpn too. That way you can connect to them directly from your desktop vnc GUI and the connection is secure. If you are using OpenVPN there is windows client for it, and I believe it can be made to autostart on boot.

Another way would be to set up port forwarding on the remote location router which will forward one vnc port to a single windows machine of your choice. Then you can connect to it using the public IP. Once you are connected to one machine, you can use vnc for any other in the local network. But be very careful to read about securing vnc for external access.

---

### Post by TheFu on 2015-11-19
Just reread the OP and don't see anything clear except multiple rPi machines and VPN between them. Could have missed something.  It isn't clear (at least to me) which machines he wants inbound to and which he wants outbound from.

ssh can be used as a pivot point once the connection is made from inside a secure network. 
"Something" --> rpi (via ssh) --> rpi (VNC) --> Windows?
or
Windows --> rpi (via ssh) --> rpi (VNC) --> "Something"?

If Windows is not involved, there are many other solutions. Also, it is possible to use an RDP session over ssh or openvpn or from inside some other remote desktop like x2go.  I travel with a chromebook running Ubuntu. From there I'll x2go back to my normal desktop at home, then from there, use rdp to a Windows machine.  The unencrypted RDP connection actually never hits any networking because both my desktop and Windows run inside the virtual server. There is a tiny danger that traffic could be sniffed, but only by the VM hostOS, not by anyone on the network and definitely not anyone on the internet.

If you use openVPN, it is possible to make a bridge between the two networks.  Don't do this without written approval. Many workplaces would terminate someone over this.

Regardless, perhaps some more clarity on the true systems layout is needed?

---

### Post by clalian on 2015-11-19
Hello everyone!
Thanks for the replies... very much appreciated!

The reason I want to install the rPi with the VPN tunnel (redundancy?) is because it's not always easy to get access to the internet-facing router.
So I can't always go into the router, and setup forward rules.

Yet the rPis with VPN, as long as I have internet, they connect to my VPN server.

====
Please correct me if I am wrong in what I wanted to do:
0- ssh into my VPN server.
1- from the server, ssh into the rPi
2- once I am in the rPi, I have visibility to their internal network
3- connect to a Windows machine running TightVNC

What do you think?
I am not an expert at any of this.
So that's why I am looking for direction... and build it "step by step".

I dunno... maybe I am thinking off?

Thank you!

---

### Post by darkod on 2015-11-19
Here is how I would do it...

1. Set up your OpenVPN server on the VPS.
2. Set up the one RPi / Linux device to connect to the VPN as client and to have routing enabled (to be able to route to other device on the remote LAN).
3. Set up your desktop to connect to the VPN as client too.

Once you have that up and running, you can reach any device on the remote LAN directly from your desktop. No need to ssh into the VPS first. ssh-ing into the VPS and then into the RPi still leaves you with command line only. How do you plan to launch TightVNC GUI from there?

By connecting your desktop and one Rpi as VPN clients, your desktop can have access to the whole remote LAN, including running GUI programs like TightVNC from your desktop.

---

### Post by clalian on 2015-11-19
Ah wow yes!
What I can do is setup a small VirtualMachine inside my Ubuntu workstation.
Then fire-up the VPN in that VM and connect to the VPN server.
Awesome!!

Any direction as to configure the rPi as "route everything to local net"?

Going to play with this tonight!
:)

---

### Post by darkod on 2015-11-19
Actually, I'm not even sure you will need to specially configure it. If it was acting as a router between two networks, it needs little configuration. But the rPi will already be aware of its local LAN, so when a package arrives with destination the local LAN it should know where to route it.

The only thing you might need to do is set static route on your desktop that will send the traffic destined to the remote LAN through the VPN connection.

You will need to play a little but it should be fairly easy to set up.

---

### Post by TheFu on 2015-11-20
I was trying to avoid the vps.

[http://www.tinc-vpn.org/](http://www.tinc-vpn.org/) is another option to consider, but I'd probably use openvpn.

---

### Post by TheFu on 2015-11-20
I was trying to avoid the vps.

[http://www.tinc-vpn.org/](http://www.tinc-vpn.org/) is another option to consider, but I'd probably use openvpn.

---

