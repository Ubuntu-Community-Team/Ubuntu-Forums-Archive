---
title: "dvd-slideshow error"
date: 2009-02-11
forum: Ubuntu Studio
---

### Post by celticbhoy on 2009-02-11
Getting this trying to run a simple 3 image command :-

[dvd-slideshow] waiting for encoder to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] No audio files passed.  Using 0:0:15.000 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:0:15.000
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:0:15.000
[dvd-slideshow] ###############
[dvd-slideshow] Creating ac3 audio...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/office/Pictures/Slides/dvd-slideshow.log for details


Any ideas how to fix, or what to install ????

---

### Post by cotcot on 2009-02-11
Impossible to tell you what happened. The only message is 'something happened with ffmpeg'. But the message tells you where you might find something. Read the text file that is mentioned : /home/office/Pictures/Slides/dvd-slideshow.log

---

### Post by celticbhoy on 2009-02-11
The log file only shows the same info, nothing else to help.

---

### Post by neu2buntu on 2009-02-11
(go-on the hoops!!)  what are the video files eg .ogv etc .. ?  just realised it is images you are working with....perhaps the audio silence isnt working well with ffmpeg

---

### Post by celticbhoy on 2009-02-11
just three plain jpg's

---

### Post by neu2buntu on 2009-02-11
update was looking through synaptic ... do u have libavcodec51 & libavcodec-dev installed alongside ffmpeg? these have the lib files for ac3 audio

---

### Post by celticbhoy on 2009-02-11
just installing the dev side now

why you not watching game !!!

---

### Post by celticbhoy on 2009-02-11
Is the problem because I have no audio specified ???

---

### Post by celticbhoy on 2009-02-11
using this command :-

 dvd-slideshow -n clips1.mpg -p -nocleanup slide1.txt

text file looks like this :-

bacardi.jpg:5:
Baileys.jpg:5:
Baileys2.jpg:5:


Any ideas ????

---

### Post by neu2buntu on 2009-02-11
spain & eng? or r the bhoys playin? really a man utd fan...lol...celts 2nd fav...  let us know if this makes any diff the libav files. didnt know u could get audio with dvd-slideshow gona try it out, have never used it yet. u could always try a couple of audio files along with images to see how it goes

---

### Post by celticbhoy on 2009-02-11
Go robbie .................

---

### Post by celticbhoy on 2009-02-11
The Republic (2) v Georgia (1)

---

### Post by celticbhoy on 2009-02-11
OBTW still the same .

---

### Post by celticbhoy on 2009-02-11
BTW using intrepid on aspire one - just see you have it listed for use. If you get it to go please let me know.

---

### Post by celticbhoy on 2009-02-11
Tryed it with an mp3 file as the audio, still the same.

---

### Post by neu2buntu on 2009-02-11
2-1 ye ha!! can only get spa eng match on my tv aw well!!!  yeah i will give it a go now,i usually get all my vid and audio apps 2 work well...lets see who gets it up n runnin 1st ...lol    (am on me wee acer now)

---

### Post by celticbhoy on 2009-02-11
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Output #0, ac3, to '/home/office/Pictures/Slides/dvd-slideshow_temp_8171/audio1.ac3':
    Stream #0.0: Audio: ac3, 48000 Hz, 5:1, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

Get this in log file if it helps.

---

### Post by celticbhoy on 2009-02-11
Ma punts r on u - been messing with this all day.

Def to do with the aac codec as it creates a wav file ok from the audio..

---

### Post by celticbhoy on 2009-02-11
Dont know if this has anything to do with it, but my ffmpeg is an svn version.

---

### Post by neu2buntu on 2009-02-11
think your 4/5 money on atm.... heres my output,... dont have aclue what im doing yet..lol

