---
title: "[SOLVED] Converting Videos for Sansa View"
date: 2008-08-17
forum: Ubuntu Studio
---

### Post by Super TWiT on 2008-08-17
I have a Sansa View and was wondering how to convert videos for it.  I was thinking of using something like mplayer, but am not sure if that will work.  I also would like to (if possible) have a dvd ripping application that will rip directly to MPEG 4 and have video resize options.  I have tried OGMrip, but it gives me an error saying "Unknown error merging files".  The videos that work on the Sansa View are H.264/MPEG-4 AVC files.

---

### Post by Super TWiT on 2008-08-17
Oops, this should really be in the Multimedia & Video section.  Sorry about that.

---

### Post by Creative2 on 2008-08-20
could you install ffmpeg then take a video that works for your "Sansa view"
and run 

ffmpeg -i INPUTFILE 2>&1 | grep Stream

---

### Post by Super TWiT on 2008-08-21
Thanks Creative2.  After running those commands the video that plays registers as this:  ```
Stream #0.0(eng): Video: h264, yuv420p, 320x240, 30.00 fps(r)
Stream #0.1(eng): Audio: aac, 44100 Hz, stereo
```

I tried encoding a video with these options using ffmpeg, but on my Sansa it says "Unsupported Format".  These are the options I used:```
ffmpeg -i video.* -acodec aac -ab 96 -vcodec h264 -qmin 3 -qmax 4 -r 30 -s 320x240 video.mp4
```  I ran the video ffmpeg made through the commands that you listed afterwards, and the video streams were exactly the same other than it said that the language listed instead of eng was undefined.  Should I change what options I am using?

---

### Post by Creative2 on 2008-08-22
mmm....mumble try with this..

ffmpeg  -i INPUT -r 29.97 -vcodec xvid -b 700k -acodec aac -ab 128k -bufsize 4M -qmax 51 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -ar 44100 -g 300 -s 320x240 -aspect 4:3 -ac 2 -f mp4 -y OUTPUT

---

### Post by Super TWiT on 2008-08-24
Thanks Creative 2, that worked really well.  Thanks!  Now I can finally ditch that buggy Sansa Media Converter! Yes!

---

### Post by Creative2 on 2008-08-24
you could  test with h264 too that command line use xvid  ...but that is slower..

---

### Post by snakep on 2008-09-06
I am trying the same thing.  However, I get error messages "Unknown video codec xvid", and if I use h264 instead I get "Unknown audio codec aac".  Where do I get these codecs, and how do I install them?

Thanks,
Jeremiah

---

### Post by snakep on 2008-09-06
I am trying the same thing.  However, I get error messages "Unknown video codec xvid", and if I use h264 instead I get "Unknown audio codec aac".  Where do I get these codecs, and how do I install them?

Thanks,
Jeremiah

---

### Post by Creative2 on 2008-09-06
-----> add medibuntu repository
------->reinstall ffmpeg
= solved

for medibuntu repository see google 
for codecs see my signature...

---

### Post by snakep on 2008-09-06
> **Creative2 said:**
> -----> add medibuntu repository
------->reinstall ffmpeg
= solved

for medibuntu repository see google 
for codecs see my signature...

Thanks for the reply.

I added medibuntu, and reinstalled ffmpeg.  I also installed the restricted-extras package.  I still get the same errors, though.  In synaptic, the ubuntu-restricted-extras package is shown as installed.  What am I missing?

Thanks,
Jeremiah

---

### Post by Creative2 on 2008-09-07
you have installed bad your ffmeg that is your problem.

open a terminal and check your installation with this

ffmpeg -formats |grep aac



if you don't get back this

 D  aac             ADTS AAC
 DEA    aac
 D A    mpeg4aac



you have installed bad ffmpeg

you should search on forum ffmpeg unknow codec aac

---

### Post by snakep on 2008-09-07
Okay, thanks.  Synaptic wasn't looking to the medibuntu repository apparently.  I don't know how it figures out where to look.  I went to the medibuntu site and downloaded and installed both ffmpeg and libavcodec, and now it works.  Thanks again.

---

### Post by MrWES on 2008-09-07
When you add a new repository, you must "reload" in synaptic to enable it.

Bill

---

### Post by ilhadad on 2009-01-10
I was able to get video converted and playing properly in my Sansa View with the following function defined in the .bashrc file in my home directory:

# Command line function to convert video for sansa player
sansavideo() {
frame_per_second="23.98"
video_bit_rate="578k"

ffmpeg -i "$1" -r 29.97 -vcodec mpeg4 -b $video_bit_rate -ar 44100 -g 300 -s 320x240 -aspect 4:3 -ac 2 -f mp4 -y "$2"

}

Every time I want a video converted I just type at my command prompt:

sansavideo inputfilename.ext outputfilename.mp4

Where inputfilename.ext is the input file name and its respective extension and outputfilename.mp4 is the MP4 file that can be copied into the Sansa View device.  To copy the file once you have your Sansa View device connected in MSC Mode do the following:

cp outputfilename.mp4 /media/SANSA\ VIEW/VIDEO/

to copy the file into the device.

For those of you who do not know what MSC mode is here is a short explanation.  MSC stands for Mass Storage Controller mode.  In this mode your device behaves like an USB thumb drive.  To place the device in this mode:
1) Prior to connecting the device to you computer, lock the device by moving the slider to the lock position.
2) Press and hold the dial on the left side until the image of the lock on the screen disappears (about 5 seconds).
3) Release the dial.
The device is now in MSC mode and is ready to be connected to the computer.  Keep in mind that you will need to follow this procedure prior to connecting the device to the computer every time you wish to be in MSC mode as it resets itself to MTP (Media Transfer Mode) once it is disconnected.

---

### Post by blissb2599 on 2009-01-23
None of these options are working for me. :confused:

I have a Fuze silver (8GB).  Firmware: V01.01.22A  I've tried every command line listed here, and still get the incompatible format error on the Fuze.

I can view videos converted with SMC, and have had no issues with laggy audio, or anything like that.

---

### Post by Ulysses on 2009-01-29
Thank you, ilhadad

That was an excellent and concise post
It got my hopes up that my Sansa wasn't such a dud after all
It plays mp3s all fine in MSC mode, but it won't play ogg files. But that's not my issue

It's the video
I followed the steps you listed and checked to make sure my ffmpeg is current, but I keep on getting this message whenever I try to convert the file
Bearing in mind, of course, that this is a learning experience for me, so please be gentle.

```
INPUT.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.
```

But I can play the file fine using any player on my desktop

Can you please help me try and figure out what I can do to make this work?

Anything would be appreciated. Thanks.

RAR

---

### Post by oxcrete on 2009-05-28
Adding, " -threads n" where 'n' is the number of parallel threads - might speed up your processing. Monitor your processor load. as a rough guideline, 2 threads per processor works for me. when ffmpeg is running, look at the status line for the FPS  and bits/sec numbers and experiment

---

### Post by SallyBlue on 2009-06-23
> **Ulysses said:**
> Thank you, ilhadad

That was an excellent and concise post
It got my hopes up that my Sansa wasn't such a dud after all
It plays mp3s all fine in MSC mode, but it won't play ogg files. But that's not my issue

It's the video
I followed the steps you listed and checked to make sure my ffmpeg is current, but I keep on getting this message whenever I try to convert the file
Bearing in mind, of course, that this is a learning experience for me, so please be gentle.

```
INPUT.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.
```

But I can play the file fine using any player on my desktop

Can you please help me try and figure out what I can do to make this work?

Anything would be appreciated. Thanks.

RAR
I'm having the same problem.  Can anyone help us out with this?

---

