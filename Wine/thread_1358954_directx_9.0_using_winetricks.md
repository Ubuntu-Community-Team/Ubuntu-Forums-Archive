---
title: "directx 9.0 using winetricks"
date: 2009-12-19
forum: Wine
---

### Post by andjustmaybe on 2009-12-19
Im trying to install directx9.0 using winetricks. I get to the last step of installation and the installer asks me to close all applications and click next so it can restart my computer. I did and i click next and nothing happens so the installation won't finish. I tried just manually restarting and directx wasn't installed. Im new to Linux so i don't know much. 

Thanks for the help.

---

### Post by beastrace91 on 2009-12-19
> directx9      MS DirectX 9 user redistributable (not recommended! use d3dx9 instead)

The above is from the [Winetricks Wiki Page](http://wiki.winehq.org/winetricks) - that being said did you try to install the directx9 package or did you install the latter mentioned package **d3dx9**? If you are trying to install the form, try the latter and see if it works for your needs.

Regards,
~Jeff

---

### Post by andjustmaybe on 2009-12-19
I was trying to intstall the directx 9.0 package. I also tried the d3dx9 as you suggested but it won't run the game. i need the actual directx 9.0. Every time i try to run the game i get the error message "Video Card or Driver doesn't support enough textures for the directx 9 code path." Any ideas?

---

### Post by beastrace91 on 2009-12-19
Hrm, what application are you trying to run?

~Jeff

---

### Post by andjustmaybe on 2009-12-19
Call of Duty 4

---

### Post by beastrace91 on 2009-12-19
What Wine version? (To find this out run **wine --version** in terminal) Sorry should have asked this sooner.

Regards,
~Jeff

---

### Post by andjustmaybe on 2009-12-20
Version 1.0.1

---

### Post by beastrace91 on 2009-12-20
> **andjustmaybe said:**
> Version 1.0.1

Upgrade your Wine to the [latest beta](www.winehq.org/download/deb). Then try the game - if that still does not work *then* install directX - it should work under the new Wine version.

~Jeff

---

### Post by andjustmaybe on 2009-12-20
Ok thanks i'll give it a try

---

### Post by andjustmaybe on 2009-12-20
It worked great thanks a lot

---

