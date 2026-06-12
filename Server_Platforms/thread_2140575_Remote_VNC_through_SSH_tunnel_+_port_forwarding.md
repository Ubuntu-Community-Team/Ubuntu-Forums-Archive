---
title: "Remote VNC through SSH tunnel + port forwarding"
date: 2013-04-30
forum: Server Platforms
---

### Post by Frankincense93 on 2013-04-30
Hi guys,

What I want to do is connect to my home PCs VNC server through a shh tunnel on my Ubuntu server, which is port forwarding onto my home PC.

My setup is the following: Windows Laptop at work -> Router at home ( forwarding ssh:22 ) -> Ubuntu Server at home running ssh -> Windows PC at home, running a VNC server on 6001.


What I basically need to know is how to setup a ssh tunnel to my Ubuntu server, and also setup the port forwarding ( if that's what I need ), on my server, to my Windows PC. I can currently connect via ssh to my server using Putty, and can also use VNC locally at home.



Cheers,
Jack

---

### Post by HermanAB on 2013-05-01
Howdy,

First you got to think about whether you really need to do that.  VNC forwards the whole remote machine desktop over the net, which is slow due to the large amount of data to transfer, while your Windows machine at work already has a perfectly good desktop. There isn't much point in overlaying one desktop with another.

Usually, what one wants to do, is run a remote graphical application and you can do that with SSH - no need for VNC.  The trick is to install an X server on your Windows machine and you can do that with Cygwin.  That will result in a more pleasant user experience.

Once you have Cygwin installed, start the X server, then run PuTTY and connect to the remote machine with -X, launch the remote program and O'l Bob's your Uncle.

---

### Post by markbl on 2013-05-01
> **Frankincense93 said:**
> Hi guys,
My setup is the following: Windows Laptop at work -> Router at home ( forwarding ssh:22 ) -> Ubuntu Server at home running ssh -> Windows PC at home, running a VNC server on 6001.

What I basically need to know is how to setup a ssh tunnel to my Ubuntu server, and also setup the port forwarding ( if that's what I need ), on my server, to my Windows PC.

The ssh client needs to set a tunnel -L5900:win_at_home:6001 when logging in to your home linux server. That is the openssh option but you will using PuTTY on windows so you will add that as localport=5901, remoteport=win_at_home:6001 where win_at_home is the IP host/address of your home windows box (wrt to your server).

Odd you have chosen 6001 as the VNC port at home. That is normally an X port, I would just use a standard 5900+ port for VNC.

From my home linux pc (@3Mbps adsl), I have been using VNC tunnelled via ssh to work on a pc on the other side of the world very frequently for 10+ years and it has always worked well enough for me.

---

