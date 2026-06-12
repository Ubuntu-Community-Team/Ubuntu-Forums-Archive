---
title: "Changing Wine style?"
date: 2009-05-31
forum: Wine
---

### Post by carlosgs91 on 2009-05-31
.

---

### Post by nolliecrooked on 2009-06-01
> **carlosgs91 said:**
> Hi, I'd like to know if there is any way to change Wine's program appearances. They look like Windows 98 and maybe there's an easy way to look them as Windows XP or more similar to my Ubuntu theme. I'd also like to know if you can change the pointer.
 
Thanks
 
yeah theres a couple of ways;
 
download this file;
 
[http://www.istartedsomething.com/uploads/royale_noir.zip](http://www.istartedsomething.com/uploads/royale_noir.zip)
 
extract it, then goto Applications>Wine>Configure Wine>Desktop Intergration. then click the "Install Theme" button and find the files you extracted, and click the one called luna. then on the left hand side of the "Install Theme" button, you will see a dropdown menu(called Themes), click it and select Royal Noir, and then click apply. and now you have the Windows XP Media Centre theme :)

---

### Post by carlosgs91 on 2009-06-01
.

---

### Post by nolliecrooked on 2009-06-01
> **carlosgs91 said:**
> Thanks it works perfectly ;)
 
And do you know how to change the pointer?
 
 
ummmmmm Ive never tried to change the pointer, Im about to reinstall Ubuntu anyway, so Ill see if I can find a way :)

---

### Post by carlosgs91 on 2009-06-01
.

---

### Post by nolliecrooked on 2009-06-01
> **carlosgs91 said:**
> Ok, good luck ;)
 
yeah ok, sorry you cant change the cursor **YET**
but its in the experimental stage.
 
you can add font smoothing to Wine, if that interests ya. 
 
heres the guide;
 
[http://www.ubuntu-inside.me/2009/03/easy-way-to-enable-font-smoothing-at.html](http://www.ubuntu-inside.me/2009/03/easy-way-to-enable-font-smoothing-at.html)
 
have fun :P

---

### Post by AndrewRiedi on 2009-06-03
Attached is the patchset I made (based off of Henri Verbeet's patches from ages ago) to:
1) Move cursors into server.
2) Implement .ani cursors completely.
3) Implement themed cursors.

They should just make Wine use your system cursors.  Good luck, and let me know how they go if you decide you want to try them out.  (Note: Using the patchset requires you to use recent Wine code and compile Wine yourself.  If there is enough demand for an Ubuntu package with said patchset, let me know.)

---

### Post by Vietman on 2009-10-04
> **AndrewRiedi said:**
> Attached is the patchset I made (based off of Henri Verbeet's patches from ages ago) to:
1) Move cursors into server.
2) Implement .ani cursors completely.
3) Implement themed cursors.

They should just make Wine use your system cursors.  Good luck, and let me know how they go if you decide you want to try them out.  (Note: Using the patchset requires you to use recent Wine code and compile Wine yourself.  If there is enough demand for an Ubuntu package with said patchset, let me know.)

Can you explain how to apply the patchset? I tried sudo bzcat cursor_work.tar.bz2| patch -p1 and i got several hunk failures.

---

