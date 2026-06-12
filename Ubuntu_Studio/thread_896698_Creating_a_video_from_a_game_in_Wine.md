---
title: "Creating a video from a game in Wine"
date: 2008-08-21
forum: Ubuntu Studio
---

### Post by jasontu on 2008-08-21
Hello all!

I am looking to create a video from captured footage in WoW run through Crossover games.  I know in Windows I would be using "fraps" along with whatever Sony editor thing I have.

Any tips on software for capturing footage in the game?  Any video editor software tips?

Thanks!

---

### Post by adrien214 on 2008-08-21
there are few desktop recording applications listed [here]("http://www.linux.com/feature/141593"), but for my part I have used recordmydekstop, just get it from apt-get... (sudo apt-get install recordmydesktop).

concerning the video editing, I'd  give KINO a try (apt-get install kino)

---

### Post by jasontu on 2008-08-21
recordmydesktop was a little too scant for me.  I started the program in the terminal and had no idea where the file was going or what the settings were.  I can't find it in the GUI menu anywhere.  

I'm trying Istanbul for now.  I'll keep you posted.

---

### Post by avik on 2008-08-21
Try XVidCap, which the article says is the most versatile.  In my limited experience, it works great.

---

### Post by adrien214 on 2008-08-22
> **jasontu said:**
> recordmydesktop was a little too scant for me...

sorry about that, I forgot to mention gtk-recordmydesktop...

it's the GUI of RmD...

just apt-get install it and it will show up in your Sound&video menu !

The GUI allows you to manage the detail settings.
Once you press "record", the gtk-recordmydesktop window will be reduced to a blue "square" (actually a "stop" button) in the system tray.

Click on the "stop" when you are done and then you can save your video, the output is *.ogg (you can open it in kino), so if you need, you can encode your video in avi, just do the following:

get ffmpeg 


```
 sudo apt-get install ffmpeg 
```

then, to convert your file, type the following in your terminal:

```
 ffmpeg -i /path/to/your/file.ogg  -f avi  /path/to/converted/file.avi 
```


if you want to have a different video format or play around with ffmpeg (very powerful), I recommend you [COLOR="Red"][this site]("http://www.itbroadcastanddigitalcinema.com/ffmpeg_howto.html#Encoding_MPEG-2_I-frame_only_in_Highest_Quality").[/COLOR]

---

### Post by Ferrat on 2008-08-25
Don't use the tools to record desktop, they are useless for recording games, often take to much resources or don't work well with OpenGL ect. 

Use a program like yukon or glc, glc is easier, records both sound and picture and has a Ubuntu install script that works really well, yukon is a little diffrent, sound should record but is only working for some but it records OpenGL really good and not much preformance drop when using, also the creator of yukon designed with using WoW and many of his examples are from WoW. One of them are much better than a desktop recording app.

Here is a recording of mine from yukon, Dungeons and Dragons Online (via launchscript and wine) 

[http://www.youtube.com/watch?v=YcFQDgPtx-4](http://www.youtube.com/watch?v=YcFQDgPtx-4)

---

### Post by Rhubarb on 2008-08-25
You're correct Ferrat, yukon is quite difficult to setup and install, glc is best.  You do need to dabble around in the terminal to get it running, to execute it, and then to encode a video from it.  But it's worth doing, because glc does an impressive job.

GLC web page:
[http://nullkey.ath.cx/projects/glc/](http://nullkey.ath.cx/projects/glc/)

The Ubuntu forums thread:
[http://ubuntuforums.org/showthread.php?t=587935](http://ubuntuforums.org/showthread.php?t=587935)

---

