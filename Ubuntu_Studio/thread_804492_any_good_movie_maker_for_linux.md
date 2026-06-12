---
title: "any good movie maker for linux?"
date: 2008-05-23
forum: Ubuntu Studio
---

### Post by StOoZ on 2008-05-23
im looking for an easy to use basic movie maker (like the one in windows,its just perfect for me) for linux, is there anything like that?

---

### Post by luisromangz on 2008-05-23
You might like kdenlive.

---

### Post by aeiah on 2008-05-23
there are loads of options really. i assume you mean one similar to windows movie maker? perhaps mandvd. there's also avidemux, although that is more like a feature filled virtualdub that windows movie maker. there are more advanced ones too

---

### Post by dnns123 on 2008-05-23
cinerella

---

### Post by Malcy on 2008-05-23
Kdenlive is great with one big exception. It is crash happy. :(

---

### Post by pietjanjaap on 2008-05-23
[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.openinhoud.nl/zoeken](http://www.openinhoud.nl/zoeken)
[http://www.osalt.com/](http://www.osalt.com/)
[http://linuxappfinder.com/alternatives?page=1](http://linuxappfinder.com/alternatives?page=1)

---

### Post by -Curtains- on 2008-05-23
Kino's the way to go for a WMM experience.

Cinelerra is pretty good too if you want something a little more advanced. It's essentially the closest youre going to get open source wise to Final Cut or Premiere.

---

### Post by cotcot on 2008-05-24
Cinelerra is good and professional level; but for what you ask it is overshooting. If you ask some basic features it is not worth to spend the (lot of) time you need to get away with cinelerra. Nevertheless keep an eye on it. A new developer team is working on somekind of a cinelerra 3.0 version.

Kino is rock solid and easy to use. (only single track unfortunately). 
Kdenlive is user friendly as well. A little bit unstable but not that much that you cannot use it. I used it without problems.

My advice is the latest version of Blender VSE (Video Sequence Editor).

---

### Post by Creative2 on 2008-05-25
i agree with  cotcot 
blender rocks if you have problem with audio type this on console 

export SDL_AUDIODRIVER=alsa && blender -g noaudio
and click on audio button as you can see in the last picture

[IMG]http://b.imagehost.org/0260/blendermovieeditor.jpg[/IMG]

[IMG]http://b.imagehost.org/0739/blendermovieeditors1.jpg[/IMG]

---

### Post by ubundah001g on 2008-05-28
[http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/](http://ubuntulinuxhelp.com/top-100-of-the-best-useful-opensource-applications/)

This site has a ton of links for you to take a look at on applications that you can use not just for video, but audio, etc. I am trying Cinelerra. It installed okay, by following the Cinelerra Community Center instructions to add the repository "http://repository.akirad.net/ akirad-hardy main". It only runs as root afterwards though, on Ubuntu Studio 8.04 amd64 install.

I think you might like Lives. [http://lives.sourceforge.net/](http://lives.sourceforge.net/)

---

### Post by mike003 on 2009-05-20
Hello, I have been with Ubunu for about 5 months now and I need to creat a movie with pictures and put music into the background. I used Windows Movie Maker when i was with xp and vista but now I need somthing new for Ubuntu. Please Help!
:popcorn:

---

### Post by Malcy on 2009-05-21
The latest version of Kdenlive (0.7.3) is very stable, easy to use and will do all that you want. It's in the repositories, give it a go. :)

---

### Post by karimruan on 2009-10-17
I could never get lives to compile. Is there a deb floating around somewhere. I have used Kino (very little) and it doesn't seem to hard, once you get used to the interface, which again, isn't that hard to do. I am download kdenlive now to test it out!

---

### Post by ArielEnter on 2009-12-09
Hi. A few days ago I was looking for a good replacement for that video creator included with windows. I wanted to create a photo presentation like I do it in that software.

I found Kdenlive, and I think is the best choice between all the other options I tried because of it similarities with Movie Make to establish the the default duration of Still Pictures.

In MM you go to tool>options and to the Advance Tab. Then you just change the value in Picture Duration. Very similar, in Kdenlive you go to Settings>Configure Kdenlive and you change the field that says: “Default duration, image clips”. You do the exact same thing for transitions in both programs.

You import pictures, videos and sound the same way you do it in MM.

Another great similarity between them is their time line. Kdenlive doesn't have a Story Board, but its time line looks very similar to MM´s.

Kdenlive doesn't have a Auto Movie yet, but I´m sure they are going to implement it soon. Until then you could use this script [http://www.kdenlive.org/forum/photo-slider-random-effects-script](http://www.kdenlive.org/forum/photo-slider-random-effects-script). It needs to be change a little by replacing “prm” with “prm.png” in the code to work with the current version (0.7.6), but it works.

Kdenlive 0.7.5 available at Ubuntu's repositories is an OLD RELEASE, NOT SUPPORTED ANY MORE!
To installed the newest release you will have to do the following:
   1. go to System Menu > Software Sources > Third-Party Software;
   2. click add and paste this line in:
      ppa:sunab/ppa
   3. close software source and click reload.
   4. Find and install Kdenlive newest version.

If you got problems with the way the program is display, you may be having the same problem I got in this thread:
[http://ubuntuforums.org/showthread.php?t=1343142](http://ubuntuforums.org/showthread.php?t=1343142) it´s easy to solve.

You can mimic many MM's title and credit functions with the use of a text slide and a picture to picture transition. Even MM's “moving title”. An example of picture to picture transition can be found in the following video: [http://www.kdenlive.org/tutorial/kdenlive-animate-images-over-video](http://www.kdenlive.org/tutorial/kdenlive-animate-images-over-video)
Many other tutorials are found here as well:
[http://www.kdenlive.org/tutorial](http://www.kdenlive.org/tutorial)

I´ll make a template of a “moving title” in kdenlive very soon.

You will find that at the end, Kdenlive lets you do a lot more things than MM.

---

