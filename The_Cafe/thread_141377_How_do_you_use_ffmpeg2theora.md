---
title: "How do you use ffmpeg2theora?"
date: 2006-03-08
forum: The Cafe
---

### Post by FISHERMAN on 2006-03-08
How do you use ffmpeg2theora? I've searched and serched, but I couldn't really find an answer.
I probably should tell that a relative newbie with CLI.
Example: I have a file XYZ.avi and I want to convert it to a theora file(with ffmpeg2theora). What should I do?

---

### Post by John.Michael.Kane on 2006-03-08
[http://www.dogphilosophy.net/SECTION-Technical_Stuff/ogg-theora-microhowto.html](http://www.dogphilosophy.net/SECTION-Technical_Stuff/ogg-theora-microhowto.html)
[http://www.annodex.net/anx_theora.html](http://www.annodex.net/anx_theora.html)
[http://www.v2v.cc/~j/ffmpeg2theora/](http://www.v2v.cc/~j/ffmpeg2theora/)
[http://www.videolan.org/doc/videolan-howto/en/ch09.html](http://www.videolan.org/doc/videolan-howto/en/ch09.html)

---

### Post by JuanC on 2006-03-15
Take a look here :
[http://www.v2v.cc/~j/ffmpeg2theora/examples.html](http://www.v2v.cc/~j/ffmpeg2theora/examples.html)

Example :
*ffmpeg2theora -v 7 -a 3 XYZ.avi*

This output a XYZ.ogg file with Video Quality 7 (of 10) and Audio Quality 3 (of 10).

For more info type *ffmpeg2theora -h*

---

### Post by Lovechild on 2006-03-16
oh.. now I can finally wath all these old vids - great tools, if only it was a GStreamer 0.10 based app then it would handle more formats

---

### Post by H.E. Pennypacker on 2006-07-25
To use ffmpeg2theora, first go to the folder the video file is located it in (using *cd* command).  Then, type ffmpeg2theora filename.extension (e.g. susie.mpg).  It will then convert the file into Ogg Theora without changing anything, and without replacing the original file.

I highly recommend Ogg Theora for saving space without losing video quality.  Ogg Theora files are generally smaller when converted, and they still retain their quality.

So far, I have had luck with all MPG videos, and on and off luck with WMV, MOV, and AVI using ffmpeg2theora.

---

### Post by zachsmith88 on 2010-11-30
I have figured out how to use this for converting single files really well.  However, when I use:
$ ffmpeg2theora *.flv

to convert all files associated with that type they don't keep their original file names.  In fact the input files are at the bottom of the alphabet and they end up getting renamed to whatever file is at the top of the alphabet.

If anyone has some insight on this issue that would be great.

---

### Post by saulgoode on 2010-11-30
You should've probably started a new thread with your question. Nonetheless, you can apply ffmpeg2theora to multiple files using a 'for' loop. 

```
for x in *.flv; do ffmpeg2theora "$x" ; done
```

---

