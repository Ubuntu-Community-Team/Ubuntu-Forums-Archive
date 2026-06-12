---
title: "Updated help for converting h.264 mkv to mp4?"
date: 2008-12-23
forum: Ubuntu Studio
---

### Post by Nixie Pixel on 2008-12-23
Hello, I am trying to stream some .mkv files to my Xbox 360, and after searching for some help I came across this thread:

[http://ubuntuforums.org/showthread.php?t=684780&highlight=mencoder+container+xbox+convert&page=2]("http://ubuntuforums.org/showthread.php?t=684780&highlight=mencoder+container+xbox+convert&page=2")

I am a complete newbie when it comes to multimedia, and I have learned only enough to know that I have (I believe) an h.264 video in a .mkv container that I need to get to .mp4 or another format that the Xbox can read.  I have installed mencoder but have no idea how to use it.

Unfortunately the links in that thread to Nero AAC don't work, so I don't know how I can use the script there.  Is there an updated script that does not require Nero AAC?  (Searching for it on Nero's site comes up with nothing)  

Is there, perhaps, another way to do this conversion?  The file I am trying to convert is an HD movie, and it is 4.4GB in size.  Reading that thread it seems this may be a problem for streaming to the Xbox (I'm using Twonky for streaming).  Is there a workaround?

Thanks in advance!

~Nix

---

### Post by Nixie Pixel on 2008-12-26
Can anyone assist?

Really, my problem seems simple.  I have a .mkv file.  I want to stream it to my Xbox 360.  How do I do this?

Thanks!

~Nix

---

### Post by ShoeUnited on 2008-12-27
Have you tried the guidelines in this thread [http://ubuntuforums.org/showthread.php?t=689757]("http://ubuntuforums.org/showthread.php?t=689757")?

-Shoe

---

### Post by Nixie Pixel on 2008-12-29
Thanks, I still can't follow the instructions as the Nero page listed no longer exists...

---

### Post by FakeOutdoorsman on 2008-12-29
You can do this with ffmpeg.  You will need to install the unstripped ffmpeg libraries first:
```
sudo apt-get install libavcodec-unstripped-51
```
Alternatively, you can compile the latest ffmpeg since it is actively developed and will give you access to the libx264 presets:

[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

Now try ffmpeg:
```
ffmpeg -i input.mkv -vcodec copy -acodec libfaac -ab 128k -vframes 300 output.mp4
```
This will create a video that is 300 frames long.  Once this video works, you should remove "-vframes 300" to encode the whole thing.  It shouldn't take too long though because the video is being copied and the audio is the only thing being encoded.

If this initial video doesn't work, then install MP4Box (part of the gpac package):
```
sudo apt-get install gpac
```
Then run the video through MP4Box:
```
MP4Box -add ffmpegoutput.mp4 newoutput.mp4
```

---

