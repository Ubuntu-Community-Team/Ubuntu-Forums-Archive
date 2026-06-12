---
title: "Ripping DVDs for Hard Drive playback - which container?"
date: 2006-06-18
forum: The Cafe
---

### Post by mmx1 on 2006-06-18
Now that I've got a rudimentary NAS setup, I'd like to rip my DVD collection and have them available for viewing over the network. What's the best container to store them as and what's the best way to rip them? My priorities are:
1. Keep subtitles and multiple audio tracks. I know Matroska can do the latter but support in windows is shoddy.
2. Playable in linux and windows with a minimum of intervention. I know WMP will automatically insert subtitles if the filenames of the video and .sub line up; I'm sure I can configure Mplayer similarly.
3. Fairly easy to rip. My only experience is with GordianKnot in Windows (I don't mind using windows to rip, I suspect the utilities are better there anyway).

So really, it comes down to, do I keep them as a decrypted video_ts directory or are there encapsulated formats that will come pretty close and aren't as clunky to store?

---

### Post by kb3hkg on 2006-06-20
not sure on subtitles but rip with DVDrip-O-Matic. you can use a format that will be playable in both OS's.

---

### Post by sup on 2006-07-09
dvd decryptor, dvd shrink and virtualdubmod all work great under wine (that means that you have them set up and running in less then ten minutes, just look them up in appdatabase - and they do not crash, at least I think). - if you prefer windows tools.

I personally use avidemux, it needs dvd to be preprocesed with mplayer (see avidemux documentation, there is a nice and easy-to-follow guide to dvd-to-avi) - if the dvd is encrypted, dvddecrypter does the job then.

If you want matroska (and can play in windows fairly good, I think, at least when you use vlc), then use mmg. [http://www.bunkus.org/videotools/mkvtoolnix](http://www.bunkus.org/videotools/mkvtoolnix)

I do not know about audio tracks, maybe you will need to actuall rip the dvd twice and then merge the audio with mmg (it is very easy)

---

### Post by tsb on 2006-07-10
You could just rip them into full isos and use VideoLan to stream them.  That should work well, and there's no hassle.

---

