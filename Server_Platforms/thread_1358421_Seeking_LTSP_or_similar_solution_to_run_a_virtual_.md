---
title: "Seeking LTSP or similar solution to run a virtual Ubuntu desktop on client machines"
date: 2009-12-18
forum: Server Platforms
---

### Post by nerr on 2009-12-18
Hey everyone, I've been doing some research lately to find new purposes for my Ubuntu 9.10 home server, and LTSP has caught my eye.  The ability to run an operating system on the server but allow dummy clients with weak hardware to control it seems very attractive, as I have two old laptops here that I would like to be able to use for simple internet browsing and word processing in an Ubuntu environment.

I have already set up Ubuntu Server 9.10 x86 on my machine, and am now looking for solutions with which to set up a desktop environment image which can be booted and controlled by the thin-clients, but powered by the server.  The server is an Intel Atom box with 2GB of RAM, but I suspect it may be more than enough for the simple tasks I am looking for, especially with how often the server is idle.

Could somebody point me in the right direction with how to get this project started?  I would prefer not to have to reinstall my base operating system on the server, but all of the tutorials and guides I have looked through so far seem to take this approach.

Any help is greatly appreciated, thanks!

---

### Post by lykwydchykyn on 2009-12-18
Not sure exactly what you're aiming for; LTSP does not really involve any kind of "virtualization".  It basically allows a client to boot to a minimal Linux OS over a network so that it can remote log-in to a server.  

Is that what you're after, or are you wanting the user's environment to be "sandboxed" in some way with virtualization?

---

### Post by kadeous on 2009-12-18
Not sure it's what your looking for but I would test out VNC connections rather then having the thin clients boot from the server. This would allow you to have a desktop view of the server on the thin clients but at the same time not have to reconfigure your installation.

[http://havetheknowhow.com/Configure-the-server/Install-VNC.html](http://havetheknowhow.com/Configure-the-server/Install-VNC.html)

---

### Post by nerr on 2009-12-18
Aha, I apologize for my confusing wording.  I'm essentially looking for a solution that will allow my server to run an Ubuntu Desktop installation in a VM or otherwise (still keeping this separate from the underlying server installation), and handle all processing and resource management for that desktop install, BUT allow thin-clients to view and operate the virtual Ubuntu Desktop install over the LAN.

Here's a quick diagram of what I want:

[IMG]http://whatimg.com/images/20973919817500077545.jpg[/IMG]_[IMG]http://nerr.ath.cx/ltsp.jpg[/IMG]_

This solution is ideal for me because it allows no contact with the actual underlying server operating system, but it also provides a desktop environment which is easy to use and packs the power of the server beneath it instead of the weak thin-client laptops.

If I'm going in the wrong direction here, feel free to offer advice to steer me in the right one.  It would be much appreciated.

---

### Post by lykwydchykyn on 2009-12-18
I'm not sure there is a shrink-wrapped solution for this, but it certainly seems like you could set something up like this with kvm, maybe setting up the user's x session on the server to just launch a virtual machine on login.

Seems a waste to emulate a whole PC just to segment the user though; I wonder if there's some way just to chroot the user.  Seems like I've heard of a solution like that.

---

