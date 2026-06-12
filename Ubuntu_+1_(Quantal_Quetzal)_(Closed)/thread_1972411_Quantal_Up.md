---
title: "Quantal Up"
date: 2012-05-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by fjgaude on 2012-05-03
All looks as it should for this phase.

Kernel 3.4 working good along with gcc 4.7. gtkperf reads 4.7 for video speed, same as in 12.04, fast!

I was able to compile VMware Player, using Effenberg's patches that were used in 12.04. gcc4.7 was needed because kernels later that 3.2 used that version.

Now I wonder if Luca, Tista knows how much better kernel 3.4 is for GMA500 Poulsbo-type netbook machines? <smile>

---

### Post by lucazade on 2012-05-04
gma500_gfx kernel module should be slight better in 3.4.. I believe there are good improvements in DRM routines.
anyway I've still to try it :)

---

### Post by jerrylamos on 2012-05-04
3.4 dead in the water black screen after splash screen on my Compaq Presario 3.3 GHz with ATI radeon Xpress 200.  Message from flat screen says no input.  Only thing that works is Ctrl-Alt-Del.  I'm no developer but it acts like a kernel crash.

Yes, I did the libXfont.so.1.4.1 thing no change.  No Ctrl-Alt-F1 cli, nothing.  I'll try "broken packages" update again, since recovery mode does boot.  I'll try to look at syslog, Xorg.0.log, .xsession-errors, /var/log/crash, etc. from recovery mode.     

?

Jerry

Beaucoup updates & reboots & messing around finally booted...

---

### Post by fjgaude on 2012-05-04
> **lucazade said:**
> gma500_gfx kernel module should be slight better in 3.4.. I believe there are good improvements in DRM routines.
anyway I've still to try it :)

Hello, Luca... it's been awhile! My GMA500 works near perfectly in 12.04, but no resume after suspend. Brightness, audio, wifi, all else, all perfect. gtkperf speed has been 30.1 to 40 over the testing phase. Remember it was 70 in 10.04 and 300 in 11.10.

Good to hear DRM will make it better in kernel 3.4.

Thanks for the reply.

---

### Post by fjgaude on 2012-05-04
> **jerrylamos said:**
> 3.4 dead in the water black screen after splash screen on my Compaq Presario 3.3 GHz with ATI radeon Xpress 200.  Message from flat screen says no input.  Only thing that works is Ctrl-Alt-Del.  I'm no developer but it acts like a kernel crash.

Yes, I did the libXfont.so.1.4.1 thing no change.  No Ctrl-Alt-F1 cli, nothing.  I'll try "broken packages" update again, since recovery mode does boot.  I'll try to look at syslog, Xorg.0.log, .xsession-errors, /var/log/crash, etc. from recovery mode.     

?

Jerry

All I did was run recovery, then from a boot partition copied the libXfont file over into 12.10. Worked correctly, updates have been working, everything really like 12.04 for now!

---

### Post by fjgaude on 2012-05-04
@Luca, the resume is fixed by creating a file in /etc/pm/config.d like so:

```
gksu gedit /etc/pm/config.d/gma500
```

and adding this line in gma500:

```
ADD_PARAMETERS=&#8217;--quirk-vbemode-restore&#8217;
```

I'll wait to try 12.10 in it, after someone else tries. <smile>

---

