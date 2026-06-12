---
title: "Multiple Users on one Ubuntu installation"
date: 2014-07-16
forum: Virtualisation
---

### Post by iExchange128 on 2014-07-16
I wonder if it is possible to have multiple users using the same computer with ubuntu installed? I would also like to allow users to access that computer remotely by a secure way(should I use VNC or something else?).

Requirements:
-They need to use the Unity graphical interface, not command line.
-When a user reaches the computer from a remote access connection, the system automatically creates an account for him and logs him into the unity desktop
-When the user logs out the computer, the system automatically deletes his account from the system.

Thanks!

---

### Post by TheFu on 2014-07-16
This isn't a virtualization question. Hopefully a moderator will move it as you requested. ;)  Ooops.

UNIX/Linux is a multiuser OS from the core, so having thousands of users on a system concurrently is possible.  

Unity with remote desktops is a terrible idea.  Remote 3D accelerated GUIs just don't work.  Use LXDE, XFCE4 or a pure WM solution.  These are all GUIs and there are 30+ other options.  The GUI is NOT the OS. There are many choices for a GUI under Linux. If a GUI is mandatory, expect 10-200 concurrent users, not thousands. There is that much overhead. Obviously, the server and bandwidth available to support these users will matter for performance.  Most of the desktop code will be shared by 40% of the users, so that won't be an issue. Sizing is hard without an estimated worklaod, but I've heard of schools putting 200 students on a single server concurrently for word processing-type stuff.

Do NOT use VNC or RDP if you care about security - unless you setup a strong VPN. That means NOT using PPTP.  Which remote desktop tool I'd recommend depends on the Ubuntu release.  I've been using FreeNX for 3-4 yrs happily. It has died and with 14.04, x2go appears to be the best alternative, though I haven't attempted it myself. It is based on the NX protocol, so an ssh tunnel is included.

Deleting an account is something you'd need to script.

---

### Post by iExchange128 on 2014-07-18
Thanks very much for sharing the information and your experiences with me, I decided to go with x2go. Could you give some recommendations on some good HTML5 web browser clients(that are secure) for it?
(I won't be using the x2go browser plugin at the moment though since its Windows version of the plugin is still in development, and my end users will be using Windows to access their remote desktop sessions)

---

### Post by TheFu on 2014-07-18
No HTML-based remote desktop is secure, IMHO, regardless of platform.  The issue is with the protocols (HTTP/HTTPS), they are not designed for security and tacking on other stuff can't fix that.  OTOH, if they are on the LAN, go for it.  **Guacamole** is an option and may have been a better choice, IFF you have openvpn as a requirement too.  NEVER use just HTTPS over the internet if you care about security.  PPTP would be only slightly worse, IHMO.

I don't use Windows for anything important.  Haven't touched Windows for work since '07. Sorry.

Clearly, my opinions may be skewed towards higher security than most, but nobody believed we shouldn't trust the NSA before Snowden leaked all that stuff. I suspect average people in the USA don't mind the NSA snooping and I don't care so much either, but that isn't the point of security. If the NSA can get in, then so can 50+ other countries/organizations around the world.  Plus when the NSA snoops on my traffic without an approved search warrant inside the USA, I think that violates US law (regardless of what the FISA court has ruled).  

Gee - went crazy there for a para, sorry.

---

