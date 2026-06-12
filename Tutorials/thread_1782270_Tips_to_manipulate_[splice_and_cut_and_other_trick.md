---
title: "Tips to manipulate [splice and cut and other tricks] video and audio files"
date: 2011-06-14
forum: Tutorials
---

### Post by shantiq on 2011-06-14
[FONT=Trebuchet MS]


Here ARE A FEW USEFUL COMMAND-LINE TRICKS to manipulate audio and video  files. I have collected these in recent times and thought it would be  good to share them here on the Forum

THESE use mencoder; ffmpeg; and sox ; MP4Box (gpac) ; mkvtoolnix all in synaptic or


[/FONT]```
[FONT=Trebuchet MS]      sudo apt-get install mencoder ffmpeg sox libsox-fmt-all gpac mkvtoolnix [/FONT]
```[FONT=Trebuchet MS]




[SIZE=2][B]AUDIO ==================================================  ====

[/B][/SIZE] 

MERGE/SPLICE AUDIO
=================


     
[/FONT]```
[FONT=Trebuchet MS]      cat 1.mp3 2.mp3 > final.mp3 [/FONT]
```[FONT=Trebuchet MS]
         cat works with mp3  and aac too

for flac and wavpack and wave  use sox


[/FONT]```
[FONT=Trebuchet MS]      sox 1.flac 2.flac final.flac [/FONT]
```[FONT=Trebuchet MS]

[/FONT][FONT=Trebuchet MS] CUT/TRIM AUDIO WITH SOX
=======================


For example, suppose that you have a recording 1 hour long and wish to  cut it into two halves. The following two commands will leave the first  half in Half1.wav and the second half in Half2.wav.


[/FONT]```
[FONT=Trebuchet MS]      sox Input.wav  Half1.wav trim 0 30:00 [/FONT]
```[FONT=Trebuchet MS]


[/FONT]```
[FONT=Trebuchet MS]      sox Input.wav  Half2.wav trim 30:00 60:00 [/FONT]
```[FONT=Trebuchet MS]

[/FONT][FONT=Trebuchet MS] The original file is unaffected, so once you have confirmed that  the two output files contain what they should, you may delete the  original if you wish to.


[COLOR=Red]SOX supports these main formats **[ALSO mp3]("http://ubuntuforums.org/showpost.php?p=10944276&postcount=5")**   ADD   ```
sudo apt-get install sox libsox-fmt-all
``` to your setup


AUDIO FILE FORMATS:  aiff  au  cdda cdr flac ircam  ogg vorbis vox w64 wav  wv 


[/COLOR][/FONT][FONT=Trebuchet MS]TO DOUBLE VOLUME ON AN AUDIO TRACK
==================================

[/FONT]```
[FONT=Trebuchet MS] sox 1.flac newflac.flac gain +6[/FONT]
```[FONT=Trebuchet MS]





[SIZE=2]**VIDEO  ==================================================  =**[/SIZE]




MERGE/SPLICE VIDEO
================



[/FONT]```
[FONT=Trebuchet MS]      mencoder -oac copy -ovc copy -o finalfile.mov    1.mov 2.mov 3.mov 4.mov 5.mov 6.mov 7.mov [/FONT]
```[FONT=Trebuchet MS]


[/FONT][FONT=Trebuchet MS]  
[/FONT]```
[FONT=Trebuchet MS]      mencoder -forceidx -ovc copy -oac copy -o file.avi 1.avi 2.avi ... [/FONT]
```[FONT=Trebuchet MS]
     
[/FONT]```
[FONT=Trebuchet MS]      mencoder -forceidx -ovc copy -oac pcm -o Finalfile.mp4  ff1.mp4 ff2.mp4 ff4.mp4 [/FONT]
```[FONT=Trebuchet MS]

[/FONT][FONT=Trebuchet MS] [COLOR=Red]**with mencoder sometimes you are asked to change -oac copy to -oac pcm**[/COLOR]

For mp4 only


[/FONT]```
[FONT=Trebuchet MS]      MP4Box -add 1.mp4 -cat 2.mp4 -cat 3.mp4 -cat 4.mp4 -cat 5.mp4 -cat 6.mp4   NameofNewCombinedFile.mp4 [/FONT]
```[FONT=Trebuchet MS]

[/FONT][FONT=Trebuchet MS]TO TRIM A SECTION OF A VIDEO
============================
[/FONT]
[FONT=Trebuchet MS] 


WITH FFMPEG
======

[/FONT]```
[FONT=Trebuchet MS] ffmpeg -i INPUT.wav -ss 00:10:00 -t 00:05:00  -acodec copy OUTPUT.wav[/FONT]
```[FONT=Trebuchet MS]

[COLOR=Red]the second time -t is the length of the cut not the time of the cut so if you want a five minute section you enter as above[/COLOR]


[/FONT]> ffmpeg -i input.mkv -ss 00:35:54 -t 00:04:12 -vcodec copy -acodec copy  output1.mp4 && ffmpeg -i input.mkv -ss 00:14:14 -t 00:14:10  -vcodec copy -acodec copy output2.mkv[FONT=Trebuchet MS]


WITH MENCODER
==========


[/FONT]```
[FONT=Trebuchet MS] [/FONT] 			 				mencoder  -ss 01:00:00  -endpos 00:05:56 -oac copy -ovc copy input.mp4 -o output.mp4 			 		
```[FONT=Trebuchet MS]

OF COURSE WITH && YOU CAN add as many cuts as you want from one input file



[/FONT][FONT=Trebuchet MS]
VIDEO SPLIT IN 15 MINUTE CHUNKS  for upload to hosting sites
=============================

FOR ALL FORMATS

[/FONT]
   >    mencoder  -ss 00:00:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part_1.mp4  &&  mencoder  -ss 00:15:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part_2.mp4  &&  mencoder  -ss 00:30:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part_3.mp4   &&  mencoder  -ss 00:45:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part4.mp4    &&  mencoder  -ss 01:00:00  -endpos 00:15:00 -oac copy -ovc copy originalfile.mp4 -o part_5.mp4 [FONT=Trebuchet MS]

[/FONT]
[FONT=Trebuchet MS] 
[B]
or[/B]

**for mp4 only**  > MP4Box -split 900 filename.mp4   give 15 minute sections 900seconds

**for mkv only**  > mkvmerge -o new_filename.mkv --split 900s filename.mkvThanx to Ron999 for info on those 2



ADD SRT SUBTITLE TO VIDEO FILE
==============================


[/FONT]```

     mencoder -sub file.srt -subcp iso-8857-9 -ovc xvid -xvidencopts bitrate=1419 -oac copy -o finalfile.avi file.avi 
```[FONT=Trebuchet MS]
[/FONT]
     ```
mencoder -sub file.srt -subcp iso-8857-9 -ovc xvid -xvidencopts bitrate=1419 -oac pcm -o finalfile.mp4 file.mp4 
```[FONT=Trebuchet MS]

[/FONT][FONT=Trebuchet MS]TO EXTRACT SRT OR AUDIO OR VIDEO FROM MKV
=========================================

First, use mkvmerge to list the MKV file&#8217;s contents:

[/FONT]```
[FONT=Trebuchet MS]      mkvmerge -i MovieFile.mkv [/FONT]
```[FONT=Trebuchet MS]

[/FONT][FONT=Trebuchet MS] You&#8217;ll see a listing similar to this:

     
     [/FONT]> File 'MovieFile.mkv': container: Matroska Track ID 1: subtitles (S_TEXT/***) Track ID 2: audio (A_MPEG/L3) Track ID 3: video (V_MPEG4/ISO/AVC) [FONT=Trebuchet MS] Next, use mkvextract to  extract certain tracks / attachments based on the output from the above  command:
[/FONT]```
[FONT=Trebuchet MS] 
     mkvextract tracks MovieFile.mkv 1:thesubtitles.srt   2:theaudio.mp3 3:thevideo.mp4 [/FONT]
```[FONT=Trebuchet MS]
[/FONT]
[FONT=Trebuchet MS] 

[/FONT]

---

### Post by andrew.46 on 2011-06-15
Thanks for making this available Shantiq, I have bookmarked the page! Just a quick addit to your note that SoX will not support mp3: this is true for the Ubuntu package as mp3 encoding has been deliberately *excluded* for licensing reasons. A properly setup SoX transcodes mp3 easily enough as I demonstrate here converting from ogg to mp3:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]sox -V3 --show-progress Bartók_4tet_1.ogg test.mp3[/COLOR]**
sox: SoX v14.3.2
sox INFO formats: detected file format type `vorbis'

Input File     : 'Bartók_4tet_1.ogg'
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:29:04.40 = 76928040 samples = 130830 CDDA sectors
File Size      : 40.8M
Bit Rate       : 187k
Sample Encoding: Vorbis
Comments       : 
title=String Quartet no.1 op.7 (1908-1909)
artist=Emerson String Quartet
album=Béla Bartók - 6 String Quartets

sox INFO mp3: using MP3 encoding defaults

Output File    : 'test.mp3'
Channels       : 2
Sample Rate    : 44100
Precision      : 24-bit
Duration       : 00:29:04.40 = 76928040 samples = 130830 CDDA sectors
**[COLOR="Red"]Sample Encoding: MPEG audio (layer I, II or III)[/COLOR]**
Comments       : 
title=String Quartet no.1 op.7 (1908-1909)
artist=Emerson String Quartet
album=Béla Bartók - 6 String Quartets

sox INFO sox: effects chain: input      44100Hz 2 channels
sox INFO sox: effects chain: output     44100Hz 2 channels
In:100%  00:29:04.40 [00:00:00.00] Out:76.9M [      |      ] Hd:1.3 Clip:0    
Done.

```

Thanks again for putting this together, I appreciate the time and effort in putting such guides together and supporting them :).

---

### Post by MrSS on 2011-06-15
Thanks for the tips .. I will keep your thread as reference. :D

---

### Post by shantiq on 2011-06-15
> andrew.46;10941007]Thanks for making this available Shantiq, I have bookmarked the page! Just a quick addit to your note that SoX will not support mp3: this is true for the Ubuntu package as mp3 encoding has been deliberately *excluded* for licensing reasons. A properly setup SoX transcodes mp3 easily enough as I demonstrate here converting from ogg to mp3:


Well Andrew this is good news

you always have one more trick up your sleeve:KS:KS:KS
Pray tell where do i get this "fuller" version of SoX one of my absolute favourite master softwares






> Thanks again for putting this together, I appreciate the time and effort in putting such guides together and supporting them :)

Glad to have put something up that can be of use to you
You have put so much that has been and is of use to me and no doubt many others:KS

---

### Post by andrew.46 on 2011-06-15
> **shantiq said:**
> Pray tell where do i get this "fuller" version of SoX one of my absolute favourite master softwares

Actually on closer examination this was only true of Ubuntu versions *before* Natty. See this in the SoX package changelog:

```

sox (14.3.1-2ubuntu1) natty; urgency=low

  * Merge from Debian unstable. Remaining changes:
    - Enable lame support (drop --without-lame and add libmp3lame-dev to
      build dependencies).

 -- Benjamin Drung <bdrung@ubuntu.com>  Sat, 12 Feb 2011 12:14:56 +0100

```

Not sure what sparked this change of mind but it does make life a little easier :). So all that is now needed is:

```
sudo apt-get install sox libsox-fmt-all
```

and the previous [repackaging guide that I came up with]("http://ubuntuforums.org/showpost.php?p=9859875&postcount=8") is now rendered obsolete :(.

---

### Post by Rasa1111 on 2011-06-15
Cool thread Shantiq!
Thanks!

---

### Post by shantiq on 2011-06-16
brilliant Andrew

now got

```
AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb amr-nb amr-wb anb au avi avr awb caf cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 fap ffmpeg flac fssd gsm gsrt hcom htk ima ircam la lpc lpc10 lu m4a m4b mat mat4 mat5 maud mp2 **[COLOR="Red"]mp3[/COLOR]** mp4 mpg nist ogg paf prc pvf raw s1 s16 s2 s24 s3 s32 s4 s8 sb sd2 sds sf sl smp snd sndfile sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc vorbis vox w64 wav wavpcm wmv wv wve xa xi

```

which means ```
play *.mp3
``` now works a treaT


but it does not seem to splice mp3; might have to stay with cat on that one unless it is just me   also cat is INSTANT on splicing mp3 takes under a second

---

### Post by FakeOutdoorsman on 2011-06-16
Nice post. Little tips like these are always good time savers.

> **shantiq said:**
> ```
ffmpeg -i INPUT.wav -ss 00:10:00 -t 00:05:00  -acodec copy OUTPUT.wav
```
Placing -ss as in input option (before the -i) will tell FFmpeg to seek and then decode, but it's potentially not frame-accurate. Placing -ss as on output option (after -i input.foo) will tell FFmpeg to decode until it reaches your -ss value, and then start encoding.

As an input option, -ss is useful for trimming long videos--especially videos that are slower to decode, but unfortunately it isn't always as accurate. I always try this method first and if it doesn't work I'll use the slower "-ss as an output option" method next.

A few more FFmpeg tips you can add if you like:

**Strip metadata:**
```
ffmpeg -i input -map_metadata -1 -vcodec copy -acodec copy output
```

**Pipe from FFmpeg:**
```
ffmpeg -i input -f wav - | lame -V4 - output.mp3
ffmpeg -i input -f wav - | faac -o output.mp4 -
```

**Getting width x height:**
There's a million ways to do this, but this works for me.
```
ffmpeg -i input.mkv 2>&1 | awk '/Video/{print $7}' | sed 's/,//g'
```

**Show duration only:**
```
ffmpeg -i input 2>&1 | awk '/Duration/{print $2}' | sed 's/,//g'
```

**Speed up a video (double speed):***
```
ffmpeg -i input -vf setpts=0.5*PTS ... output
```

**Slow down a video (half speed):***
```
ffmpeg -i input -vf setpts=2.0*PTS ... output
```

***** As of Ubuntu Natty you will need to [compile FFmpeg](http://ubuntuforums.org/showthread.php?t=786095) to have access to the video filters.

---

### Post by shantiq on 2011-07-26
=== always wondered why ffmpeg sometimes cut in the wrong place  thanx for this

> Placing -ss as in input option (before the -i) will tell FFmpeg to seek and then decode, but it's potentially not frame-accurate. Placing -ss as on output option (after -i input.foo) will tell FFmpeg to decode until it reaches your -ss value, and then start encoding.

As an input option, -ss is useful for trimming long videos--especially videos that are slower to decode, but unfortunately it isn't always as accurate. I always try this method first and if it doesn't work I'll use the slower "-ss as an output option" method next.

---

### Post by shantiq on 2011-08-18
also easy way to burn to a cd from a cuefile

```

cdrdao write --eject --speed 16 --device /dev/cdrom --driver generic-mmc name.cue
```


```
wodim dev=/dev/cdrw -v speed=8 -dao -text cuefile=name.cue
```

---

### Post by dcsoldschool53 on 2011-09-07
**Nice tutorial. Thank you.**

---

### Post by shantiq on 2011-09-15
ok if you get  a concert in video form broken down in parts say flv or mp4 or really any type of video file supported by ffmpeg 

**AND**   you wish for a single audio file retaining the kbps of the original video



**USE**

```
for f in *.flv do ffmpeg -i "$f" "${f%.flv}.flac" done && 
{ sox *.flac final.flac ; ffmpeg -i final.flac -ab 160k final.mp3 ; rm *.flac }
```




or you have mp3 enabled on sox ( see [posts]("http://ubuntuforums.org/showpost.php?p=10944276&postcount=5") above to add ) alternative and **faster** route is

```
for f in *.flv
do  ffmpeg -i "$f" "${f%.flv}.flac" 
done && { sox *.flac -C 160 final.mp3 -V3 ; rm *.flac  }
```


Thanx to Ron999 for coding advice:KS

---

### Post by shantiq on 2012-04-18
there is a piece of software called mp3splt   which will do this really fast since it does nor re-encode  [like SoX]



to split in 15 mn sections


```
mp3splt -f -t 15.0 -a -d split inputfile.mp3
```


to split in 3.5 mn sections


```
mp3splt -f -t 3.30 -a -d split inputfile.mp3
```






**[extra info click!]("http://wiki.librivox.org/index.php/How_To_Split_With_Mp3Splt")**   

> All the command line options are listed farther below. Here's an explanation of the recommended options: 

-f: for MP3 files only, increases precision and is needed if the MP3 files are variable bit rate (VBR). 

-t TIME: specifies the length, measured in time, to make each piece. You will replace `TIME` with a numerical value expressed in minutes, such as 4.0 for four minutes or 7.30 for seven minutes, thirty seconds. In our example, we picked four minute pieces, so the command line will be 

```
mp3splt -f -t 4.0 -a -d split *.mp3

```
-a: automatically adjusts the split points to occur during silences, which avoids splitting in the middle of a word. 
Therefore, the pieces will vary in their exact length. 

-d split: writes the split files to a sub-folder named split(you may pick any name you wish). The folder will be created if it doesn't already exist. It's more convenient if you don't put the split files in the same folder with the original ones. 

*.mp3: process all the MP3 files in the current folder. If you are splitting Ogg Vorbis files, change this to *.ogg.



will even cut it to hundredth of a second   here 4 minutes 30 seconds 55/100 second  :KS:KS


```
mp3splt -f -t 4.30.55 -a -d split inputfile.mp3

```



thanx to Temüjin for info

---

### Post by Jose Catre-Vandis on 2012-04-20
Increasing volume with ffmpeg using the -vol option:
```
ffmpeg -i input.mp3 -vol 512 output.mp3
```
will double the volume as "normal" is 256

---

