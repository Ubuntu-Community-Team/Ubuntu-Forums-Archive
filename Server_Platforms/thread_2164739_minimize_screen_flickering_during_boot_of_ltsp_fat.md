---
title: "minimize screen flickering during boot of ltsp fat-clients?"
date: 2013-08-01
forum: Server Platforms
---

### Post by xris_xcess2 on 2013-08-01
Hi:

I have an ubuntu server and a small lab of fat-clients. Overall they work very well and are much, much, easier to maintain than the old-nfs-root recepie. Not to mention robust.

Anyway, now I'm onto fixing or trying to polish the overall experience, and one of the most annoying is the repetitive screen flickering I get when booting the clients.

After the pxe-linux screen goes past - flicker - plymouth - flicker - ldm login - flicker - pause - desktop.

Sometimes I don't even get the plymouth splash (and I have failed to fix this one, since there is no grub, and changes in initramfs have no effect ).

Then, when I logout - flicker - pause - ldm login.

What can I do to get a smoother-non-flikering experience. I'm going to try and add the video modules to initramfs and also to the lts.conf file of the clients to see if this fixes the problem. Untill now I have stayed clear of trying to use the specific drivers (nvidia, intel, etc) and just stuck to vesa, but I wonder...

BTW, I build a custom chroot and ltsp.img, from minimal install then added minimal xfce and then built upon that. It's rather snappier that the full xubuntu-desktop and rather slimmer too :-)

Any ideas?

---

