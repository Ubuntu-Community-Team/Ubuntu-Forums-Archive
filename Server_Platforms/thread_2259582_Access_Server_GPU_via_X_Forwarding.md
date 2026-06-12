---
title: "Access Server GPU via X Forwarding?"
date: 2015-01-05
forum: Server Platforms
---

### Post by TripleD on 2015-01-05
Is it possible to use x forwarding (e.g. "ssh -X" or "ssh -Y") to access the full graphical power of a server, or do I have this whole model backwards?

Full Story: I have two computers, a mid-range gaming/media computer running Ubuntu Server, and a 2006 MacBook. The MacBook is on its last legs, but I was hoping to squeeze another year out of it by using it as a thin-client to the more powerful machine. I looked into actual thin client software, but that would require installing over OS X and there are a few programs I still like to use, not to mention I finally have all my passwords, environment variables, etc. set up just the way I like them. Instead I decided to check out x forwarding.
[U]
Server Side[/U]
```
startx
glxgears
glxgears -info
```

Produces a smooth animation. The "-info" output reveals that the graphics card (Nvidia GTX 580) is being used.

_Client Side_
Running

```
ssh -Y username@server
glxgears
glxgears -info
```

produces a slow, stuttering animation. "-info" shows that the laptop's internal graphics chip is being used. Switching to "ssh -X" makes no difference.

Every source I could find said that rendering is done on the side running x server, with the client merely showing output. Did I skip a step, or am I fundamentally misunderstanding what is happening here?

---

### Post by lukeiamyourfather on 2015-01-05
When using X tunneling the server sends commands for the client to draw. So you're just getting the commands to draw whatever glxgears wants to draw which then get run on the client GPU and end up as pixels on the screen. Though the processing of everything up to drawing the pixels is still done on the server. 

If you want to render pixels on the server and send those pixels to the client rather than commands for drawing you need something like x11vnc with the noxdamage flag. Then whatever VNC client you want to use on the other end.

Either way I wouldn't recommend doing any kind of multimedia over a setup like that. It's fairly cumbersome and there's lag. It also eats up a lot of resources to encode and decode the pixel data compared to the commands for drawing. Gaming and watching videos will probably be rough.

There are solutions out there for low latency remote graphics like the AMD FirePro R5000 but my understanding is they use a specialized thin client (the example on AMD website is a Dell Wyse P45). It won't work with any old computer that has Linux installed.

---

### Post by MAFoElffen on 2015-01-05
More on that... 
True-- Xorg Xserver is the server side (even when installed on a desktop), the rendering of and/or remotely connected remote that renders that is the client of XServer. You can make thin clients, but it shows only to the capability of that client. Performance of a remote is not as much as is it was all there, but once used to it... We used to do this all the time, but you don't see much of this anymore. A good standard Desktop doesn't cost $1k to $2k anymore (early 'to mid 90's).

SSH X Forwarding is tricky and someway slower, because of translation of the pieces. Some things do not to behave as if setup as above. Some things can be written to run on the host (like some of my management utils,,, which display as if they are just another app on the local desktop, but see what is on the host. Somethings don't want to XForward at all. Running just console is a lot faster and you don't get the network load.

But VNC varies from that. You can run remote to VNC from a headless virtual or a full version and the VNC client do not have to be running 3D if it is set up as VNC video. Then the VNC rendering is different in how is translates that. I do this all the time with KVM virtuals. There is a performance hit and a lag, but it work to my management consoles just fine. It you are on a network of your own... that may be acceptable. But If I have about 4 VNC sessions going, my wife is upset, because her online games slow down to a crawl. It can be done, but you have to accept the cost. If on a bigger net, that might be something to subnet off the main network. I set up my desktop virt's as VNC VESA, 1920x1080.

But by the time you figure out the time and possible extra cost of additional NIC's, 3D capable GPU's can be got for less than $50 now... Just because something is possible, doesn't mean it makes sense.

---

### Post by TheFu on 2015-01-05
> **TripleD said:**
> Is it possible to use x forwarding (e.g. "ssh -X" or "ssh -Y") to access the full graphical power of a server, or do I have this whole model backwards?

No.  The local GPU is used for all display work.  If you want non-graphical work to be performed by the remote GPU, perhaps using [CUDA]("https://developer.nvidia.com/about-cuda"), that should be possible with specially written applications - usually something like a bitcoin or password cracker.

X-servers are local and X-clients are remote. Backwards of the normal client/server architecture.

On the LAN, using x-forwarding through ssh is fine and easier than other options.  However, over a WAN or untrusted network using the **x2go** client and server makes more sense. It is easier to setup than other alternatives and about 2x more network efficient than RDP or VNC. It has tunable parameters for bandwidth, so even from halfway around the world it is highly responsive for productivity applications.  Forget about running remove video -- that isn't a real option with any of these tools. Try it, you'll see for yourself.  There are x2go clients for the main 3 PC OSes - never tried the OSX version, but both the Widnows and Linux versions work very well.

---

### Post by TripleD on 2015-01-05
Thank you to everyone for your replies and suggestions. They were very thorough, and I now understand x server and ssh a bit more than I did before.

Looks like "x forwarding" is off the table. I'll change this to "solved" and give VNC or x2go a try. I won't be using them for multimedia or gaming (there are a million and one other programs for that) just for running newer versions of software my laptop cannot physically run (2006 was the last 32-bit MacBook; lucky me). The gaming PC was built during more halcyon days (a.k.a when I was still employed) so I'm trying to see if it can pull double-duty without radically altering its setup until I'm more stable financially.

---

### Post by MAFoElffen on 2015-01-07
> **TheFu said:**
> On the LAN, using x-forwarding through ssh is fine and easier than other options.  However, over a WAN or untrusted network using the **x2go** client and server makes more sense. It is easier to setup than other alternatives and about 2x more network efficient than RDP or VNC. It has tunable parameters for bandwidth, so even from halfway around the world it is highly responsive for productivity applications.  Forget about running remove video -- that isn't a real option with any of these tools. Try it, you'll see for yourself.  There are x2go clients for the main 3 PC OSes - never tried the OSX version, but both the Widnows and Linux versions work very well.
Fu-- You recommended it and caught my curiosity. Never heard of it before now. Goggled it to find out more. But I didn't see any screen shots.

Does it come up like a remote desktop?

---

