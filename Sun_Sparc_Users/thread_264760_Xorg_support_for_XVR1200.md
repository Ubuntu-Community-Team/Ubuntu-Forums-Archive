---
title: "Xorg support for XVR1200"
date: 2006-09-25
forum: Sun Sparc Users
---

### Post by torches on 2006-09-25
I trying to get X.org server to run on a SPARC 2500 and the workstation has an XVR 1200 graphics adapter. I would like to know which driver works with it. 

Thanks

---

### Post by tideline on 2006-09-25
Do you have ubuntu installed yet?  Can you get to a command line?

Mike

---

### Post by netztier on 2006-09-25
> **torches said:**
> I trying to get X.org server to run on a SPARC 2500 and the workstation has an XVR 1200 graphics adapter. 

(typing with a nose turned slightly green out of sheer envy)

From [Sun's Website]("http://www.sun.com/desktop/products/graphics/xvr1200/") about the XRV-1200
> The Sun XVR-1200 graphics accelerator features a **3Dlabs Wildcat** graphics processing unit core and over 400 MB of on-board memory, including 128 MB of dedicated frame buffer memory, 256 MB of dedicated texture memory, and 32 MB of display list memory.

At present, I can't remember if X.org comes a 3Dlabs module driver - but once you're faced with the setup dialogue to choose you may better know what select.

*Edit: Best match for 3Dlabs chips seems to be the glint driver, according to [X.org]("http://wiki.x.org/wiki/VideoDrivers"). If it is available in Ubuntu-Sparc, please try it and give us some feedback.*

regards

Marc

---

### Post by mips on 2006-09-26
> **netztier said:**
> (typing with a nose turned slightly green out of sheer envy)


Ouch, those are pretty pricey, $2.5k

---

### Post by netztier on 2006-10-02
> **netztier said:**
> If it is available in Ubuntu-Sparc, please try it and give us some feedback.[/I]


"... And they never heard of him again."

Is it just me or has giving feedback to the forum become something unusual, that one just doesn't do anymore these days? (together with seemingly not using the forums for research anymore).

I for one am interested if the glint driver works with the XVR-1200 - and I would like to know if the information I provide is helpful at all.

So? a  bit of feedback, please? And it's perfectly OK to inform us that glint doesn't work at all with an XVR-1200.

kind regards

Marc

---

### Post by torches on 2006-10-03
man , give me a break !!!!! :) 

getting linux to work on a sparc is not part of my job. I just happened to have access to this H/W and wanted to try it out. 

anyway. I tried the glint driver and that did not work. 

here are the xorg.conf file

[[IMG]http://www.uploadtemple.com/thumb/thumb_txt.jpg[/IMG]](http://www.uploadtemple.com/view.php/1159874471.txt)

and Xorg.0.log

[[IMG]http://www.uploadtemple.com/thumb/thumb_txt.jpg[/IMG]](http://www.uploadtemple.com/view.php/1159874636.txt)

---

### Post by torches on 2006-10-03
I also found in the following in [http://auroralinux.org/cgi-bin/wiki.pl?HardwareCompatibility](http://auroralinux.org/cgi-bin/wiki.pl?HardwareCompatibility)

XVR-100 	Framebuffer 	None 	?  Does not work in Linux
XVR-500? 	Framebuffer 	None 	?  Never tested
XVR-600? 	Framebuffer 	None 	?  Never tested
XVR-1000 	Framebuffer 	None 	?  Does not work in Linux
XVR-1200? 	Framebuffer 	None 	?  Never tested
XVR-4000? 	Framebuffer 	None 	?  Never tested

so this does not look good.

---

### Post by netztier on 2006-10-09
> **torches said:**
> I also found in the following in [http://auroralinux.org/cgi-bin/wiki.pl?HardwareCompatibility](http://auroralinux.org/cgi-bin/wiki.pl?HardwareCompatibility)

XVR-100 	Framebuffer 	None 	?  Does not work in Linux
XVR-500? 	Framebuffer 	None 	?  Never tested
XVR-600? 	Framebuffer 	None 	?  Never tested
XVR-1000 	Framebuffer 	None 	?  Does not work in Linux
XVR-1200? 	Framebuffer 	None 	?  Never tested
XVR-4000? 	Framebuffer 	None 	?  Never tested

so this does not look good.

Definitely not. :( 

Why on the other hand does a SPARC port of the glint driver exist, then? Why would the maintainers go that way? Is there other graphics hardware by Sun for SPARC machines that is based on a 3Dlabs chip that would require the glint driver? :-k 

regards

Marc

---

