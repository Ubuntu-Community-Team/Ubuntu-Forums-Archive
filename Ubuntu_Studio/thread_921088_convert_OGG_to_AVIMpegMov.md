---
title: "convert OGG to AVI/Mpeg/Mov"
date: 2008-09-15
forum: Ubuntu Studio
---

### Post by kestal on 2008-09-15
I know, OGG is great. I use it for a lot of things. However, I also use video editing software on my XP parition which does not support OGG/MKV input.

What would be the quickest/easiest/painless way to do this? (if any, at all). The program I use in XP is Ulead Video Studio.

---

### Post by Creative2 on 2008-09-16
mm if you have ubuntu i think it's better winff or pytube
if you kubuntu you could try fuoco tools it works fine in gnome too but it's a bit different from the others , winff pytube
for fuoco tools i am sure if you convert into mov they will be played nice on win xp

---

### Post by eye208 on 2008-09-16
mencoder **file.ogg** -ovc xvid -oac mp3lame -xvidencopts fixed_quant=2 -lameopts cbr:br=128:aq=0 -o **file.avi**

---

