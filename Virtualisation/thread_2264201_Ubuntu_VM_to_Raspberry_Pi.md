---
title: "Ubuntu VM to Raspberry Pi"
date: 2015-02-06
forum: Virtualisation
---

### Post by rbengr on 2015-02-06
Hi,

I have setup VirtualBox on my Macbook (late 2009).  Ubuntu 14.04 is running as a VM.  I want to connect to a remote RaspberryPi through Ubuntu.  Then I can control the Pi on my Macbook through Ubuntu.  So far, I have established a good SSH connection.  Now I want to create a GUI (desktop) connection.  I understand that I need to use VNC. Is there a step-by-step guide for my situation?

UPDATE:  I found a step-by-step guide on the Raspberry Pi site.  I also looked at the Remote Desktop Viewer app in the Ubuntu repository.  The app seems pretty good.  The question remains:  Will all this work within my VirtualBox setup.  I suppose I could try it, but it would be nice to know if I'm on the right path.

Thanks.

---

### Post by TheFu on 2015-02-06
VNC is slow and almost always doesn't have sufficient security. It requires a VPN to use over the internet, securely.
Why not just use VNC from the Mac directly?  I don't see the point of Ubuntu for you.  Of course, you could wipe OSX and run Ubuntu - I hear they make great hardware and Ubuntu runs well. ;) Had to suggest it. ;)

I prefer using x2go - there's a client for most OSes.  Don't know of there is a compatible ARM x2go server - sorry. NX security is good - uses ssh - and performance feels to be 2-3x faster than RDP or VNC. I think x2go requires ARMv7, so you may be stuck.

Other than that, if you must use VNC, it is a client/server system. Just start the server on the Rpi with the options you want, then connect from a client.

---

