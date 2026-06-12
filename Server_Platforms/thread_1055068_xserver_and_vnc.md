---
title: "xserver and vnc"
date: 2009-01-30
forum: Server Platforms
---

### Post by Noccy on 2009-01-30
I'm trying to get a VirtualBox virtual machine to load up in a separate Xserver so that I can connect to it with VNC.

VirtualBox OSE doesn't support RDP, and I'm trying to run it as a system service in order to run the last few server components in Windows 2000 that I still hasn't migrated to Linux.

The idea is creating a new Xserver, with VNC attached to it, and then tell VirtualBox to launch inside this new server.

Is this possible?

Best regards,
Chris

---

### Post by HermanAB on 2009-01-30
I cannot tell what you are trying to achieve.

If you want to control Win2000 VM with VNC from Linux, then all you need to do is install VNC server on the Win2000 VM adn connect to it from Linux using an Ultra VNC or Tight VNC client.

If you want to control a Linux machine from Windows, install openssh-server and control it from Windows using Xming and PuTTY.

Cheers,

Herman

---

### Post by Noccy on 2009-01-30
> **HermanAB said:**
> I cannot tell what you are trying to achieve

In essence, i want VirtualBox to run without being connected to any actual Xserver. The functionality to do this, from what I can tell, is only available in the commercial VirtualBox when you provide a parameter to allow access to the virtual machine using the Microsoft RDP protocol.

From there, I want to be able to access the visual elements of the virtual machine via VNC. In essence, I would be creating an entire "virtual desktop" that is only accessible via VNC.

Cheers,
Chris

---

