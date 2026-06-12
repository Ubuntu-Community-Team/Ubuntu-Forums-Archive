---
title: "Some progress booting on Nexus One"
date: 2010-05-14
forum: Ubuntu Moblin Remix
---

### Post by SeaWeedz on 2010-05-14
Hi

I followed the really awesome directions provided by jairuncaloth at [http://forum.xda-developers.com/showthread.php?t=631389](http://forum.xda-developers.com/showthread.php?t=631389) but made some tweaks to try to work with a Ubuntu Netbook Remix install.  

It actually went very well, and it booted into X on my first try.  

This was my debootstrap command:
sudo debootstrap --arch=armel --foreign --verbose --include=ubuntu-netbook lucid /media/rootfs

Now for the bad news..  the Nexus one doesnt respond to any input.  Touch screen, volume, power, trackball..nothing.  It's running, the clock keeps ticking, but I can't do anything with it.  Also, adb doesn't show a device when ubuntu is loaded, and I haven't been able to ssh into the phone yet.  I thought maybe I could do a remote desktop connection or something to get started.  

Trying to render and upload the video to youtube..using PiTiVi.  Not sure what settings I have to use..

---

