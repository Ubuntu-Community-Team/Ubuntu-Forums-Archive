---
title: "Convert wav or mp3 for upload on youtube"
date: 2009-08-28
forum: Ubuntu Studio
---

### Post by [rtmf] on 2009-08-28
hi, i want to upload self-made music to youtube, but everytime i upload an mp3 (youtube says it supports this format), i get a format conversion error on youtube after uploading.

how can i convert a wav or mp3 so its uploadable to youtube?

greetz [rtmf]:guitar:

---

### Post by tgeer43 on 2009-08-28
No, YouTube doesn't accept straight mp3 uploads, only video files. What you might have seen is that they recommend that the audio portion of your video file be encoded with the mp3 codec. So you'll have to convert your mp3 into a video file format that YouTube does recognize, .flv for instance.

There's various ways to accomplish this. Here's one that's fairly easy and works quite well:

- You'll need to have the packages 'ffmpeg' and 'gstreamer0.10-plugins-bad' installed.
```
sudo apt-get install ffmpeg gstreamer0.10-plugins-bad
```- Then just run this command to convert from mp3 to flv:
```
ffmpeg -y -i /path_to_your/song.mp3 -f flv -ab 131072 -ac 1 /path_to_your/video.flv
```Just replace the path and input and output file names to yours. The '131072' is the bitrate of the resulting file (128Kbps in this case) and can be changed as you wish.

Hope this helps,

tgeer

---

### Post by [rtmf] on 2009-08-28
Conversion on youtube failed again :(

---

### Post by sgx on 2009-08-28
> **'[rtmf] said:**
> Conversion on youtube failed again :(

Try making a video, add the soundtrack -your mp3, convert that complete production to flv. People often post video of just an album cover, with a song playing, but it is video with an audio track. Free stock video footage is plentiful to download, avidemux, or kino are easy to use for
making such a project ready for converting. 
Cheers

---

### Post by FakeOutdoorsman on 2009-08-28
> **tgeer43 said:**
> No, YouTube doesn't accept straight mp3 uploads, only video files. What you might have seen is that they recommend that the audio portion of your video file be encoded with the mp3 codec. So you'll have to convert your mp3 into a video file format that YouTube does recognize, .flv for instance.

There's various ways to accomplish this. Here's one that's fairly easy and works quite well:

- You'll need to have the packages 'ffmpeg' and 'gstreamer0.10-plugins-bad' installed.
Why install gstreamer0.10-plugins-bad?
> Then just run this command to convert from mp3 to flv:
```
ffmpeg -y -i /path_to_your/song.mp3 -f flv -ab 131072 -ac 1 /path_to_your/video.flv
```Just replace the path and input and output file names to yours. The '131072' is the bitrate of the resulting file (128Kbps in this case) and can be changed as you wish.
Instead of "-ab 131072" you could use "-ab 128k".

> **sgx said:**
> Try making a video, add the soundtrack -your mp3, convert that complete production to flv. People often post video of just an album cover, with a song playing, but it is video with an audio track. Free stock video footage is plentiful to download, avidemux, or kino are easy to use for
making such a project ready for converting. 
Cheers

I provided some command-line examples in the following thread to create an image and combine it with the audio track to make a video.  The audio is just being copied and not re-encoded so the quality is preserved:

[Convert mp3 to avi](http://ubuntuforums.org/showthread.php?p=7822073)

---

### Post by [rtmf] on 2009-08-29
> I provided some command-line examples in the following thread to create an image and combine it with the audio track to make a video.  The audio is just being copied and not re-encoded so the quality is preserved:

[Convert mp3 to avi](http://ubuntuforums.org/showthread.php?p=7822073)

This one DID help. Thanks big time!

---

### Post by krishan404 on 2010-02-25
hi guys, i modified the script from the link above to create a simple music video with one image for youtube:

```

#!/bin/bash
#dependencies: ffmpeg
# Usage: ./mp32youtube.sh input.mp3 output.mpg

background=/home/blabla/picture.jpg
#change it to the picture you want for your clip on youtube


ffmpeg -loop_input -i "$background" -i "$1" -acodec copy  -shortest -qscale 5 -s 640x480 "$2" 
exit

```
u can change -s parameter to your desired resolution. hope this helps!

---

### Post by robhardwick on 2010-12-18
You could try an online tool such as [mp32flv]("http://www.mp32flv.com") to do the job.
Rob

---

### Post by Geremia on 2011-06-23
> **robhardwick said:**
> You could try an online tool such as [mp32flv]("http://www.mp32flv.com") to do the job.
RobDoes it re-encode or just pass it through? Thanks

---

### Post by slooksterpsv on 2011-06-23
xcfa - it's in the Repos and it's GUI.

---

### Post by Geremia on 2011-06-23
> **krishan404 said:**
> hi guys, i modified the script from the link above to create a simple music video with one image for youtube:

```

#!/bin/bash
#dependencies: ffmpeg
# Usage: ./mp32youtube.sh input.mp3 output.mpg

background=/home/blabla/picture.jpg
#change it to the picture you want for your clip on youtube


ffmpeg -loop_input -i "$background" -i "$1" -acodec copy  -shortest -qscale 5 -s 640x480 "$2" 
exit

```u can change -s parameter to your desired resolution. hope this helps!Thank you! I used eyeD3 to extract the image album_art.jpeg from the MP3:
```
eyeD3 -i . my_mp3.mp3
```and fed it into ffmpeg with the simple command:```
ffmpeg -loop_input -r 1 -shortest -i album_art.jpeg -i my_mp3.mp3 -acodec copy out.mp4
```The "-r 1" option limits the framerate to 1 frame per second so the video isn't as big.

---

