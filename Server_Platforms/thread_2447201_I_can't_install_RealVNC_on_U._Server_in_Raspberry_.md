---
title: "I can't install RealVNC on U. Server in Raspberry Pi4"
date: 2020-07-14
forum: Server Platforms
---

### Post by WhiteTigerIT on 2020-07-14
On a Raspberry Pi4 I installed Ubuntu server + XFCE desktop.
Everything works properly.
Then I tried to install RealVNC Server, but the installation doesn't even start because there are no libraries.
I don't know what to do and I need something that allows me to connect from outside the LAN without someone having to type in codes and passwords as with TeamViewer.

---

### Post by TheFu on 2020-07-14
Use x2go.  It is 2-3x faster that any vnc option.
it works over ssh, so ssh-keys can be used for authentication.
The first step is to get ssh working between any clients and servers and secure those connections.
You should do that with any VNC solution too,  BTW.  VNC should only be used through an ssh-tunnel or a full vpn.

---

### Post by HermanAB on 2020-07-16
"the installation doesn't even start" - good thing too.

On UNIX systems, you will have far more success with SSH, which is installed on the Pi by default and for very good reasons.

BTW, Win10 nowadays supports SSH also.

---

### Post by slickymaster on 2020-07-16
*Thread moved to **Server Platforms**.*

---

