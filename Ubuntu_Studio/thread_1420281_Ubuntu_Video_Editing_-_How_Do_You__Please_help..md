---
title: "Ubuntu Video Editing - How Do You ??? Please help."
date: 2010-03-02
forum: Ubuntu Studio
---

### Post by LuridCinema on 2010-03-02
Hey linuxxxx lovers ! I have a question and a challenge for some. Please PM or post here if you have had luck w/ video editing and FX in Ubuntu. im looking for successes in video production like Shooting Day for Night, Gun Flashes, Creepy visual FX. Compositing, Masking. Chroma-Key, any how-tos you can share.. Any creative and entertaining FX would be greatly appreciated. If you can use a desktop recorder and audio or a text file to explain what you are doing, then please share. 

Im doing a website for FOSS video production. Your efforts will be credited and all due recognition will be given on [http://indiebudgetmoviemaker.com](http://indiebudgetmoviemaker.com) my website will be devoted to making low-budget movie making and showing how-tos to and share our learning to produce videos using Ubuntu & FOSS

thank you and I hope Im not deleted for spam
Eugene

---

### Post by Linuxforall on 2010-03-02
[http://www.openshotvideo.com/](http://www.openshotvideo.com/)

Please take a look here, there are many other choices but this one is new and does close to Adobe Premiere.

---

### Post by delectate on 2010-03-02
sorry, english is very pooooor

maybe you want a video editor?

i tried before,but it seems too hard to me work on linux only platform

on windows,i use avisynth ,aviutl and adobe after effort

on linux,i use LiVES,avidemux,pitivi

i hope this can help you

---

### Post by lyall on 2010-03-02
have you looked at **Ubuntu Studio**
it is for Art, Graphic and Video
it is like Studio64

you might like what you see a lot of programs for Graphics and Video making

good luck and have fun learning

---

### Post by SoFl W on 2010-03-02
Check out this thread:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by delectate on 2010-03-02
good idea

---

### Post by LuridCinema on 2010-03-03
Hello thanks everyone... Im lookin for people to share how-tos  not the software.
thanxx again
Eugene

---

### Post by Keyper7 on 2010-03-03
> **LuridCinema said:**
> Hello thanks everyone... Im lookin for people to share how-tos  not the software.
thanxx again
Eugene

The OpenShot editor has a nice manual that explain in details several common tasks in video editing.

[http://www.openshotusers.com/](http://www.openshotusers.com/)

---

### Post by Astreja on 2010-03-06
> **Linuxforall said:**
> [http://www.openshotvideo.com/](http://www.openshotvideo.com/)

Please take a look here, there are many other choices but this one is new and does close to Adobe Premiere.Thanks for the link!

I've been intermittently fighting with Linux-based video editing for a little while now (tried Cinelerra, Kino and a command-line capture tool on Fedora) and have several projects on the back burner because I just didn't feel like fighting with software.

I'm currently running Ubuntu Studio 9.10 and have successfully installed OpenShot on my system.  Now I'm off to see what it can do with my DV files... Wish me luck. :D

---

### Post by mango42 on 2010-03-06
Some good plugs for OpenShot here but all I get is a funky window showing fuzz and sounding just like a TV with its aerial unplugged.

Gave up & went back to Kino - life is too short to spend it debugging every new offering... ;-)

To the OP; we'll all get to share experiences once we can run the programs successfully, I guess...?

---

### Post by wkulecz on 2010-03-09
If you actually intend to finish an "indie" video production, bite the bullet and build a Windows 7 quad core box with as much RAM as you can afford and buy Sony Vegas Video Pro 9.  If you shop carefully you can come in for about $1000-1200 total hardware and software with software being about half the total.

Linux video software just ain't there yet and your hardware costs will be the same. 

You can skimp on the video card, my system is in the 7s on the Win7 performance score for CPU, RAM, but the low 5s for the video (Nvidia 9400, $70 card).

Having three hard drives helps -- system, source, previews/outputs.  An external hard drive for backups is necessary if you are serious about your work!

---

### Post by LuridCinema on 2010-03-09
To each his own. I too was on the Dark Side.. I paid for Sony Vegas, XP operating system. I have created, FINISHED and am now selling my own Indie Feature movie on Amazon.  I do know what it takes to produce a marketable product. I am now 100% linux and I see NOTHING keeping me from making another project and using 100% Ubuntu to do it. 

 Cinelerra, Cinepaint, Gimp, Synfig, Audacity and ffmpeg will be my complete video production software. My work will only be limited by my creativity and my time available. I have EVERYTHING I need to make another movie w/ Ubuntu & FOSS for production. I have plenty of software tools and will not lack in any way to be able to make my projects come to fruition.

---

### Post by b1lancer on 2010-03-09
OpenShot seems the best for us who just want an alternative to Win Movie Maker. 

It is my understanding that ubunto studio includes software that already came with the ubuntu distro. does that mean it wont install that stuff (such as gimp) or will it override it? how does that work?

---

### Post by stuartcnz on 2010-06-03
Might I suggest Ardour for audio? No point limiting Audio post production with audacity when the cost is the same.

---

### Post by BobLand on 2010-06-03
I think Cinelerra will give you the best bang for the buck.  Unfortunately, I can't get it to read the mov files created by my T2i.  It will read the video but just can't get it to read audio.  For that reason, I went back to Kdenlive.  I've found the others are not very useful for creative editing.

---

### Post by zettberlin on 2010-06-03
> **LuridCinema said:**
> 

 Cinelerra, Cinepaint, Gimp, Synfig, Audacity


If really release yourself from the dark side you want in terms of audio, mastering ardour you must.

;-)

I really absolutely recommend this kind of workflow: 

1.) shoot material as good and cool as possible.
2.) If you need to apply chroma-key compositing, have a look at open shot. If it must be pro-grade CGI, dig into blender. If you just need  effects to spice up your clips and for basic stuff like color-correction, get your clips into open movie editor.
3.) Start jack and then Open movie editor 
4.) Import the preproduced material in OME, edit it, until the movie itself is just right and then export the audiotrack from OME.
5.) Start Ardour, make a new project, change timing-source from "internal" to "jack", import the exported basic-soundtrack into one stereo-track in Ardour.
6.) record, import, arrange and edit audio-overdubs at will. Use realtime plugins and automation unparallelled under Linux. OMEs playhead will follow Ardours playhead faithfully synched via jack transport and vice-versa - Ardour will obey to OMEs playhead. 
**Save often, save early!!**
If OME crashes, nevermind -  just restart it, it has near-perfectly working desaster-recovery so has ardour(yet ardours is not that perfect but ardour crashes much less often....).
7.) Once everybody is happy with the soundtrack, export it from Ardour as a 48KHz-Stereo-WAV. You can also mix and export BCWave-Files with more then 2 channels from Ardour but you need to find a way to mux those to the movie - I do not know a way... Maybe Avidemux can do that.
8.) A stereo-file you can simply import to OME and finish the whole procedure by:
8.1.) mute all audio in OME expect the stereo-track imported from Ardour
8.2.) export the movie to any format you find appropriate.

I explored this way in many tests for magazine-articles and video-projects. It just works. 
I doubt, that this toolchain would be good enough for commercial Movie-production but if some punk-appeal can be tolerated you can get great results making cool underground-movies that way.

---

