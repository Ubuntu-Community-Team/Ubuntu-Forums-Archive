---
title: "Helping a friend to make music..."
date: 2011-04-16
forum: The Cafe
---

### Post by Jay Car on 2011-04-16
I am putting this in the Cafe because it's not (strictly speaking) a support or help request on any specific technical issue, and it doesn't yet qualify as an experience or testimonial (maybe later). 

What I am hoping for are some personal experiences, and perhaps a little guidance, from other UF folks who are (or who work with) musicians.

**So, here's the situation...**
Next week I will be setting up a new desktop system for a (very dear) friend. He has been a professional drummer for the last 3 decades, but has suffered two strokes in the last two years, the first stroke was minor, but the second was seriously debilitating. His right side was paralyzed for a while, though he never lost speaking or singing ability, his coordination and balance were badly damaged. He can no longer play drums.  

However, he has begun playing guitar again and writing songs (and singing them!). It's been excellent therapy, both physically and emotionally, and resoundingly approved by his doctors and physical therapists. He's also becoming more interested in recording his music on his own computer and asked me to help. 

There's no way I'd say no. :) But I AM a little worried that I'm not experienced with the kind of software he'll need.

His current computer is quite old and low in resources. It does run XP sufficiently for everyday tasks, but is mind-numbingly slow with resource-hungry apps. So the decision was made to get parts for a new desktop. Which is where I come in, because he also wants Ubuntu on the new computer. 

Now, I've been happily successful with helping friends and family migrate away from Windows over the years, but the main reason has been that I make sure they are well prepared for the change, and I keep things very simple. 

This is also the case with my friend. He is already using Audacity, and Open Office, Gimp, etc., so he can use those on Ubuntu too. He has also used my computers many times, so he understands most of what will change and he already likes Ubuntu a lot. 

**This time it's ME that's not prepared...** 
The software he needs for recording and editing his music seems very complex to me. Unlike the simpler setups I've done before, I'll soon be installing software I've never used myself.  

I'm a bit nervous about it all, which is basically why I'm here...trying to prepare and think this task through.

I was looking over the [software included in Ubuntu Studio]("https://wiki.ubuntu.com/UbuntuStudio/PackageList"), but installing the full Ubuntu Studio seems like overkill for this situation. My plan is to just install Lucid, then add the same audio packages that are listed in Ubuntu Studio, leaving out all the video and graphics apps (except Gimp for basic image editing). 

But, to be honest, that audio-package list looks rather intimidating.   

**About the hardware...**
Because my friend is now on a fixed income, he couldn't afford a high-end machine, but I didn't think that would be a huge issue since the new one is still far, FAR better than what he currently has.  

He chose to buy an inexpensive, bare-bones bundle, which is now put together (mostly). No software has been installed yet, because I ordered a better power supply than what came with it. The new PS should be here by Tuesday. 

