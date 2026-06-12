---
title: "Getting 3D-rendering on 64-bit Server"
date: 2007-12-03
forum: Server Platforms
---

### Post by steve_c on 2007-12-03
I have a newly-installed Ubuntu 7.10 server, 64-bit version. I need the 64-bit because my group needs to do 3D visualizations of molecules whose input data range into the multiple gigabytes.

I've managed to get VMD installed and going, but I can't view isosurfaces. I'm thinking that *might* be because I'm lacking good 3D support. This would seem to be confirmed by:

```
$ glxinfo
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: SGI
client glx version string: 1.4

$ glxgears
1239 frames in 5.2 seconds = 238.093 FPS
1200 frames in 5.2 seconds = 228.706 FPS

```

Now while 228FPS sounds pretty good glxgears is quite visibly lagging badly.

Looking at the proprietary drivers it tells me to install the restricted-drivers-manager-<kernelversion>-server, which doesn't exist. Or I can install the regular restricted-drivers-manager which wants to change my kernel to the generic kernel instead of the server version. I don't really want to do that since this is, after all, a server.

Does anyone have any suggestions where I should go from here?

Thanks in advance.

---

### Post by dfreer on 2007-12-03
228 FPS is actually quite bad. My nvidia 7400, which is actually gets really low FPS in glxgears compared to others, gets about 2000 FPS.

The best thing would be if you let us know what sort of video card you have in your server. Restricted Drivers Manager makes things easier (because it uses a GUI interface), but that doesn't mean you *need* it to install your video card drivers.

---

### Post by steve_c on 2007-12-03
It's an ATI card. Sorry, I should've mentioned that earlier.

---

### Post by steve_c on 2008-04-16
This is an older thread of mine which I'm bumping because it's about to become relevant again.

I wound up solving this problem the first time by formatting and installing Ubuntu Desktop 64-bit on the server, then I could use the restricted drivers manager to install the proprietary ATI drivers and get hardware 3D acceleration.

That said, I've been keeping usage on the server minimal because I would like to back up and reinstall when Hardy is released (because it's an LTS release), and ideally I'd like to go back to the server edition. That said, I'll still need X libraries so that users can X-forward applications such as VMD to their desktops and 3D hardware acceleration most likely provided by proprietary drivers.

Will this be possible with the server version of Hardy? Have they fixed the bug that makes attempting to install proprietary video drivers ask for the non-existant restricted-drivers-manager-<kernelversion>-server package?

Thank you for any advice. I'm usually really uncomfortable with upgrading a production machine, but this has seen low usage thusfar and I believe it's for a good overall cause.

---

