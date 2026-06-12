---
title: "Window Controls moved to right hand side"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by imafatmess on 2012-04-21
The Windows Controls (max, min, close) have been moved to the right hand side without me realising. I was just wondering, how would I go about changing it back to the left and does anyone know why this might have happened?

I changed the theme a few days ago, but now back to standard Ambiance. Probably no effect but thought I'd add it. I really don't understand this at all!

Thanks for any help :)

---

### Post by JRV on 2012-04-22
Install ubuntu-tweak with the commands:```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

```

Run ubuntu-tweak
click on Tweaks
click on Window Manager Settings

---

### Post by kansasnoob on 2012-04-22
My step #6 here might be helpful:

[http://ubuntuforums.org/showpost.php?p=11835822&postcount=389](http://ubuntuforums.org/showpost.php?p=11835822&postcount=389)

---

### Post by Dngrsone on 2012-04-22
The theme change likely is what caused the effect-- a lot of people still hung up about having those controls on the right...

Unless a theme specifically calls for the controls to be in a specific location, they will remain where they were last set.

---

### Post by imafatmess on 2012-04-22
Thanks for the help. However it still doesn't answer why it happened. The theme had the window buttons on the left hand side and it happened a day or two after I changed back! This implies to me that it has nothing to do with it.

However, I guess I will just have to live in ignorance. One of the oddities of Ubuntu I guess; it all adds to its character!

---

### Post by sammiev on 2012-04-22
Sometimes when you play with different themes, some of them will not take place till you reboot your computer. If you only reboot every few days, then this can happen.

---

### Post by mc4man on 2012-04-22
Possibly your metacity settings where changed somehow. 
close,minimize,maximize: means buttons on the left
:close,minimize,maximize  buttons on the right

if you have gconf-editor installed can be checked, set, adjusted there
(apps/metacity/general/button_layout

---

