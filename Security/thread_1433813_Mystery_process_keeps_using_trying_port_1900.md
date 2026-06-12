---
title: "Mystery process keeps using trying port 1900"
date: 2010-03-19
forum: Security
---

### Post by [censored] on 2010-03-19
Hi again. According to firestarter, there's some process on my machine that keeps trying to access port 1900, every two minutes exactly. I don't know what it is.

I've tried netstat -tnlp, but it doesn't show up. Presumably I have to do it at the exact second the process is trying to access the port.

Does anyone know of a bash subroutine that will keep doing netstat -pl until it finds a process on port 1900?

---

### Post by cdenley on 2010-03-19
Use wireshark to capture the traffic. What IP is it trying to connect to on port 1900? Is it TCP or UDP? It is probably avahi.

---

### Post by doas777 on 2010-03-19
1900 is upnp's SSDP protocol. do you have a mediaplayer or a upnp capable torrent client?

---

### Post by cdenley on 2010-03-19
Vino server uses SSDP to port forward 5900 on upnp enabled routers. Did you enable "remote desktop" and the "configure your network" setting? I'm not sure if it would broadcast every two minutes, though.

---

### Post by OpSecShellshock on 2010-03-19
It looks like port 1900 is just used for announcing UPnP availability on a given device once something else goes looking for it. So you might see an incoming UDP packet to check if you're listening on 1900 for a particular thing, and then if you are, you'll see it followed up by a TCP connection over 5000 (or 5900? I'm not sure what's current). But basically, since it's just the announcement, it's not going to last long enough to nail it down. What you might want to check instead are any TCP connections around 5000 or so that come afterwards.

Best thing to do would be to disable UPnP, of course. If you must allow incoming connections, it's better to specify the exact port, only use that one (so you always know which process it is), and close it back up when you aren't using the service.

---

