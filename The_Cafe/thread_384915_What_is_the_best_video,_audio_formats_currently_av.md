---
title: "What is the best video, audio formats currently available?"
date: 2007-03-15
forum: The Cafe
---

### Post by billdotson on 2007-03-15
I have heard of OGM, AVI, MPEG-1, MPEG-2, MPEG-4 and MKV.  For audio MP3,CDA (CD format I think) M4A (proprietary iTunes I believe), OGG and then the audio equivelant of MKV.

I have also heard of codecs like DivX, xVid, AC3, etc.

What are/do you think is the best video format? audio format?  I am asking in terms of quality.. like an MPEG-4 encoded w/ xVid seems to be pretty good.. fitting a 2.5 hour video on a CD you know..  

As I am not too knowlegable about codecs and containers and that stuff could someone please explain a bit about it?  I have been told that MPEG is more of a transport than a container like AVI and that the files are encoded with the codec and the file is then put into MPEG or AVI.  I do not completely understand..

---

### Post by jdhore on 2007-03-15
I wouldn't encode a 2.5 hour video to 700MB with Xvid or DivX because it would probably look like crap...for that i would have to say, as much as i hate to admit it, use OGG.

if you want high quality, i'd use h.264 or a really high bitrate and XviD...and AVI, MOV, H.264, Xvid, Divx, they're all codecs that are on the MPEG-4 "base" spec.

---

### Post by fenian on 2007-03-15
Ogg is just a container for compression formats ,i.e. ogg-vorbis  is the ogg container with vorbis audio  encoding.Some people use the open souce theora for video compression with the ogg container but you can use a number of different types of compression ,matroska,xvid,divx,etc...The thing to remember is that any compression is lossy and therefore degrades the image quality.To encode a 2.5 hour video to be put on cds,I would split the file in half with avidemux and then use ffmpeg or mencoder to encode each half in vcd format which you would then burn onto 2 cds.You end up with 2 cds but the video  quality would be better.

---

### Post by Polygon on 2007-03-15
not all compression is lossy....... take for example .zip and .tar.bz2 files... those archive are small then the orginial file but when you extract the file it is still the same file.

and also for example, FLAC compresses an audio file, but it is not a lossy compression

---

### Post by fenian on 2007-03-15
> 
not all compression is lossy....... take for example .zip and .tar.bz2 files... those archive are small then the orginial file but when you extract the file it is still the same file.

and also for example, FLAC compresses an audio file, but it is not a lossy compression

You are correct there are forms of lossless video compession (SheerPNG,Huffyuv,MSU Lossless Video Codec,etc...),however when it comes to video it is impracticle and rarely used [HERE]("http://wonko.com/article/286") is a good link that explains why better than I can.

---

### Post by RandomJoe on 2007-03-15
What is "best" would probably also vary depending on your intended use of the end product.  If you are simply burning to the discs as an archival / transportation mode, and will only be playing them on a computer using the same or similar software as what made it, you can just shoot for the best quality / smallest size.

However, if you are hoping to use the discs in a standalone player, you may have to be more careful.  I bought a relatively cheap standalone DVD player recently, first one I've ever owned, partially because it said it would play MPEG-4 and DivX files.  Okay, that's the format I use.  But on trying to make some discs and try them out on the machine, yes I could see all the files but they wouldn't play.  Turns out on further reading the thing only plays a very specific version of said files, and the way I'm using MPlayer to create mine does something different.

I also have quit trying to compress movies down to CD size.  The quality is annoying!  DVDs have become cheap enough that I now just compress to fit those.  Although I haven't actually burned any of mine in a long time - I just built a big server and store everything there, streamed to a small "media PC" playing in the living room.  (Currently a Mac Mini running VLC on OSX.)  

I currently tell MPlayer to shoot for a 2k video bitrate encoding to MPEG4, which lands me in the 1.5-2GB range for most movies, I seldom can tell that it's been compressed from the original, and they are small enough to stream over a 100Mbps network connection smoothly.  It's been a while since I set that up, it might be worth seeing what other formats are now available...

For audio, I store everything on my server compressed with FLAC, streaming from there in-house.  I also created two MP3 sets at one point - a higher bitrate for regular listening on my Windows work laptop, and a lower one to cram more time into a player I take with me on my bike.

---

### Post by billdotson on 2007-03-15
so I am somewhat lost on the technicalities of video and audio containers, transporters, codecs, etc.

I have heard that compressing a 2-2.5 hr video down to 700MB size doesn't affect the quality that much.. unless you are obsessed w/ quality.  I recorded Back to the Future off of cable so first of all BtF isn't a high-def movie and secondly it is on normal cable so it wouldn't be HD anyway.  I was encoding it w/ avidemux and set the bitrate to something like 800 and it said the final output would be 650MB.  I set the final size to 650 because the first time I set it to 700 and it came out being 780 or something like that.

So if I were to compress my videos down to an acceptable size to keep on a harddrive for watching on the PC what would be the best to use?

If I wanted to play them on a DVD player like the X360 for instance I would have to use Mpeg-2 and AC3 audio wouldn't I?

thanks

---

