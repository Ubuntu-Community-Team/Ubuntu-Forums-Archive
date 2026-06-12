---
title: "This is REALLY simple."
date: 2008-06-13
forum: Ubuntu Studio
---

### Post by El Lance-O on 2008-06-13
All I want to do, I add an mp3 as background music to video with none.

That's it. Nothing else.

I've tried Kino, Cinelerra, and Piviti or whatever it's called.

None of them work, or have any instructions. I'm having troubling finding help on google, so I thought I might take a chance at getting help here.

Anyone?

---

### Post by roaldz on 2008-06-13
> **El Lance-O said:**
> All I want to do, I add an mp3 as background music to video with none.

That's it. Nothing else.

I've tried Kino, Cinelerra, and Piviti or whatever it's called.

None of them work, or have any instructions. I'm having troubling finding help on google, so I thought I might take a chance at getting help here.

Anyone?

I´ve done it with cinelerra. Just import the mp3 file as a new resource. go to your resources, en drag it into a stereo audio track.

---

### Post by El Lance-O on 2008-06-13
I don't think it is working properly. I don't hear any audio output, and I can't just save it as an AVI and go on my happy way.

This is REALLY irritating.

I will even send the files to someone if they can do it for me. This is so INCREDIBLY simple, there is no reason why I had to spend HOURS last night trying to find a program that will do it, only to realize none of them will. :)

Please help!

---

### Post by FakeOutdoorsman on 2008-06-13
You can try ffmpeg:
```
ffmpeg -i videofile.avi -i audiofile.wav -vcodec copy -acodec copy output.avi
```
No reencoding needed.  If you're working with [restricted codecs]("https://help.ubuntu.com/community/RestrictedFormats") you will need to use a third-party repository such as Medibuntu or [compile ffmpeg yourself]("http://ubuntuforums.org/showthread.php?t=786095").  MEncoder can probably do this too, and you wouldn't need to use Medibuntu or compile anything.  If you're working with mp4 files, then MP4Box (part of gpac) will work as well:
```
MP4Box -add audiofile.mp3 videofile.mp4
```
I don't see many Alaskans here. I'm in Juneau.

---

### Post by roaldz on 2008-06-14
> **El Lance-O said:**
> I don't think it is working properly. I don't hear any audio output, and I can't just save it as an AVI and go on my happy way.

This is REALLY irritating.

I will even send the files to someone if they can do it for me. This is so INCREDIBLY simple, there is no reason why I had to spend HOURS last night trying to find a program that will do it, only to realize none of them will. :)

Please help!

I assume you are using cinelerra from the akirad repos. 
> Settings> Preferences> playback> audiodriver> esound>

on server leave empity
on port set 7007).

BEFORE USE CINELERRA ON HARDY UPDATE TO KERNEL 2.6.24-17 (JUST UPDATE THE SYSTEM WITH UPDATE-MANAGER).


---

### Post by ugm6hr on 2008-06-14
I did exactly that with kdenlive.

You import the video, mute the video's soundtrack (which is presumably silent anyway). and then import the audio track on a separate channel.  Then unmute the audio track.

Make sure you align the timings of audio vs video tracks (i.e. where you want the audio to start), and use fades in / out if you want.

Then export.

Kdenlive is still a bit unstable - so just make sure you save at regular intervals.

---

