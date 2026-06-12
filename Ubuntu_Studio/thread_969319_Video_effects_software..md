---
title: "Video effects software."
date: 2008-11-03
forum: Ubuntu Studio
---

### Post by fidde88pven on 2008-11-03
Hi!

For long Ive wanted to swap from Windows to Linux but the problems has been many.

My "latest" big issue is about movie editing.

Ive found a lot of medium quality editors for linux (like Kdenlive, Kino, Cinelerra, Blender, Lives, Open movie editor, pitivi and so on). 

The editing part is therefore, for me, covered, but the video effects of this apps is not perfect...

I would like to know if there is some app that can add these effects:

These I would like to be found in the editing sofware:
Titleeffects
Slow/fast motion
Colorchange (Sepia etc.)
Motionfilter (shows motions in for example blue)

These could be put on after the film has been edited:
Noise reduction video/audio
Film looks (like Magic Bullet for Vegas etc.) !REALLY WANTED!
FPS change from 24/25-whatever

If I new anything about making plugins or even my own software, I would try to fix this, but now I really dont so...

Hope someone can help me, regards Fredrik (sorry for bad english)

---

### Post by paulmerchant on 2008-11-03
As you've probably already figured out, you'll want to work in a modular fashion in Linux and use different applications for different steps in your editing process. What works best for you will depend on a number of things.

For changing frame rates, smoothing motion, sharpening, adjusting color spaces, etc., you might want to look into Avidemux. It gives you a GUI to do quite a bit of video processing and transcoding.

If you're editing with Blender's sequence editor, you should probably use Blender for titles and most of your effects (glows, etc.). The same would apply for some of the other editors.

For audio, you may want to use a completely separate application. For example, after editing, you can export your main audio track into something like Ardour and then run noise reduction, compression, add a music bed, etc. Ardour will allow you to work with audio in sync with a video stream.

I hope these tips help.

---

### Post by cotcot on 2008-11-03
Slow/fast motion and frame fps changes : Blender VSE can do this

Sepia effect : is included in kdenlive. 

Color effects : Blender and Cinelerra

Title effects : I make my titles in Gimp ; there you can get a lot of effect. However it is better to use blender 3D but I am not so far yet in learning blender.

---

### Post by fidde88pven on 2008-11-04
Thanx for replies!

Did actually know some of the things you wrote, but the rest was helpful!

One thing I cant make out is... How to use Blender, I get the basics, but I think it is not good at all. Any GOOD video blender-instruction-links?
I presume google gives a few...


Anymore ideas?
Regards Fredrik

---

### Post by brokenjack on 2009-03-07
I know this is an old post but had to comment. I too would love to work with video in linux. For some reason though, most of the applications I've used in linux don't really work that great, and there doesn't seem to be much enthusiasm in creating a NLE thats geared towards the creative editor. I think you are looking for something like After Effects. There was an exciting prospect I discovered called Jahshaka, but it hasn't been developed that much and the public release didn't work for me. Blender on the other hand (even though it's difficult to learn) has to be the greatest contributions to open source software ever.

---

### Post by cotcot on 2009-03-08
Both blender and cinelerra allow a lot of creativity. Both will be more appreciated the more you study their good manuals and tutorials (Blender essential for blender; cinelerra on-line manual from the cinelerra website is very good as well). With creativity I mean keyframing (blender and cinelerra), camera/projector (cinelerra), masks (cinelerra and blender), node editor (blender) and 3D animation (blender).
I am sure that at least 90 % of the critics against these apps disappear if you allow enough time to study the manuals.

---

### Post by ispyamoose on 2009-03-08
> **fidde88pven said:**
> Thanx for replies!

Did actually know some of the things you wrote, but the rest was helpful!

One thing I cant make out is... How to use Blender, I get the basics, but I think it is not good at all. Any GOOD video blender-instruction-links?
I presume google gives a few...


Anymore ideas?
Regards Fredrik

I have used Blender for around 2 years, and it is a very good program. A good source of tutorials can be found [here]("http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro").

If you want to see what Blender is capable of, check [this]("http://www.vimeo.com/1084537").

---

### Post by buloyz on 2009-03-20
hi! i am new to ubuntu... have been using windows vista on this hard drive & installed ubuntu on my other hard drive. my question is, what is the adobe after effects counterpart on ubuntu? i am making youtube videos and i use AE a lot for my lower third animations, opening billboards, etc. 
this is a sample of the graphics i do on AE, is it possible to make an identical one on ubuntu?
[Sample graphics]("http://www.youtube.com/watch?v=JLWdqxZFoqE")

thanks and more power^^

---

