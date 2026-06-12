---
title: "Will a mono source result in a mono .OGG (vorbis) file?"
date: 2006-06-21
forum: The Cafe
---

### Post by MetalMusicAddict on 2006-06-21
I cant find a answer to this. I just bought "The Beatles - Live At The BBC" and everything is mono. Im still a little new to vorbis and am wondering if the input is mono will the output file be as well?

Thanx.

---

### Post by G Morgan on 2006-06-21
If the input is mono then the recording would be mono on any format.

---

### Post by MetalMusicAddict on 2006-06-21
[QUOTE=G Morgan]If the input is mono then the recording would be mono on any format.[/QUOTE]
Not always so. Ive seen mp3 encoders that force stereo and therefore create an unnecessaryly large file.

For instance. I use Grip to make mp3s. I ripped 1 track from the CD. If I encode it using **-V 3 --vbr-new**, my current settings, I get a 185kbps VBR Joint Stereo mp3 with a filesize of 295KB. If I add the **-V 3 [COLOR="Red"]-m m[/COLOR] --vbr-new** switch I get a 90kbps VBR mono mp3 with a filesize of 144KB. So the **--vbr-new** or the **-V 3** switch has a default set in it. So for my mp3 versions I had to add a mono switch.

The defaults in vorbis is what Im wondering about I guess. I cant seem to find a switch reference either.

---

### Post by G Morgan on 2006-06-21
I see what you mean now. Some encoders create stereo but enevitably produce the same sound out of each (so essentially mono in stereo). To be honest I'm not certain, they may be a configuration option somewhere, I use KAudioCreator which allows you to pass command line switches but I'm not sure if theres a force mono mode.

---

### Post by MetalMusicAddict on 2006-06-25
Anyone know of a command line switch reference for .ogg (Vorbis)?

---

