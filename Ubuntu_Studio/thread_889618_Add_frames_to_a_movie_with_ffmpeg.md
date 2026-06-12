---
title: "Add frames to a movie with ffmpeg"
date: 2008-08-14
forum: Ubuntu Studio
---

### Post by kevinchannon on 2008-08-14
Hi,

 I'm trying to use ffmpeg in a program that I'm writing in C/C++ and I was wondering if anyone knows if it is possible to add frames to the end of a movie file, without converting the whole video to a series of images and then re-converting them back into a movie.

   Many thanks,
             Kevin

---

### Post by FakeOutdoorsman on 2008-08-14
This would be a good question for the [ffmpeg-user mailing list]("http://ffmpeg.mplayerhq.hu/mailinglists.html").  Just make sure you're using the latest version of ffmpeg, don't top post, and they will probably give you an answer.  There is also the #ffmpeg IRC channel, but it is usually quiet.

If you need help compiling ffmpeg SVN:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by Creative2 on 2008-08-15
well i think ffmpeg like mencoder can do it just create a video  of your photos with ffmpeg ... then you could merge  2 videos with cat



see here for encoding picture

[http://ffmpeg.mplayerhq.hu/faq.html#SEC14](http://ffmpeg.mplayerhq.hu/faq.html#SEC14)

if you have a 25fps you have to create almost 1 s of movie from your photo so you have to create 25 copies of your photo, if you don't want a second of your picture but only a frame you should consider to try to use 

ffmpeg -f image2 -i img%d.jpg  -r 1  /tmp/a.mpg instead of default command line 

anyway if you want merge 2 videos it's always better  have 2 videos with the same characters like frame for seconds bitrate and codec ...

if mpg is not your prefered format you could encode "picture-movie" with ffmpeg as you like then you could use

cat INPUT1.avi INPUT2.avi > MERGEDFILE.avi

maybe this is better (maybe could work only with mpg format i have never tested)

cat INPUT1.avi INPUT2.avi  | ffmpeg -y -i  -genpts -vcodec copy -acodec 
copy MERGEDFILE.avi

cheers

---

