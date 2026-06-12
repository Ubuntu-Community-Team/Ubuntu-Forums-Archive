---
title: "ubuntu 8.10 guest in vmware on vista--possible to get compiz desktop effects?"
date: 2009-03-02
forum: Virtualisation
---

### Post by rpardee on 2009-03-02
Hey All,

I'm dipping a toe in the ubuntu waters w/vmware player running on windows vista.  When I try to enable the fancy compiz desktop effects (system -> preferences -> appearance -> visual effects) I get a "Desktop Effects could not be enabled" dialog.  I *think* this is b/c vmware is hiding my real video card from ubuntu, thereby preventing ubuntu from using a 3d-capable driver.  (Is any of that plausible?)

At any rate, I guess my real question is, is it possible to enable compiz in a vmware player hosted instance of 8.10 running on vista?

Many thanks!

-Roy

---

### Post by LegendofTom on 2009-03-03
The virtualized video card VMware supplies the guest operating systems does not have 3D capabilities, so compiz is out of the question.  Just more reason to ditch that Vista and go solid Ubuntu.

---

### Post by divague on 2009-03-03
Maybe you could try installing ubuntu in virtualbox. The latest version has 3d capabilities.

---

### Post by pparks1 on 2009-03-03
I would have to bet that performance within a virtual environment for 3d graphics and Compiz...if it worked...would be quite poor.   The best bet is to play with Linux virtually and hold off on the desktop effects and stuff for down the road.

---

### Post by veloce on 2009-03-03
> **rpardee said:**
> Hey All,

I'm dipping a toe in the ubuntu waters w/vmware player running on windows vista.  When I try to enable the fancy compiz desktop effects (system -> preferences -> appearance -> visual effects) I get a "Desktop Effects could not be enabled" dialog.  I *think* this is b/c vmware is hiding my real video card from ubuntu, thereby preventing ubuntu from using a 3d-capable driver.  (Is any of that plausible?)

At any rate, I guess my real question is, is it possible to enable compiz in a vmware player hosted instance of 8.10 running on vista?

Many thanks!

-Roy

As noted the free versions of vmware do not support 3d graphics.  vmware workstation and fusion (for the Mac) both do.  

Hopefully the technology will "trickle down" to the free versions at some stage.

---

### Post by rpardee on 2009-03-04
Drat.  I was hoping to be able to use the avant window manager, and do other cool things.

I'll have a look at virtualbox--maybe that'll be the cheese...

Thanks all!

-Roy

---

### Post by jsodini on 2009-03-04
VMware Workstation & Fusion support DirectX 9 but not OpenGL. Once OpenGL is in the picture Compiz should run just fine.

-James

---

### Post by divague on 2009-04-06
This guy is running compiz in a virtual machine. He's using virtualbox.

/[http://christoph-langner.de/en/2009/03/compiz-und-3d-beschleunigung-in-virtualbox/]("http://christoph-langner.de/en/2009/03/compiz-und-3d-beschleunigung-in-virtualbox/")

---

### Post by rpardee on 2009-04-12
Ah--hopeful!  Thanks very much!

> **divague said:**
> This guy is running compiz in a virtual machine. He's using virtualbox.

/[http://christoph-langner.de/en/2009/03/compiz-und-3d-beschleunigung-in-virtualbox/]("http://christoph-langner.de/en/2009/03/compiz-und-3d-beschleunigung-in-virtualbox/")

---

