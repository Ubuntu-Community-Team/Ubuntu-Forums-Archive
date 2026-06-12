---
title: "Gimp doesn't cut it with PSDs"
date: 2009-04-08
forum: Ubuntu Studio
---

### Post by imaginarythomas on 2009-04-08
I'm a web developer and I just switched to Ubuntu at work. One part of my duties is taking PSDs (Photoshop documents) and cutting them up and whatnot to make them into beautiful websites.

The problem is GIMP's support of PSDs leaves much to be desired. Some layers don't show, it renders text, etc.

Is there a better solution for using PSDs in Ubuntu?

---

### Post by mcduck on 2009-04-08
Not really. PSD is Adobe's proprietary file format and only Adobe's own programs have full support for it.

If possible, I recommend using some other file format. If not, then you could try installing Photoshop in Ubuntu with Wine.

---

### Post by ragtag on 2009-04-09
GIMP tends to have better luck with older versions of the Photoshop format. I know some versions of Photoshop let you save to older versions of the format, so that might help. Or if you don't need all the layer info, you could ask whoever is making the images for you to give you a flattened tif or png file instead.

Secondly, Photoshop 7 runs okay under WINE, while more recent versions are much harder to get to run. I don't think CS3 runs at any usable level. You can run any version of Photoshop in a virtual machine, such as VMWare or VirtualBox, but this requires a Windows license.

---

### Post by kayosiii on 2009-04-10
The specifications for photo shop files up to version six was available to third parties newer versions are not. Any features that are newer than or have been changed since version six do not work.

There isn't really a good solution to this at the moment. You could try multilayer tiffs though Gimp will only read and not export these.... so multilayer tiff from photoshop to gimp psd from gimp to photoshop. Either that or ask for flat images.

---

### Post by wkulecz on 2009-04-10
Yup the PSD format is how Adobe holds your data hostage.

--wally.

---

