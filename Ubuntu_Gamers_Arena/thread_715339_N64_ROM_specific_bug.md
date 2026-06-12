---
title: "N64 ROM specific bug"
date: 2008-03-04
forum: Ubuntu Gamers Arena
---

### Post by ace214 on 2008-03-04
This happens in Project64 in WINE and in native Mupen64. In Zelda OoT Master Quest, my hearts don't show up all the time. When I have 2 or  3 hearts (out of the 3) only two show up. When I have 1 heart, the first one and the empty 3rd one show up. I am using Rice's video plugin, with OpenGL. Any help would be greatly appreciated.

UPDATE: The problem seems to be caused by OpenGL as it occurs under Windows as well.

Now I need to know how to make DirectX work under WINE because it results in a black screen for me...


EDIT: Followed [this guide]("http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html") to install DirectX under WINE. But now stuff displays even weirder....

---

### Post by forrestcupp on 2008-03-08
Try the glN64 plugin in Mupen64.  I'm playing that game without any trouble.  You may have a bad ROM, too.

---

### Post by ace214 on 2008-03-12
What video settings do you have? Cus when I try to use that plug-in lots of things are messed up... More than before...

---

### Post by ace214 on 2008-03-13
Ok for anyone searching for this problem, Rice's video plugin needs the Primary Depth hack and Near Z Plane options checked. Found the answer here:

[http://www.emutalk.net/archive/index.php/t-26320-p-2.html](http://www.emutalk.net/archive/index.php/t-26320-p-2.html)

Now able to use Mupen64 :-)

---

