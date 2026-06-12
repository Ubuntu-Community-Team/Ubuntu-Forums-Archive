---
title: "Virtual machine that shares everything with the host except the desktop environment"
date: 2013-10-04
forum: Virtualisation
---

### Post by odror on 2013-10-04
Hi

The new version (version 4) of the free nxserver (from nomachine.com) does not support virtual desktop.

I would like to use virtualbox and create a virtual machine that shares everything with the host except the desktop environment.

I basically would like to create a virtual desktop that will be used by nxserver instead of the real desktop.

Is it possible?

Thanks

---

### Post by TheFu on 2013-10-06
It would be easier to just use **FreeNX** as the server and let the client login manage virtual desktops.  
At least, I do that now ... assuming I understand your issue.

---

### Post by odror on 2013-10-06
> **TheFu said:**
> It would be easier to just use **FreeNX** as the server and let the client login manage virtual desktops.  
At least, I do that now ... assuming I understand your issue.

I agree with you, but in the  the new version of nxserver (4) the virtual desktop feature is not free.

---

### Post by TheFu on 2013-10-06
> **odror said:**
> I agree with you, but in the  the new version of nxserver (4) the virtual desktop feature is not free.

In my setup, virtual desktops are part of the window manager, not the remote desktop viewer.  Can you please explain for a v3.5 user where the virt-desktop controls are?

I'm using FreeNX right now with the last version of NoMachine's NX-client.  In the bottom toolbar - that's where I prefer it for my installs - there are 3 virtual desktops which are 100% controlled by the Ubuntu OS running on the remote machine.  I can't see any way for any remote desktop software to prevent those from being displayed.  RDP, NX, Spice, VNC ... doesn't matter. Those are control by the window manager as long as X/Windows is running. If you aren't running a Window Manager ... well, I suppose that is possible. I've never used it that way.

Happened to pull down the nxc v4 this week. I was unable to figure out how to get the new client to connect to my server.  Seems they may have decided to prevent connections to FreeNX servers as a corporate decision?  I dunno. I do know it was not intuitively obvious what settings meant what in the setup, so I punted and loaded the v3.5 version.  I won't change until it becomes mandatory. I'll try whatever is new then and if it doesn't work, I'll probably deploy spice over TLS desktops instead. Glad that I kept the .deb and .exe setup files.  

I realize this doesn't help with your specific issue if you seek to do it the same way you have previously done it.  But if you do run the WM, then you can have as many virtual desktops as you like ... 1, 4, 9, 16 ... RAM is the only limitation.

---

### Post by odror on 2013-10-06
In the new version the free server allows you to loging to the real desktop that is connected to the monitor(s). You have to pay to get what you have in 3.5. I.e loging to a virtual desktop that is not related to the actual physical desktop.  I have 4 monitors. I do not want to have a remote connection to 4 monitors. I even tried to create a virtual machine. When I am connect to it I get a black screen.

---

### Post by TheFu on 2013-10-07
> **odror said:**
> In the new version the free server allows you to loging to the real desktop that is connected to the monitor(s). You have to pay to get what you have in 3.5. I.e loging to a virtual desktop that is not related to the actual physical desktop.  I have 4 monitors. I do not want to have a remote connection to 4 monitors. I even tried to create a virtual machine. When I am connect to it I get a black screen.

Ok, so you are using a single NX client to spread the remote desktop across {n} local monitors and using them like we used virtual-desktops on Linux/UNIX without multiple monitors.  Interesting.

Is this accomplished by checking the "spread across multiple monitors" setting in the older client?  I've never used it, because I switch remote clients without starting new sessions - netbook, laptop, and from home on a dual monitor setup.

I can understand why NoMachine is charging for this - it is definitely beyond the beginner's needs.  As the owner of a  for-profit company, I understand reserving certain features for paid-only customers.  I need to see how much they charge ... 

You can download the older clients, if that helps.  OTOH, if this is a server side limit, I don't have any answer beside using FreeNX.  FreeNX doesn't support all the same features of the commercial NX-Server products tho.  Their pricing is definitely out of reach for small customers.

---

### Post by odror on 2013-10-07
> **TheFu said:**
> Ok, so you are using a single NX client to spread the remote desktop across {n} local monitors and using them like we used virtual-desktops on Linux/UNIX without multiple monitors.  Interesting.

Is this accomplished by checking the "spread across multiple monitors" setting in the older client?  I've never used it, because I switch remote clients without starting new sessions - netbook, laptop, and from home on a dual monitor setup.

I can understand why NoMachine is charging for this - it is definitely beyond the beginner's needs.  As the owner of a  for-profit company, I understand reserving certain features for paid-only customers.  I need to see how much they charge ... 

You can download the older clients, if that helps.  OTOH, if this is a server side limit, I don't have any answer beside using FreeNX.  FreeNX doesn't support all the same features of the commercial NX-Server products tho.  Their pricing is definitely out of reach for small customers.

They charge linux user much less than windows aprox $124.
I am not a corroborate user. I am only looking for a gui to access cursedly my home computer. As if I am at home,  but not using my home desktop) The alternative that am I am looking at is  to use tunnled vnc4server.

---