The Bare-bones bundle included a Biostar mainboard (N68S+), on-board Nvidia graphics (GeForce 7025) and on-board sound (it's described on the Biostar box as: 6-channel HD audio), 2GB ram, an AMD Phenom II x4 processor.

Hopefully he can get a better sound card soon, but for now the on-board sound will have to do. He already has a good set of speakers, as well as an "H1 Zoom" digital recorder which can connect to a computer via USB.

I'm not anticipating any hardware issues with Ubuntu, but the sound card worries me a little, in regards to recording and such. 

So, at this point I'd be happy to hear what others have learned regarding setting up a simple home recording studio on Ubuntu. I know there are many musicians here, and hope some might point out any difficulties we might encounter, or things (hardware or software) that might still be needed, that we haven't thought of yet. 

My friend doesn't need everything to be perfect, but just wants a setup to learn with. He isn't afraid of trying new things or learning new apps, but since the last stroke he has to work a little harder at everything. I'd like to help him get a good start with this computer, without causing him unnecessary frustrations.

And that's it. Any feedback, inspiration, encouragement, ideas, personal experiences, funny stories, I'd truly like to hear them all (and warm 'thank yous' and appreciation to all who respond).

**One last thing...**
I'm hoping this thread will be a good place to introduce him to Ubuntu Forums. He seems to think forums (in general) are unfriendly places and he didn't seem interested in visiting here at all. But I think he'd fit right in, if I can just get him here. 

**Okay, I'll shut up now... :)**

---

### Post by Frogs Hair on 2011-04-16
This is in the repository and is also included with Ubuntu Studio. [http://ardour.org/](http://ardour.org/)

---

### Post by Frogs Hair on 2011-04-16
I don't know if a former drummer would want to use , but it is also in the software center. [http://www.hydrogen-music.org/hcms/](http://www.hydrogen-music.org/hcms/)

---

### Post by Jay Car on 2011-04-16
> **Frogs Hair said:**
> This is in the repository and is also included with Ubuntu Studio. [http://ardour.org/](http://ardour.org/)

Hi! Thanks!

Yes, Ardour is on my list of 'must-haves', along with Audacity, Rosegarden, and Lilypond. But I don't know if everything on the Ubuntu Studio's audio-package list is essential. I'm hoping to learn what's absolutely needed to get started, so I'm not adding unnecessary complexity. 

I've never really had to worry about sound on any computers, with Ubuntu it's always (so far) just worked.  But that's for everyday needs. 

For someone who needs to do recording and playback, I don't know what extras might be best, or which can be left out at first.  For instance, will all the things listed under "JACK and JACK Utilities" be necessary? 

If this were for graphics I'd have no worries, but I'm treading in new territory this time. I'm probably worrying too much...

---

### Post by cchhrriiss121212 on 2011-04-16
There are 2 angles of approach for music recording software on Linux: the simple, or the complex.
If you want something that is simple to pick up then look at either Jokosher or LMMS, they are both complete packages that won't require any extra tweaking. They are very user friendly but I have had issues with both in terms of stability, YMMV.

If you want the advanced features and lower latencies, look to JACK,  Ardour, rosegarden, seq24, hydrogen etc. JACK based audio is a modular system, meaning you can have one specialised program for every task you do and hook them all together with JACK connections. 
There is some good JACK based software out there, but don't expect any of this stuff to be easy to use. If you choose the complex route, expect to spend at least a week getting to grips with JACK, low latency kernels, system configuration and what software is suitable for you. 

That is just the software, and hardware should be sorted out first. I am not sure that the Zoom H1 will work or not, the [ALSA database]("http://www.alsa-project.org/main/index.php/Matrix:Main") displays what cards are supported, but Zoom has no page there. However, I have read that other Zoom devices are working well for users here on this forum.
Recommendations: If you want a PCI card, M-audio delta 44/66/audiophile is a good choice, for USB an [Edirol UA-25 ]("http://www.rolandus.com/products/productdetails.php?ProductId=704")would do. 

Then you have the art of reocrding itself, mic placement, editing, what effects to use, mixing, mastering etc. There is a lot to learn that software and equipment can't help you with, but there are scores of forums and free guides for home recording which will help you on the way. 

My notes on the matter:
I picked up Linux about a year and a half ago, and the reason I did so was the wealth of FOSS available to record my music. It took me about a month before I actually recorded something, but once I got to grips with things, I liked the way it works, the freedom and the flexibility in the workflow. I don't think it is for everyone however, so if you don't want to put the time in, go for something on Mac or Windows.
My main tools are now JACK plus Qtractor with a few synths or Hydrogen added when I need them. Qtractor doesn't get as much press as Ardour, but it is a great recording program, another poster described it like having a pencil and paper, which is a good way of describing it.

---

### Post by steveneddy on 2011-04-16
** This is just my opinion **

I tried to get a Linux based recording setup going over the Christmas holidays this last year and it failed miserably.

The only alternative IMHO is to purchase a Mac - whichever model you can afford - and simply use Garage Band - or if you can afford ProTools and some add on applications go that route.

I beat my head into the wall and finally gave up after three weeks of head aches - one night when you finally get it working - or think that you do - come back to the studio in the morning hoping to get some work done only to find that NOW ARDOUR AND JACK DON"T WANT TO PLAY NICE TODAY!

Also the hardware interfaces that you should be able to use with Ardour don't work all the time either and lack full functionality.

IMHO I would never recommend to anyone setting up a recording studio with Linux - Mac is virtually plug and play and then you can get some work done.

** This statement is my opinion only **

---

### Post by linuxforartists on 2011-04-16
That's really awesome you're helping your friend this way.  One resource I'd point you to is [Linux Musicians]("http://www.linuxmusicians.com/").  It's the best and most active forum I've found for open-source musicians.  Good luck!

---

### Post by jerenept on 2011-04-16
Ubuntu Studio uses a real-time kernel, so if you want to get into video editing and Audacity and stuff I'd definitely recommend it over a vanilla Lucid install.

---

### Post by Zoot7 on 2011-04-16
> **steveneddy said:**
> 
IMHO I would never recommend to anyone setting up a recording studio with Linux - Mac is virtually plug and play and then you can get some work done.

I'd have to agree, having tried to use things such as Ardour and Jack in the past only to be greeted with abmisal failure.

TBH if you're looking for comprehensive music production and recording that'll actually work and work reliably, then the only option is Windows or Mac as platforms, there's plenty both free and un-free DAW packages for both that do the job quite well. Cubase is the one I use myself for all my music production. 

Linux doesn't really have anything that can hold a candle to similar software packages. *Were it me* I'd save myself the trouble and forget about using Linux as a platform for music production.

---

### Post by Jay Car on 2011-04-16
> **cchhrriiss121212 said:**
> There are 2 angles of approach for music recording software on Linux: the simple, or the complex.
If you want something that is simple to pick up then look at either Jokosher or LMMS, they are both complete packages that won't require any extra tweaking. They are very user friendly but I have had issues with both in terms of stability, YMMV.

If you want the advanced features and lower latencies, look to JACK,  Ardour, rosegarden, seq24, hydrogen etc. JACK based audio is a modular system, meaning you can have one specialised program for every task you do and hook them all together with JACK connections. 
There is some good JACK based software out there, but don't expect any of this stuff to be easy to use. If you choose the complex route, expect to spend at least a week getting to grips with JACK, low latency kernels, system configuration and what software is suitable for you.

Thank you! I've read so many threads (both here and other forums) about problems with JACK, and it's really the part that worries me the most (because I don't really understand what it does). But I also know that it's only people with problems who ask for help, so I'm hoping there's far more people out there that don't have problems and that I'll be one of them. :)  

> **cchhrriiss121212 said:**
> That is just the software, and hardware should be sorted out first. I am not sure that the Zoom H1 will work or not, the [ALSA database]("http://www.alsa-project.org/main/index.php/Matrix:Main") displays what cards are supported, but Zoom has no page there. However, I have read that other Zoom devices are working well for users here on this forum.
Recommendations: If you want a PCI card, M-audio delta 44/66/audiophile is a good choice, for USB an [Edirol UA-25 ]("http://www.rolandus.com/products/productdetails.php?ProductId=704")would do. 

I don't think the Zoom will be a problem, it's basically a microphone that records sounds.  It can be plugged into a computer so those sound files can be transferred onto it. It works fine with that cranky old XP machine, so I'm sure it'll work with the new (soon-to-be Ubuntu) machine.

Thank you for the sound card recommendation, I'll pass that along to my friend to consider when he can afford to upgrade the on-board sound.

> **cchhrriiss121212 said:**
> Then you have the art of reocrding itself, mic placement, editing, what effects to use, mixing, mastering etc. There is a lot to learn that software and equipment can't help you with, but there are scores of forums and free guides for home recording which will help you on the way. 

That will all be for my friend to learn on his own. I'm just doing my best to give him the right tools, he can take it from there.

> **cchhrriiss121212 said:**
> My notes on the matter:
I picked up Linux about a year and a half ago, and the reason I did so was the wealth of FOSS available to record my music. It took me about a month before I actually recorded something, but once I got to grips with things, I liked the way it works, the freedom and the flexibility in the workflow. I don't think it is for everyone however, so if you don't want to put the time in, go for something on Mac or Windows.
My main tools are now JACK plus Qtractor with a few synths or Hydrogen added when I need them. Qtractor doesn't get as much press as Ardour, but it is a great recording program, another poster described it like having a pencil and paper, which is a good way of describing it.

This is very helpful, and I'm pretty sure my friend has the time and patience to learn the software. Thanks for all the info!


> **steveneddy said:**
> ** This is just my opinion **

I tried to get a Linux based recording setup going over the Christmas holidays this last year and it failed miserably.

The only alternative IMHO is to purchase a Mac - whichever model you can afford - and simply use Garage Band - or if you can afford ProTools and some add on applications go that route.

I beat my head into the wall and finally gave up after three weeks of head aches - one night when you finally get it working - or think that you do - come back to the studio in the morning hoping to get some work done only to find that NOW ARDOUR AND JACK DON"T WANT TO PLAY NICE TODAY!

Also the hardware interfaces that you should be able to use with Ardour don't work all the time either and lack full functionality.

IMHO I would never recommend to anyone setting up a recording studio with Linux - Mac is virtually plug and play and then you can get some work done.

** This statement is my opinion only **

Hi steveneddy!

I appreciate your opinion! Thank you for adding it. I'm hoping we won't have the same problems as you described, but I know such things are always possible. 

I guess all we can do is give it an honest effort, and if it doesn't work, we'll try something else. There's always a way to figure things out if we're persistent, it just might not be the way we planned. I'm pretty sure a Mac is out of his budget, but maybe I can help find a used one if all else fails. 

Thanks for writing your experiences. :)

---

### Post by Jay Car on 2011-04-16
> **Zoot7 said:**
> I'd have to agree, having tried to use things such as Ardour and Jack in the past only to be greeted with abmisal failure.

TBH if you're looking for comprehensive music production and recording that'll actually work and work reliably, then the only option is Windows or Mac as platforms, there's plenty both free and un-free DAW packages for both that do the job quite well. Cubase is the one I use myself for all my music production. 

Linux doesn't really have anything that can hold a candle to similar software packages. *Were it me* I'd save myself the trouble and forget about using Linux as a platform for music production.

Thanks for your post! 

Windows won't be an option, a Mac is possible, if all else fails. But for now, we'd like to try using Ubuntu (and the audio packages) first. I've known this man for nearly 20 years now, he has a lot of patience and a great sense of humour. Plus, he already has some good skills and talent to bring to the project, so if there's a way to get this done, we'll find it. 
We don't consider it "trouble" - it's just a learning experience. 

I know that at our age the phrase "lots of time" is a relative thing, but still, we have lots of time, no deadlines here.

If I can just get the system and basic software set up (and get him on these forums), I think he'll do fine with it.  I hope...we'll see. :D

---

### Post by Jay Car on 2011-04-16
> **jerenept said:**
> Ubuntu Studio uses a real-time kernel, so if you want to get into video editing and Audacity and stuff I'd definitely recommend it over a vanilla Lucid install.

I see. I didn't know that. My only problem with Ubuntu Studio is that it seems like too much for someone who has no interest in all the video and graphics programs.  I guess I could just uninstall what isn't needed.

It certainly can't hurt to give it a try! 

Thank you for that information (I'm going to go read more about it now)!

---

