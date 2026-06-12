---
title: "Listening for network (un)mounts without X"
date: 2008-03-10
forum: Server Platforms
---

### Post by Digimer on 2008-03-10
Hi all,

  I am not sure if this or the programming thread is best for this question, so mods, move if you thing it's best.

  I need a way to listen for NFS, SMB and so on devices to be (un)mounted. I know that the Gnome-vfs-daemon does this, but I am working on a server program where I can not expect Xorg to be installed, never mind Gnome.

  What I've done for hardware devices is use DBus to listen to the HAL bus for signals, and react accordingly. Is there a typical bus for this? What does gnome-vfs-daemon listen to? I've been digging through it's source, but I am no c coder. :(

  I know I could just create a timed loop, but I don't like how generating so much noise for an event that is likely to be rarely occurring, specially when there is something like DBus out there which deals with it so elegantly.

Thanks for any advice!

Digi

---

