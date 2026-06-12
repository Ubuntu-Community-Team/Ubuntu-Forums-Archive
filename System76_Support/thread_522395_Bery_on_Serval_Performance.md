---
title: "Bery on Serval Performance"
date: 2007-08-10
forum: System76 Support
---

### Post by toddpedlar on 2007-08-10
I've just downloaded Beryl for my new Serval Performance, and when I select the Beryl Windows Manger (or Compiz, it doesn't matter) the title bars on all my windows disappear.  The desktop cube rotates fine, but since the title bars go away, I can't move windows around... so I'm outta luck.

Is there any known incompatibility between Beryl and the GeForce 7600 card that's installed on the Serval Performance?  Everything else is just great... but this isn't good the way it is.

Thanks,

Todd

---

### Post by thomasaaron on 2007-08-10
No, Beryl should work fine on the Serval.

It sounds like a theme issue. Are you using a custom theme from System > Preferences > Themes?

If so, I'm wondering if it might be incompatible with Beryl.

---

### Post by steveneddy on 2007-08-10
I own a serval performance laptop and I can assure you that it is not hardware related. You will have better luck searching the forums for, specifically the Desktop Customization section, for the answer to your dilemma. 

This question has been asked and answered many times over in other parts of the forums.

The key to getting the 3D effects working on any linux box is to get the nvidia settings correct before you jump into DL-ing Beryl or Compiz.

Try reading a few how-to's before jumping in over your head. You will be a lot happier.

Look [here]("http://ubuntuforums.org/showthread.php?t=272104") and [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#3-D_Desktops").

---

### Post by voidmage on 2007-08-10
I'm thinking you didn't install emerald. Try installing that and see if it works.

---

### Post by steveneddy on 2007-08-12
Try this [link]("http://ubuntuforums.org/showthread.php?t=489509").

Basically it says:

run this in terminal

```
sudo nvidia-xconfig --add-argb-glx-visuals
```

---

