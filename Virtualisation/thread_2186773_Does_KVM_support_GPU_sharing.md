---
title: "Does KVM support GPU sharing?"
date: 2013-11-09
forum: Virtualisation
---

### Post by junk.here on 2013-11-09
By "GPU sharing", I'm referring to how VMware, VirtualBox, etc. create a virtual graphics adapter for each VM as opposed to VT-d GPU passthrough which is exclusive to a single VM.

---

### Post by TheFu on 2013-11-09
The actual GPU means nothing to KVM by default, unless you force it.  You can run 50 Linux desktop clients on a single server, if you like.
[http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization](http://blog.jdpfu.com/2013/11/03/setup-kvm-virtualization) might help with a diagram.
Actually, I've never used any GPU passthru with any virtualization technology, so I am a little confused by the question.

---

### Post by junk.here on 2013-11-10
To clarify, I would like to know about KVM's ability to handle 3D rendering, specifically, DirectX and OpenGL. To be even more precise, does KVM have anything comparable to VMware's Horizon View, Citrix's HDX 3D, or Microsoft's RemoteFX?

---

### Post by TheFu on 2013-11-10
So, you want to run a desktop on a desktop .... all on the same physical machine? 

I have seen 3 types of graphics connections in virt-manager.
* VGA emulation  ... VNC is the normal client.
* Spice - this uses high performance networked connections to QXL graphics drivers - OpenGL might work [http://www.spice-space.org/page/Spice3DNotes](http://www.spice-space.org/page/Spice3DNotes)  ; Spice is a bandwidth hog from my testing.
* libsdl .... never used this, but SDL is a graphics API for high performance games.

Do not expected DirectX support ever.

---

### Post by junk.here on 2013-11-11
It would be more accurate to say that I want to run a desktop on a tablet, actually. I suppose that KVM is probably not the best choice for this kind of thing.

---

### Post by TheFu on 2013-11-11
> **junk.here said:**
> It would be more accurate to say that I want to run a desktop on a tablet, actually. I suppose that KVM is probably not the best choice for this kind of thing.

What sort of tablet?  With Android, VNC seems to be the only, realistic, remote desktop available. VNC has all sorts of issues, regardless of remote host.  The gotomypc stuff means you have to trust a 3rd party - that is a non-starter for me.

NoMachine has threatened to release an Android client for v4.x of their stuff in December. NX is a good protocol, but no OpenGL.

Most of the remote desktops only work well for "productivity apps", not video.

Are you changing your requirements mid-thread?

---

### Post by junk.here on 2013-11-11
> **TheFu said:**
> What sort of tablet?

Various iPads, last year's Nexus 7, this year's Nexus 7, and a Windows 8 tablet.

> **TheFu said:**
> Are you changing your requirements mid-thread?

Not really. My goals are:

[LIST=1]
[*]To provide a full PC* experience to any device that can act as a thin client 
[*]To provision more PCs* than I physically have 
[/LIST]

[SIZE=1]* By PC, I mean something comparable to a typical laptop with integrated graphics. In other words, something capable of thin client gaming at low-medium settings. This is actually much harder than I had hoped it would be as enterprise thin client solutions don't really support fast motion and consumer thin client solutions are generally built into standalone devices.[/SIZE]

---

