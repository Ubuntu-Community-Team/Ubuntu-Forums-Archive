---
title: "Animated GIF supported video editor???"
date: 2009-09-28
forum: Ubuntu Studio
---

### Post by JBabz on 2009-09-28
Hello everyone!
I was wondering i have some pivot stickfigure animations and am making more and i got pivot working completely in WINE, but i really need the gifs to go onto youtube, and i cant find any ubuntu movie editing software that supports animated gifs or converters for ubuntu that can convert gif to avi or something, so was just wonderin if anyone knew of any software that could.
Thanks!

P.S. Here is two of my anis, they arent really that good, just wanted to show you them.
[http://public.animatorhost.com/superstick2uks3.gif](http://public.animatorhost.com/superstick2uks3.gif)
[http://public.animatorhost.com/superstick16hc9.gif](http://public.animatorhost.com/superstick16hc9.gif)

---

### Post by bitchricu on 2009-09-28
Glad to hear you're using this: I plan to keep it much more aggressively up-to-date than has been the case in the past, but don't hesitate to let me know if you find errors or need clarifications.:)

---

### Post by JBabz on 2009-09-29
Ummmm...if you havent noticed what i am posting about is one big error XD.

---

### Post by cotcot on 2009-09-29
This is something for Blender. I have not done it meself. I used blender mainly as video editor. But blender is made to animate 3D drawings. And [[COLOR="Red"]here[/COLOR]]("http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/Creating_animated_GIFs_using_Blender_and_Gimp") is a tut on animated gifs.

---

### Post by JBabz on 2009-09-30
Blender doesnt support animated gifs, and i dont want to know how to make them, i already do that, i wanna know how to get a video editor that has support for them so i can put my pivots on youtube.

---

### Post by VertexPusher on 2009-09-30
GraphicsMagick can convert animated GIFs to image sequences which can be loaded into most video editors.

---

### Post by JBabz on 2009-09-30
you know what, i am just going to save it as an image sequence, thanks for bringing that up, should have remembered that.

---

### Post by JBabz on 2009-10-02
well, turns out that in kdenlive it takes so many images that it simply doesnt load, so the question still lies, is there any movie editor that supports animated gifs?

---

### Post by justsomedude on 2009-10-02
You could try mencoder. Does kdenlive take Motion JPEG?

```
mencoder superstick2uks3.gif -o test.avi -ovc lavc -lavcopts vcodec=mjpeg
```

---

### Post by JBabz on 2009-10-10
ok, i am going to try that right now

---

### Post by JBabz on 2009-10-10
omg, it actually worked, except now the frame rate is screwy, any ideas?

---

### Post by JBabz on 2009-10-12
hello???

---

### Post by hellocatfood on 2010-01-06
Hey, maybe I can help. For the command line option I haven't used mencoder before, but I have used ffmpeg. The command I'd use is
```
ffmpeg -i image%03d.jpg -r 10 -b 1000 film.avi
```

the bit after "-i" specifies the input images. "%05d" is there because it specifies the amoutn of 0s in the image file name e.g. if each jpg was named image00001.jpg image00002.jpg etc I'd use -i image%05d.jpg. If they were named image002.jpg etc I'd use image%03d.jpg. I think you get the idea.

The important part, which relates to your problem is "-r", which is the framerate. If you animation is originally 20 frames per second, put "-r 20", for 5 frames per second put "-r 5". The "-b 1000" specifies the bitrate. THe higher the number the clearer the image but the larger the file.

Another option, which would be better for those who don't like to use the command line, is to use the GAP plugin for GIMP. Once you have it installed open up all of the frames as layers and then go to Video > Master Videoencoder and choose your preferred settings there.

I hope this helps!

---

