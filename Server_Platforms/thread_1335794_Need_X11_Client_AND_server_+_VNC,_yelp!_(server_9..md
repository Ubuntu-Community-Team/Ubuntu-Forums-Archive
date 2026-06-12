---
title: "Need X11 Client AND server + VNC, yelp! (server 9.10)"
date: 2009-11-23
forum: Server Platforms
---

### Post by Arkaniad on 2009-11-23
Basically, i am using wine to run Source Dedicated server, which launches an X11 window.

But a server is only as good as it's uptime, and i have no x11 client running on the box.

I had it going with debian, but i nerfed the hard drive and started over with ubuntu. What i need is the server to log in automatically and launch an X11 desktop and just sit there. Right now, all it does is boot up into a text login prompt.

I can ssh, forward ssh to my laptop or my desktop, but who wants to leave their desktop on all day, come on.

---

### Post by windependence on 2009-11-23
Why not leave the machine on? It's really not a "desktop" any more, it's a server. Even so, turning a machine on and off all the time is extremely hard on the hardware. The components and boards expand and contract each time you do this and eventually, the soldered components on the board get loose and fail. A machine at idle consumes very very little power. My machines run 24/7/365.

At any rate, I see there is a way to run your source dedicated server on Linux directly so why are you running it on wine? Also, according to the documentation, you don't need to GUI working on the machine to run this at all. Your box will run much better without the GUI and be much more secure.

-Tim

---

### Post by HermanAB on 2009-11-24
Hmmmm? If it is an Ubuntu server installation then you should have sshd running on it, so from your other desktop/laptop machine simply do:
$ ssh -X -C -c blowfish user@server gnome-panel

La voila!

---

### Post by Arkaniad on 2009-11-24
> **windependence said:**
> Why not leave the machine on? It's really not a "desktop" any more, it's a server. Even so, turning a machine on and off all the time is extremely hard on the hardware. The components and boards expand and contract each time you do this and eventually, the soldered components on the board get loose and fail. A machine at idle consumes very very little power. My machines run 24/7/365.

At any rate, I see there is a way to run your source dedicated server on Linux directly so why are you running it on wine? Also, according to the documentation, you don't need to GUI working on the machine to run this at all. Your box will run much better without the GUI and be much more secure.

-Tim

Sorry, i didn't provide enough info.

GMOD Srcds doesnt have a linux binary yet and will probably never have one.
And when i launch srcds it launches it's own x11 window whether i specify
console or GUI :\

---

### Post by Arkaniad on 2009-11-24
> **HermanAB said:**
> Hmmmm? If it is an Ubuntu server installation then you should have sshd running on it, so from your other desktop/laptop machine simply do:
$ ssh -X -C -c blowfish user@server gnome-panel

La voila!

What does that do? Because i'm already able to get an x11 client, my aim is to get it running x11 when the server starts so i can VNC to it and have it always running e_e

---

