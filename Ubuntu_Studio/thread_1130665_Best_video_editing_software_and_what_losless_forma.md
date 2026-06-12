---
title: "Best video editing software and what losless format should I use?"
date: 2009-04-20
forum: Ubuntu Studio
---

### Post by SnowPunk98 on 2009-04-20
Two noob questions that have been answered before I am sure, any help is appreciated.

1. What video editing software should I use, I lack creative skill and just want to do basics but eventually more would be nice.

2. I use MiniDV tapes and would like to rip the video off at its largest/best quality so that I can re-use the tapes. I want to make sure I have the best quality (regardless of size) how should I go about doing that?

---

### Post by wildman4god on 2009-04-20
**Kino **is the gnome program for ripping and editing videos from a DVcam, As for just video editing if you don't like kino, there are many video editors out there, but they all have a learning curve, you'll have to take time to learn the controls of the program, but some other video editors are, **PiTiVi **(works but not finished yet, has promise for an "easy-to-use" video editor), **Lives **and **Cinnerella **(used for more advanced stuff), **openvideoeditor **(basics and some advanced stuff, supposed to be easy to use) and **Bleander **(although a 3d modeling and animation program, I hear it also has a powerful video editor, ofcourse I have also heard that its interface is not easy to use (as I hear with almost any program in linux) you'll need to take an afternoon to just play around with it and learn how it works, there are also tutorials).

---

### Post by kayosiii on 2009-04-20
Well coming from minidv there is not much point converting before you go to your editing software most programs should dv encoded files (Kino is probably the best option for capture - you get to choose between DV encoded AVI's, Quicktimes and rawdv files.

If you want encode outside of your editing program or you tend to work back into the same video sources repeately (I do this when preparing video for visuals in live shows but it is hardly a typical thing to do)... Then you will want to go to a lossless format.

YUV4Linux is a pretty good option for this (it's still in YUV Colorspace so it is still a lot smaller than most other uncompressed formats). PNG or raw encoded Quicktime videos are another good option. Very High quality MJPEG seems to be another good option for moving video files around.

---

### Post by SnowPunk98 on 2009-04-20
Ill try out Kino when I get a chance I am still at a loss on which lossless format to use. I don't mind using up a ton of space for the videos, space is easy to come by. Basically I want the most raw video possible because I would re-use the tape which means the originals will be gone and I will be left with what is on my HDD and don't want to damage or lose that.

---

### Post by petespoors on 2009-04-20
I have Ubuntu Studio 8.10 as I thought this would make my job straight forward.  I have home dvds created on my SONY HD910  I was simply wanting to split the video into chapters and send relevant bits to family members, no fancy work or encoding etc, just load, snip, re-burn to dvd and distribute.  But loading the dvd does not automatically do anything, and Kino does not seem to have a "Rip DVD" feature.  I can open individual .vob files with MovieMaker, but there is no sound, and opening Movie Editor simply freezes the system (which is a fresh install from CD).

I had hoped 'Studio' would make this a simple task, but maybe I am expecting too much.  I really want to get to grips with Linux, but it still seems to rely heavily on command line input and sudo this and mount that.

If there is a simple process for my needs, I would appreciate the pointers. ( I have tried Windows MovieMaker, but it too appears to lack a "ripdvd" feature)


Pete

---

### Post by wildman4god on 2009-04-20
> **petespoors said:**
> I have Ubuntu Studio 8.10 as I thought this would make my job straight forward.  I have home dvds created on my SONY HD910  I was simply wanting to split the video into chapters and send relevant bits to family members, no fancy work or encoding etc, just load, snip, re-burn to dvd and distribute.  But loading the dvd does not automatically do anything, and Kino does not seem to have a "Rip DVD" feature.  I can open individual .vob files with MovieMaker, but there is no sound, and opening Movie Editor simply freezes the system (which is a fresh install from CD).

I had hoped 'Studio' would make this a simple task, but maybe I am expecting too much.  I really want to get to grips with Linux, but it still seems to rely heavily on command line input and sudo this and mount that.

If there is a simple process for my needs, I would appreciate the pointers. ( I have tried Windows MovieMaker, but it too appears to lack a "ripdvd" feature)


Pete

you need a dvd ripping program to rip the dvd first, I would suggest Handbrake as its the easiest dvd ripper I have used, it also converts your ripped dvd (or any video file) into any format you want. Then you can edit using your favorite video editor. As far as I know there is no video editor with a built in dvd rip option as dvd ripping is a rather long and involved process on it's own.

here is the link for hand brake:

[http://handbrake.fr/](http://handbrake.fr/)

Edit: Also to split the dvd into chapters you just rip each chapter individually as thats how they are stored on the dvd, and also just to explain why there is no "easy" way of doing this thats because dvd's wern't made to have their video ripped or edited (supposed to cut down on piracy).

---

### Post by petespoors on 2009-04-20
OK thanks, I'll give handbrake a go (as long as I can get it without all the sudo mount in sda0 etc)  As for dvd ripping, home vids will invariably have no protection to overcome (the illegal bit) and is now the format of choice surely? for home video.  I can after all "copy" straight from my DV tapes in the editors, so why not dvds?  I bet those with dvd video recorders think this is all a bit longwinded.

Thanks,

Pete

---

### Post by petespoors on 2009-04-21
HAndbrake simply does not run for me!  DownloadManager installed it ok and it appears under the "sound & video" heading, but clicking the bookmark does nothing, nothing in the system monitor either.
 Using the windows version works, but it seems as it it is going to take 6 hrs to do a single 1hr 30min  home dvd.  This could take me a long time,


Pete

---

### Post by wildman4god on 2009-04-21
> **petespoors said:**
> HAndbrake simply does not run for me!  DownloadManager installed it ok and it appears under the "sound & video" heading, but clicking the bookmark does nothing, nothing in the system monitor either.
 Using the windows version works, but it seems as it it is going to take 6 hrs to do a single 1hr 30min  home dvd.  This could take me a long time,


Pete

I have never had a problem with handbrake before, try running it from terminal and post the termianl feedback, it will say why it won't open. also yes ripping dvd's take a long time depending on what kind of computer you have, that's part of the reason it's not common, what are the specs of the computer your ripping on, if it takes a while then start it before you go to bed and let it chew on it through the night and it should be done by morning.

---

### Post by skullmunky on 2009-04-21
@SnowPunk98: just use the regular DV file compression, what you get when you capture using Kino from your MiniDV tape via Kino, etc.  (Note: I don't know about HD formats, this is advice for standard DV, 720x480).

The video on the tape is actually already compressed, using the Quasar DV codec.  The file you get when capturing from Kino or dvgrab or other programs is an exact copy of the data on the tape - there's no compression or conversion process involved in that step.  So, if you just keep the capture files, they're the same as keeping the tapes.  

If it's footage that's important to you, though, shell out the $ and buy more tapes instead of re-using.  Your HD will die before long (I don't mean anything about your drive specifically - hard drives just don't last that long).  

@petespoors: try out k9copy, it's a KDE app for ripping and copying DVDs.  There's also a neat desktop utility called "KRip2Clip" which lets you R-click on a DVD and rip a section to an AVI.

---

### Post by ryanisablond on 2009-04-21
@SnowPunk98: I agree with skullmunky: don't reuse miniDV tapes if you can help it. I'm a media major who has gone through dozens of them in the last 4 years. Whenever you re-use a tape, you run many risks: the tape itself being damaged/dirty from use, the timecode getting messed up from writing over older, different timecode. 

Moral of the story: shooting on used tape is Russian roulette. You'll eventually get burned. 


P.S.
Sorry you're having troubles with Handbrake. It's a very handy program to have.

---

### Post by kayosiii on 2009-04-21
Cinelerra can edit VOB files directly if the disk has doesn't have encryption or has been decrypted. I use this extract soundtracks from music DVDS :)

---

### Post by Junkieman on 2009-04-25
@snowpunk as mentioned, try kino. It looks like a good balance between usability and functionality.

@pete Next time create your own thread, it's pretty fun! Try ripping your DVD with [pgc.net]("http://clonead.co.uk/"), a DVD program chain ripper (win) and also with [Thoggen]("http://www.thoggen.net") (Ubuntu). 

However it looks like your cam compresses with the newer [MPEG4 AVC/H.264 compression]("http://www.camcorderinfo.com/content/Sony-and-Panasonic-Announce-Blu-Ray-High-Definition-Camcorder-Format.htm") (compared to older Mpeg2 DVD), do you have the codecs installed? Go to Add/Remove and search for "gstreamer", if it shows up unchecked (or not at all), have a look at [how to enable restricted software in Ubuntu]("http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html"), then try install gstreamer again. Good luck!

---

### Post by akakingess on 2009-04-26
When is Avid coming out with Xpress for linux?  That would be nice.

---

### Post by ssdt on 2009-04-26
I don;t understand something with Kino, there is no option to save the file in avi or even any kind of video format so that you can view it later. They all save them so it looks like text.

---

### Post by inobe on 2009-04-27
> **ssdt said:**
> I don;t understand something with Kino, there is no option to save the file in avi or even any kind of video format so that you can view it later. They all save them so it looks like text.

[http://www.youtube.com/watch?v=Ld9YsG8lZJ0](http://www.youtube.com/watch?v=Ld9YsG8lZJ0)

---

### Post by roberto.eiberle on 2009-04-27
export, not save. save produces a file you can only reopen in kino to get to where you left your edit. Export produces videofile.

---

