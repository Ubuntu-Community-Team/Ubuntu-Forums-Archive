---
title: "VLC Ubuntu server Problems."
date: 2011-06-11
forum: Server Platforms
---

### Post by Thegmandrive on 2011-06-11
Hi all.. 
I have installed Mediatomb and have it running perfect.. accept the transcoding doesn't work. 

I am trying to use VLC to transcode .MKV files. I realize (at least right now that my problem lies with VLC launching)

When I try to launch VLC I keep getting this error. 

> VLC media player 1.0.6 Goldeneye
[0x8f39c10] inhibit interface error: Failed to connect to the D-Bus session daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

[0x8f39c10] main interface error: no suitable interface module
[0x8e8c148] main libvlc error: interface "inhibit,none" initialization failed
[0x8f26368] main interface error: no suitable interface module
[0x8e8c148] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8f26368] dummy interface: using the dummy interface module...
[0x8f3f000] mux_ps mux: Open
[0x8f3f000] mux_ps mux: Close
[0x8f22800] signals interface error: Caught Terminated signal, exiting...I have tried to launch VLC in many different ways with no avail. 
for example
I have tried to run commands
cvlc
vlc -I dummy
vlc -I http
cvlc -I http
vlc


Im pretty much trying everything I can think of, and I keep getting the error above(or very similar errors)

Im not sure what else to do but ask the experts.

---

### Post by donniezazen on 2011-06-11
Their isn't an easy solution to on-demand-video-streaming. I have started using subsonic to stream audio and video to my android and on the go using any browser. It does everything on its on plain and simple.

---

### Post by Thegmandrive on 2011-06-11
well I got mediatomb working just fine. It's the transcoding that I seem to be having difficulty with. 

Its transcoding from VLC that is the problem. VLC wont even run proper due to the error.

---

### Post by Thegmandrive on 2011-06-11
alright, I gave up on mediatomb. Mediatomb would have been more than great if i didn't need to transcode anything... but alas.. i do. 

I am now running ps3mediaserver... It now works great.. and playing around with it for 6 hours... 

ps3mediaserver does everything I need it to.

---

