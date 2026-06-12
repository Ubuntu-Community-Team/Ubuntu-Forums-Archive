---
title: "New in town: questions and doubts"
date: 2016-01-18
forum: Ubuntu Studio
---

### Post by marcelo20 on 2016-01-18
Hi all, I am doing an effort here to change from Mac OS to Ubuntu. I have downloaded Ubuntu Studio and installed it in VitualBox in a MacBook Pro to try it before changing, but have been having problems to connect Jack audio to the computer dac: it fails to connect all the time. Can anyone teach me how to do it? I've read a lot of forums tips, codes suggestions, but none of them worked. 
Second I really would love to know someone who is working with Ubuntu for professional music production, or sound design, sound art, or for electronic/electroacoustic music composition, video art and competing with all kind of professional audio production on the market. Also universities and companies using Ubuntu as the main professional OS to teach, research and create audio projects.
So, if you could help me with these problems/questions, I would be very greatful.
thanks a lot.

---

### Post by marseille2 on 2016-01-18
Hi Marcelo. Since VB does not offer stellar performance or reliability when it comes to pro-audio or 3D graphics, I would take it out of the equation and boot from a live CD or USB to see if Jackd is OK (or not). Also check out [Mactel's community documentation]("https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages"), and the [Apple Hardware User]("http://ubuntuforums.org/forumdisplay.php?f=328") and Virtualization forums.

As for creativity ... check out [LinuxMusicians]("https://linuxmusicians.com").

---

### Post by CrocoDuck on 2016-01-20
Hey there! I Agree with marseille2 about Virtual Box, you are better try a live image. About Linux artists: there are many. Here you can find some:

[Libre Music Production Musicians page]("http://libremusicproduction.com/music")
[This list]("http://audio-and-linux.blogspot.co.uk/2013/02/music-made-with-linux.html#comment-form")
[LMMS showcase]("https://lmms.io/showcase/") (not sure these are all made on Linux though)

If you have Facebook search for LinuxMusicians, Linux Audio Development for the Recording Musicians, Linux Audio groups. Sometimes people post tracks in there.

> **marcelo20 said:**
> ...Also universities and companies using Ubuntu as the main professional OS to teach, research and create audio projects...

Sorry, I was at work and I did not see this bit.

Many recording studios use Linux, but they are usually own by small indie companies. Can't really recall them now, sorry.

Many universities use Linux as a main OS, but usually for technical courses. I studied Physics and Acoustics and in both cases most of the universities computers where equipped both with windows and Linux, Linux used mainly for teaching programming or technical computing. However, as long as audio engineering is concerned, pretty much all the computers in the uni recording studios were Macs. Macs do not really offer any technical advantage/disadvantage really. I think the only limit they have is the combination of vendor lock-in and release cycle, that cutoff for commercial reasons tons of otherwise usable software from the up to date OS releases. However, they have a significant advantage: they have become (for some reason I don't know) the standard of audio industry. I guess Pro Tools is what we have to point the finger at for that. Of course, sticking to the standard of industry increases a lot the chances you have to be able to work with partners, as you likely use the same formats. That is pretty much all, technically any modern OS is good for audio (a similar topic was discussed [here]("https://linuxmusicians.com/viewtopic.php?f=4&t=15078")) and what that really matters is how well the software a particular OS can run fits your workflow.

However, you will find that while Macs are ready to go, Linux needs a lot of user action to be optimized for audio. Also, Linux tends to be modular: you unleash the full potentiality of Linux by using simultaneously different applications communicating on the same API, while on Mac you are used to much more centralized pieces of software that have all the functionalities you need. That is why I think that the learning curve for audio stuff on Linux is pretty slow. Run some live distro, make experiments, have fun! By doing so you will see if Linux software is really what you need for your audio stuff!

By the way, [this guy]("http://onyx-ashanti.com/") was used to run on a customized Gentoo Linux. Not sure what he uses now though.

---

### Post by marcelo20 on 2016-01-21
Hi. I want to thank you all for your replies: they were all very useful and enlightening. I will test Ubuntu Studio booting it from a usb and check if I can handle the OS properly. I am pretty sure I will have a lot of work to do to learn the System, but I will try to have fun with it. Bests to you all.

---

### Post by Sakrecoer on 2016-01-25
> **marcelo20 said:**
> Hi all, I am doing an effort here to change from Mac OS to Ubuntu. I have downloaded Ubuntu Studio and installed it in VitualBox in a MacBook Pro to try it before changing, but have been having problems to connect Jack audio to the computer dac: it fails to connect all the time. Can anyone teach me how to do it? I've read a lot of forums tips, codes suggestions, but none of them worked. 

Like suggested, running ubuntustudio virtually may cause problems with audio-interface connections. I'd try a dualboot or boot the liveUSB, but i havn't stepped foot in Apple realm for a long time. Make sure your audio-interface is supported, search the web for *<Insert_your_audiointeface_model> AND ubuntu* OR *linux*

> Second I really would love to know someone who is working with Ubuntu for professional music production, or sound design, sound art, or for electronic/electroacoustic music composition, video art and competing with all kind of professional audio production on the market. Also universities and companies using Ubuntu as the main professional OS to teach, research and create audio projects.
So, if you could help me with these problems/questions, I would be very greatful.
thanks a lot.

I saw some casual screens featured in a show about the prison system in the US that has a program to teach inmates to code, and it was an ubuntu desktop.
In swedish university in Uppsala, you are encouraged to familiarize yourself with GNU/linux, but i don't believe it is mandatory. 

I could also take the opportunity to lobby for myself; mini-moi Sakrecoer. 
I produced this animation entirely with ubuntustudio : [https://vimeo.com/83261266](https://vimeo.com/83261266) (music by /franky fresco/ tho)
I operate this Music Syndicate: [http://basspistol.com](http://basspistol.com)
I make this music: [http://sakrecoer.com/music](http://sakrecoer.com/music)

I know, the production is not perfect. But really, the weakest link in my production is **not ubuntustudio**, it is *me.* ):P 

I believe, the main thing that keeps a modern Multimedia Production Studio as well as schools from migrating towards open tools, is the time required to readjust to the new workflows, teach a teacher to teach somethingnew# can be hard, teach MANY teachers to teach somethingnew# is a cultural change :D  But really, Blender has little to nothing to envy from suits of the likes of: After effects, cinema 4d, zbrush and finalcut. Jack really is a bad ass mega rack to connect a big chunk of big bunch of killa synthesizers, sequencers and recorders. GIMP; Inkscape and Scribus is perfect for print! And you can sync it all with your ubuntu-server pimpampom! It's a matter of getting comfortable with it. :D

---

### Post by yoshii on 2016-01-27
I'm not musically employed, but I am an electronic music composer.  
Here's my music:  [https://soundcloud.com/nystagmuse](https://soundcloud.com/nystagmuse)

My OS is Ubuntu Studio, but I actually use 32-bit Reaper (for Windows) in Wine.  Similarly, I use the Windows version of EnergyXT (free beta 3) and the 32-bit version of FL Studio for some things too.  Of the three, Reaper seems the most reliable, but I like the MIDI editing and input quantizing in EnergyXT better.  FL Studio doesn't seem to use all my computer's CPU cores which is unfortunate.  

Gradually I will learn how to use the native Ubuntu Studio music programs.  But right now I have access to most of my VST instruments and effects with the programs mentioned above.  I use Toxic Biohazard, Harmor, Poise, and Surge; also I use a bunch of freeware plugins.  

I've been on Ubuntu Studio for a little over a year now.

---

### Post by marcelo20 on 2016-03-06
Hi Sakrecoer, thanks. I've been experimenting with a lot of stuff with Ubuntu Studio this last month. I was desapointed about the lack of multichannel audio interfaces for Linux. I am trying to figure out what to do. As a electroacoustic music composer, those multichannel sound cards are essential. I am also learning Ardour and getting used with the system. I am enjoying despite the sound card problem. Thanks for your tips and message. Cheers.

---

### Post by marcelo20 on 2016-03-06
Hi yoshi, thanks. I did not understand: you use Ubuntu as OS but run Windows software? I don't know how to do that. I know Reaper well: it has been being my major DAW for years now. The problem is that Reaper does not work on Linux, and I am trying to get familiarized with Ubuntu Studio environment. Thanks for your link, and for the tips. Cheers

---

### Post by marcelo20 on 2016-03-06
Nice video, by the way. Congratulations. Can you tell me what was the hardware configuration you used to create it? Thanks

---

