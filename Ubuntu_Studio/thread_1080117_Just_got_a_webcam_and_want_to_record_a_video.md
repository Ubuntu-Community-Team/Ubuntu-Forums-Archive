---
title: "Just got a webcam and want to record a video"
date: 2009-02-25
forum: Ubuntu Studio
---

### Post by brnetonboy on 2009-02-25
However, I'm totally confused about where to start. I've installed kino, cinelerra, camera monitor, but can't figure out how to record. Ekiga turns on my webcam and shows what the cam is taking, but doesn't record. I read that VLC or MPlayer can record, but I went into "open capture device" and clicked play but nothing happened...

What software do I need to download in order to record from my webcam to Ubuntu (8.10)?

Thanks!

---

### Post by Teamgeist on 2009-02-25
Hi.
You could try cheese.

```
Sudo apt-get install cheese
``` or via Synaptic.

Website: [http://projects.gnome.org/cheese/tour](http://projects.gnome.org/cheese/tour)

---

### Post by brnetonboy on 2009-02-25
Wow... amazing that after hours of google searches and hacking I didn't find this. It does just what I want. I've got a problem with it taking up 100% of my processor and grinding everything to a hault, but this is definitely the program I want. Is there a program that will integrate the audio with it as well?

---

### Post by patchin_house on 2009-03-01
Yow! I had wondered about finding a program to record webcam commentary with on my penguins, and lo and behold...

Maybe my HP desktop unit will be able to work with it. Sweet.

Philip David
2009.03.01

---

### Post by kd8cgo on 2009-03-01
I've been looking into something to do this as well, in order to post quick youtube videos and the like.  Unfortunately, cheese does not seem to have an option to record audio with the video.  I have installed kino and cinelerra as well, and those seem ok for editing work and I got a capture from my DV camera with sound on ubuntu, but I had to run kino as root in order for it to work properly.  

I suppose I could use something like sound recorder and cheese together, and then mux the two in cinelerra, I haven't tried that yet, but at that point it sortof defeats the purpose of making a "quick" video for youtube.  I tried capture with mencoder to get audio and video and got frustrated with that after about a day - then I tried VLC which got some video and audio, but its encoding codecs seem to cause me some problems.

I wonder, brnetonboy, do you need audio with your videos as well?

---

### Post by Samhain13 on 2009-03-02
^ Try VLC. Open "Video4Linux", tick "Stream/Save" and go to "Settings". From there, you'd want to tick "File" (provide a filename), and choose your codecs and container. :)

---

### Post by regebro on 2009-04-23
Cheese records in a format Kino doesn't understand. Converting it with mencoder and then import into Kino makes the audio completely out of sync. Recording with VLC will ignore all sound. Importing the resulting file in Kino will make everything run rellyreallysuperfast so the whole recorded video is over in a 10th of a second.

I've tried every tool I can find that claims to grab video and none of them work, it seems. So I'm at a loss here. Possibly it's Kino that's complete crap at importing, should I use something else for editing? Or is there a grabber that can actually grab from my webcam and create something that Kino can import?

---

### Post by Detonate on 2009-04-23
I don't know what camera you have, but if it is one that uses the uvcvideo driver, then this program is absolutley the best I have found for use with my camera, A Logitech Pro9000.

[http://guvcview.berlios.de/](http://guvcview.berlios.de/)

---

