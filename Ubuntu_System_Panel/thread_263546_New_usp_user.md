---
title: "New usp user"
date: 2006-09-23
forum: Ubuntu System Panel
---

### Post by jcrnan on 2006-09-23
So, I have some problems and Im kinda confused.

1. my theme changes some the colors of only some of the panels in usp. Is there any way I can change the colors to what I want or make the theme not change the colors of the panel?

2. How do I install plugins?


3. Is there any way to make somewhat more minimalistic? I do like it but its very large. Even on my 1200x800 screen it takes almost a third of the screen.

---

### Post by Henry Rayker on 2006-09-23
I have the same problem with the size. I think a lot of the problem is the size of the icons. Fooling around with the configurations allowed me to drop the size of some icons, but not others.

---

### Post by Henry Rayker on 2006-09-24
no ideas?

---

### Post by chanders on 2006-09-24
> **jcrnan said:**
> So, I have some problems and Im kinda confused.

1. my theme changes some the colors of only some of the panels in usp. Is there any way I can change the colors to what I want or make the theme not change the colors of the panel?

2. How do I install plugins?


3. Is there any way to make somewhat more minimalistic? I do like it but its very large. Even on my 1200x800 screen it takes almost a third of the screen.

1. You can check the "use_custom_color" in gconf editor under /apps/usp and set the color. That way USP matches your GTK theme. All other colors in USP is determined by the GTK theme you use

2. This is doccumented very well in the Howto thread and the main Release thread. Essentially you put plugins in ~/.usp/plugins and add them to "/apps/plugins_list" in gconf editor

3. Not with the current version. But USP2 when released shortly will contain USPSlab which is a minimalistic menu. I used a 1200x800 screen before and you are right, it takes up a lot of space...

---

### Post by jcrnan on 2006-09-24
I checked the use system colors but it still mixes the black theme color with the light gray.

---

### Post by Briquet on 2006-09-24
I made some mockups of the USP [http://ubuntuforums.org/showthread.php?t=230439](http://ubuntuforums.org/showthread.php?t=230439) , maybe you like the USP that way, hopefully one day they'll become true as a plugin :D 
Cheers

---

### Post by chanders on 2006-09-25
I know you guys are waiting for me to get this done as a plugin.. It is still on the timeline. As soon as USP2 is out, this will be my next project along with USPKickoff... :-)

---

