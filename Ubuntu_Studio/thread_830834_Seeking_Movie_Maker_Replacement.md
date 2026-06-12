---
title: "Seeking Movie Maker Replacement"
date: 2008-06-16
forum: Ubuntu Studio
---

### Post by BlueMonkMN on 2008-06-16
I'm trying to do my video editing in Ubuntu instead of Windows (I almost gave up halfway and tried to run MovieMaker under wine, but that didn't work very well).  I can't find any usable video editing application.  The problem with Avidemux is that it doesn't allow me to string together multiple clips into a single video.  The problems with Open Movie Editor is that the audio is not aligned with the video and it's not easy to do that manually, and I can't find an output format that reduces the size of the video (instead of increasing it) to a better compression ratio and includes the video (I've just spent too much time fiddling with it and getting nowhere most of the videos end up without any video).  The problem with Kino is that it doesn't work with video files like MPG or AVI as far as I can tell.  What should I be using as a Movie Maker replacement?

---

### Post by Exonimus on 2008-06-16
I tend to do quite some video editing in adobe premiere(on windows, that is) and I tried some programs on Ubuntu, none of which I really liked. I recently came across a program called kdenlive. I have yet to try it out, but you might want to try it.


just open a terminal and type

sudo apt-get install kdenlive


in my case, it didn't create a link to the menu, so you might want to create one, or just launch it from the command line(just type 'kdenlive' without the brackets)

---

### Post by BlueMonkMN on 2008-06-16
Among other output, I get this fatal error output when I try to run it:
```
KCrash: Application 'kdenlive' crashing...
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3600459
kdenlive: Fatal IO error: client killed
KCrash cannot reach kdeinit, launching directly.

```

This may have something to do with the fact that I'm running Gnome (simply because that's the first/default Ubuntu download I happened to find when I installed Ubuntu... if that makes any sense).

Any other ideas?

---

### Post by Exonimus on 2008-06-17
That's too bad.. it worked fine for me.

Anyway, I've done a bit of reading(I am in NO way an ubuntu expert, far from it, actually) and I found a link to a bug that has the same symptoms you describe. One person tells us he solved it by changing the 'video driver' setting in kdenlive. (Settings"->"Configure Kdenlive'' but that´s probably not much of a help since you can´t launch it. Another user says he got it to work properly by turning off desktop effects(again, I have no clue why this'd help, but I guess it's always worth a try!)

that you have gnome installed shouldn't have anything to do with the program not running. That is, I also don't have KDE installed.

also, if anyone else has an idea about why kdenlive crashes or has a better suggestion, please post :)

finally, I suggest also posting the problem on the kdenlive forums. They are the experts, after all.

[http://www.kdenlive.org/bbforum/viewforum.php?f=6](http://www.kdenlive.org/bbforum/viewforum.php?f=6)

---

### Post by BlueMonkMN on 2008-06-17
I finally found a custom output format that works in Open Movie Editor and gets OK compression (but not great): Video: FFMPEG MPEG-4; Audio: ima4

But a file created with this combination does not play in Windows.  So I'm still stumped by the output format... what works and what doesn't and why.

Maybe I'll try re-installing kdenlive and try some of the suggestions.  I am running on a non-open video driver (NVIDIA) in order to support all the desktop effects.

---

### Post by philc on 2008-06-17
I use Openmovieeditor quite a lot, but never render out to my intended final format from this application. Generally, I render my project to a high resolution QuickTime Motion JPEG. Then I transcode this file to my final output format using FFmpeg.

Sure, this adds an aditional step and more machine time, but it offer two advantages. Firstly, I have a high resolution master file that I can archive for the future. Secondly, using FFmpeg directly gives more finite control over encoding options which aren't all available in the OME export dialogues.

---

### Post by eye208 on 2008-06-17
Blender's video editor has FFMPEG export.

---

### Post by DAC1138 on 2008-06-19
I also think Open Movie Editor is a great tool (see my sig :) )

But Blender 3D also has a very powerful editor built into the sequencer. I have been playing with it the past few days and it's really really good. Check out using the blender sequencer. PapaSmurf (google him) has some video tutorials on using the sequencer to cut/splice/blend clips together.

---

