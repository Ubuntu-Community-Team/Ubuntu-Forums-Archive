---
title: "Network Manager and DHCP &amp; DNS annoyance.  Be nice if DNS was separate like Windows."
date: 2009-07-15
forum: The Cafe
---

### Post by MechaMechanism on 2009-07-15
SOLVED

In Microsoft Windows the DNS servers can be changed to the users choice without messing with DHCP.  In Ubuntu the DNS servers are locked to DHCP and DHCP itself is locked to Network Manager.  I really lament the lack of a GUI for specifying the DNS servers without touching any other network setting.  Oh sure you can edit the DHCP3 config files and all but I really think a proper way for Ubuntu would be a GUI.  Is there some method that one can use to request a usability enhancement?  Please Ubuntu developers make the DNS settings separate.

---

### Post by cariboo on 2009-07-15
If you are using Jaunty or newer, you can set up your own dns addresses manually by selecting method-->Automatic DCHP Addresses only in Network Manager-->Edit Connections-->IPV4 Settings.

---

### Post by MechaMechanism on 2009-07-16
> **cariboo907 said:**
> If you are using Jaunty or newer, you can set up your own dns addresses manually by selecting method-->Automatic DCHP Addresses only in Network Manager-->Edit Connections-->IPV4 Settings.Wow, thanks man.  I guess I was so used to the previous way of doing networking that I had not thought of checking Jaunty's Network Manager.  Just go to show that sometimes I need to redo stuff just to see if something changed.  Thanks again, just what I was looking for.

---

