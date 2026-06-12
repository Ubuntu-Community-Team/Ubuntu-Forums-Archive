---
title: "Can Not See the Border"
date: 2007-03-11
forum: Ubuntu Customization Guide
---

### Post by novavon on 2007-03-11
I cannot see the window border after setting the window manager to beryl.
This is the output that I get when I turn it on.
I would appreciate any comment regarding this issue.

```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32

```

---

### Post by fktt on 2007-03-13
having the very same problem with it! :(

---

### Post by fktt on 2007-03-15
ok, sorry for the double post.. but, i got it working for me.. ^^''
so there just was an update for beryl.. (um for me at least..) and after that there still wasn't any window decorations.. so i thought id try to change some things..(im using nvidia geforce fx5200 btw) and got it to work!
heres what i did, real easy:
```

 >right-clicked the beryl-manager icon at the toolbar
  >Advanced Beryl options
   >Rendering path
     *changed to copy
```

yeah, i agree, ridiculously easy.. :oops:

---

### Post by darksong on 2007-03-17
I tried this, but i lost the functionality of beryl, any ideas?

---

### Post by rennen01 on 2007-03-18
Here is the guide I used to install Beryl.  I had some border issues as well, but I followed the instructions and everything works now.

[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

GL all.

---

### Post by rennen01 on 2007-03-18
More info:

[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=howto%3A+beryl](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=howto%3A+beryl)

---

### Post by snakecharmer on 2007-03-26
i have the same problem, when i maximize my window the border disappear, my semi-fix is:

1) In emerald theme manager chose a theme 
2) select edit-theme
3) set radius to 0
4) set left/right to 0

Strange but i can see the border...

Bye

---

### Post by tzulberti on 2007-03-26
That happened to me becuase i didn't installed emerald... Try to install emerald and emeral-themes

---

### Post by emorphien on 2007-05-20
> **snakecharmer said:**
> i have the same problem, when i maximize my window the border disappear, my semi-fix is:

1) In emerald theme manager chose a theme 
2) select edit-theme
3) set radius to 0
4) set left/right to 0

Strange but i can see the border...

Bye

Well, that works but it isn't exactly how I want to fix it myself.

---

