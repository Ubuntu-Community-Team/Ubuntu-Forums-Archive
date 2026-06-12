---
title: "A Windows scripting question (sorry!)"
date: 2009-08-18
forum: The Cafe
---

### Post by decoherence on 2009-08-18
Didn't there used to be an "other OS" forum? Well, I couldn't find it. Anyway, this is a question for anyone familiar with Windows scripting (vbs, i guess)

I need to implement a drag and drop video encoding doo-dad for XP. Basically, you would drag an MPEG2 on to an icon and it would spit out a similarly named WMV. I need this in order to support Windows Movie Maker (barf).

I have Windows Media Encoder installed and, according to [this article]("http://www.microsoft.com/windows/windowsmedia/howto/articles/AutomatingEncoding.aspx") I can use the command line to encode.

So basically what I'm wondering is if it's possible to trigger that command line by dropping a file on an icon and whether that file's name can be accessed in the script (a la $1.)

ADD: by way of example, to do this in GNOME you would write a script that references $1, then create a launcher that runs the script. When you drag a file on the to launcher icon, the script will run and $1 will be set to the path of the file you were dragging (i didn't know this before now, actually. very handy! surely it's just as easy to do in Windows? haha)

---

### Post by koenn on 2009-08-18
it probably works the same in windows : create a desktop shortcut that runs a script   (a bacth file, i.e e text file with extension .bat), use %1  as a positional parameter to pass the filepath/name, then in the script, again use %1 to pass the filename to the converter utility  your documentation refers to.

Maybe you can just  call that cscript command line with %1 directly from the launcer, i don't know.

If you want it all in vbs, look here for how to  pass arguments to vbscripts
[http://users.telenet.be/mydotcom/howto/scripts/tricks.htm](http://users.telenet.be/mydotcom/howto/scripts/tricks.htm)


Other than that, you're probably better of on a windows scripting forum.

---

### Post by Chronon on 2009-08-18
koenn, the %1 trick should work fine.  Here's a sample Windows batch file for converting an input file to MPEG in VLC that uses this method.  

[http://www.rockbox.org/twiki/pub/Main/PluginMpegplayer/VLC-transcode.bat](http://www.rockbox.org/twiki/pub/Main/PluginMpegplayer/VLC-transcode.bat)

---

### Post by koenn on 2009-08-18
cool.

---

### Post by decoherence on 2009-08-18
Yay! Thank you, both! I'm glad it's a similar method.

```
echo %1 > output.txt
```

behaves like I expect when I drag a file on it, which is all I care about until I get to work tomorrow. Thanks for posting that VLC bat, too; I may use that instead.

OK that's my quota of Windows questions on this forum for this year ;)
:guitar:

---

### Post by Chronon on 2009-08-18
You're welcome. I'm glad I could help. :)

---

