---
title: "cinelerra and AVCHD"
date: 2009-09-22
forum: Ubuntu Studio
---

### Post by FunkyRes on 2009-09-22
Hi -

I'm brand spanking new to video editing. Currently I'm using kino - which is perfect because it is simple and well documented, and my camera (JVC) uses MiniDV tapes that work just dandy over FireWire with it.

While the reality is most of my stuff will probably still be done with MiniDV, I would like to shoot some stuff in HD. It looks like pretty much all the consumer HD cameras out there use AVCHD and googling, it seems that Cinelerra is crash prone with AVCHD source.

Thus, transcode to something else may be necessary. There seem to be several options that are used for this. What is the consensus here of the best format to transcode AVCHD to for import into Cinelerra? It seems mpeg2 is a popular choice from my googling, but some of the posts are old is that still the best?

Also, I really would prefer to shoot progressive source.
One camera I'm looking at says it does that - the Canon VIXIA HF200

> 
In addition to the standard interlaced video frame rate of 60i, you may choose to set the VIXIA HF200 to capture video in 30p (30 progressive frames, recorded to 60i), which is particularly useful for footage to be used on the Internet.


Internet is my target, but when it says "30 progressive frames, recorded to 60i" - I assume that it is somewhat cheating?

Are there other options under $800 that do "true" progressive?

I know footage can be de-interlaced (I do that now with my 480i source) but I understand that de-interlacing isn't exactly a lossly process. Maybe it isn't destructive enough to worry about.

Finally, anyone know of a short AVCHD clip under a friendly license that I can use to play with transcoding for cinelerra import and try to figure out cinelerra features? a couple of minutes worth is probably sufficient for learning.

-=-

OK - really finally, my hardware is a AMD X2 5200+ (2.6GHz) w/ 2GB of RAM. I'll be using a dedicated SATAII hd for editing. I assume that is sufficient. I could potentially add RAM or upgrade the CPU. If things are too slow or crashy, which would be better to spend the money I'm not rolling in on?

---

### Post by Cresho on 2009-09-22
HMM......

I use Winff to convert mp4 to mpeg2.  THen i use edit in cinelerra and render to mov.  I use 720p@60fps footage.

Here are my notes for exporting, importing and exporting.  YOU CAN FIGURE OUT THE EDITING PART ON YOUR OWN BUT>>>I Realise that the importing and exporting is the important part.  Openshot video editor can edit the files directly and works fine but if the footage is true720p@60fps, there is problems with sync from my perspective.
```

here let me show you my winff settings to convert mp4 to mp2
preset-name :xacti2cinelerra720p60fps
preset-label :xacti 2 cinelerra 720p@59.94fps
preset-command line :-vcodec mpeg1video -r 59.94 -s 1280x720 -b 20000K -acodec mp2 -ab 320k -ar 48000 -ac 2
output-file :mpg
category:xacti 2 cinelerra

after it creates my files, takes seconds btw, i open cinelerra and in settings->format, i use 720p/60.

when I export after I do my high definition editing with all text, transitions, music score mix and all, I use this setting i created "HD mov"
quicktime for linux
audio:(click on wrench icon) select mpeg 4 audio
video:(click on wrench icon) select mpeg 4 video

```
render range project and leave uncheck for creating new file.  insertion nothing an i use my home directory and create a 1.mov file.

It is the best

give openshot video editor a shot

[http://www.openshotvideo.com/](http://www.openshotvideo.com/)

this guy will show you how to install the good cinelerra
[http://www.youtube.com/watch?v=bcBxE6m7x8w](http://www.youtube.com/watch?v=bcBxE6m7x8w)


If i compared cinelerra to vegas, I preffer cinelerra.  What takes me to render a video in vegas 8 or 9 in 4 days takes me 3 hours in cinelerra.

---

### Post by FunkyRes on 2009-09-22
I will give OpenShot a try.
My plan is to at least use 720p dimensions for HD clips. I may shoot in 1080 (either 60i or 30p) and reduce when when I compress for web.

I also am hoping to do a 4:3 crop to make 640x480 and 384x288 available - I'd rather crop for lower resolution, hopefully after mastering the widescreen clip whichever tool I end up using makes is easy to crop to 4:3 - preferably giving me some control over what gets cut rather than just having dead center throughout clip.

---

### Post by cotcot on 2009-09-23
I use ```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 00126.MTS -vf lavcdeint -ofps 25 -fps 50 -o 00126.mpg
```
to convert .MTS from a Canon HF100 to .mpg and then do the editing with blender VSE or cinelerra.
This is a command to convert a batch of .MTS files : cd to the folder with the .MTS files and ```
find ~/ -name '*.MTS' -type f -exec mencoder '{}' -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 -vf lavcdeint -ofps 25 -fps 50 -o '{}'.mpg \;
```

---

### Post by kayosiii on 2009-09-25
Probably the best place to be asking these questions is at the cinelerra CV site [http://www.cinelerra.org/mailinglists.php](http://www.cinelerra.org/mailinglists.php) The people there will have a much better idea of when/if AVCHD is likely to be supported.... 

Currently transcoding is the only option....
[http://www.fsckin.com/2008/01/03/transcoding-mtsm2ts-avchd-video-files-with-free-software/](http://www.fsckin.com/2008/01/03/transcoding-mtsm2ts-avchd-video-files-with-free-software/) in case you haven't found it already will probably give the best advice....

---

### Post by Cresho on 2009-09-25
I have not perfected my converting scheme but with winff, i convert 2 hours worth of video footage under...30 minutes.  how long does your transcoding take?  i use mpeg2 with a high bitrate and hd quality.  I would preffer to keep the codec and change the container instead of reconverting the whole thing.

---

