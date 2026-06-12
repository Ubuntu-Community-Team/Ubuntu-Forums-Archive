---
title: "Ink-level monitoring for remote printer from client?"
date: 2009-12-16
forum: Server Platforms
---

### Post by sloopveedub on 2009-12-16
Have a printer connected to a server, accessible via CUPS.  

*Inkblot*, as far as I can tell, only works for **locally** connected printers or certain specific network printers.  On the server, I do have *ink* & *libinklevel* installed and while in a SSH session I can say
```
sudo ink -d /dev/usb/lp0
```
which will output xx% for each ink cartridge.  While this works fine, it would be nice to be able to get this info on my normal Ubuntu client machine rather than going into the server.  

Is this possible through Inkblot and I'm just missing it?  Perhaps there's another application?  Lacking that, I suppose it would be possible to create some sort of script to simply send me a system email if levels get below some specified amount?

---

