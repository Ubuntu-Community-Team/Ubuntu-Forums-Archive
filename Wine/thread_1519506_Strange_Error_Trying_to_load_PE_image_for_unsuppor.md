---
title: "Strange Error: Trying to load PE image for unsupported architecture (I386)"
date: 2010-06-28
forum: Wine
---

### Post by Steyr on 2010-06-28
Hey, I'm trying to install EVE Online, a game verified to work with wine. However, when I try to run the installer from the GUI I get nothing, and when I run from the command line i get the error "Trying to load PE image for unsupported architecture (I386)".

As I understand, this is an error you usually get when you try to run a 32 bit program with the 64 bit version of wine. However, as far as I know I have the 32 bit version. I am using a 64 bit processor, and I think that my Ubuntu install is also x64, but according to the wiki it seems that using the package installer should still give me the 32 bit version.

I've repeatedly uninstalled and reinstalled through the Ubuntu software center, uninstalled then reinstalled using the method on winehq, uninstalled then reinstalled via command line, and I'm still getting this error. I would build from source, but I'm not sure how, as the last time I used unix was 8 or 10 years ago and my command line skills are VERY rusty.

I'm running Lucid Lynx. Can anyone give me some help with this?

---

### Post by cogadh on 2010-06-28
Sounds like you don't have the ia32-libs package installed.

---

### Post by Steyr on 2010-06-28
> Sounds like you don't have the ia32-libs package installed. 	
I do. Got it with getlibs. Checked in the software center just to make sure, and yeah, ia32-libs is installed.

---

### Post by Steyr on 2010-06-28
FIXED! Built from source, then deleted my old .wine folder in my home directory. Thanks!

---

