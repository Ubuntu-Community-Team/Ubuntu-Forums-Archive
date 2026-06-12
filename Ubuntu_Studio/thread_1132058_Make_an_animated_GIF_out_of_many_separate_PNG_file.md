---
title: "Make an animated GIF out of many separate PNG files?"
date: 2009-04-21
forum: Ubuntu Studio
---

### Post by crazyfuturamanoob on 2009-04-21
I got plenty of PNG's called "somefile 0001, somefile 0002, somefile 0003".

Any software for combining the frames into one neat GIF?

---

### Post by lukeiamyourfather on 2009-04-22
GIF is probably not the best way to view a sequence of PNG files. The PNG files are usually 8-bits per channel color with a possible 16,777,216 colors and GIF supports a maximum of 256 colors per image (from within 8-bit color range).

Putting the PNG sequence into a Flash document or compressed video would be a better way to go. FFMPEG can help to get the image sequence into a video. Cheers!

---

### Post by FakeOutdoorsman on 2009-04-22
ImageMagick would definately be able to do this (this is an untested command):
```
convert -delay 10 -loop 0 inputfiles*.png animaion.gif
```

[Examples of ImageMagick Usage](http://www.imagemagick.org/Usage/)

---

### Post by crazyfuturamanoob on 2009-04-22
The PNG's are ripped from a very old game which uses 256 color palette so the image quality stays the same.

Thanks man :D Now I have plenty of cool smileys for IM and animated avatars for forums.


But how can I apply a color key for the frames? I don't like this blue background:
[img]http://img210.imageshack.us/img210/2747/wrench.gif[/img]


PS. RED ALERT 2 IS THE BEST GAME EVER!
:guitar:

---

### Post by wsonar on 2009-04-22
easiest way I have ever made gif's besides flash is adobe image ready comes installed with photochop you can put the images in a folder then open the folder as frames so each image becomes a frame and then you can choose the time to delay then save as a .gif 

not sure the best open-source solution tho I'll have to look into that image magik

---

### Post by crazyfuturamanoob on 2009-04-23
I first made an animated gif with your command, then I tried to remove the blue background with this:
```

convert wrench.gif -alpha set -channel RGBA -fill none -opaque blue wrench2.gif

```

Result:
[img]http://img7.imageshack.us/img7/5606/wrench2.gif[/img]

What happened? What's wrong with that? I want new frames to replace the old ones, not merge!



Edit: Solved, correct colorkeying command:
```

convert -dispose previous wrench.gif -alpha set -channel RGBA -fill none -opaque blue wrench2.gif

```

[img]http://img264.imageshack.us/img264/5606/wrench2.gif[/img]

---

### Post by skullmunky on 2009-04-25
Fantastic!  

We should start an ubuntu surf club, e.g.

[http://nastynets.com/](http://nastynets.com/)

---

### Post by elliotn on 2009-04-25
Wow I always wanted to remove the bg color in my pics

---

### Post by loell on 2009-04-25
you might also want animated PNGs (APNGs)

much smoother imho

[http://people.mozilla.com/~dolske/apng/demo.html]("http://people.mozilla.com/~dolske/apng/demo.html")

---

