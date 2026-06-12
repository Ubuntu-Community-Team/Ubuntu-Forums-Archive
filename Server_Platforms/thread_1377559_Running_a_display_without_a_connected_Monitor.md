---
title: "Running a display without a connected Monitor"
date: 2010-01-10
forum: Server Platforms
---

### Post by AWilco on 2010-01-10
Okay I don't know if this belongs here or in the Desktop environment forum, as it's a bit of a cross.

I'm running Ubuntu Desktop edition, but as a home server wihtout a connected monitor. I use the desktop via VNC from my main computer, and so the server doesn't have a monitor connected normally/at startup. This worked fine until a recent set of updates (including NVidia stuff, which is my graphics card). Now when ubuntu starts it complains about not having a /dev/fb0 device, and so cannot start the desktop. How can I fake this device so that the desktop runs?

I was using the NVidia restricted drivers, but disabling them didn't help. Apparently adding a vga=789 tag to the GRUB loading line may cause it to create a framebuffer, but as of GRUB 2 making changes to this seems difficult as it is all done by scripts, and I don't want to mess it up. Does anyone know how likely this is to work, and how to do it?

Apologies if this is the wrong forum.

---

