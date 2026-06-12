---
title: "any good solution for ubuntu VNC to a Vista PC?"
date: 2009-08-07
forum: Server Platforms
---

### Post by beterhans on 2009-08-07
ubuntru is the client
and VIsta is the server.

I only find out a VNC called ultravnc which could install on vista. others can't

but the vnc viewer inside the ubuntu is not compatible with UltraVNC... :(

---

### Post by juancarlospaco on 2009-08-07
**FreeNX  **
:)

---

### Post by HermanAB on 2009-08-07
Vista comes with Remote Desktop.  Enable it and connect to it from Linux using rdesktop.  You don't need VNC.  VNC is slow and insecure - not a good idea.

---

### Post by zemon_ on 2009-08-07
TightVNC:D

---

### Post by beterhans on 2009-08-07
> **HermanAB said:**
> Vista comes with Remote Desktop.  Enable it and connect to it from Linux using rdesktop.  You don't need VNC.  VNC is slow and insecure - not a good idea.

my vista is Home premium come from dell pc. not ultramet. so only remote desktop client no server

and FreeNX is not for windows. :(

---

### Post by beterhans on 2009-08-07
trying tight VNC :D

---

### Post by HermanAB on 2009-08-07
Hmm, then TightVNC or UltraVNC is your best bet, but  don't expose it to the internet.  Only use it on a LAN.

---

### Post by windependence on 2009-08-08
Herman is right. VNC is very insecure lately and there are better alternatives. If you MUST use VNC, please tunnel it over ssh.

-Tim

---

### Post by pricetech on 2009-08-08
TightVNC works for me, though I haven't used it under vista.  We're still an XP shop.
Security is a concern.  I only use VNC on a couple of "servers" that require a user be logged in to run the application that it "serves" and traffic is restricted to the LAN.
It's a little grumpy about getting the server component running as a service on the winders box, but after the initial grumpiness it works just fine.
Good luck with it.

---

### Post by cariboo on 2009-08-08
You can get the Microsoft rdp server [here]("http://www.microsoft.com/windowsxp/downloads/tools/rdclientdl.mspx"), then use Applications-->Internet-->Terminal Server Client to connect to your Windows desktop, It works much better than VNC.

---

### Post by Vegan on 2009-08-08
> **beterhans said:**
> ubuntru is the client
and VIsta is the server.

I only find out a VNC called ultravnc which could install on vista. others can't

but the vnc viewer inside the ubuntu is not compatible with UltraVNC... :(

You have it backwards, Linux should be the server, Vista is the client.

Vista is not a server, its a desktop client.

---

### Post by windependence on 2009-08-09
> **Vegan said:**
> You have it backwards, Linux should be the server, Vista is the client.

Vista is not a server, its a desktop client.

Ummm....not in this case. He is referring to server and client in terms of remote desktop connections, Vista is serving the desktop to Ubuntu.

-Tim

---

