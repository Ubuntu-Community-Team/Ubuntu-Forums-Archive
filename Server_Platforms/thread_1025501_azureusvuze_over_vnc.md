---
title: "azureus/vuze over vnc"
date: 2008-12-30
forum: Server Platforms
---

### Post by bartvh on 2008-12-30
I've installed the bittorrent client Vuze (formerly Azureus) on my home server. I'm currently running it as a semi-daemon (the console version in a screen session) with access through the swing web interface. This interface is sufficient for managing downloads, but otherwise quite limited. I'd like to have access to the full, normal interface without physically being near the machine.

My idea is something like this:
- On boot, start a new XFCE (or something even more compact) session in the background (as in, not on the physical screen) with the vuze user logged in.
Oh, and preferrably on a lower resolution than the physical screen.
- Start the full Azureus interface in this session.
- Share this session through VNC (I'm currently using x11vnc to share the physical screen).

Now, I have two questions:
- I think this is possible, but how would I do it?
- How much would it impact the server performance? It's a 3GHz Pentium 4 with 1GB RAM.

---

### Post by MaximB on 2008-12-30
Well, I had a similar problem with vuze and aMule...

I've connected to my machine at home via ssh protocol using NXclient (GUI mode).
I was able to see my desktop and work, but I couldn't open aMule and vuze, it appears as they do not work/pass trough the ssh protocol - no x forwarding.

I can do nothing to fix it, the problem is at those programs. 
I think you will have the same problem with your method.

---

### Post by bartvh on 2008-12-30
I don't think you quite understand my problem. I don't want to run Vuze on the "real" desktop, I want to start a second one besides it and open it to VNC.

---

### Post by MaximB on 2008-12-30
> **bartvh said:**
> I don't think you quite understand my problem. I don't want to run Vuze on the "real" desktop, I want to start a second one besides it and open it to VNC.

I don't think that "real" or "virtual" matters in this cease as this program still needs x-forwarding to appear on your screen from a different desktop.

But I might be wrong.

---

### Post by bartvh on 2008-12-30
It works on my real desktop just fine, including VNC.

---

### Post by windependence on 2008-12-31
You should be able to do this over FreeNX quite easily. I don't see why there would be any limitations on it. Another alternative that seems to be very popular is rtorrent.

-Tim

---

