---
title: "Installing Linksys Adapter on server Edition"
date: 2009-10-21
forum: Server Platforms
---

### Post by Redoctober21 on 2009-10-21
I'm completely new to the Linux OS, and the Server Edition of Ubuntu. 
I'm trying to install the software for the Linksys WMP54G PCI Adapter, and I don't know how to even try to install it. Is there a command to install from a cd, or something like that?

---

### Post by cariboo on 2009-10-21
You may not need to install any software, with luck your device should be detected and the driver loaded already. Could you paste the output of:

```
sudo lshw -C network
```

The above command will list your network devices and whether they are detecteded properly and if the drivers have been loaded. 

If at all possible I would suggest a wired connection as you won't be very happy with the file transfer speeds using wireless.

---

