---
title: "Help creating server."
date: 2010-10-04
forum: Server Platforms
---

### Post by bonbeeno on 2010-10-04
Hi,

Right now I have extra computers at home. With that said I decided just for the hell of it, to try and set up a file server at home. Currently I use Windows 7 x64 currently on a wireless USB device (not connected to the router) and would like to set up server with Ubuntu Server x64. Basically what my end goal is is to be able to access the file server from my windows machine. But since I am a noob and I have absolutely no idea about anything about setting up a file server, I am asking for your help so...please respond, and thanks.

---

### Post by Crazedpsyc on 2010-10-04
Ahh, what kind of file server? a file sharing service such as samba? do you want it to be accessible from a browser or a file browser in the network section? If so samba is the choice. Otherwise I would use apache2

---

### Post by arrrghhh on 2010-10-04
If you're used to a GUI, you may want to go with ubuntu-desktop rather than -server.

Nothing wrong with -server, but it is CLI only.  There are some tools that help with configuration, like Webmin.

But if you're starting from square one, you may want to have a look-see thru the [Ubuntu Server Guide](https://help.ubuntu.com/10.04/serverguide/C/index.html).  Tons, TONS of helpful info there for you to read :D

Assuming you want to only share files with your local PC, samba is the way to go for Win clients, NFS for Lin clients.

---

### Post by bonbeeno on 2010-10-04
IS there any way to have the computer connect to the server without a router and by that I mean through direct Ethernet connection?

---

### Post by arrrghhh on 2010-10-04
> **bonbeeno said:**
> IS there any way to have the computer connect to the server without a router and by that I mean through direct Ethernet connection?

Yup, just gotta use a crossover cable and static IPs...  I guess if one box had a DHCP server running on it you wouldn't need a static IP.

---

