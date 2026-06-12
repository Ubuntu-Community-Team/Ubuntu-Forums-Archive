---
title: "connecting ubuntu from outside homenetwork (openSSH)"
date: 2011-02-02
forum: Server Platforms
---

### Post by ximie5 on 2011-02-02
hello,
i'm trying to use my home internet connection from outside my home network.
So i've set up an linux 10.10 computer and installed openssh-server on it and got it running on port 443.
Also i configured my router to forward 443 to the ubuntumachine.

i tried to connect to my ubuntu through a windows machine in the homenetwork using putty (using the INTERNETAL ip and port 443) and i was able to login :)
But, when i try to connect from outside my network it doesn't work.

So this is what i do on windows: I open putty, put in the EXTERNAL ip of my homeUbuntu pc, as port i say 443. When i press 'OK' i have a connection error.

What should i do to make it work?

Thanks in advance!

---

### Post by volkswagner on 2011-02-02
First verify port 443 is open from your isp.

From inside your LAN navigate to canyouseeme.org, from there you can scan port 443 to see if it is open.

---

### Post by ximie5 on 2011-02-02
you're right, i can't connect to that port.
What should i do now?

---

### Post by pl@yer on 2011-02-02
try higher numbered port maybe 4430?

---

### Post by ximie5 on 2011-02-02
Ok that port is open!
fantastic.
I changed the forward in my router and i changed the openssh server to work on port 4430.

When i try putty now, it doesn't work either:(
But i think that all ports on my outside network are blocked except for 80; 443

What to do now?

---

### Post by kroon78 on 2011-02-02
I'm not sure what your end game is on this setup but i'll tell you what i did to use my home network as my internet connection from a remote location.  I setup a VPN server on my ubuntu server at home and would login to it from a remote location.  After that all traffic through the remote machine was travelling through the home server first.  An ip check from the remote machine would show my home ip address.  The interesting thing about this setup is from all points of view it appears my remote machine is at home giving me the ability to VNC to any machine on the home network.  I can do anything from the remote location I could do sitting at my desk at home.  The only down side is you don't have physical access to the hardware fro obvious reasons.

---

### Post by ximie5 on 2011-02-02
the thing i want to do is being able to surf any website and acces my homenetwork and do some things over there, so just like you say it.
I'm guessing that it's wrong what i'm doing and VPN is a better way to do it.

Will it be able to work if the external isp has only ports 443 and 80 open and my home isp doesn't allow me to send through these ports?

Do you have a good manual for this (i'm newbie)

Thx

---

### Post by kroon78 on 2011-02-02
Can you confirm these ports are closed?

---

### Post by ximie5 on 2011-02-02
no i can't but i'm pretty sure. Can you tell me how to be sure that they are closed?

---

### Post by cariboo on 2011-02-02
You can check open ports using [canyouseeme]("http://www.canyouseeme.org/")

---

### Post by ximie5 on 2011-02-02
i've tried that already and al the ports i tried were blocked. But aren't these the ports that other ones from outside your network can connect to? I'm looking for the ports that are open for the ones INSIDE the network to connect to the outside (if i'm not wrong)

---

### Post by volkswagner on 2011-02-02
> **ximie5 said:**
> i've tried that already and al the ports i tried were blocked. But aren't these the ports that other ones from outside your network can connect to? I'm looking for the ports that are open for the ones INSIDE the network to connect to the outside (if i'm not wrong)

OK, heres what I have found with canyouseeme.org.  Oddly I don't recall this being true in the past, so I'm not sure if it is router dependent or isp specific, or my memory is shot.

For accurate results with canyouseeme.org you will need the following in place.

For any port check to work, you will need your router forwarding that port to a specific machine, that machine will need a service listening on that port, and your ISP must not block that port for you to see success.

I have verified this.  The machine you use to check need not be the host for the open port, but must be inside your LAN.

I have verified the above by first forwarding a port such as 80 to an internal machine, check port 80 and it says blocked... I then enable a service on port 80 on said machine then I get "success".


Hope this helps.  You can't just randomly check ports.  I have not tested this by setting a DMZ though.

---

### Post by ximie5 on 2011-02-03
yes, i can acces 4430 from outside to my home. BUT in the outside network is a strict firewall that blocks almost every port so i can't connect from the outside to the port of my home network.
I can't access the router of the outside network, neither can i change port forwarding

---

### Post by ximie5 on 2011-02-03
i've used local port scanner and i can confirm now that only port 80 and 443 are open in my outside network

---

### Post by YesWeCan on 2011-02-03
Erm...how do you know that you cannot SSH from outside using port 443?

Are you concluding this from the fact that you cannot SSH from your Windows PC using your external (router WAN) address? Have you tried connecting from a PC that is actually outside your local LAN? Some routers are too clever.

---

### Post by ximie5 on 2011-02-03
ok i restart my story, i've figured out a few things.
So i try to set up a server inside my homenetwork (inside) and want to be able to contact it from the outside (outside).
The setup of the server is completed and it works on port 4430, so i've tried from inside the network (LAN) and outside the network (WAN) and it works each time!
So that's great, the only problem i'm having is that another ISP that i sometimes use have all outgoing ports blocked, except a few, unfortunaly not 4430.
So my question now is: How will i be able to connect to my home server when the port is blocked on the outside internet connection?

Extra hickup: I can't open any ports of the outside connection and in my home connection is 4430 the only open port.

Hope i'm a bit clear :)

---

### Post by kroon78 on 2011-02-04
Not sure if there is an free or open source solution similar to the following but gotomypc, gotomeeting and the others by citrix are for just a situation.  NAT traversal may end up being the only solution. A UPnP option or something similar.

---

