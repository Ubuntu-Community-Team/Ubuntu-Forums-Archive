---
title: "Using xorg edgers ppa with QQ"
date: 2012-08-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ELD on 2012-08-02
Okay guys I have a question here about testing;

I have an nvidia optimus laptop and only the newer nvidia beta drivers work with The Bumblebee Project for my chip (its a new chip).

So i needed to add the xorg edgers PPA to for when i installed TBP for it to grab the newer drivers, it also upgraded a load of xorg stuff like intel drivers and all that.

After this was installed I removed the xorg edgers PPA.

So to my question - will it mess anything up for me while testing? If newer versions come into main ubuntu repo will it overwrite the xorg edgers ppa versions I have at the moment?

---

### Post by dino99 on 2012-08-02
> **ELD said:**
> 
So to my question - will it mess anything up for me while testing? 

[COLOR="Magenta"]you will know if you test it :P[/COLOR]

If newer versions come into main ubuntu repo will it overwrite the xorg edgers ppa versions I have at the moment?

the greatest version always overwrite minor version.

Thats said if you fail into troubles, then simply purge edgers ppa.

---

### Post by Harry33 on 2012-08-02
And you must be able to work from the console, if you loose the desktop functionality. That may very well happen with xorg-edgers with a new xserver.

---

