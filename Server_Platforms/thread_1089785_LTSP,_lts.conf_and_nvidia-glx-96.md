---
title: "LTSP, lts.conf and nvidia-glx-96"
date: 2009-03-07
forum: Server Platforms
---

### Post by kfleten on 2009-03-07
I have a LTSP environment running Edubuntu 8.10, and with some of the clients having a Nvidia Geforce2 Integrated GPU. Those clients goes for 800x600 in resolution, but I would prefer 1024x768.:-k

I have found out that the right drivers for this is the nvidia-glx-96. I have installed this, and made a "sudo ltsp-update-image --arch i386" (my server is x64). Then I have modified /var/lib/tftpboot/ltsp/i386/lts.conf adding the lines:
[00:E0:18:AE:94:8E]
   XSERVER = nvidia-glx-96
   X_MODE_0  = 1024x768

When I do this, the client starts up, and the display turns black. If I remove the "XSERVER = nvidia-glx-96"-line, the client boots up in 800x600 resolution. The "X_MODE_0  = 1024x768"-line seems to have no effect.

Is there any suggestions how to solve this ?

---

### Post by kfleten on 2009-03-11
I can see that old Nvidia cards do not work very well with Ubuntu 8.10:
[http://techreport.com/forums/viewtopic.php?f=7&t=64554](http://techreport.com/forums/viewtopic.php?f=7&t=64554)

However I can see that the latest release (09. March 2009) of the legacy-glx-96 driver from Nvidia adds support for recent Linux 2.6 kernels and X.Org server 1.5 and 1.6 ! Maybe time has come ?

Now, - how do I easily upgrade the legacy-glx-96 driver on a x64 Edubuntu 8.10 LTSP server with x86 clients ?

---

### Post by kfleten on 2009-03-12
I have taken it a step further:
downloaded both "NVIDIA-Linux-x86-96.43.11-pkg1.run" and "NVIDIA-Linux-x86_64-96.43.11-pkg2.run" from NVIDIA's homepage. The installer quits because there is no supported Nvidia GPU on the system I install on. I know that ! It's the clients ! But how do I tell this to the server ?

---

### Post by kfleten on 2009-03-16
Actually, it seems like the installer don't quit because there is no Nvidia GPU, but because the X system still runs. How do I quit the X server on a Edubuntu server ?

Have tried "sudo init 1", but this brings the server to rescue mode, and my sudo password does not work in this state for some reason ? How can I get into a text based environment on a Edubuntu server ?

"sudo /etc/init.d/gdm stop" also just brings me to the rescue mode.

---

### Post by PerryMason on 2009-03-29
Trying somewhat the same.
[http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg31778.html](http://www.mail-archive.com/ltsp-discuss@lists.sourceforge.net/msg31778.html)
[http://www.ltsp.org/~sbalneav/LTSPManual.html#chroot](http://www.ltsp.org/~sbalneav/LTSPManual.html#chroot)

I'm using ubuntu 9.04 beta on a vm-server and ran into a mus problem after i upgraded, so i can't say it will work.

---

