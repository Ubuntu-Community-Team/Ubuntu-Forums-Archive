---
title: "Gufw"
date: 2017-05-24
forum: Security
---

### Post by Robbyx on 2017-05-24
At the moment I have **Deny incoming and Allow outgoing **on the software firewall in ubuntu ie gufw.

What I would have preferred was to block all outgoing calls with a popup to give permission to allow individual requests for outgoing connections  but  I could not find it elsewhere, and gufw does not offer it. Has any one seen a simple firewall  that offers the popup?

I also have the firewall in the my router set to:
**Allow all outgoing connections and block all unsolicited incoming traffic. Games and application sharing is allowed.**

I have one computer and devices like a tv, dvr, and vonage box on the lan.

My second question is can you see any point in my using gufw as the router seems to me to be  doing almost the same thing?

Robin

---

### Post by wildmanne39 on 2017-05-24
*Thread moved to **Security**.*

---

### Post by TheFu on 2017-05-24
Routers have to guess about connections. They don't know when you are done. They guess.

The computer actually making requests KNOWS about connections.  Look at the firewall logs on the computer. You'll probably see lots of blocked attempts that got through the router-firewall.

Layers of security help when 1 layer is compromised.  Routers are very helpful, but not perfect.

I wouldn't trust any router that isn't running a Linux I can patch daily or a BSD-variant that can be patched weekly.  That means no consumer router meets those needs, since most do not get new firmware after 1-2 yrs of sales by the vendor.

I would NOT enable "Games and application sharing" - that is too vague to know what it really means.  Open the exact, specific, port(s) you need to the exact, specific, device which needs it.

If you care about security, use the principle of least access as your guide.  Only provide the required access for the required systems for the people who actually need it.  That is much easier to type than to accomplish.  I would find using GUFW cumbersome to accomplish that goal. Scripting would be more efficient, IMHO.

---

### Post by Robbyx on 2017-05-24
Thank you for  a clear and helpful answer.  

Is there a program  that will enable me to recognise which ports need opening and the devices which need it?

---

### Post by TheFu on 2017-05-25
> **Robbyx said:**
> Is there a program  that will enable me to recognise which ports need opening and the devices which need it?

Any web browser. Use it to visit the site for each program and search for a list of required ports. Then manually open those. I know this isn't the answer for which you hoped.

The first part of the solution is to setup **DHCP reservations** for all your LAN devices. This will make each have a known IP on the LAN, so forwarding ports to a specific device is even possible by the router. Not all routers support this and some make it very hard to setup.  But if you've switched to using a non-consumer router, then this is usually fairly easy.  My pfSense router even has a GUI for it!

Without static IPs, it is impossible to forward any required ports to the specific devices. DHCP reservations is the easiest way for most people to accomplish that goal, which still letting portable devices work as expected outside the home.

---

### Post by Robbyx on 2017-05-25
I am looking at the my devices section of the router manager. Each device has both an IP address and a mac address, some are DHCP and others static. Does that mean i have satisfied the first stage above re setting up DHCP reservations?

My router is a BT Smart Hub.

---

