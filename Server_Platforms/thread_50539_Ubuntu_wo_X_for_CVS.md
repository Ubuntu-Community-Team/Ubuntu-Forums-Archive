---
title: "Ubuntu w/o X for CVS?"
date: 2005-07-20
forum: Server Platforms
---

### Post by kook44 on 2005-07-20
Hi-
Im interested in setting up an Ubuntu box as a CVS server.  I would like to not have gnome, or ideally, be able to use it (or a simpler window mgr)  periodically to do updates, troubleshoot, etc. - but I don't want gnome eating system resources during normal use.  Is this a possible, or even common configuration?

---

### Post by LordHunter317 on 2005-07-21
Well, GNOME wouldn't eat any resources during normal use unless someone was using it, but you can do a server install in 'hoary' that doesn't install X.

---

### Post by kook44 on 2005-07-22
[QUOTE=LordHunter317]Well, GNOME wouldn't eat any resources during normal use unless someone was using it.[/QUOTE]

Really?  
No extra memory for the GUI?

Is it feasible to use gnome on a remote X server, so I don't have to attach a monitor to the server?

---

### Post by LordHunter317 on 2005-07-22
Well, the GUI would use memory, but that memory would be paged out when it wasn't ever used.

X might be able to lock some memory, but it'd only be a few MB, tops.  And I'm not sure the locked memory isn't like device registers or vcard memory, meaning it has no impact on system memory.

And yes, you can forward X applications as needed, if you wanted to.  For a whole desktop, using VNC or FreeNX is probably an eaiser solution though.

---

