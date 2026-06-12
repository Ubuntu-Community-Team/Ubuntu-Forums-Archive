---
title: "remote desktop"
date: 2010-02-25
forum: Server Platforms
---

### Post by paintballer4lfe on 2010-02-25
Ok, here's my problem, i have a windows 7 client computer, and im running a ubuntu server, i need to install a vnc like server program on my server and configure it to load on server start up and have a password entry based on user name and passwords for server log ins.

i basically need a program like VNC to run on my ubuntu server and have remote access.

need help ASAP. Thanks

---

### Post by mcarrara on 2010-02-25
VNC will work on Ubuntu

---

### Post by doas777 on 2010-02-25
or freenx. alternatively if you are having trouble getting logins setup as you would like with vnc, try tunneling it through ssh. 
I think freenx is the best match for what you describe though.

---

### Post by landrew on 2010-02-25
> **paintballer4lfe said:**
> [...snip...]
i basically need a program like VNC to run on my ubuntu server and have remote access.

need help ASAP. Thanks

VNC is already installed in the Ubuntu-9.10 desktop, I believe via the package "vino".  If you're running the default Gnome desktop, then you'll find it under the "System->Preferences->Remote Desktop" menu.

If you don't have it, you can do an "apt-cache search vnc", to find all the packages mentioning VNC (assuming you don't already have it loaded.)  If you're using Synaptic for managing software, you should be able to do the same search there, and click to install what you need.  Install the package (and any dependencies), and you should be good to go.

In the vino preferences settings, you can specify if others can share the desktop, if a password is required, and if you need to allow access when someone attempts to connect (in your case, it sounds like you probably don't, as there's probably nobody at the "console" on your server.)

If you just need remote access to shared terminals on the "server", you can also consider using "screen", which is a text-only way of sharing text "terminals".  It takes some getting used to, but is extremely handy for managing multiple remote systems from a single terminal

Cheers,

-Andrew

---

### Post by noway2 on 2010-02-25
paintballer4lfe, did you do a search in the forums for information on VNC?

If you do, you will find that there are some serious security flaws with it that cause it to be about the number one source of cracked servers.

---

### Post by landrew on 2010-02-25
> **noway2 said:**
> paintballer4lfe, did you do a search in the forums for information on VNC?

If you do, you will find that there are some serious security flaws with it that cause it to be about the number one source of cracked servers.

Quite true.  I should have mentioned to the OP that you can't trust VNC (well, the free VNC - RealVNC has commercial versions that are reputed to be fully encrypted and secure...) to provide other than casual security (ie: a password.)  There is no encryption or real authentication done with what you get for free with vino.

In my networks, I restrict the VNC servers to listening on the local loopback interface only, and use an ssh tunnel to connect to the VNC server.  **If you fully trust your local network**, and don't allow access to it from any insecure systems (ie: no open WiFi, and sitting behind a NAT router/switch on a home network), you could use it on the local network.

Just remember that **what's going across the network between the VNC client and server is NOT secure** unless you do something (ie: ssh or VPN) to secure it.  If you use it over the Internet, any systems on networks between the two endpoints could be compromising your server.

-Andrew

---

### Post by paintballer4lfe on 2010-02-26
> **landrew said:**
> Quite true.  I should have mentioned to the OP that you can't trust VNC (well, the free VNC - RealVNC has commercial versions that are reputed to be fully encrypted and secure...) to provide other than casual security (ie: a password.)  There is no encryption or real authentication done with what you get for free with vino.

In my networks, I restrict the VNC servers to listening on the local loopback interface only, and use an ssh tunnel to connect to the VNC server.  **If you fully trust your local network**, and don't allow access to it from any insecure systems (ie: no open WiFi, and sitting behind a NAT router/switch on a home network), you could use it on the local network.

Just remember that **what's going across the network between the VNC client and server is NOT secure** unless you do something (ie: ssh or VPN) to secure it.  If you use it over the Internet, any systems on networks between the two endpoints could be compromising your server.

-Andrew

well its just going through my LAN, im not letting VNC traffic out or in my LAN, im not worried about security, but im talking about running the server on ubuntu, can someone show me a tutorial how to set it up.

Thanks

---

### Post by doas777 on 2010-02-26
> **paintballer4lfe said:**
> well its just going through my LAN, im not letting VNC traffic out or in my LAN, im not worried about security, but im talking about running the server on ubuntu, can someone show me a tutorial how to set it up.

Thanks

sure, here are a dozen or so. there really isn't much to set up. less than 10 clicks.
[http://www.google.com/search?q=ubuntu+remote+desktop&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=ubuntu+remote+desktop&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

