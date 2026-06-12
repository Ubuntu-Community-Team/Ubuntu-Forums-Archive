---
title: "Wine issues on Ubuntu 8.10 32-bit"
date: 2009-01-25
forum: Wine
---

### Post by MrPatrick on 2009-01-25
I am having issues with Wine. Neither 1.0.1 or 1.1.13 works on my laptop.
I downloaded the Wine folder for 1.0.1 then the Steam Installer, but when I tried to execute the file "SteamInstaller.msi", it said:

"The program 'wine' is not currently installed. You can install it by typing: sudo apt-get install wine."

So, I typed that, and when it would've finished installing so I could install Steam, it said:

"E: Couldn't find package wine"

What do I do to fix this?

---

### Post by Cresho on 2009-01-25
Your repo is not set up.

fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.  put a checkmark on all minus source code unless you want that.

---

### Post by MrPatrick on 2009-01-25
> **Cresho said:**
> Your repo is not set up.

fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.  put a checkmark on all minus source code unless you want that.

Oh, okay. Thanks.

---

### Post by TIMU-Is-My-Username on 2009-01-26
> **Cresho said:**
> Your repo is not set up.

fix software sources "Download from" usa to main server.  update the resources.  It is in Administration->Software Sources.  put a checkmark on all minus source code unless you want that.

Okay, I DEFINITELY did that, and I'm still having the problem.
The things checked:
"http://archive.canocical.com/ubuntu intrepid partner"
"http://archive.canocical.com/ubuntu intrepid partner (Source Code"
"WineHQ - Ubuntu 8.10 "Intrepid Ibex""

I don't have internet connection on my laptop though.  :(

---

### Post by TIMU-Is-My-Username on 2009-01-26
Oh, and I think mine is a 64-bit.  I don't know how to get any 32-bit libraries.

---

### Post by Cresho on 2009-01-26
sudo apt-get update
sudo apt-get upgrade

then open up synaptic manager and search for wine.

mark for install, 

wine

then click apply

---

