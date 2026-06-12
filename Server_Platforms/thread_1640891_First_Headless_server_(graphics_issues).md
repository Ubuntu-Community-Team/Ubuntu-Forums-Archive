---
title: "First Headless server (graphics issues)"
date: 2010-12-08
forum: Server Platforms
---

### Post by drewerd on 2010-12-08
OK so I have an old computer which I installed Ubuntu 10.04, but then the graphics card died. I actually  looks like the fan shorted and kind of exploded. There are scorch marks  around the processor! I wasn't really doing much anyway so I decided to turn it into a headless game server.
     So I grabbed the video card from another computer and plugged it in, it  boots but I get a warning message saying Ubuntu will run in low graphics  mode. And I have to click through a few menus to get it to boot.  So is there anyway to disable the graphics? I would like to be able to run this without any graphics card at all.
     So far I have gotten pretty much everything set up. VNC for my local network SSH for elsewhere. Is there anything I am forgetting? 
Thanks

---

### Post by windependence on 2010-12-08
I think you're gonna need a graphics card in the box no matter what.
 
Did you load a GUI on Ubuntu server? You may want to reconsider that. Everything you can do from the GUI can be done from the command line.
 
-Tim

---

### Post by drewerd on 2010-12-08
Thanks for your quick reply.
I have a normal Ubuntu desktop installed, to make good server will I need ubuntu server? Or will Ubuntu desktop be good enough? Also I have found cases where people will run a server without a video card. Anyway i was planning on getting an el chepo card but I wanted go ahead and get the server running.

---

### Post by windependence on 2010-12-08
To turn off X at boot:
 
```
 
sudo update-rc.d -f gdm remove

```
 
If you need to run X after you have done this all you have to do is type:
 
```
 
startx

```
 
-Tim

---

### Post by drewerd on 2010-12-08
Thanks that worked. However I don't think my mobo will even allow booting without a vid card. So I found an old used one. Craig's list rocks!

---

