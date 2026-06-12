---
title: "Help VMware Player Jaunty"
date: 2009-05-16
forum: Virtualisation
---

### Post by IamWayne on 2009-05-16
I can't figure out how to install vmware player. I try typing sudo sh VMware-Player-2.5.2.156735 in the terminal, but says it can't read the file, HELP!

---

### Post by mpp on 2009-06-07
> **IamWayne said:**
> says it can't read the file

Is the file executable?  Try ```
chmod u+x VMware-Player-2.5.2.156735
``` to make it executable.  Also you may need to put a ./ in front of the filename to make sure it is trying to use the local file.

have fun()
mike

---

