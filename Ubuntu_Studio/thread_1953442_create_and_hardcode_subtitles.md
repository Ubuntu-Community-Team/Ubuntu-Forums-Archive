---
title: "create and hardcode subtitles"
date: 2012-04-06
forum: Ubuntu Studio
---

### Post by DataSpy on 2012-04-06
I have a friend that spoke at an Albanian church and someone made a DVD of it.  I copied the DVD to my hard drive (video.vob) and used kdenlive to put a watermark on (video.vob) and then encoded it to .flv (video.flv) since he wants to upload it to youtube.

The next thing I have to do is add subtitles to (video.flv), my question is: how should I go about doing this?  I want to hardcode the subtitles and I don't want to reencode the .flv file.  Can I accomplish this with kdenlive or would I need to use another program?  

Any help is greatly appreciated, thanks in advance!!

---

### Post by SeijiSensei on 2012-04-06
[Aegisub]("http://www.aegisub.org/") is the most commonly-used free program to create subtitles.  You'll have to re-encode the video if you want to create "hard" subtitles that are burned into the video stream itself.  You can also use "soft" subtitles which are a separate stream in a container format like MKV or MP4.  In that case, though, you'd need to play the videos with software that knows how to handle soft subtitles, like smplayer/mplayer.

---

### Post by DataSpy on 2012-04-06
I was messing with this a little, I had trouble installing it on ubuntu so I installed it on windows in a vm.  It also looked kinda complicated :P

What's the best way to avoid quality loss, I tried to open the .vob but it doesn't show the video.  I don't want to have to encode it just so I can open the file and then reencode it.

Thanks, 
Jim

---

### Post by SeijiSensei on 2012-04-06
I'd say the easiest solution would be to use [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases") to rip the DVD to Matroska (MKV), create the subs in Aegisub, and store them in a .srt file.  Then use Handbrake again to integrate the subs with the original video.  It has options to create a hard-subbed version.  Let YouTube handle the conversion from MKV to Flash for you during the upload.

---

### Post by DataSpy on 2012-04-06
Thanks!!!!!!!!!!!

---

