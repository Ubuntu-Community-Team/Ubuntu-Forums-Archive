---
title: "just starting- very basic and general"
date: 2011-01-12
forum: Ubuntu Studio
---

### Post by spencerownside on 2011-01-12
firstly, i am sorry if i am posting this in the wrong place. i am curious about some video and audio stuff that i am doing but don't know if i am even posting this in the right place.
is "ubuntu studio" different than say "ubuntu 10" as an os or is 'studio' just a specific program? i ask that only because 'studio' is a prefix option- sorry that's such a stupid starting point.

i am trying to make videos and such for broadcasts for my band. we are running 2 videos on 2 different comps (both ubuntu 10) and a 3rd comp is the audio. the audio comp is windows xp and the audio program is cakewalk. basically running cheese for the vids. i am curious about suggestions for combining all these separate sources and different file types. 

i will hold off on more info until i find out if this is the right location for this discussion. thank you for assistance and sorry if wrong place.

---

### Post by argoson on 2011-01-12
Well... Ubuntu Studio is actually a spin-off of Ubuntu, designed in a way that when you install it, you will have a set of software tools designed for a specific target: edit and create Audio, Video and Graphics. Of course you can use it a a regular OS, for all your regular needs: browse the web, listen to music and videos, social networking, create office document etc.

The version number is the same: 10.04,10.10 and so on, because Studio is based on the same Ubuntu version.

basically you can achieve having the same environment - be it for Audio, Video or Graphics production, by installing any flavour of Ubuntu- Kubuntu,XUbuntu and so on, but you will have to install all the needed software and tweak the OS so that it will have the necessary components (RealTime kernel and so on).

Hope this answers your question...

---

### Post by spencerownside on 2011-01-12
it kind of answers my question but also gives me more questions. i am downloading the studio .iso and am reading about ubuntu studio in the community section; so i am working on learning. 
do i need a super duty sound card for a 'studio'? i assume that i could download studio onto a pc that is already hooked up to a mixer and break-out box and all that fun stuff? can i use 'studio' as just an OS and be able to have a choice of which comp i use for as my "workstation"? in addition to all the programs listed on studio, i assume that i can add my basics such as open office and tetris? and i can also add say a kdenlive and avidemux? 
as an example of some of my challenges: i am reading the upgrade from ubuntu version page, and where it discusses going into the terminal and typing command "blahblahblah" and then a list of different packages and what to do with those etc... i can go into the terminal and type stuff in -- [and am actually also studying the working within terminal sections of the ubuntu communities pages] -- ie, i can follow directions and do what i am told, but i don't necessarily know what i am doing. i didn't grow up playing with computers so i don't always know the basics and the specifics. i'm probably an intermediate who doesn't understand jargon or why what i do works - if that helps any. 
thank you for any assistance.

---

### Post by lisati on 2011-01-12
Yes, you can use Ubuntu Studio as a regular OS. I was using a version of Ubuntu Studio on one of my machines for a while until my needs changed.

---

### Post by spencerownside on 2011-01-12
thank you

---

### Post by Bucky Ball on 2011-01-12
You can also just install the AV packages from UStudio right in your Ubuntu install without installing the whole OS! It's easy. System->Admin->Synaptic Package Manager, then search for and install:

ubuntustudio-audio
ubuntustudio-video

You can even go for the full experience by installing:

ubuntustudio-desktop

This will also install the rt kernel (real time kernel for better latency). ;)

I love the hybrid! My studio box is Xubuntu install with the UStudio AV packages, Edubuntu and Ubuntu Satanic Edition artwork and themes.

Enjoy!

---

### Post by spencerownside on 2011-01-13
there are some parts of that last paragraph i am not completely clear on, but it sounds pretty cool. 
let me know if this is the wrong place to ask this question, but i am going to be doing a pretty crazy set-up here soon:
the basic plan is to run multiple cameras (webcam) as video, but wanting to integrate audio from cakewalk. i have studio in one of the rooms in the house and the plan is to try and broadcast live streams and to record rehearsals and writing sessions etc... 
1) what video recording programs would be better than cheese and could handle 2 usb inputs?
2) is there a ubuntu equivalent to cakewalk that would allow for editing together tracks?
3) is there a program that monitor all of these inputs live and simultaneously?
i am sure i could come up with more, but i suppose i will start there. i am sure there is another better thread somewhere too -- any suggestions would be greatly appreciated; thank you. 

