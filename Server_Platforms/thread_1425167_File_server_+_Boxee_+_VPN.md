---
title: "File server + Boxee + VPN"
date: 2010-03-08
forum: Server Platforms
---

### Post by tertius on 2010-03-08
Simply put I have a new box that I'd like to do all of the above.

1. Network fileserver (with per user share from windows and linux boxes)
2. HDMI to my HDTV for boxee (Therefore I need the standard ubuntu)
3. VPN from outside, i.e. hotspots or any other network.

It's on a normal comcast cable connection (behind a router).

I can figure out #2.  But not #1 and #3.

For #3 (VPN) I'd like access to the rest of my network.  I have a Windows 7 machine and 2 printers next to the server.

Do I need to have an external dynamic DNS for the router? Or the server?

Thanks for any help!

---

### Post by doogy2004 on 2010-03-09
> **tertius said:**
> 1. Network fileserver (with per user share from windows and linux boxes)
Use samba to share files with Windows and other linux boxes.
> **tertius said:**
> 3. VPN from outside, i.e. hotspots or any other network.
I like OpenVPN AS, as it is dead simple to setup the server and the clients.  OpenVPN AS is free but limits the concurrent connections to 2 (you can purchase a license for more concurrent connections)

> **tertius said:**
> For #3 (VPN) I'd like access to the rest of my network.  I have a Windows 7 machine and 2 printers next to the server.
When you connect to the VPN the client will essentially act like it is sitting within your network.  Everything should be transparent.

> **tertius said:**
> Do I need to have an external dynamic DNS for the router? Or the server?
I use NoIP to map my external IP from my ISP to a static domain name, such as myserver.no-ip.com.  NoIP will update the domain name when ever your external IP changes, as long as you use the domain name everything should be transparent.

---

