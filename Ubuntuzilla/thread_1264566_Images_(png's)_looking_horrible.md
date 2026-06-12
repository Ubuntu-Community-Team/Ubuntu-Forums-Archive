---
title: "Images (png's) looking horrible"
date: 2009-09-12
forum: Ubuntuzilla
---

### Post by Prosis on 2009-09-12
I've just installed, not as sudo, Firefox 3.5.

Problem is that now many images appear horribly, greenish and pinkish (see screenshot).

What can I do?

Thanks :)

Edit: Oh never mind.  Here's a soution:

-Go to about:config 
-Search for gfx.color_management.mode.  If it's not set to 2 try to do so and restart Firefox
-If it is then search for gfx.color_management.display_profile
-Search for a color profile: find / -name "*.icm"
-The one I found was: /usr/share/ImageMagick-6.4.5/config/sRGB.icm
-Set the value to the one you found and restart Firefox.

Problem solved! :)

---

### Post by nanotube on 2009-09-12
heh wow, never seen that before...
thanks for sharing your solution! :)

---

### Post by Prosis on 2009-09-13
Pleasure! :)

On my Mint Linux, the text has a weird color but I don't know if that's connected :P

---

