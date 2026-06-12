---
title: "Create a Reversed Video Clip"
date: 2009-12-13
forum: Ubuntu Studio
---

### Post by Jose Catre-Vandis on 2009-12-13
When putting together some old home movies, I can across a section I needed to run in reverse, just like we did at home with the Cine Projector (jumping backwards out of a swimming pool). OK, it made us laugh then! So searched for a solution using mencoder or ffmpeg but nothing was forth coming, so I set about sorting this out with a script.

Mplayer has a useful feature that exports frame by frame to jpeg, I wrote a short code loop to reverse the numbering order of the created files, and then used mencoder to recombine the files into a video again.

For the audio, ffmpeg is used to decode to wave, then sox can apply a reverse filter on the sound file, and ffmpeg again to create the output file.

Finally mencoder again to remux the video and audio.

The script is probably only useful for home / casual use, and on my old slow PC required me to slow the playback of mplayer right down to allow it to generate all the images.

Here is the script, and it is also attached here ->[ATTACH]139681[/ATTACH]

> #!/bin/bash

#This script is designed to provide a reverse playback video clip
#using mplayer, mencoder, ffmpeg and sox. For home use only it
#offers the user the ability to generate short video clips with
#both video and audio in reverse. It's not perfect by any means
#but for casual use does the job.

#If you don't need the audio you can comment out the audio section,
#the remux section, and the remove section. These are highlighted.

#Requisites: mplayer, mencoder, ffmpeg, sox.

#Advice: use ffmpeg -i movie.avi to discern frame rate before you start
#You'll need the input video in the same directory as the script!
#Leave STARTNO & MAXFILES variables alone

#Usage: 
#Make sure you have plenty of disk space, a 1 minute clip can
#generate up to 1500 jpg images taking up 750mb space!

#place script and target video in a directory of your choice
#ensure script is executable
#cd to the directory with the script and the movie in it
#edit the script variables to ensure correct start and end positions
#(STARTPOS is the starting point of the clip, ENDPOS is the length of the clip)
#You may need to play around with the speed setting to generate all the
#frames if you have a slow PC

#type ./scriptname moviename at the command line

#variables
STARTPOS=00:01:00	#start of the clip
ENDPOS=00:00:30		#duration of the clip
QUALITY=100			#for best quality output
MAXFILES=100000 	#allows for an hour of jpegs
START=99999			#allows for an hour of jpegs
SPEED=0.15			#reduce speed accordingly for longer segments
FPS=25				#either 25 or 23.976
					#inputvideo = $1 (from the filename you type)
#
#extract and reverse audio using ffmpeg and sox
#this could be streamlined but provides an "out of the box" solution
####Comment out the three lines below if you do not need audio###
ffmpeg -i $1 -ss $STARTPOS -t $ENDPOS -vn -ac 2 -ar 44100 input.wav
sox -V input.wav output.wav reverse
ffmpeg -i output.wav -acodec libmp3lame -ac 2 -ab 128k -ar 44100 output.mp3
#
#grab jpegs
mplayer -idx -speed $SPEED -ss $STARTPOS -endpos $ENDPOS -vo jpeg:quality=$QUALITY:maxfiles=$MAXFILES $1
#
#rename files in reverse
i=$START
for f in *.jpg
do
mv $f $i.jpg
i=$(($i -1))
echo $i
done
#
#encode jpegs back to a movie
mencoder "mf://*.jpg" -mf type=jpg:fps=$FPS -o reverse.avi -ovc lavc -lavcopts vcodec=mpeg4
#
#remux audio and video
###Comment out the line below if you do not need audio###
mencoder reverse.avi -ovc copy -oac copy -audiofile output.mp3 -o reverseoutput.avi
#
#cleanup
rm *.jpg
rm *.wav
rm *.mp3
###Comment out the line below if you do not need audio###
rm reverse.avi
#
#end

#Nothing to undo


Welcome all/any comments on how to improve script or on other methods that have been used to achieve the same thing with open source.

---

### Post by imwithid on 2010-07-12
This is incredibly helpful, albeit confusing for those who aren't familiar with some of the cl mentioned. I've been trying to do this via Avidemux, however, only the video can be reversed using the filters. The audio features are very limited.

Thanks.

[Edit]

I got it!

An easier way is to use Avidemux:

Step 1:
Select clip to trim (A to B), use the filters in the video section and add reverse. The audio will not be altered as there is no filter to allow for this.

Step 2:
Save file.

Step 3:
Open saved file. Go to Audio > Save

Step 4:
Make sure ffmpeg and sox are installed. Then use Jose Catre-Vandis's method above.

```
ffmpeg -i audiofile.mp3 -vn -ac 2 -ar 44100 input.wav
sox -V input.wav output.wav reverse
```

Step 5:
Open video that was reversed in step one. Go to Audio > Main Track. Select 'Audio source' as 'External wav' and in the 'External file' choose the output from step 4 that you had reversed.

This is more for us gnoobs and gnobs who aren't just yet at the cl level that the OP had put together. It was a tremendous bridge that allowed me to figure out a simpler way.

---

### Post by Jose Catre-Vandis on 2010-07-14
Glad you found another way, its handy to know, even if i don't use Avidemux

---

