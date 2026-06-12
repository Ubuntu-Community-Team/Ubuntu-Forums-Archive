---
title: "Where's a decent movie maker clone?"
date: 2008-07-23
forum: The Cafe
---

### Post by miggols99 on 2008-07-23
I'm looking to make an installation guide for Arch Linux as a video. I've got the base video. All I need to do is add some text above it to tell you what to do. I tried kdenlive but it is very unstable and crashes all the time. Kino just sits there importing the video file. What else is out there that works quite well?

---

### Post by madjr on 2008-07-23
try avidemux

but save before doing the final step as i heard it sometimes crashes in that step.

so after 1 or 2 tries it will get the job done. I haven't tried the latest version thou

---

### Post by Orlsend on 2008-07-23
Sadly there is nothing more user friendly as WMM

Kino is the best user friendly for Linux

Cinerella is easy too, but a bit Funky...

While Avidmux its good but not user friendly...

---

### Post by artir on 2008-07-23
Canonical or somebody should put some money on this.

---

### Post by miggols99 on 2008-07-23
> **madjr said:**
> try avidemux

but save before doing the final step as i heard it sometimes crashes in that step.

so after 1 or 2 tries it will get the job done. I haven't tried the latest version thou
I've installed Avidemux. Now what? All it seems like is a video player and encoder and a bit of fixing up of the videos. Where can I get to the things I want?

---

### Post by ad_267 on 2008-07-23
Kino requires ffmpeg to import videos. Have a look at the recommended packages for kino.

---

### Post by zmjjmz on 2008-07-23
Try OpenMovieEditor?
Oh, on the other hand, there's something called Wink, while it's not a video editor, it's used for making software tutorials, and could be useful for this

---

### Post by fred_miller on 2008-07-23
> **miggols99 said:**
> I've installed Avidemux. Now what? All it seems like is a video player and encoder and a bit of fixing up of the videos. Where can I get to the things I want?

Google avidemux?   First hit you get [http://www.avidemux.org/admWiki/index.php?title=Main_Page](http://www.avidemux.org/admWiki/index.php?title=Main_Page)

---

### Post by Bungo Pony on 2008-07-23
Video editing is the ONLY reason I still use Windows. Once a decent video editor is developed for Linux, I can dump MS forever.

I even tried running Nero Vision in Wine with no success.

---

### Post by TBOL3 on 2008-07-23
Use blender, yes I mean the 3d graphics aplication blender.

What you need to do is, after you open it up, you should see a box SR:2-Model.  Click on it and choose 4-Sequence.  Then, you can add files in .mpg, .avi, .mov, and many others.  Then, Import the audio you want, and sync it with the video (you may need blender 2.46 to do this).  After that, go back into the modeling setup, and press space -> add -> text.  Make it how you want (yes, it is possible to make 2d text), and then go back to the sequencer.  Add the text.  Choose your resolution, file type, and using ffmpeg, choose multiplex audio.  Then click on Do seqence, and then click on ANIM.  By default, your movie should be hot and ready, waiting in the /tmp folder.

Enjoy (BTW, there are bettor instructions then this).

---

### Post by madjr on 2008-07-23
> **miggols99 said:**
> I've installed Avidemux. Now what? All it seems like is a video player and encoder and a bit of fixing up of the videos. Where can I get to the things I want?

here is the latest avidemux and a few others

[http://getdeb.net/category.php?id=12](http://getdeb.net/category.php?id=12)

---

### Post by samwyse on 2008-07-23
Avidemux is a linear editor. You probably want a non-linear editor.

---

### Post by TBOL3 on 2008-07-23
Also, if you decide not to try out blender, the only non-linear video editors that I know of are:

Pitvi (I think)
Kino
Cinalerra
Lives

But none of them are nearly as good a blender.

---

### Post by Ubuntiac on 2008-12-15
Blender totally rocks (especially the game engine and compositing), however for editing it's beaten hands down by Kdenlive 0.7. Just make sure not to get the buggy, year old, SVN grab version we have in the Ubuntu repos (0.6svn).

There's documentation in the Ubuntu community wiki docs on how to get the latest version, updated as often as you want with a shiny GUI.

It's worth mentioning too, since you mentioned Kino, that Kino's lead developer (Dan D) stopped development of Kino and now works on MLT/Kdenlive. :)

---

