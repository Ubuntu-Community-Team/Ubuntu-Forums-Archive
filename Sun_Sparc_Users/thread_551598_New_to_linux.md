---
title: "New to linux"
date: 2007-09-15
forum: Sun Sparc Users
---

### Post by charlie-s on 2007-09-15
I am new to linux, but have just recently acquired a sparc ultra60 with solaris 10 loaded on it. after reading about Ubuntu, I wanted to load it with a desktop rev. 
After reading this thread, it appears that I can only run a server version.

I have a desktop rev 7 loaded on an old pc and will be using it with my wife's business, would really like to let her use that one and I use the ultra60 as my workstation. 

Will I be able to do so running the server version?

---

### Post by jcastill on 2007-09-15
you can install any GUI on the Ultra60, just read the forums on how to make the X11 server work.

---

### Post by USPB on 2007-09-30
I tried this but it doest work

---

### Post by jfinkels on 2007-09-30
> **USPB said:**
> I tried this but it doest work

What problems are you having exactly?

In general, the procedure for installing a server with a GUI is to

1. Install the server using the server install iso for your specific architecture (SPARC in your case).

2. Type the following:```
sudo aptitude install ubuntu-desktop
``` or ```
sudo aptitude install kubuntu-desktop
``` or ```
sudo aptitude install xubuntu-desktop
``` or ```
sudo aptitude install fluxbox
``` or ```
sudo aptitude install openbox
``` to get all the functionality of the Ubuntu desktop versions. Installing, for example, the "ubuntu-desktop" meta-package will install all programs necessary to run and install GUI applications (in the case of ubuntu-desktop GNOME and gtk dependencies, in the case of kubuntu-desktop KDE and Qt dependencies, in the case of xubuntu-desktop XFCE, etc.)

---

### Post by zanderred on 2007-09-30
[QUOTE=charlie-s;3369677]I am new to linux, but have just recently acquired a sparc ultra60 with solaris 10 loaded on it. after reading about Ubuntu, I wanted to load it with a desktop rev. 
After reading this thread, it appears that I can only run a server version.

 Xubuntu, (Xubuntu/ports/sparc) this sould give you a desktop :)

---

