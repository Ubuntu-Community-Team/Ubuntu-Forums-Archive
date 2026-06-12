---
title: "How do I turn a *.mod file into something usefull?"
date: 2008-05-28
forum: Ubuntu Studio
---

### Post by Morichalion on 2008-05-28
I recently got a new hdd camera, and it creates .mod files. Now, I can watch the video in pretty much any video player I like, they work fine.

The problem I'm experiencing happens whenever I try putting the damn thing into a video editor. On my windows box, I use Magix Movie Edit Pro, and on my Ubuntu box, I'm trying out Kdenlive. In both cases, when loading up the video file, the audio is lost.

---

### Post by lisati on 2008-05-28
Possibly the camera is using some minor variation of the MOD format that the video editor isn't recognizing.

The hdd cameras I've used produce MPG files which have played quite happily in Windows Media Player, even though the instruction books say they're "Dolby Digital", a different audio format.

Does the software that came with the camera have the ability to convert the files to a different audio format?

---

### Post by Morichalion on 2008-05-28
> **lisati said:**
> Possibly the camera is using some minor variation of the MOD format that the video editor isn't recognizing.

The hdd cameras I've used produce MPG files which have played quite happily in Windows Media Player, even though the instruction books say they're "Dolby Digital", a different audio format.

Does the software that came with the camera have the ability to convert the files to a different audio format?

I haven't been able to get the software to get any video from the camera, and the software appears to lack the capability to import from the pc's hard drive.

---

### Post by Digressive on 2008-05-29
The only experience I've had with HD based video cameras with .mod files is on Windows XP and rather than install the supplied software which the media techies (you know I love you guys really) had misplaced, the codecs installed with Nero Express 6 seemed to allow WMP11 to play the file okay. Don't know if this will help any but maybe it'll open up a door or something.

D 

Edit: Just one more thing: without the Nero Express being installed we got video but no audio, so it must just  add an audio codec of some sort. Sorry, okay, I'll shut up now.

---

### Post by mstjohn1974 on 2009-11-05
I'm having a Panasonic and I am using the mod2avi script from [http://mod2avi.sourceforge.net/](http://mod2avi.sourceforge.net/) it works very well after a little tweak you have to do...it converts mod (mpeg2/ac3) files to avi (xvid/mp3) files.

just follow the steps and then use nano and change:

xvid to libxvid

mp3 to libmp3lame

save it and use it...works great

---

