---
title: "VSTi on Ubuntu. Anyone did it?"
date: 2008-08-29
forum: Ubuntu Studio
---

### Post by rafafredd on 2008-08-29
Hi. I love Ubuntu. I don't wanna go to 64studio. But I need to run VSTi's on Linux, and I would like to know if anyone has aver tried it on Ubuntu. There is a tutorial here for 64Studio users, and I though I might ask if anyone tried this tutorial on Ubuntu before I try it on my Ubuntu and crash my system forever. It was a hard, many days install, and configuration, and compiling many apps to get it going as good as it is now... so I would hate to have to do it all again.:(

BTW, I'm on Hardy, and I run Ardour VST with my RME cards, with 16/16 inputs and outputs. Works great, but No VSTi's, only VST efects on Ardour is possible.

So here is the 64studio tutorial:

[http://www.64studio.com/howto_vst](http://www.64studio.com/howto_vst)

Thanks for any inputs and advice.


Rafael

---

### Post by sonicb00m on 2008-08-29
I have run VSTi's using wine and the asio patch. It works ok but it's not great. Not all VSTi's work well and usually they have interface problems. The audio quality is good but you get latency problems and with some you get stuttering or incorrect playback or a non responsive UI.

Which ones are you using?

The biggest problem with audio on linux, for me, was that it's so cumbersome. Particularly wiring things into jack and synching apps together. I gave up in the end because it's a lot less productive than just using something like SX where everything works perfectly well.

Maybe one day linux will be great for audio but right now it's more tinkering and fixing than doing anything than productive, in my opinion.

Sorry, I just realised I haven't really answered your question.

I can't get jack to work properly on Ubuntu nevermind configuring anything like that.

---

### Post by thorgal on 2008-08-29
I don't agree with that. It's all about how confortable you are with a work flow that you build up yourself. Personally, after the initial building up and tweaking my linux DAW, it's only been about production, and I use VSTi's (for the OS, I use a customized debian sid, and my VSTi's are a drum sampler and a piano sound generator, which work both flawlessly thanks to the dssi-vst host or as a standalone exe app).
Of course, if I had the use of unstable VST's under linux, I would have a slightly different opinion, but this is not the case. I like the modular world of jack, I never used any other DAW environment so I am not only used to work with the jack env but also enjoy doing so. So YMMV :)

---

### Post by sonicb00m on 2008-08-30
> **thorgal said:**
> I don't agree with that. It's all about how confortable you are with a work flow that you build up yourself. Personally, after the initial building up and tweaking my linux DAW, it's only been about production, and I use VSTi's (for the OS, I use a customized debian sid, and my VSTi's are a drum sampler and a piano sound generator, which work both flawlessly thanks to the dssi-vst host or as a standalone exe app).
Of course, if I had the use of unstable VST's under linux, I would have a slightly different opinion, but this is not the case. I like the modular world of jack, I never used any other DAW environment so I am not only used to work with the jack env but also enjoy doing so. So YMMV :)

I'm glad you've got it working productively. 

I spent a couple of weeks trying to convert to Ubuntu studio. I found it cumbersome setting all the outputs on jack every time because it didn't save my mappings properly and I found it cumbersome syncing Rose Garden to perform midi playback in line with Ardour. It's also extremely old fashioned to have to record the output of Rose Garden into Ardour by playing back a project to capture it's output. Hydrogen really was no replacement for Battery either.

I managed to get a working set up that I might have been happy to work with but when I looked at how complex my project became and how tiresome it was to trouble shoot any problems with this setup I decided that it was kind of pointless.

I really think Ardour is a great program and has a very bright future as long as the developer makes enough in donations to keep plodding on with it.

What it really comes down to though is that Windows and Mac audio is far more advanced when it comes to software and vsti's etc that Linux is still a long long way behind.

I could probably happily use Ardour just to record multitrack and mix with the standard plugins though, in that respect it's pretty good. For now though, I use a dual boot system for any audio work I might want to do and use Linux for my desktop and server use.

---

### Post by thorgal on 2008-08-30
> **sonicb00m said:**
> I'm glad you've got it working productively. 

I spent a couple of weeks trying to convert to Ubuntu studio. I found it cumbersome setting all the outputs on jack every time because it didn't save my mappings properly and I found it cumbersome syncing Rose Garden to perform midi playback in line with Ardour. It's also extremely old fashioned to have to record the output of Rose Garden into Ardour by playing back a project to capture it's output. Hydrogen really was no replacement for Battery either.


that's not the way I use rosegarden, what I plugged to ardour's tracks is VSTi's outputs. I never use the audio output of rosegarden, I just use it for MIDI sequencing, nothing more. But when ardour has MIDI sequencing abilities as good as that of RG, I will certainly do everything in ardour. Of course, I can only use RG like that thanks to the dssi-vst host which transforms any VSTi into an independent jack client. And that's exactly how I want the VSTi's to behave. Indeed, some may be unstable and using them as an internal plugin in your multitrack software may crash the entire DAW. If the VSTi wants to die, so be it but let it do that alone :lol:

> **sonicb00m said:**
> 
I managed to get a working set up that I might have been happy to work with but when I looked at how complex my project became and how tiresome it was to trouble shoot any problems with this setup I decided that it was kind of pointless.

I am an "old" unix user and I didn't grow up with the monolithic paradigm of windows,, so for me, this modular approach, either in positive or negative contexts (such as crashes), is preferable.

> **sonicb00m said:**
> 
I really think Ardour is a great program and has a very bright future as long as the developer makes enough in donations to keep plodding on with it.

true enough. That's even harder for them than commercial proprietary development.

> **sonicb00m said:**
> 
What it really comes down to though is that Windows and Mac audio is far more advanced when it comes to software and vsti's etc that Linux is still a long long way behind.

I have to disagree. Why do you call it "far more advanced" ? this is a subjective perception due to your longer experience with one work "paradigm". This paradigm has been defined by commercial entities (MS, Apple, Steinberg, etc) and generations of musicians, sound engineers, etc, grew up within it. Changing paradigm is never easy due to that. As I said, I grew up with unix systems and I find the linux audio environment perfectly fine. But I must say, my DAW is very stable! I produce music, not fiddle around with system tweaking, etc, that part is done and I see no reason for me to change something that works. So again, it all comes down to how confortable you are with a work flow you define. In your case, you still have to find out a few things if you wish to use linux for your audio work. That could take you quite a while. Is it worth it ? It all depends on how and when you meet your expectations after the long learning of the linux audio world. If you are experienced and confortable with MS and Apple, I see no reason why you should switch to linux. As with many MS and Apple users, you might expect linux to be a "free version" of windows or OSX-Aqua. Maybe not you in particular but this happens more often than not, and the disappointment is almost certain. 

> **sonicb00m said:**
> 
I could probably happily use Ardour just to record multitrack and mix with the standard plugins though, in that respect it's pretty good. For now though, I use a dual boot system for any audio work I might want to do and use Linux for my desktop and server use.

perfectly fine. VST's and VSTi's work best on an OS that supports them natively. The fact that wine got that mature and other ppl implemented some interface to make them usable in linux is just amazing and I would like to express my gratitude to them since I could hardly work on the production of my current album without these 2 VSTi's I purchased a few months ago.

---

### Post by sonicb00m on 2008-08-30
> **thorgal said:**
> that's not the way I use rosegarden, what I plugged to ardour's tracks is VSTi's outputs. I never use the audio output of rosegarden, I just use it for MIDI sequencing, nothing more. 


I was more talking about the fact that you have to record the output of whatever you are sequencing in RG in real time. Fine if it's an external synth or something since but not so hot with internal instruments. I also dislike RG as a piece of software and don't like KDE either. But I know that's a personal choice.

> 
I am an "old" unix user and I didn't grow up with the monolithic paradigm of windows,, so for me, this modular approach, either in positive or negative contexts (such as crashes), is preferable.


Yeah I can see your point. I've been a proper linux user for about 2 years. I've been running my desktop exclusively through it and also set up all the company servers with debian. I am a comfortable Linux user and don't give up that easy :lolflag:

> 
I have to disagree. Why do you call it "far more advanced" ? this is a subjective perception due to your longer experience with one work "paradigm". 


Well you certainly have more choice of whats available with windows audio since so many companies produce plugins and what not. With Linux there are many many different ways to make your software work and many many different programs that don't always have a "fully finished" feel. It's a problem with the free software model in a way. It's a similar thing with the Desktop but there are so many great and fully working Linux programs now that you don't need the millions of shareware programs offered by windows.

Ardour is a great sequencer and connects to the audio system in a better way then ASIO or WMD did with Windows. But Ardour is still very embryonic in certain ways in comparison to the latest versions of Sonar and SX. Of course, they are very expensive to purchase and Ardour costs nothing. When it comes to effect plugins there is a much wider choice to contend with from windows. 

I don't mean "advanced" in a patronising sense. There's more choice, more availability, a robust and completeness that the free software just somewhat lags for me right now. Of course, those things come at a price and it's hard to fairly compare closed source paid for software with open sourced free software.

> 
perfectly fine. VST's and VSTi's work best on an OS that supports them natively. The fact that wine got that mature and other ppl implemented some interface to make them usable in linux is just amazing and I would like to express my gratitude to them since I could hardly work on the production of my current album without these 2 VSTi's I purchased a few months ago.

Yes , it's incredible that it does what it does and i also appreciate and use it.

I will probably give it all another go when I only want to record my acoustic tracks again and don't need the same setup as I had in SX to record more complex projects.

IT's a shame ardour isnt available for the windows platform to help ease into an entirely different way of working.

---

### Post by Lou_Cypher on 2008-08-31
Rafael,

Take a look at this thread on the forum: 

[How To: Install VST support (fst) in UbuntuStudio (also applicable to other Ubuntus)]("http://ubuntuforums.org/showthread.php?t=557466")

as well as the [FST VST page]("http://www.joebutton.co.uk/fst/").

Regards,

LouC.

---

### Post by eric71 on 2008-09-02
I've had some success with dssi-vst and Rosegarden. A few weird crashes and the interfaces and presets don't always work right.

I have had the most success using Reaper via Wine with wineasio. A fraction heavier on system resources than under Windows, but basically works great. Reaper's developer pays attention to how the program runs under Wine. In a sense, you are running the vsti in a native windows situation, letting Reaper do all the work and Wine only has to deal with Reaper.

I guess it all depends on if Reaper fits your work flow.

---

### Post by thorgal on 2008-09-02
if one wants a windows VST host running under wine, savihost.exe may be lighter than reaper. It also relies on wineasio, which I am not very fond of but I can try it with wine 1.1, see if it behaves OK. 

My setup dssi-vst and rosegarden is very stable. I don't use rosegarden for audio at all. All i want is its MIDI sequencing and easy tempo changing / ramping (really friendly). I use the ability of dssi-vst to interface with the VST's IOs. By the way, the lastest dssi-vst also provides a LADSPA descriptor so any host that can use ladspa can now enjoy VSTs through dssi-vst.

---

### Post by ZippiDi on 2011-01-01
watch this: [http://www.youtube.com/watch?v=aB1Dspd8o6Q](http://www.youtube.com/watch?v=aB1Dspd8o6Q)
and this: [http://www.facebook.com/photo.php?pid=5569010&l=fde4492004&id=537494393](http://www.facebook.com/photo.php?pid=5569010&l=fde4492004&id=537494393)
and this: [http://www.facebook.com/album.php?aid=72452&id=537494393&l=72f0ee0c74](http://www.facebook.com/album.php?aid=72452&id=537494393&l=72f0ee0c74)

---

