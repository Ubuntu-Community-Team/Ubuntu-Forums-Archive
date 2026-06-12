---
title: "[SOLVED] Making avi files smaller"
date: 2009-01-07
forum: Ubuntu Studio
---

### Post by japtar10101 on 2009-01-07
Currently, I have 4 23-minute avi video files that exceeds 5 GB in size,each.  They were exported by Kino, with settings: DV AVI Type 2.  I wanted to make this video smaller, preferably through mencoder, as it seems ridiculous that the original 2-hour video they derived from is only 1.8 GB in size.

I realize my information is rather minimal.  If there's any command line or programs I can use to analyze what the video and audio formats are, that will help.  I unfortunately know next to nothing about video format and differences....

Edit:
Also, if possible, can anyone tell me how to concatenate 4 videos into one?  I tried this with mencoder, and it didn't work:
```

cat vid1.avi vid2.avi vid3.avi vid4.avi | mencoder -noidx -oac copy -ovc copy -ofps 30000/1001 -o out.avi -

```

---

### Post by The-IRS on 2009-01-07
the 1.8 GB that you see may not be AVI. It could be mp4 or wmv too. but my recommendation is to convert the file into a smaller size at mediconverter.org. 

P.S. by the way, I personally have never heard of having 2 hours of video in 1.8 GB

EDIT: What is the resolution of your vids?

---

### Post by The-IRS on 2009-01-07
I know that I double posted. sorry.

have you tried to combine the videos with software?

---

### Post by japtar10101 on 2009-01-09
> **The-IRS said:**
> the 1.8 GB that you see may not be AVI. It could be mp4 or wmv too. but my recommendation is to convert the file into a smaller size at mediconverter.org. 

P.S. by the way, I personally have never heard of having 2 hours of video in 1.8 GB

EDIT: What is the resolution of your vids?

Durr...Why didn't I notice that before?  The file properties have a video/audio tab!
[IMG]http://i9.photobucket.com/albums/a87/japtar10101/Scrap/Screenshot-2.jpg[/IMG]
I decided to make a quick bash script to convert the video to Xvid MPEG4, and audio to MP3:
```
#!/bin/sh

VID_SET="-ovc xvid -xvidencopts bitrate=1000:pass=2"

AUD_SET="-oac mp3lame"

FRA_SET="-ofps 30000/1001"

if ["$#" -ne "2"]; then
	#print usuage
	echo "Usuage: input_movie output_movie"
	exit 0
fi

#call mencoder
mencoder -idx $1 $VID_SET $AUD_SET $FRA_SET -o $2

```
I think my if statement is screwed up, but it works, nonetheless.

---

