---
title: "how to make starcraft work"
date: 2009-07-04
forum: Wine
---

### Post by starcraftmaster on 2009-07-04
hey guys
i just got ubuntu
and its great thats why am keeping it:p
but i got one problem playing favorite game star craft
its very slow:mad:
i got nvidia drivers installed

so i looked on the wine website
it says to do this to fix the slowness:
__   Use the key "DirectDrawRenderer" and add that to your registry with the value "opengl"; you may also need to add the key "RenderTargetLockMode" with the value "readtex". 
   (Found under HKEY_CURRENT_USER/Software/Wine/Direct3D using regedit)

but the only one problem with that fix is i got no idea how to do it
they tell ya how to do it,  but its hard and where do i get reg edit from ?
i know how to use reg edit on windows and i changed things on the windows registry many times

so i need some help on how to change withs on wine

---

### Post by ChaiTan on 2009-07-04
Press Alt+F2 and type regedit

---

### Post by starcraftmaster on 2009-07-04
ok then
so i did all it said but it says to put a 2 values
but when i right click and then click new it has the option of 4 value keys
these are them: string value
binary value
dword value
multi string value

so which one do i choose?

---

### Post by ChaiTan on 2009-07-04
string value

---

### Post by starcraftmaster on 2009-07-04
well i did it
and it still slow
what do i do next ?

---

### Post by elitenoobboy on 2009-07-04
Make sure the string value is in the correct place (in the direct3d folder IIRC), then also make sure that its value is actually set (after making the string, right click on it then hit modify, then type the "opengl" or readtex into it to set it)

Also, make sure there are no typos.

Also, to patch the game, go to blizzards site and download it and apply it manually, I don't think it will update correctly if you try updating by using battle.net.

---

### Post by starcraftmaster on 2009-07-05
> **elitenoobboy said:**
> Make sure the string value is in the correct place (in the direct3d folder IIRC), then also make sure that its value is actually set (after making the string, right click on it then hit modify, then type the "opengl" or readtex into it to set it)

Also, make sure there are no typos.

Also, to patch the game, go to blizzards site and download it and apply it manually, I don't think it will update correctly if you try updating by using battle.net.

whats a IIRC?
mabye you can post a picture or two for me so i can see how to do it
i be very gratefully::)

---

