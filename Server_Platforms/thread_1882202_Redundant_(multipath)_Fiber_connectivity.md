---
title: "Redundant (multipath?) Fiber connectivity"
date: 2011-11-16
forum: Server Platforms
---

### Post by rokdevil on 2011-11-16
I've got a dell 10-blade enclosure with 1955s, two EMC fiber switches and a powervault 660f.  Anyone know the correct method of hooking up the hardware or have a direction in which to point me?
What I thought to do was have redundant fiber connections between the enclosure and 660f.  Without me muddying the waters with BTDT what recommendations does anyone have?

Thanks!

---

### Post by seannon on 2011-11-22
> **rokdevil said:**
> I've got a dell 10-blade enclosure with 1955s, two EMC fiber switches and a powervault 660f.  Anyone know the correct method of hooking up the hardware or have a direction in which to point me?
What I thought to do was have redundant fiber connections between the enclosure and 660f.  Without me muddying the waters with BTDT what recommendations does anyone have?

Thanks!

it really depends on the hardware you have, and what options it has... also, if you are looking at fiber connections... you have more variables to consider... first, what are the connections at the different hardware, are they the same? different? you will also frequently have them in pairs from device to device, the next thing you will need to know is what wavelength each of the ports on your devices are (they have to match or they will not "Talk" to each other...) you can have different wavelengths, but the points at the ends of each fiber MUST be the same here... the end connections are only important in what type cables you need are... also, NEVER look into the end of a fiber cable with the naked eye... regardless of if it is hooked up or not... (you don't want an IR laser that you cannot even see damaging your vision, and it is a good habit to form...) also, before you power ANY fiber equipment up plug up any unused ports with the proper cables or covers for the very same reason... it protects the ports, but also protects you... as for the layout... consult the manufacturers documentation... contact a local contractor that deals with implementation of fiber etc... last but not by any means least... set up the switches... you will need them reconfigured if the configuration of the network has been changed... once that is done and everything can talk... back up the configurations, document document document and keep the config files and documentation of your setup in a very safe place... also, remember physical access by someone that is unfamiliar with fiber can easily take down this new network...

Seannon

---

