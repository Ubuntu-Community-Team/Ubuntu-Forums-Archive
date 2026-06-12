---
title: "make the desktop and applications menu icon sizes bigger in ubuntu studio"
date: 2015-01-07
forum: Ubuntu Studio
---

### Post by mrule on 2015-01-07
Hi all, sorry if this is a repeat, but I can't seem to figure it out. The applications menu icons and desktop icons are too small in ubuntu studio. All the information i am finding seems to relate to config files that don't exist on my machine, or apply to other versions of ubuntu not ubuntustudio.

Does anyone know how to do this? I've done it in the past I just can't find the options anymore. 
Thanks!

---

### Post by bhilmers2 on 2015-01-07
> **mrule said:**
> The applications menu icons and desktop icons are too small in ubuntu studio.

What version of Ubuntu Studio are you using? I can give you instructions for 14.04+.

Changing the Desktop icon size is straightforward. Open the menu and choose "Settings Manager > Desktop > Icons" and raise the value of Icon Size.

I don't know of a way to change the menu icons other than increasing the system font size, which would be "Settings Manager > Appearance > Fonts" and increasing the point size. This is probably not what you want.

You can make some of the panel icons bigger by increasing the panel size in pixles: "Settings Manager > Panel > Row size"

Maybe you want to lower the screen resolution so everything seems bigger? Hope this helps a little.

---

### Post by mrule on 2015-01-08
Thanks bhilmers! 

I found the desktop icon size setting, that works great! I know that there is a way to adjust the applications icon menu size independently of other system properties ( e.g. fonts / dpi / global icon size ), because I used to be able to do it on other machines. If I recall correctly, it just involves manually editing a config file somewhere. The trouble is, all the documented tutorials I am finding for this use config files I can't seem to find. My guess is that these tutorials assume some basic knowledge about how X or XFCE is configured that I simply do not have.

---

### Post by bhilmers2 on 2015-01-08
I decided to look into this problem further and it seems the option to enlarge icons is no longer global, but theme dependent. In other words, you would have to make changes for every icon theme you use. Here is [a thread]("http://ubuntuforums.org/showthread.php?t=2219919&p=13004304#post13004304") from earlier this year with the same problem. The index files mentioned on that page would be located in the folders under /usr/share/icons/, but I have yet to make this work and I'm out of time for the day.

---

### Post by bhilmers2 on 2015-01-09
I figured it out! I was able to easily change the menu icon setting using a method found on the XFCE forum: [https://forum.xfce.org/viewtopic.php?pid=17078#p17078](https://forum.xfce.org/viewtopic.php?pid=17078#p17078)

If you want to use the GUI instead of the command line, follow this path:

Settings Manager > Settings Editor > xsettings >IconSizes, then edit the value to say gtk-menu=24,24

I really like how it looks, I'm glad I worked on this thread (mark it solved if this method works for you). Have a good day.

---

### Post by mrule on 2015-01-10
Beautiful! Thank you so much, it looks great!

---

