---
title: "Gimp Doesn't Work!"
date: 2009-08-09
forum: Ubuntu Studio
---

### Post by AndrooUK on 2009-08-09
Hey, I've always had problems with Gimp (usually fill bucket never worked), but now I can't draw with a paintbrush or pencil, use gradients, fill, or type text. Nothing shows up, and there isn't even an undo option for the actions I try to perform (except adding text, which shows up as a layer, but is not visible).

I tried reinstalling Gimp and that hasn't helped.

This is so annoying!

Any suggestions?  Thanks!

---

### Post by jerrrys on 2009-08-09
I had problems with gimp once and resolved it by doing a complete uninstall and reinstall.

---

### Post by mcduck on 2009-08-10
> **AndrooUK said:**
> Hey, I've always had problems with Gimp (usually fill bucket never worked), but now I can't draw with a paintbrush or pencil, use gradients, fill, or type text. Nothing shows up, and there isn't even an undo option for the actions I try to perform (except adding text, which shows up as a layer, but is not visible).

I tried reinstalling Gimp and that hasn't helped.

This is so annoying!

Any suggestions?  Thanks!

Does this happen when you create a new image, or when you are editing existing image? If it happens when editing an image make sure the image is set to RGB mode (Image->Mode->RGB). Most tools can't be used in indexed color mode.

---

### Post by AndrooUK on 2009-08-19
> **mcduck said:**
> Does this happen when you create a new image, or when you are editing existing image? If it happens when editing an image make sure the image is set to RGB mode (Image->Mode->RGB). Most tools can't be used in indexed color mode.

This happens for new images and when editing images. I've tried to reinstall Gimp, but this doesn't help.

I'm not sure if an upgrade has broken Gimp, because it used to work fine, most of the time.

The only thing I can think of now is reinstalling Ubuntu, which I'd rather not try.

---

### Post by mcduck on 2009-08-19
> **AndrooUK said:**
> This happens for new images and when editing images. I've tried to reinstall Gimp, but this doesn't help.

I'm not sure if an upgrade has broken Gimp, because it used to work fine, most of the time.

The only thing I can think of now is reinstalling Ubuntu, which I'd rather not try.
Have you tried removing Gimp's configuration files? (reinstalling Gimp doesn't remove your personal configuration files, located in ~/.gimp-2.6).

---

### Post by AndrooUK on 2009-08-19
> **mcduck said:**
> Have you tried removing Gimp's configuration files? (reinstalling Gimp doesn't remove your personal configuration files, located in ~/.gimp-2.6).

Oh hey, it works great now. Funny, when I told it to completely remove Gimp (and its configuration files) they were still there!

Thank you very much! :)

---

### Post by mcduck on 2009-08-19
> **AndrooUK said:**
> Oh hey, it works great now. Funny, when I told it to completely remove Gimp (and its configuration files) they were still there!

Thank you very much! :)

The "complete remove"-option will only remove system-wide configuration files. The package manager will never, ever touch files in user's home directories. They belong to the user.

Anyway, great that this solved the problem. :)

---

### Post by zaug on 2010-11-12
Thanks!
This fixed the same issues with my Gimp install.
\\:D/

---

### Post by christopherbalz on 2013-01-27
The approach described above worked for me.  On Ubuntu 12.04 LTS, all up to date, using Synaptic to completely remove gimp, gimp-data, and gimp libraries, and manually removing ~/.gimp-2.6, and then using the Ubuntu Software Store to install Gimp and Xsane again, worked.

---

