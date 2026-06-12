---
title: "a bug in the Settings plugin (aka computer)"
date: 2007-05-23
forum: Ubuntu System Panel
---

### Post by groggyboy on 2007-05-23
i have a wireless card (at eth1).  the Settings plugin correctly displays my IP address, but regardless of whether i'm using eth0 (wired) or eth1, Network states that I'm connected to a "wired network".  is there any way to make it properly display my network (ie, "wireless network")?

---

### Post by Malac on 2007-05-24
> **groggyboy said:**
> i have a wireless card (at eth1).  the Settings plugin correctly displays my IP address, but regardless of whether i'm using eth0 (wired) or eth1, Network states that I'm connected to a "wired network".  is there any way to make it properly display my network (ie, "wireless network")?
Hi groggyboy,
Currently the "Settings" plugin recognises the type of network by the connection name. Here is the code from that section of the plugin(lines 214-218 ):
```
                if self.netiface in ["eth0","eth1","eth2","eth3"]:
                    devtype = "Wired Network"

                if self.netiface in ["wlan0","rausb0"]:
                    devtype = "Wireless Network"
```The easy fix for you would be to move the "eth1" to the second if statement.
Or you could try renaming your connection in /etc/interfaces and other files it's mentioned in.
I don't use wireless for anything so not sure what effect this would have on your connection.

Hope this helps.

---

### Post by groggyboy on 2007-05-24
thanks malac!

editing the computer.py file worked fine.  i could try renaming the interface, but that seems like a lot of trouble.  if i saw a clear benefit i might.  in the meantime, this'll do.

cheers!
groggyboy

---

