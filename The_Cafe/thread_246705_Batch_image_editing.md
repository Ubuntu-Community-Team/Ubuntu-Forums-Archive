---
title: "Batch image editing?"
date: 2006-08-29
forum: The Cafe
---

### Post by hizaguchi on 2006-08-29
I love the Tango icon theme for it's simplicity and uniformity, but I'm really tired of all the blue.  I was thinking it would look nice if I could fade them all out to grey (reduce saturation, convert to black and white, etc.) and use them with one of the many nice grey gtk themes.  But there's a TON of these things!  Is there an app that I can just point at the theme directory and have it take care of this automatically?

---

### Post by IYY on 2006-08-29
The app you are looking for is called ImageMagick and I believe it's already installed in Dapper.

The command to perform a conversion is 'convert'. You can find many examples on the official ImageMagick site.

Here is an example:

convert -modulate 100,0 input.png  output.png

This will reduce saturation of image input.png to 0, and create image output.png out of it.

---

### Post by hizaguchi on 2006-08-29
Ah ha, thanks!

---

### Post by JacobK on 2009-11-23
Sorry for the mega-kick, but it's better than opening a new topic, I'd say.

Basically I want to do the same as the topic-starter. My theme looks really nice now, but I want the applet-icons to be grey, that would finish it. So what I have to do is select all files in /usr/share/icons, and all files in the subfolders in that, and saturize them.

 Can someone give a detailed how-to for that? :)

---

