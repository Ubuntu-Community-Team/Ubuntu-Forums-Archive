---
title: "Recording via Firewire and Ubuntu 6.06"
date: 2009-07-07
forum: Ubuntu Studio
---

### Post by caalamus on 2009-07-07
My apologies in advance if my complete lack of knowledge regarding Ubuntu, or proper conduct in/use of this forum is frustrating or offensive. I am quite new to & confused by both. Also open to any suggestions and instruction

I am running Ubuntu 6.06 LTS (Dapper Drake) on a 500Mhz G3 iBook with 512MB of plugged in RAM (in addition to the less than 150MB built in). It is difficult for me to provide any further system configuration info as pre my lack of knowledge on how to access said info with out using the familiar "System Profiler". Would like to learn how to use this seemingly, capable and straight forward interface for all it can do, any side info about basic Ubuntu navigation is welcome.

But here's my current question. Can you help me figure out how to get this guy recording via firewire?

This machine was running OS 10.4 when I bought it and (though a bit dicey) Garageband was recording via my Mackie Onxy Satelite, so I know that bus is operational. I downgraded to OS 9.2.2 because I wanted to run a system that wouldn't drive this poor old machine so hard and though OSX is great, most of the coolest features were out of this little 500Mhz range of capability. I couldn't find any software for OS 9. Audacity would detect my audio interface, but then crash & freeze my machine when I tried to select it. 

So I had heard about Ubuntu and I gave it a try. So far I am REALY impressed... and enthusiastic to learn!

My primary use of computers is music... I'm hoping Ubuntu wants to play.

When I open Ubuntu's "Device Manager" (System>Administration>Device Manager), my "Mackie Onxy Satelit" appears under "UniNorth/Pangea Firewire"

When I try to run "Sound Recorder" (Aplications>Sound & Video>Sound Recorder), I get this error message:
[IMG]http://i168.photobucket.com/albums/u177/profanuscaalamus/2009/August/SoundError.png[/IMG]

"Your audio capture settings are invalid. Please correct them in the mulitmedia settings."

(this happens even when my firewire device is not connected)

When I search for these "Audio Capture Settings" I can't even find the "Multimedia Settings" they are supposed to be a part of... 

I can introduce and use a flash drive no problem and (although glitchey) can also rip tunes from CD using "Sound Juicer" and playback via  "Rhythmbox"... if knowing that is of any help.

I see people talking about "Jack", "FFDO", "Freebob" & even a "Commandline recorder" which I think is a bit out of my league. I've just figured out how to right click! hahaha!

(Holding control and clicking doesn't work, right click is achieved via my laptop's eject CD drive button)

What do you think?

One thousand thank you's to anyone who takes the time to consider my query :]

Here's something for you to listen to.

