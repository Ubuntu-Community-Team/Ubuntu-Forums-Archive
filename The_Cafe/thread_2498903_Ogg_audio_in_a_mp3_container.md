---
title: "Ogg audio in a mp3 container"
date: 2024-07-02
forum: The Cafe
---

### Post by xinuzi on 2024-07-02
Noticed that if you give an ogg vorbis audio file a mp3 extension it gets accepted by (some) devices that are compatible with mp3 only.

music.ogg = not allowed, but samemusic.ogg.mp3 is.

Is that normal?

---

### Post by 909mjolnir on 2024-07-02
yeah, i've seen wierd stuff like that on MacOS, Windows, and Linux, and even in some DVD player hardware that supported a huge list of codecs more than they claimed.  
Technically, renaming the extension doesn't change the "container".  A Matroska file is a type of container.  

In some of my image programs for Windows and Linux, if the file is misnamed, the program will fix it.  
For example, if a file is a GIF but labeled as JPEG, the program will say, "Hey, this is really a GIF; do you want me to rename it?" and then it really renames it with the correct .GIF name extension.  I like stuff like that.  usuaully it still shows the file no matter what.  It's a nice trick or treat to get more filetypes supported than the devs claim.

---

### Post by xinuzi on 2024-07-03
> **909mjolnir said:**
> 
Technically, renaming the extension doesn't change the "container".  A Matroska file is a type of container.  


Knew I wasn't quite right about the 'container' in my title... It 'looks like' a container, let's say. Good of you to rectify.

Asamof, I tested this ogg-odd-thing on my car stereo.

music.ogg (and also music.aac) = no way!
music_ogg.mp3 = no problemo (didn't test music_aac.mp3, yet).

music_ogg.mp3 keeps running as an ogg-file on my linux.

---

### Post by xinuzi on 2024-07-03
> **909mjolnir said:**
> 
For example, if a file is a GIF but labeled as JPEG, the program will say, "Hey, this is really a GIF; do you want me to rename it?" and then it really renames it with the correct .GIF name extension.  I like stuff like that.  usuually it still shows the file no matter what.  It's a nice trick or treat to get more file types supported than the devs claim.

It does this because the header within the file claims 'this is gif'.

But, indeed, it seems that, whatever the header, some, presumably incompatible, file types do pass on some devices/systems just by renaming the extension to something that is compatible.

Linux will rather look for the header than for the extension in order to define the file type.

My car stereo is stupid enough to think: "o, nice, let's play this '.mp3' (but ogg)", lol.

And maybe it's best to put 'ogg' somewhere in the file name so you keep track of what the file actually is.

---

### Post by 909mjolnir on 2024-07-03
that's nice about the car stereo.  
supposedly OGG has slightly higher audible fidelity than MP3, higher resolution in focus group quality tests and such maybe I guess.  

It'd be nice to do audio.FLAC.mp3 and get FLAC output LOL.  
I think some companies are afraid to advertise some of their "strange and exotic" (Linux, alt codec) nicer features.  
So instead they just erase the specs and market towards a specific user.

---

### Post by xinuzi on 2024-07-06
okay, mp3 stays sufficient quality anyway.

I would say oga or aac/m4a, but there's that stubborn car stereo (mp3 Only) and I reach very decent music quality with mp3 vbr V2 (for the favorites) or V3 (for the regular).

I used to use mp3 cbr 128 khz 44.1 joint stereo for anything, but mp3lame (certainly since 3.1) vbr V2 or V3 khz 44.1, joint stereo gives that bit more kbps whilst still keeping file size acceptable.
Let's say vbr is my choice for newer music albums.

I could use mp3lame coding itself for my batch bash conversions, but also ffmpeg handles things swell.

Larger (but basic and logical) bash script with more formats, questions/answers/settings/tunings, metadata etcetera. The thingza for which I love Linuxa (& ubuntua & minta) so mucha :-) 
(in addition to general smooth/fast system updates)

---

