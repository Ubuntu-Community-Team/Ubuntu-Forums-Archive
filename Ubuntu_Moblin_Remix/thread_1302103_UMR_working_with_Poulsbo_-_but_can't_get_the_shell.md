---
title: "UMR working with Poulsbo - but can't get the shell running."
date: 2009-10-26
forum: Ubuntu Moblin Remix
---

### Post by Jackyboy86 on 2009-10-26
Hi,
I've used a workaround (created by Lukazade, i think?) to get the GMA500 drivers working in Karmic - and so far, so good.
However, I'm not able to access the UMR shell - I have to use gnome, which works at 1024x576 without a hitch.
However, if I try to use the 'Moblin experience' setting at the login window, it starts to load, briefly fliks to a blank screen, then boots me back to the login window.
Also, the web browser's stopped working... I'm not sure whether somethings been blacklisted or something in the poulsbo drivers is conflicting with the shell...
Any ideas about what this could be? I've already boasted to my boss that i'm going to have an OS that makes Snow Leopard look dull and slow (he's a big mac buff) so i'm rather interested in getting this running!
I'm not sure what log file I should be looking at either? Xorg.0.log maybe?

Just FTR, in gnome, it's running like a dream (with firefox), got my mobile broadband up and running this afternoon, so i've got full use of it. It loads in under 15 seconds (to login window). Fast, sexy, and i'm a very happy bunny!

---

### Post by Jackyboy86 on 2009-10-27
Bump!
Anyone?

---

### Post by Jackyboy86 on 2009-10-28
I've now found the right log  - syslog spat this out:


Oct 28 13:03:25 jack-laptop gnome-session[6921]: Gtk-WARNING: Unable to locate theme engine in module_path: "industrial",

AND

moblin-panel-me[1420]: segfault at e ip 04009131 sp bf8bf620 error 4 in psb_dri.so[3fde000+2b2000]

I think the second one is more important - with psb being the poulsbo drivers - but i've no idea what it means, or how I can fix it!

---

