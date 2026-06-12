---
title: "Producing screencasts on vanilla Ubuntu"
date: 2009-04-16
forum: Ubuntu Studio
---

### Post by PacSci on 2009-04-16
I plan on making some screencasts to teach people how to use Ubuntu. What I'm looking for is a process for recording a desktop session, narrating it, and exporting it to Ogg Theora or another common, non-proprietary format. Based on what I've read so far, I'll probably use recordmydesktop to do the recording part, but I don't know how I'm going to edit the videos and narrate them. Any suggestions?

---

### Post by rorkimaru on 2009-04-17
This is something I've struggled with myself. At the moment I have to choose between going onto my old windows PC and doing it in windows movie maker (not a solution at all) or record the audio with Audacity and add it in with kdenlive. It's not a perfect solution but you can sync the audio pretty well and since it's not live video, just a screen cast manual syncing is ok.

The thing I like to do is edit my video (saving constantly, the program looks nice but tends to crash) and then open audacity and record while I watch the playback of the video.

As far as I know there is no direct naration software for Ubuntu at the moment

---

### Post by Dai777 on 2009-04-20
> **PacSci said:**
> I plan on making some screencasts to teach people how to use Ubuntu. What I'm looking for is a process for recording a desktop session, narrating it, and exporting it to Ogg Theora or another common, non-proprietary format. Based on what I've read so far, I'll probably use recordmydesktop to do the recording part, but I don't know how I'm going to edit the videos and narrate them. Any suggestions?

yep RMD will work just fine for what you want
just get a head set and talk while you sre recording

---

### Post by lukeiamyourfather on 2009-04-20
Most of my work has been converted over to Linux, but screen recording is something that simply hasn't evolved enough to be mainstream usable from what I've seen. There's no lossless video codec appropriate for screen recording, there's no appropriate editor, and few transcoding tools that are user friendly.

I ended up buying a copy of Camtasia Studio to record VNC sessions from an Ubuntu system. Somewhat of a Rube Goldberg setup, but it works very well until the day when there's a better native solution in Linux. If you need 3D support then x11vnc server can be used with the -noxdamage flag. Cheers!

---

### Post by krevuru on 2009-04-20
Did you try **_gtk-recordMyDesktop_**?
That produces some decent quality Screencasts. I have done a few screencasts in the past and they were decent enough. And the app itself is not so bad, and comparable to Camstudio/likes.

---

### Post by Junkieman on 2009-04-25
> **krevuru said:**
> Did you try **_gtk-recordMyDesktop_**?
That produces some decent quality Screencasts. I have done a few screencasts in the past and they were decent enough. And the app itself is not so bad, and comparable to Camstudio/likes.
I second gtk-recordMyDesktop, being the most stable I've found so far. It saves the files in the .ogv format which imports into Avidemux, and is playable on Ubuntu machines anyway :)

You can strip the audio out and remove noise and normalize it using Audacity, if it comes to that.

Additionally it would be very handy to get a video editor to add captions and transitions for that professional look, I'm currently on the hunt for one myself.

---

