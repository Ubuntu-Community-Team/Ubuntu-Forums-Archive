---
title: "Multimedia in Firefox, WinXP Guest under Ubuntu Gutsy"
date: 2008-04-27
forum: Virtualisation
---

### Post by jwiggs on 2008-04-27
I have successfully installed WinXP Home in a VMWare virtual machine running under Ubuntu 7.10.  The hardware is a Dell Latitude D600 laptop with 1.25 GB of RAM and a 1.4 GHz P4 mobile CPU.  Inside the VM I've installed Firefox, OpenOffice 2.4, Quicktime, Adobe Flash player, and Adobe Acrobat Reader, all the most current downloads as of Apr. 26th, 2008.  VMWare was downloaded and installed from the tarball available on their website as of Wednesday, Apr 23rd, version 1.0.5.

   I have been trying to view multimedia inside the Firefox browser under the VM, and so far all attempts have hard-locked the VM, requiring me to do a reset.  This happens when viewing content from video.google.com, [www.rottentomatoes.com](www.rottentomatoes.com), and [www.apple.com/trailers](www.apple.com/trailers).  The former are both (I believe) Flash-based video, the latter are all Quicktime.  The players "start", indicating that the plugins are working inside the browser, but then things freeze up inside the VM such that nothing responds to mouse clicks, and even sending a "Ctrl-Alt-Del" from VMWare console has no effect.

   Has anyone successfully gotten multimedia applications working in this sort of setup?  Any pointers to documentation would be fantastic.  Google searching and searching the forums hasn't turned anything up yet, though I will continue.

   I primarily have this virtual machine set up so that my friend (the machine is not actually for me) will be able to use windows-specific software for things like her digital camera and video recorder, plus things like tax prep software.  Any reports on these sorts of applications would also be useful!

thanks,
Jim

---

### Post by dpj23 on 2008-04-27
I would recommend increasing the amount of RAM allocated for the host xp machine.  The spec's that you listed would allow you to increase the RAM...  I would try using 768mb...

---

