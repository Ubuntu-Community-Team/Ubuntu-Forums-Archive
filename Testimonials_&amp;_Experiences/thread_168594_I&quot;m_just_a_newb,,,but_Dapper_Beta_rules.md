---
title: "I&quot;m just a newb,,,but Dapper Beta rules"
date: 2006-04-30
forum: Testimonials &amp; Experiences
---

### Post by gordong11 on 2006-04-30
I just installed the new Dabber Beta 2, and I think it's a huge step forward in the right direction! Still a bit buggy....but OMG they made it much easier for us newb's. Just my thoughts on 6.06. I actually got Mepg-2 DVD's to work flawlessly in less than 2 minutes... never got it to work in breezy.

I also didn't have to install video drivers(although I'm not sure if it just took it from old install...but I chose erase entire disk during install). I would need to check and see if it defaulted to VESA or if it has the new Nvidia drivers built-in...either way it was much easier than "dpkg-reconfigure Xserver-xorg". would be cool to know which driver I'm running...any ideas on how to check it?

I actually did the full install while running the Live version...genius!

Plus the built-in help files were a big plus. I have only played with it an hour, but so far it looks great.....can't wait till June. Far and away the best Linux distro, made even better.

---

### Post by nalmeth on 2006-04-30
Yeah, I think dapper is looking slick and more slick so far
to just look at your xorg.conf, type this in the terminal
cat /etc/X11/xorg.conf

---

### Post by gordong11 on 2006-05-07
Cool, 

I checked the x11.conf and I am running the nv drivers on dapper. Good to know, I also just upgraded from a 7600GT to a 7900GT yesterday...no issues whatsoever. I'm just glad I no longer have install the nvidia drivers, or go into Vesa to have my video working.

How much more optimal is it to have the 8756 Nvidia driver, over the standard nv driver? I really don't want to go down that road again, since I was never able to get the 8756 drivers working in 5.10. If it makes a huge difference I may give a go again.

Thanks

---

### Post by testube_babies on 2006-05-07
I find the biggest performance difference between the nv drivers and the nvidia drivers comes when working in 3D, especially with OpenGL.  If this isn't something you need, and you already know that installing the nvidia drivers on your machine is a big hassle, you might just want to skip it.

Although, 8756 is included in the Dapper repositories.  Maybe the hassle came from installing it manually in 5.10?  If that's the case, try installing via apt-get or Synaptic.  I believe the packages you need are nvidia-glx and nvidia-kernel-common.

---

### Post by Scunizi on 2006-05-08
The latest nv drivers are in Synaptic labeled nvidia-glx.  After that just edit the xorg file changing nv to nvidia.  restart and try running glxgears from the command line.  There is a thread that shows several different methods to install by hand.  But what a hassle.  It's nice that you can click and go... mostly!

---

### Post by jason.b.c on 2006-05-08
What i'm curious to know is, when will **Dapper ** be ready from **Ship it** ??:confused:

---

### Post by nanotube on 2006-05-08
[QUOTE=jason.b.c]What i'm curious to know is, when will **Dapper ** be ready from **Ship it** ??:confused:[/QUOTE]
i'm guessing june 1 - the planned release date?

---

### Post by ubuntu_demon on 2006-05-08
I moved this thread to Testimonials.

shipit.ubuntu.com says :
> 
    * Please note requests usually take from 4 to 6 weeks to deliver, depending on the country of shipping.
...
...
We are currently taking requests for Ubuntu 5.10 (Breezy Badger). If you are interested in requesting Ubuntu 6.06 (Dapper Drake), please check back with us again around mid-May 2006.


So if you order them before june then I hope you will get them in july.

---

