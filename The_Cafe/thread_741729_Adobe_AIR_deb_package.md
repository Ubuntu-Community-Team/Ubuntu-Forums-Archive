---
title: "Adobe AIR deb package"
date: 2008-04-01
forum: The Cafe
---

### Post by JT673 on 2008-04-01
I have completely no idea why you'd want a deb package...Other than if you're remastering (making a custom LiveCD/DVD) (like I am):

[http://www.mediafire.com/?x2xymf72k0x](http://www.mediafire.com/?x2xymf72k0x)

What I did was:

1) I downloaded and installed the .BIN file like Adobe said.
2) Look in /tmp.  There should be two folders that start with "air.".  Go in to the one that has the directory "build" in it, and go into that.
3) ```
cp -r opt/Adobe\ AIR/Versions/1.0/control/ DEBIAN
```
This will copy the control and post/pre install scripts.
4) ```
cd .. && dpkg -b build adobeair-enu_0.1alpha_i386.deb
```

That should do it.

---

### Post by loell on 2008-04-01
hmm, interesting, will this also add an entry in the menu like the bin does?

---

### Post by JT673 on 2008-04-01
> **loell said:**
> hmm, interesting, will this also add an entry in the menu like the bin does?

Yep (all the files are decompressed into those two folders in /tmp)

---

### Post by loell on 2008-04-01
> **JT673 said:**
> Yep (all the files are decompressed into those two folders in /tmp)

i'm kinda skeptical, how that would add the entry in the gnome menu, if its just copying the original files into the /tmp directory.

---

### Post by JT673 on 2008-04-02
> **loell said:**
> i'm kinda skeptical, how that would add the entry in the gnome menu, if its just copying the original files into the /tmp directory.

No, it unpacks into the /tmp dir, then copies all the files into your root folder.  That's why there's a "opt" and  "usr" folder in "build"; it overlays onto of your system, like layers in GIMP/Photoshop.

---

### Post by loell on 2008-04-02
i see :)

---

### Post by ZephyrXero on 2009-06-04
> **JT673 said:**
> I have completely no idea why you'd want a deb package...

Oh I don't know...maybe perhaps I might want to easily uninstall Air one day, or ::gasp:: upgrade ;)

---

