---
title: "browser fingerprinting - panopticlick (eff.org)"
date: 2010-01-27
forum: Security
---

### Post by njiii on 2010-01-27
browser fingerprinting - panopticlick  EFF has an interesting tool available: [https://panopticlick.eff.org/](https://panopticlick.eff.org/) 

technical details at [https://www.eff.org/deeplinks/2010/01/primer-information-theory-and-privacy](https://www.eff.org/deeplinks/2010/01/primer-information-theory-and-privacy) 

an interesting look at exactly how distinguishable your default browser configuration may be... 

[http://yro.slashdot.org/story/10/01/27/1638216/Tracking-Browsers-Without-Cookies-Or-IP-Addresses](http://yro.slashdot.org/story/10/01/27/1638216/Tracking-Browsers-Without-Cookies-Or-IP-Addresses)

---

### Post by tubbygweilo on 2010-01-27
Set it to IE something, Windows something and hide in the crowd - job done. The last thing you want is FreeBSD and Lynx browser or some other uncommon combination as you may well stick out like a sore thumb and attract attention.

---

### Post by Agent ME on 2010-01-27
It checks more than just the User Agent string.

---

### Post by Lars Noodén on 2010-01-28
> **Agent ME said:**
> It checks more than just the User Agent string.

You need to disable javascript, too.  For preventative measures, you need to talk some sense into web sites that fail to work without javascript, usually it also causes problems with compliance with accessibility regulations.  

A lot of pulldown menus, popout menus, pop ups, hovers, rollovers, popovers or what have you are fully available as CSS.  

See one example of pulldown menus:
[http://www.ubuntu-fi.org/](http://www.ubuntu-fi.org/)

By moving away from client side scripting, you save tons of development time and money, save lots of maintenance time and money, avoid lots of security problems, avoid lots of privacy problems and avoid lots of accessibility problems.

It's not 1998 anymore when only a few browsers supported a [small subset of CSS](http://www.w3.org/StyleSheets/Core/).  Nowadays the major browsers (forget the infamous [Microsoft Internet Explorer](http://news.bbc.co.uk/2/hi/technology/8465038.stm), I mean serious browsers not that) [support CSS](http://www.webstandards.org/action/acid2/) very well for many years.  These all support [CSS2](http://www.w3.org/TR/CSS2/) well.  [CSS3](http://www.css3.info/preview/) is in the final stages of standardization.

 [http://www.webstandards.org/action/acid2/](http://www.webstandards.org/action/acid2/)

---