[Http://www.MySpace.com/Caalamus](Http://www.MySpace.com/Caalamus)

[Http://www.MySpace.com/ProfanusCaalamus](Http://www.MySpace.com/ProfanusCaalamus)

[Http://www.MySpace.com/BornAzul](Http://www.MySpace.com/BornAzul)     


 ~Caal

PS my internet access is inconsistent... feel free to contact directly :]
(Caalamus@Gmail.com)

---

### Post by trulan on 2009-07-07
Well, to record with firewire you're going to need a firewire audio driver.  The two in existence for linux are freebob (older) and ffado (newer).  Glad to see you are somewhat familiar with these terms ;)  And you're also going to need the Jack audio connection kit to get whichever driver you choose up and running.

Is this possible on a 500Mhz machine running Dapper?  I have no idea.  I think I would enjoy trying, if it were my machine.

I am sure, however, that by the time you know the answer to that question you will have learned and accomplished a lot more than you thought possible.  See what you can find on the net about running Jack in Dapper, and post back if you jave more questions.

---

### Post by dawiba on 2009-07-08
As Trulan says, you'll need the right Firewire driver.

You can find out all about the FFADO drivers here

[FFADO Page](http://subversion.ffado.org/)

My first experience of Ubuntu was 8.10 and my first experience of audio on Ubuntu is with 9.04, so I can't help with your version, but good luck!

---

### Post by caalamus on 2009-07-08
You guys are awesome thanks! If these questions seem a bit lazy... bare in mind that I have no web access ;] So even the leg up you've given by clarifying that FFADO and Free Bob are drivers, not applications... is invaluable. After reading for two hours without any useful posts found it can be a bit frustrating... Cheers!

---

### Post by Stochastic on 2009-07-10
Getting firewire audio drivers to work in Dapper will be fairly difficult.  For an experienced Ubuntu user this process may be doable, but for a new user it'd be next to impossible (unless you're already pro at sourcing library dependencies and compiling programs from scratch - and even then, config may be tough).

The freebob driver wasn't in Dapper, and FFADO is the newer generation of that driver.  Hardy does have freebob drivers, and I'd recommend a system upgrade to at least Hardy if you want to use audio through firewire.

If you really want to try getting things working in Dapper, you'll need to do the following (minimum) procedures:
- download, compile, & install either freebob or FFADO drivers/libraries (I'd actually go with freebob here because it may conflict less with the older Dapper libraries)
- download, compile & install Jack from scratch (do some research to find if the Jack version in Dapper can use the freebob or ffado backend, if so, use this version, if not, use the closest version to it that can)
- do some research into Dapper's udev permissions for firewire, as you'll need to adjust these permissions manually to get access to the device

A system upgrade to a newer version of Ubuntu would prove much easier - and shouldn't tax your system very much (maybe go with [Xubuntu]("http://www.xubuntu.org/") if you're concerned about rescources - it can be configured for audio just as easily as regular Ubuntu).

---

### Post by Cheesemill on 2009-07-10
A bit off topic but I thought I'd let you know that support for 6.06 runs out in 4 days, so the repositories will no longer be available. It might be time to install 8.04 :)

---

### Post by caalamus on 2009-07-11
Hey! more replies... this forum thing ain't so bad after all :] 

 Both of you guys made reference to Hardy Heron... Based on my knowledge: 

([http://old-releases.ubuntu.com/releases/hardy/](http://old-releases.ubuntu.com/releases/hardy/))

...my 500mhz g3, non-intel is not sufficiently configured for running Ubuntu 8.o4 [?]

Homme last night was telling me of some OS 9 options that I hadn't previously been privy to... which diminishes the immediacy of need in terms of learning Ubuntu.

I'll just run my copy of 9.22

But this operating system is pretty cool and the idea of it being possible to manipulate it... learning linux.... I'm really interested.

Cheesemill, thanks for the heads up on expiration of support. ¡Pinguinos son chidos!


Stochastic...

"If you really want to try getting things working in Dapper, you'll need to do the following (minimum) procedures:
- download, compile, & install either freebob or FFADO drivers/libraries (I'd actually go with freebob here because it may conflict less with the older Dapper libraries)
- download, compile & install Jack from scratch (do some research to find if the Jack version in Dapper can use the freebob or ffado backend, if so, use this version, if not, use the closest version to it that can)
- do some research into Dapper's udev permissions for firewire, as you'll need to adjust these permissions manually to get access to the device"


Well o.k... 

Thank you, there are some good inroads there. But no help on recording via firewire and Ubuntu 6.06, due to my lack of understanding in regards to the terms you are using. Rather, you just taught me that I need to rewind a bit first.

Like I said above I'l just fall back on the Mac OS intended for this machine...

But in the meantime I'm going to try and learn about:

     Compiling drivers and libraries
     What people mean when they say  "back end"
     Udev & permissions in general

So compiling sounds like organizing hierarchies of files/folders. Seems like it would involve creating an install disc. Or would you just use a standard data disc and command line  prompt?

Permissions are pretty important to system function from what I've experienced... seems like they direct and govern processor/ram/hard drive resource requests made by applications & decide which users/applications have access to what & how.

Wish I could afford the interwebs... 

Lots of potential reading.


Thanks all for continuing to feed my curiosity &#8730;

Rock out!

---

### Post by Stochastic on 2009-07-11
caalamus, from what it sounds like, you probably would want to load xbuntu hardy heron onto your machine.  It's a version of Ubuntu that's designed to need lighter system rescources.

I also think a large portion of my post was too technical for your needs.  Essentially all you need to know about recording firewire on Dapper is that it's too difficult for you to waste your time on.

Hardy Heron Xubuntu has firewire functionality if configured right.  If you want to install that I'd be happy to walk you through configuring it (no need to research UDev permission rules and compiling etc...).

---

### Post by caalamus on 2009-07-13
That's very kind of you Stochastic. I think that sounds like a plan! ;] Do you make music? Maybe I could return the favor? Providing you have some inquiry I happen to know something about...

But here's the thing...

[http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04/release/)

makes it sound as though my iBook is far too old for this release. Is this one of those scenarios where in the proprietors information regarding system requirements are more stringent than need be and one has a bit of room to play with?

To reiterate:


G3 500Mhz iBook with 576MB of RAM. 64 built in and 512 plugged. 

So providing you think it's alright I'll download the image and burn an instal disc for Hardy Heron.

Sorry it takes me a minute to get back.

Thanks again to everyone who has responded to this post :]

---

### Post by Stochastic on 2009-07-13
So I just realized that your system isn't too slow or weak to handle things, it's just that the architecture of your processor (PowerPC) is no longer an officially supported version of Ubuntu.  This is why it looks like the newer releases won't work for you.

There is good news, bad news, and consolation news that comes along with this though.

The good news is that the PowerPC version of Ubuntu is still actively maintained by the community (i.e. no longer associated with Canonical).  Here's a post that points people in the right direction: [http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714) and here's the download location for xubuntu and other derivatives: [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

The bad news is that Ubuntu Studio doesn't have a PowerPC version, nor is there any other audio-specific versions of Linux that I'm aware of that have PowerPC versions (maybe CCRMA).

The consolation news is that you should still be able to record fine without the specialized audio tweaks.  Firewire can still be setup, jack can work fine (though without the RT kernel, you'll get a higher latency - nothing horrible though), and all the recording applications should still be available.

So, if you get yourself a newer PowerPC version of Ubuntu or Xubuntu (either one should work just fine) installed (I'd recommend Jaunty for you), then I'll be able to walk you through setup steps.

---

### Post by caalamus on 2009-07-13
wonderful... 
 I'll check those out now :]

Thanks for the "support"

So, Ubuntu studio is an audio-centric OS? That's a novel idea :]

---

### Post by caalamus on 2009-07-13
Actually,

 I was wondering:

Stochastic, you recommend "Jaunty", but is that necessary? ...or just "nicer". I can suffer graphical inferiority in the name of stability.

I ask because I have one CD left... kinda feel like they are a media of the past and rely primarily on external hard discs & flash drives.

I see here:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

...that I can also download installs of Intrepid Ibex, Hardy Heron, Gutsy Gibbon, Edgy Eft & Dapper Drake. They all have Kubuntu, Edubuntu, Xubuntu versions available as well (save for the two version 6 offerings).

I want to put an OS on this book that will get the job done and maybe initiate me into the nuances and complexities of Linux without spending my time researching instead of recording.
If going with the current release is the most stable choice due to developer buzz and support availability/architecture stability, simply say the word. But, if I can get away with an older release and doing so would make my poor little Mac happier... that's the ticket. Especially if all I'm sacrificing are the creature comforts of appearance and new gizmos?

Is this question even relevant to Ubuntu?

Also are you recommending Xubuntu 9.04?


:] :] :]

---

### Post by Stochastic on 2009-07-14
Because you aren't going to be running an RT kernel, I'd recommend 9.04 for your machine.  It has FFADO drivers (which are more stable for firewire than earlier freebob) and it's vanilla kernel performs better than older vanilla kernels.  You can turn extra gizmos and flasshy window decor off/on anytime you like.

Xubuntu would be just fine, but some (myself included) prefer the comforts that the gnome desktop provides.

It's been ages since I've run anything less than the box I'm on and it handily out powers yours, so it's tough for me to say if you need Xubuntu or regular Ubuntu, do some research between the two yourself.  I would recommend 9.04 though.

If you don't want to burn a CD, there are other install methods available too, (network installs, USB thumb drive installs, etc...) but I'm no expert there.

---

### Post by caalamus on 2009-07-16
I now have discs of Ubuntu & XUbuntu 9.04. Both seem solid & install fine. However, both have screen resolution issues. I get the desktop in the upper left 5/6 of the screen. There is a colorful band across the bottom and the desktop repeats, partially. The whole right and bottom 1/6 is blank

(fractions merely eyed estimates)

I tried settings tweeks... no luck. In fact adjusting the resolution or refresh rates made things much worse, requiring a reinstall.

Hunted around a bit here... thought I'd drop a line and now I'll get back to reading.

P.S. Not with firewire, but 9.04 records quite nicely!

---

### Post by caalamus on 2009-07-18
I found a thread relevant to my EXACT machine!

¡**POW**!


[http://ubuntuforums.org/showthread.php?t=1114297&highlight=iBook+G3+Working+Tutorial](http://ubuntuforums.org/showthread.php?t=1114297&highlight=iBook+G3+Working+Tutorial)


Will try fix for screen reso issues when I return home :]


(lat night WiFi in the park with a different machine)


Big respect to this forum and it's wonderful users!!!

---

### Post by caalamus on 2009-08-04
status update...



 Screen reso issue solved!
(though with much confusion and frustration)

Connecting to an ethernet modem & accessing the interwebs
(easy as plug and click)

CD drive not recognized
(new research topic)

Airport card not functioning
(also on deck)


Stochastic...


I'm down for the walk through whenever you've got a minute. The screen makes sense now... I've pretty much mastered Majhong (hehehe!) & I'm ready to start experimenting with the mobility this little guy offers. I found some really wierd natural reverb situations that my bus powered firewire interface and this guy would make possible if I could get them to play nice.

:P

---

### Post by caalamus on 2009-10-19
seems like I have Ubuntu studio installed[?]

But I can't get sound!

Tried a few suggestions... to no avail....

I'm trying to hunt Stochastic down again... but I can't send a message... cause I need more BEANS!

MAN! I don't even drink coffee!

hahaha!

---

