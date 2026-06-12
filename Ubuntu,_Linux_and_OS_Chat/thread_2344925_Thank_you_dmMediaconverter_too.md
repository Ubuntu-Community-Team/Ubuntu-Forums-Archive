---
title: "Thank you dmMediaconverter too"
date: 2016-11-29
forum: Ubuntu, Linux and OS Chat
---

### Post by xinuzi on 2016-11-29
Encoding/editing video is first of all a visual thing to me.

FFmpeg cli has lots of possibilities and a rather complicated learning curve. Demands a lot of knowledge of specifics of digital video also. Not easy for everyday end users...

So people look for a comprehensible gui program to help them with basic (and extensive) video converting and editing tasks.

Mentioned FFqueue before in the FFmpeg suit context. 
FFqueue converts well, filters work well, but it can't cut up and join videos in stream copy mode.

Another FFmpeg suit that does do basic stream copy editing is dmMediaConverter ([http://dmsimpleapps.blogspot.be/](http://dmsimpleapps.blogspot.be/) - See further down on that page for the 32bits and 64bits deb-files)

This program, created by Marius Dalacu, gives you a 'Job Type' menu with the possibilities: 'Convert', 'Merge the same', 'Merge different', 'Split' and 'Bulk'.

The splitting function just cuts up the input and saves all the parts as different, numbered video files. 

It doesn't cut parts (preferably on keyframes) of the input file and then gives you the possibility to save what is left over as one video file (as e.g. avidemux does). 
Avidemux doesn't work well (anymore) on Ubuntu. DmMediaConverter is an effective alternative.
As VLC, dmMediaConverter has problems with handling folders which have certain accents in their name (E.g. "Video's" folder on Dutch language systems.). Save to or call from folders without accents or spaces.

Unfortunately many of the bigger repositorywise proposed video editing applications don't stream-copy-split-and-merge at all. You almost always have to reencode.

---

### Post by TheFu on 2016-11-29
Free tools for transcoding videos are handbrake, ffmpeg, avconv, mencoder.  **handbrake** is my GUI tool for much.  Don't forget the F/LOSS **mkvtools** set.  Handy for when cutting all tracks (including multiple audio and sub/srt tracks are included) around stuff you don't want. No re-encoding.  The downside for some is that mkv containers have to be used.  OTOH, MKV is the most versatile container available today and most playback devices support it, but not all. If your HW player doesn't like mkv, not much can be done.  Normal operating systems do support MKV if the files inside the container are encoded with normal video/audio codecs (h.264/aac/mp3/ac3/ogg/vorb ... you get the idea).

There just isn't any need to pay for an app like the OP, but sometimes a few bucks makes life much easier.  The OP seems a little like an ad, btw.

Should also point out that this is distributed as an unsigned binary.  Attempted to run it inside a firejail namespace and it failed to start. Looks like a GTK app, so it should work - every other GUI tool I've tried under firejail has worked, so this is a first for me. The debug output isn't helpful. *I won't run unknown binaries from unknown sources.* The author is probably very respectable, but I don't KNOW that.

Does DmMediaConverter handle .EDL files and handle multiple tracks correctly?  That's the only reason I'm still using Windows Video Redo Suite - proper EDL file support.

---

### Post by sonicwind on 2016-11-29
> **xinuzi said:**
> 

The splitting function just cuts up the input and saves all the parts as different, numbered video files. 

It doesn't cut parts (preferably on keyframes) of the input file and then gives you the possibility to save what is left over as one video file (as e.g. avidemux does). 


Marius recently told me on another forum that this feature will be available in version 1.9.

---

### Post by xinuzi on 2016-11-29
> **sonicwind said:**
> Marius recently told me on another forum that this feature will be available in version 1.9.

Great :p

---

### Post by mdalacu on 2016-12-29
Here you can find an x64 deb. Enjoy!
[https://drive.google.com/folderview?id=0B1MiTYJef5a9TG9kMC04WWE3YkU&usp=sharing#list](https://drive.google.com/folderview?id=0B1MiTYJef5a9TG9kMC04WWE3YkU&usp=sharing#list)
...and Thank You!

---

### Post by mdalacu on 2016-12-30
> **TheFu said:**
> Free tools for transcoding videos are handbrake, ffmpeg, avconv, mencoder.  **handbrake** is my GUI tool for much.  Don't forget the F/LOSS **mkvtools** set.  Handy for when cutting all tracks (including multiple audio and sub/srt tracks are included) around stuff you don't want. No re-encoding.  The downside for some is that mkv containers have to be used.  OTOH, MKV is the most versatile container available today and most playback devices support it, but not all. If your HW player doesn't like mkv, not much can be done.  Normal operating systems do support MKV if the files inside the container are encoded with normal video/audio codecs (h.264/aac/mp3/ac3/ogg/vorb ... you get the idea).

There just isn't any need to pay for an app like the OP, but sometimes a few bucks makes life much easier.  The OP seems a little like an ad, btw.

Should also point out that this is distributed as an unsigned binary.  Attempted to run it inside a firejail namespace and it failed to start. Looks like a GTK app, so it should work - every other GUI tool I've tried under firejail has worked, so this is a first for me. The debug output isn't helpful. *I won't run unknown binaries from unknown sources.* The author is probably very respectable, but I don't KNOW that.

Does DmMediaConverter handle .EDL files and handle multiple tracks correctly?  That's the only reason I'm still using Windows Video Redo Suite - proper EDL file support.

If that post it's an AD then it is not made by me...:-) 
Yes, i don't sign the binarys. Nobody asked me to do it and right now i don't know how to do it. The program is 3$ on Ubuntu Software Center but is free on my site...just grab the deb file.
Give my an .EDL file to test it.
Thank you.

---

### Post by mdalacu on 2017-04-04
#dmMediaConverter 
[http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html)
Version 2.1.0 is up
- Now you can have special characters in file names on windows and single quote on linux systems.
- FFMpeg progress output is done on single line.
- Clear settings when done option (default on).
- Split: new Trim mode
- More... now you could manually specify input file format (in case FFMpeg auto detection fails)
- NVENC on Linux x64 and Windows.
- Intel QuickSync on Windows (you must have Intel Media SDK installed). If you manage to get the SDK installed on Linux it should be working also.
- Lots of bug fixing
- Updated FFMpeg binary with latest version
- WinXP - no longer supported. You could use this version with a ffmpeg binary without mfx.
Enjoy and please provide feedback!&#65279;

---

