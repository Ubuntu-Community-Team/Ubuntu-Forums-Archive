---
title: "batch convert avi files"
date: 2008-10-01
forum: Ubuntu Studio
---

### Post by SpazDes on 2008-10-01
Just figured I'd share this, I use it too turn AVI movies too DVD's...

You'll need too have sox, multimux, mplex, ffmpeg, transcode, dvdauthor


What this does is it loops itself over a folder full of movies, and converts them too a dvd and adds a sort of fake surround sound too it, as well, as makes it into an iso file too burn later.

```
#!/bin/bash
cd Movies
for i in $( dir convert ); do
	FILE="`basename $i .avi`"
	echo "Splitting Audio and Video for $FILE"
	transcode -i convert/$i -y ffmpeg --export_prof dvd-ntsc --export_asr 2 -o working/movie -D0 -s2 -m sound/movie.ac3 -J modfps=clonetype=3 --export_fps 29.97
	echo "Working sound files now"
	ffmpeg -i sound/movie.ac3 sound/movie.wav
	sox -V sound/movie.wav -r 48000 -c1 sound/left.wav avg -l
	sox -V sound/movie.wav -r 48000 -c1 sound/right.wav avg -r
	sox -V sound/left.wav sound/right.wav -r 48000 -c1 sound/centre.wav
	sox -V -v 0.5 sound/centre.wav sound/lfe.wav lowp 150
	multimux -f sound/left.wav sound/centre.wav sound/right.wav sound/left.wav sound/right.wav sound/lfe.wav
	echo "Cleaning up..."
	echo "Sound Finished..."
	mplex -f 8 -o dvd_movie.mpg working/movie.m2v 6ch.ac3
	dvdauthor -x dvdauthor.xml
	mkisofs -dvd-video -o complete/$FILE.iso DVD/
	rm 6ch.ac3 dvd_movie.mpg sound/* working/*
	cp convert/$i $BACKUP
	rm convert/$i
	cd DVD
	rm -r VIDEO_TS AUDIO_TS
	cd ..
	done

```

Inside a folder named Movies in the home/<username> directory the directory structure should look like this:

[IMG]http://i37.tinypic.com/28jkzlw.png[/IMG]

dvdauthor.xml
```
<dvdauthor dest="DVD">
  <vmgm />
   <titleset>
     <titles>
       <pgc>
         <vob file="dvd_movie.mpg" chapters="0,15:00,30:00,45:00,1:00:00"/>
       </pgc>
      </titles>
   </titleset>
 </dvdauthor>

```

If anyone wants to shed some light on how to make it handle more file types it'd be much appreciated.


Anyway just figured I'd share that. :D

---

### Post by aeiah on 2008-10-02
looks nice, although i suspect i dont currently have enough free disk space for that sort of thing. you know, before the iterating part of the script, you could add a series of mkdir commands to create the folder structure, so people didnt need to copy whats in your screenshot manually. that might be a nice addition. if the folder existed already it'd just skip over it.

or you could just throw all the temporary files into /tmp/ and not bother with most of the filenames.

the whole surroundsound bit is very elaborate. i dont think i know anyone who has a surround sound system though so i guess id crop that bit out.

what's the advantage of -J modfps=clonetype=3 --export_fps 29.97? wouldnt ffmpeg convert the frames depending on -dvd-ntfs or -dvd-pal anyway?

as for more filetypes, id have though ffmpeg could handle anything you throw at it, and if movie.ac3 is actually an mp3 file, ffmpeg will still convert it to .wav

i dont really understand why you have converted .ac3 into .wav though. wouldnt that force the sound into 2 channel audio?

---

