---
title: "LTSP Client - i915/i945 Failed to load Driver(s)"
date: 2014-04-24
forum: Server Platforms
---

### Post by charlieott on 2014-04-24
When using PXE Boot Thin Client on my Laptop with 64-bit Centrino vPro with 2GB RAM:

**developer@ltsp:~$ glxgears**
**libGL error: failed to load driver: i945**
**libGL error: Try again with LIBGL_DEBUG=verbose for more details.**
**384 frames in 5.0 seconds = 76.739 FPS**

This was quite acceptable, even though the libGL error occured.  Scrolling and fullscreen youtube video worked fine.

However, when using the targeted thin clients: [http://www.disklessworkstations.com/1700-series-thin-clients.html#spec](http://www.disklessworkstations.com/1700-series-thin-clients.html#spec)
I get the following results:

**developer@ltsp:~$ glxgears**
**libGL error: failed to load driver: i915**
**libGL error: Try again with LIBGL_DEBUG=verbose for more details.**
**105 frames in 5.0 seconds = 20.858 FPS**


Now video's are quite choppy and, scrolling is delayed.  Which will not be acceptable to the end users.  I speculate the thin clients are using 'software rendering' instead of using the actual integrated GPU?

There are a lot of packages in the repository with the words "intel" and "Xorg".  Since this is a thin client image, running Xserver, I'm not sure how to properly update the drivers in the image.  Also interesting is this:

ltsp@ltsp:~$ dpkg --list | grep video-intel
ii  xserver-xorg-video-intel-lts-saucy         2:2.99.904-0ubuntu2.1~precise1      X.Org X server -- **Intel i8xx, i9xx display driver**


Notice the description mentions the i9xx series drivers are included with the package?  Now when i list the files in that package...



ltsp@ltsp:~$ dpkg -L xserver-xorg-video-intel-lts-saucy
/.
/usr
/usr/lib
/usr/lib/xorg
/usr/lib/xorg/modules
/usr/lib/xorg/modules/drivers
/usr/lib/xorg/modules/drivers/intel_drv.so
/usr/lib/libI810XvMC.so.1.0.0
/usr/lib/libIntelXvMC.so.1.0.0
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/xserver-xorg-video-intel-lts-saucy
/usr/share/doc
/usr/share/doc/xserver-xorg-video-intel-lts-saucy
/usr/share/doc/xserver-xorg-video-intel-lts-saucy/README
/usr/share/doc/xserver-xorg-video-intel-lts-saucy/NEWS.gz
/usr/share/doc/xserver-xorg-video-intel-lts-saucy/README.Debian
/usr/share/doc/xserver-xorg-video-intel-lts-saucy/copyright
/usr/share/doc/xserver-xorg-video-intel-lts-saucy/changelog.Debian.gz
/usr/share/man
/usr/share/man/man4
/usr/share/man/man4/intel.4.gz
/usr/share/bug
/usr/share/bug/xserver-xorg-video-intel
/usr/lib/libI810XvMC.so.1
/usr/lib/libIntelXvMC.so.1
/usr/share/bug/xserver-xorg-video-intel/script


I don't actually see anything that lends me to believe the intel i9xx drivers are included.(which are ironically the ones i am missing?) However, it could just be a configuration issue with the thin clients?

I used the LTSP Server installation mode, and did not make any custom modifications to the X settings.  Could someone explain a few things to me?

1.) Why does glxgears claim the driver cannot be found?
2.) How do I update the video driver being used by the thin clients booting from the ramfs image?

Currently, I've just been using chroot to login to the image filesystem, and then making changes, followed by an image rebuild.

Thanks in advance to anyone who can help.

Also i set DIRECTX=True, since i don't need the ssh -X encryption for now.  This didn't really help.  As i assumed it wouldnt since the more powerful laptop ran ~70 FPS on the same configuration.

---

### Post by charlieott on 2014-04-24
Update: Verbose glxgears output from thin client:

developer@ltsp:~$ export LIBGL_DEBUG=verbose
developer@ltsp:~$ glxgears
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/i915_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/i915_dri.so
libGL error: failed to authenticate magic 59
libGL error: failed to load driver: i915
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /home/developer/.drirc: No such file or directory.
libGL: Can't open configuration file /home/developer/.drirc: No such file or directory.


[https://bugs.freedesktop.org/show_bug.cgi?id=51400](https://bugs.freedesktop.org/show_bug.cgi?id=51400) 
It looks like it could be a bug.  I guess I'll have to find out what packages need to be updated.

---

### Post by charlieott on 2014-04-24
Okay, i think i see an issue here.  In the above post, it looks like the driver is in the x86_64 path... Which would indicate that the driver is 64-bit.  However, this thin client is 32 bit.  It may be some kind of mix up, since i have both amd64 and i386 thin clients.  

The original install of LTSP Server generated amd64 client image.  I had to manually create the 32 bit ones by specifying the --arch i386 parameter when building the image, then modify the DHCP to load the i386 image based on host mac address.

Thoughts?  Anyone???

---

### Post by charlieott on 2014-04-25
worked it all out.  The glxgears was being run on the server.  In order to run applications at the local thin/thick client you must use ltsp-localapps <cmd>

Of course, the default client built by the LTSP server does not have glxgears, which is part of the mesa-utils package.

So, chroot into the image, 32bit or 64:

$ sudo chroot /opt/ltsp/i386||amd64

$ apt-get install mesa-utils
$ exit

$ sudo ltsp-build-image -a i386||amd64

Then, bounce your client.  When it comes back up, run $ ltsp-localapps glxgears

Should see a drastic improvement, as the xsession is now using a localhost Unix Socket, and not streaming the frames from the LTSP server.




I still think there is probably some optimization that can be done with the client/server X connection to get better results running from the server.  As I mentioned before, other PCs I have used as thin clients show better results, even as high as 77 frames per second when running on the ltsp server.  This leads me to believe that there is some kind of codec or decompression that is straining the thin client's CPU, causing low framerate.
Anyway, marking as solved for now.

---