```
[dvd-slideshow]            dvd-slideshow 0.8.0
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2006 by Scott Dylewski
[dvd-slideshow]            
[dvd-slideshow] Output directory not specified.
[dvd-slideshow] Using /home/h4ck3r
[dvd-slideshow] Parsing input file 909beat01.ogg
[dvd-slideshow] ###########################################################
[dvd-slideshow] Found 0 images.
[dvd-slideshow] Found 0 audio files.
[dvd-slideshow] Found 0 background slides.
[dvd-slideshow] Found 0 title slides.
[dvd-slideshow] Found 0 transitions (fadein/fadeout/crossfade/wipe).
[dvd-slideshow] Video: NTSC 720x480 29.97fps 4:3
[dvd-slideshow] Audio: AC3 48000 192
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=dvd Border=0
[dvd-slideshow] Using SMP optimizations for multi-processor machines
[dvd-slideshow] Title_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Subtitle_font=...r/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] Total audio length = 
[dvd-slideshow] Total video length = 0:0:15.000
[dvd-slideshow] Temp dir is /home/h4ck3r/dvd-slideshow_temp_10946
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Unrecognized or malformed line in your input file:
[dvd-slideshow] OggS&#65533;&#65533;o\J&#65533;'dvorbisD&#65533;p&#65533;OggS&#65533;&#65533;o\&#65533;-ÿÿÿÿÿÿÿÿÿÿÿÿ&#9524;&#9146;&#9148;&#9225;&#9227;&#9149;X&#9227;&#9147;&#9252;.O&#9148;± &#9484;&#9227;&#9225;V&#9146;&#9148;&#9225;&#9227;&#9149; I 20050304&#9524;&#9146;&#9148;&#9225;&#9227;&#9149;"BCV@$&#9149;*F¥&#9149;&#8222;BPãBÎ&#9488;ìBL&#8218;2L[Ë%&#9149;!¤ B&#710;[(ÐU@&#8225;A&#9474;&#8222;&#352;!&#8222;%=X&#8217;&#402;'!&#8222;&#710;9&#9474;&#8222;&#9227;!&#8222;!&#8222;!&#8222;E9&#9252;&#8217;&#402;'&#8222;ã08
                                              &#402;å8ø&#8222;E9X&#402;'Aè &#8222;B&#65533;&#65533;&#65533;&#65533;!&#65533;$5HP&#65533;9&#65533;&#65533;&#65533;,(&#65533;&#65533;&#65533;0&#65533;&#65533;5(&#65533;&#65533;&#65533;0&#65533;&#1283;
                  B&#65533;&#65533;&#65533;I5&#65533;&#65533;gAx&#65533;i!&#65533;$AH&#65533;&#65533;A&#65533;&#65533;FAX&#65533;&#65533;9&#65533;&#65533;&#65533;A&#65533;&#65533;*&#65533; 4d&#65533;&#65533;&#65533;(&#65533;&#65533;(. effect=OggS&#65533;&#65533;o\J&#65533;'dvorbisD&#65533;p&#65533;OggS&#65533;&#65533;o\&#65533;-ÿÿÿÿÿÿÿÿÿÿÿÿ&#9524;&#9146;&#9148;&#9225;&#9227;&#9149;X&#9227;&#9147;&#9252;.O&#9148;± &#9484;&#9227;&#9225;V&#9146;&#9148;&#9225;&#9227;&#9149; I 20050304&#9524;&#9146;&#9148;&#9225;&#9227;&#9149;"BCV@$&#9149;*F¥&#9149;&#8222;BPãBÎ&#9488;ìBL&#8218;2L[Ë%&#9149;!¤ B&#710;[(ÐU@&#8225;A&#9474;&#8222;&#352;!&#8222;%=X&#8217;&#402;'!&#8222;&#710;9&#9474;&#8222;&#9227;!&#8222;!&#8222;!&#8222;E9&#9252;&#8217;&#402;'&#8222;ã08
                                 &#402;å8ø&#8222;E9X&#402;'Aè &#8222;B&#65533;&#65533;&#65533;&#65533;!&#65533;$5HP&#65533;9&#65533;&#65533;&#65533;,(&#65533;&#65533;&#65533;0&#65533;&#65533;5(&#65533;&#65533;&#65533;0&#65533;&#1283;
     B&#65533;&#65533;&#65533;I5&#65533;&#65533;gAx&#65533;i!&#65533;$AH&#65533;&#65533;A&#65533;&#65533;FAX&#65533;&#65533;9&#65533;&#65533;&#65533;A&#65533;&#65533;*&#65533; 4d&#65533;&#65533;&#65533;(&#65533;&#65533;( effect_params=OggS&#65533;&#65533;o\J&#65533;'dvorbisD&#65533;p&#65533;OggS&#65533;&#65533;o\&#65533;-ÿÿÿÿÿÿÿÿÿÿÿÿ&#9524;&#9146;&#9148;&#9225;&#9227;&#9149;X&#9227;&#9147;&#9252;.O&#9148;±&#9484;&#9227;&#9225;V&#9146;&#9148;&#9225;&#9227;&#9149;I20050304&#9524;&#9146;&#9148;&#9225;&#9227;&#9149;"BCV@$&#9149;*F¥&#9149;&#8222;BPãBÎ&#9488;ìBL&#8218;2L[Ë%&#9149;!¤ B&#710;[(ÐU@&#8225;A&#9474;&#8222;&#352;!&#8222;%=X&#8217;&#402;'!&#8222;&#710;9&#9474;&#8222;&#9227;!&#8222;!&#8222;!&#8222;E9&#9252;&#8217;&#402;'&#8222;ã08
                       &#402;å8ø&#8222;E9X&#402;'Aè&#8222;B&#65533;&#65533;&#65533;&#65533;!&#65533;$5HP&#65533;9&#65533;&#65533;&#65533;,(&#65533;&#65533;&#65533;0&#65533;&#65533;5(&#65533;&#65533;&#65533;0&#65533;&#1283;
                                                                          B&#65533;&#65533;&#65533;I5&#65533;&#65533;gAx&#65533;i!&#65533;$AH&#65533;&#65533;A&#65533;&#65533;FAX&#65533;&#65533;9&#65533;&#65533;&#65533;A&#65533;&#65533;*&#65533;4d&#65533;&#65533;&#65533;(&#65533;&#65533;(
Fix it and try again.
[dvd-slideshow] cleanup...
/usr/bin/dvd-slideshow: line 913: kill: (26432) - No such process

```    think imtrying to merge jpeg and .ogg here?

---

### Post by neu2buntu on 2009-02-11
not sure about the svn snapshot of ffmpeg,... have u tried -mp2 option this changes the default ac3?

---

### Post by celticbhoy on 2009-02-11
Yeah tried that too. Just compiling the latest version now. I think from the website all versions are svn, or git but both are linked.

---

### Post by celticbhoy on 2009-02-11
:lolflag:

@ long fecking last.

Had to download the latest .deb from sorceforge for dvd-slideshow.

Woo Hoo !.....

---

