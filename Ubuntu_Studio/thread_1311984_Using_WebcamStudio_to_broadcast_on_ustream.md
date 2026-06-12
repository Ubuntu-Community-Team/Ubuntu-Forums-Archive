---
title: "Using WebcamStudio to broadcast on ustream?"
date: 2009-11-02
forum: Ubuntu Studio
---

### Post by Johndo1 on 2009-11-02
I found a tutorial here: [http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/]("http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/")

I think they have a different webcamstudio than me for the tutorial because I can't seem to find most of the "tabs" he is talking about. I have a logitech webcam (if that has anything to do with it), and this version of webcamstudio: WebcamStudio for GNU/Linux 0.51a (Build: 626).

Anyone have a different tutorial or wanna tell me how to get the video working on ustream?

---

### Post by Johndo1 on 2009-11-03
nobody?
(bump)

---

### Post by howefield on 2009-11-03
Why not try the homepage ?

[http://www.ws4gl.org/home](http://www.ws4gl.org/home)

Screenshots and video demos.

---

### Post by Johndo1 on 2009-11-03
I guess I never even thought of going to the website. Now I feel kind of silly anyways here's what I did. 

I went to: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager06.html)

Then I just selected always allow on anything that had to do with ustream and it worked.

Tyvm

---

### Post by cprofitt on 2010-02-03
I just found this gem of a program yesterday. It allowed me to broadcast to sites that previously just locked up on my camera -- and it also allowed me to do multiple cameras.

I will play with it more in the next few days, but it is worth a look for anyone trying to do advanced streaming from Linux.

---

### Post by grahams on 2010-03-11
How did you broadcast to ustream?

I've created a ustream.tv account, logged in. Allowed ustream.tv on the macromedia page and then open webcamstudio and I don't see how to select ustream. Anyone found a good (current) Howto on this?

thanks

---

### Post by afrodeity on 2010-06-24
Streaming to ustream with flash, but no audio stream. How to, please.

---

### Post by MezzFA0 on 2010-06-28
The audio stream is pretty simple if you're doing a basic setup.

All you need to do is set the default recording device in pulse audio and away you go.  Ustream picks up the audio as Linux Microphone.  A quick run down is if you click on the speaker and go to sound preferences then input, you select the connector from there.

I normally use pavucontrol in favour of the sound preferences but it should work all the same.

As for usb webcams with built in audio I don't really know.  First thing you'll need to check is that the audio line from your webcam is working in linux at all.  From memory a lot of the drivers for different webcams only deal with the video side of things.

If you're doing things slightly more complicated such as using a DV cam and taking the firewire feed from it, then you need a separate audio feed.  I simply connected the audio to line in although I guess you could use mic too, set the default recording device as above and happy streaming.

---

### Post by afrodeity on 2010-06-28
eventually figured out what i needed to do 

this link helped [http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/](http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/)
 
open pulseaudio applet and volume control

go to recording tab and there should be an alsa firefox plugin showing

click on the stream and change it to simulaneous mode as per the tutorial link

---

### Post by afrodeity on 2010-06-28
eventually figured out what i needed to do 

this link helped [http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/](http://ronnietucker.co.uk/blog/broadcasting-video-from-ubuntu-to-ustream-with-webcamstudio/)
 [LIST]
[*]open pulseaudio applet and volume control

[*]go to recording tab and there should be an alsa firefox plugin showing

[*]click on the stream and change it to simulaneous mode as per the tutorial link
[/LIST]

---

### Post by VcDeveloper on 2010-10-27
I just download the 0.56 version, build (890) and have no clue where to start.  Looks nothing like the above links and so far I can't find a tutorial on this version.  Should I uninstall it a go to the previous version or can anyone provide me a link for this version?

---

