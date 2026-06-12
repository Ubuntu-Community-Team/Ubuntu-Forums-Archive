---
title: "Weirdness using default remote desktop server"
date: 2010-01-26
forum: Security
---

### Post by cariboo on 2010-01-26
I was doing some testing using gnome-shell this afternoon, someone in another sub-forum suggested that remote desktop access didn't work with gnome-shell, it partially does, but that's not what I ran into. 

This affects at least Karmic and Lucid on three different systems, if you enable the remote desktop server and select under Security, configure network automatically to accept connections, the programs opens a port 5900 on my Linksys WRT54GS running dd-wrt to the world.

I'm going to spend some time tomorrow, trying to track how this happens, so this is just an initial warning.

Check out the screen shots.

---

### Post by cdenley on 2010-01-26
It sounds like that option turns on UPnP, and it is enabled on your router.

---

### Post by HermanAB on 2010-01-26
Yup, using VNC on Ubuntu is not a good idea.  These forums are full of tales of woe from people who got hacked thanks to a forgotten VNC server which they played with a bit and then abandoned, leaving it running and open to the wild wide world.

If you want to grant remote access to a machine, always use SSH and only SSH.

---

### Post by cariboo on 2010-01-26
I very rarely use remote access, I was doing some testing, to confirm if it worked with gnome-shell or not. The server is turned off, and automatic start on boot is disabled.

I just found it unusual that it opened a port on my router when I enabled the server and told it to setup the connection.

I do have Upnp enabled on the router.

---

### Post by cdenley on 2010-01-26
> **cariboo907 said:**
> I very rarely use remote access, I was doing some testing, to confirm if it worked with gnome-shell or not. The server is turned off, and automatic start on boot is disabled.

I just found it unusual that it opened a port on my router when I enabled the server and told it to setup the connection.

I do have Upnp enabled on the router.

Not odd at all, since it configured your NETWORK (router) to forward the traffic using UPnP. If you place the cursor over that option, it even says "The router must have the UPnP feature enabled". That is what the option is for.

---

### Post by cariboo on 2010-01-27
> **cdenley said:**
> Not odd at all, since it configured your NETWORK (router) to forward the traffic using UPnP. If you place the cursor over that option, it even says "The router must have the UPnP feature enabled". That is what the option is for.

I must have missed that part. :)

---

