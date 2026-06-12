---
title: "Problem recording Flash Player with Audacity"
date: 2010-11-21
forum: Ubuntu Studio
---

### Post by windeguy on 2010-11-21
I had a project where I wanted to record a stream from the Flash Player using Audacity and convert it to MP3. However, when I launch Audacity, it does not show up in JACK connections nor does it show up in Patchage.  So I cannot connect to it from the Flash Player. I tried all of the available input settings on Audacity but none were recording the Flash Player. 

Instead I used Ardour and was able to record a stereo stream in Ardour from the Flash Player. But then I exported to .wav,  imported to Audacity and converted to MP3.  It would be much simpler if I could just use Audacity to record directly from the Flash Player.  

I found a solution here:

[http://wiki.audacityteam.org/wiki/Recording_audio_playing_on_the_computer](http://wiki.audacityteam.org/wiki/Recording_audio_playing_on_the_computer)

I had to select Jack Audio Connection Kit for the Host and then select "flash" under Preferences in Audacity as the recording device so I can record the Flash Player stream. 

I am still curious as to why Audacity does not show up in Patchage? Is that a bug or a feature?

---

### Post by cchhrriiss121212 on 2010-11-21
No need to use jack or Audacity for this, Avidemux can handle it in one step:
[http://techblissonline.com/rip-audio-from-video/](http://techblissonline.com/rip-audio-from-video/)

Just tested this myself and only takes a few seconds. the only thing is that you must save your audio file with the .mp3 extension, it will not be added automatically for some reason.

---

### Post by windeguy on 2010-11-21
> **cchhrriiss121212 said:**
> No need to use jack or Audacity for this, Avidemux can handle it in one step:
[http://techblissonline.com/rip-audio-from-video/](http://techblissonline.com/rip-audio-from-video/)

Just tested this myself and only takes a few seconds. the only thing is that you must save your audio file with the .mp3 extension, it will not be added automatically for some reason.

Thank you.  I will look into that solution, although I did find the way to use Audacity as well and edited my original post to show how I did it.

---

### Post by cchhrriiss121212 on 2010-11-21
I think the newer versions of Audacity do not work with jack. It has never worked well with jack in the past anyway.

---

### Post by windeguy on 2010-11-21
> **cchhrriiss121212 said:**
> No need to use jack or Audacity for this, Avidemux can handle it in one step:
[http://techblissonline.com/rip-audio-from-video/](http://techblissonline.com/rip-audio-from-video/)

Just tested this myself and only takes a few seconds. the only thing is that you must save your audio file with the .mp3 extension, it will not be added automatically for some reason.

I installed Avidemux. How do you feed the Flash Stream from YouTube into it in real time and convert it to mp3?

I see how you can do it with videos already stored to disk, but that is not what I was looking for.

---

### Post by cchhrriiss121212 on 2010-11-21
You can check the directory where temporary files are stored. If using firefox, type in about:cache into the address bar to see where they are stored. Mine for example:
> **Disk cache device**

 
   **Number of entries:** 1967    **Maximum storage size:** 512000 KiB    **Storage in use:** 94069 KiB    **Cache Directory:**  /home/chris/.mozilla/firefox/rpn584e3.default/Cache

---

### Post by windeguy on 2010-11-21
> **cchhrriiss121212 said:**
> I think the newer versions of Audacity do not work with jack. It has never worked well with jack in the past anyway.

I just used this version selecting JACK so that I could record the streaming flash audio. 

Audacity ® 1.3.12-beta (Unicode)

As for using Avidemux, I can't find a way to use that to process streaming audio from YouTube.

---

### Post by windeguy on 2010-11-21
> **cchhrriiss121212 said:**
> You can check the directory where temporary files are stored. If using firefox, type in about:cache into the address bar to see where they are stored. Mine for example:

OK. Thanks, so Avidemux does require the files to be on disk. I thought I was missing something. 

I also found this method using an on-line service

[http://techblissonline.com/capture-or-download-audio-from-streaming-youtube-video/](http://techblissonline.com/capture-or-download-audio-from-streaming-youtube-video/)

tube2tone.com

It is always good to have options.

---

### Post by 12apennachi on 2010-11-21
youtube-dl is a terminal based program and it worked really well, and fast. I highly recommend it. It is in the repositories.

sudo apt-get install youtube-dl

---

### Post by windeguy on 2010-11-21
[http://forum.audacityteam.org/viewtopic.php?f=18&t=4174](http://forum.audacityteam.org/viewtopic.php?f=18&t=4174)

It turns out that JACK support with Audacity comes and goes with versions. 

The link shows a workaround.  When you hit record in Audacity, a PortAudio block shows up in Patchage and then you can connect to it if JACK isn't supported in the version you have installed.

---

### Post by Pablo_F on 2010-11-21
Hi, I strongly recommend a much simpler solution. 

You only have to do in a terminal:

jack_capture -mp3 

or, if you want to specify the audio file name:

jack_capture -mp3 audiofilename.mp3

And press play in the youtube video. 

You don't have to make jack connections because jack-capture autoconnects to its capture ports every port that is connected to the system: playbacks, so you record literally what you are hearing. Neither have you to use audacity or any other program to encode to mp3 later.

You can make a launcher and you are done with a click or you can also can use its front-end, called jack_capture_gui2 (included in jack_capture).

jack_capture is not by the time being in the official repos though, but it should be easy to install it through a ppa or by compiling the sources.

Cheers! Pablo

---

### Post by windeguy on 2010-11-21
Thanks again Pablo and all the rest for helping.

Jack-capture was in the repositories I already had set up, so I will give it a try.

---

