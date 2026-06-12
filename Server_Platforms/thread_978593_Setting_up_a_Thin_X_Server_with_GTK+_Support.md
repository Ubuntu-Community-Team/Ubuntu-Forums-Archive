---
title: "Setting up a Thin X Server with GTK+ Support"
date: 2008-11-11
forum: Server Platforms
---

### Post by GenuineXP on 2008-11-11
I'm running Hardy on a server box of mine and would like to setup a "thin" X server with support for GTK+ widgets/themes. Is there a simple way to get this running? I'd like GTK+ support, but I don't want to install a desktop environment like GNOME. I haven't forwarded an X session for awhile, so I don't remember if GTK+ libraries are even required on the server to see GTK+ themed widgets on the client.

Also, support for XDMCP would be a plus. It looks like xdm supports XDMCP, and it also depends on core X libraries. Would the xdm package do the trick by itself? Is it possible to install the necessary GTK+ libraries without the need for a ton of GNOME dependencies?

Lastly, I want to be sure that users local to the server never log into an X session automatically (and that the machine never starts an X session on boot automatically). I want to use the X server solely for forwarding to other machines, not for local access.

Thanks.

(Note: I'm aware that XDMCP is not very secure, but I would strictly be using it on my LAN, never from the Internet; I don't even expose the right ports for that.)

---

