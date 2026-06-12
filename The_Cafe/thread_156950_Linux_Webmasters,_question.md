---
title: "Linux Webmasters, question"
date: 2006-04-08
forum: The Cafe
---

### Post by dolny on 2006-04-08
I want to create some small icons for my websites, like:

[http://www.simplebits.com/images/cube_birch.gif](http://www.simplebits.com/images/cube_birch.gif)
[http://www.simplebits.com/img/0306/icon-perm.gif](http://www.simplebits.com/img/0306/icon-perm.gif)

...but I don't know how. I tried Inscape, and then finishing touches with Photoshop/Gimp - but after resizing to icon size everything looks terrible.

What programs do you use for this purpose?
Maybe someone ran Ulead Gif Animator on Linux?

PS. I found mtpaint (seems good for icon creation!), you will probably have problems with compiling so I created a .deb package:
You can find it here [http://www.seattle-sound.com/trainchaser/ubuntu/](http://www.seattle-sound.com/trainchaser/ubuntu/)

It will probably give you an error when you'll be trying to run it, 
make a symbolic link from /usr/lib/libtiff.so.4 to /usr/lib/libtiff.so.3

Cheers.

---

### Post by majikstreet on 2006-04-08
well i know that mostly you make it in the size you want and zoom in huge.. that's pixel art, btw.

---

### Post by maruchan on 2006-04-08
Making icons that are small, yet look good, is hard work. You will have to learn a lot of little tips that icon designers use. There's a reason why this is really its own field.

And your discovery was correct: Drawing big and resizing is not going to work. That's because icon design is, in many ways, the same as drawing a cartoon caricature of a person. You can't draw their entire personality, and you have to do it quick, so you over-emphasize some features. If you just use a photo of somebody, your main idea (the basic gist of their character) may not get across. 

Important considerations:

-Icon silouhette (should be distinctive, not just a basic shape like a circle)
-Icon outline (should be discernable at all resolutions, and not break apart at low resolutions - this means you will have to magnify the border at low res.)
-Icon contrast (should be a good range of dark and light - not all greyish if you squint at it)
-Icon depth (consider using 3D features like highlights, drop shadows, etc.)
-Etc.

In my experience you should study the icons up close, figure out how many pixels you want for a border (things will be disproportionately sized at this resolution), highlights, shadows, details, etc.

It's not nearly as hard to create a good icon as it is to create lots of good icons with the same consistent style. This is why the GNOME team (and I think the KDE guys) have put together style guides for icon creation.

Here are some links I hope will help you:

[http://70.24.158.31:8080/inktut.php](http://70.24.158.31:8080/inktut.php)
[http://wiki.inkscape.org/wiki/index.php/Icons](http://wiki.inkscape.org/wiki/index.php/Icons)
[http://mmmaybe.gimp.org/tutorials/Creating_Icons/](http://mmmaybe.gimp.org/tutorials/Creating_Icons/)
Video of Jakub Steiner's workflow: [http://avc.sh.cvut.cz/archiv/index.php?id=1041&rid=278](http://avc.sh.cvut.cz/archiv/index.php?id=1041&rid=278) (It's cool but it's not in English - worth it to see him make a minidisc player icon in Inkscape and GIMP though; notice how he adds contrast to the border of the low-res version in GIMP, etc.)

General: [http://www.pixel2life.com/tutorials/Adobe_Photoshop/Icon_Creation/](http://www.pixel2life.com/tutorials/Adobe_Photoshop/Icon_Creation/)

Basic pixel art guidelines: [http://www.natomic.com/hosted/marks/mpat/](http://www.natomic.com/hosted/marks/mpat/)

Good luck! :)

---

### Post by JonJon on 2006-04-08
open those examples up in gimp or pixel or xara(?) or whatever your favorite it and zoom in about 5 to 10 times and see how they used shaded pixels and so forth to create a nice icon....

learn from example :)

---

### Post by dolny on 2006-04-08
Well, I created a couple of sprite characters for a game back in the days - so I know what pixel art is. Thank you for your comments and link guys.

---