ps- what is edubuntu? it sounds like a nifty thing for someone in a school type setting?

---

### Post by cchhrriiss121212 on 2011-01-13
Yes there are audio programs like Cakewalk for Ubuntu, but your success with them may depend on your hardware. What sound card do you use?

Try looking at [LMMS]("http://en.wikipedia.org/wiki/LMMS") and see if it has all the features you need.

---

### Post by spencerownside on 2011-01-14
Integrated Audio: Hi-Def (HD) Audio support Dolby home theater v3 audio enhancement -- 
i think is what i will be working with. i suppose i should be more clear of what i am trying to do. 
i have a band and i think i mentioned that we want to do recording and  broadcasting of the recording, rehearsing, songwriting stuff. we  basically want to run 2 cameras (right now from 2 different  computers/sources). then all the mics, mixer, and cakewalk are on  another computer (running XP). i assume that what i will have to do is  essentially set up a network, send the individual files from the  individual sources, then mix them all together at a 'workstation'- which  will probably be a laptop with the above mentioned sound card. 
in my dream: i would like to find a program that will on the fly take  multiple video feeds, and an audio input. the mixer we have has a rc out  that is currently plugged into a stereo for listening to playbacks.  what we are thinking we'd like to do- if the program is available  (presumably able to be found for/on studio) - is to plug the rc out from  the mixer into either a 1/8" adapter or a usb adapter (if there is such  and if the sound quality would be any different) into the same computer  that is taking the video feeds. hopefully route all the inputs into a  single program: essentially like any program that would be used for any  news broadcast, tv show, live stream concert, etc per se. 
i don't know if i explained that clearly or just muddied the water, but any ideas are appreciated again. 

ps- what is edubuntu? i did skim the ubuntu page, but i suppose i don't understand what is special about it versus any other ubuntu version. forgive my newbieness please

---

### Post by cchhrriiss121212 on 2011-01-14
The audio capture is do-able, I would go with a 1/8" adapter then use something like Audacity to capture the stream from the mixer. Not sure about multiple video feeds at the same time, you might need to use mencoder via the CLI.

---

### Post by Bucky Ball on 2011-01-14
Spencer, you should definitely try Ubuntu Studio or AVLinux:

[http://ubuntustudio.org/](http://ubuntustudio.org/)
[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

You can install the UStudio AV packages by Sytstem >Admin >Synaptics and searching for 'ubuntustudio-audio' or 'ubuntustudio-video'. For the full experience you can go 'ubuntustudio-desktop' and that will also install the realtime kernel which will be selectable at boot (rt-kernel). Have fun

---

### Post by spencerownside on 2011-01-14
thank you for the assistance- i appreciate it greatly. i am 98% certain that i will be upgrading at least 1 pc with studio today- i am curious about 1 thing though. if i go into the terminal and add the upgrade codes correctly, is it like actually changing the OS? ie, i am i going to lose what i currently have on my pc? do i need to backup current files like i would when changing an OS? 
gracias

---

### Post by Bucky Ball on 2011-01-16
If you do a full install you will. That's why I suggested just loading the ustudio packages. It is *exactly* the same. You can also install the rt-kernel and boot into that at start-up. 

This way you will keep your files. ;)

---

### Post by Bucky Ball on 2011-01-16
. In error! Why is there four posts and I made one???

---

### Post by Bucky Ball on 2011-01-16
If you do a full install you will. That's why I suggested just loading the ustudio packages. It is *exactly* the same packages. You can also install the rt-kernel and boot into that at start-up. 

This way you will keep your files. ;)

---

### Post by Bucky Ball on 2011-01-16
If you do a full install you will. That's why I suggested just loading the ustudio packages. It is *exactly* the same packages. You can also install the rt-kernel and boot into that at start-up. 

This way you will keep your files. ;)

---

