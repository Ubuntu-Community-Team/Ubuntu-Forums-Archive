---
title: "VNC Proxy?"
date: 2006-03-24
forum: Server Platforms
---

### Post by oaaltone on 2006-03-24
Background: I am working on a project to make my life easier at work. We're looking to implement a free, open-source solution to accessing remote Windows desktops to provide support from Windows workstation (sorry, but that's the facts). I have created a decent solution using reverse-VNC with [SC UltraVNC]("http://sc.uvnc.com/") to get around the firewalls/NATting going on on the remote end, but that doesn't help us at this end, since ports need to be forwarded to NATted workstations on our own LAN, and it would be a hassle for us to constantly update the firewall rules to forward ports to dynamic IPs on the LAN here.

My question is this: is there a free, open-source VNC proxy server that exists? I came across [EchoServer]("http://www.echovnc.com/download_echoserverlinux.htm"), but it requires a license. I know I can accomplish this by setting up an SSH tunnel to a server here and forwarding the appropriate port to the local machine, but that would require some level of configuration on the remote end, and we want to deploy a single executable for support with no user configuration necessary.

---

### Post by LKRaider on 2006-03-24
If you haven't already, check out [http://www.uvnc.com/addons/index.html](http://www.uvnc.com/addons/index.html), where they have a Repeater and a NAT-to-NAT connector.

---

### Post by oaaltone on 2006-03-24
Thanks, I'll check it out.

---

