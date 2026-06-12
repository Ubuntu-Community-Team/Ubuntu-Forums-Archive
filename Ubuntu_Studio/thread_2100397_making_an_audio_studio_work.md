---
title: "making an audio studio work"
date: 2013-01-01
forum: Ubuntu Studio
---

### Post by de Bacon on 2013-01-01
Again thinking of learning to use the audio portion of Studio.  I am a musician, 40 years plus (mainly acoustic guitar, don't use electronics really), have been using ubuntu as a main computer since 2008 (currently running Kubuntu 12.04).  For all my audio work, I use  cakewalk pro audio 9 on win 98 OS (on a separate desktop machine)for all audio work.  It is getting old, the machine, and I know it won't last forever.  It may be time to convert to something new before it crashes, but I won't buy or use any new Windows products.  Thus I have a lot to learn.

I tried Ubuntu Studio with 8.04 but never could figure it out, so I gave up.  I am not very aligned with the language used in tech stuff, thus the language of communication seems to be a huge hindrance in the process.  I really have no aversion to learning, but language in tech, the use of acronyms etc. is really a stopper for me.  

Thus I am wondering how to best go about changing over.  The desktop I am now using is marginally within requirements being a 2006 model 64 bit processor with only 2 Gb memory. The memory could be expanded quit a lot but, it might be best to get a new machine???  I am currently downloading the 12.04 studio ISO, though I wonder if it might be easier to simply install the software needed for the audio portion ( I won't be using the other parts of studio) and go from there, rather than loading a new OS?  

Then still I wonder if I will hit the same language wall, regardless of the method of getting the software in place?  

Any helpful thoughts?

---

### Post by jejeman on 2013-01-01
If you can, buy new PC, but no need until you learn how to work with Ubuntu Studio.
You need at least 2GHz CPU (perferably core2duo). 2GB of RAM is enough. Hope you installed 32bit system.
I don't know what you should learn first, maybe learn how audio works in linux
Read this [http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)
when you understand that. Start learning JACK, you will probably need it. When you setup JACK, and it is stable. Then it all depends of what you want to do.

Install Ubuntu Studio 12.04 32bit on separate partition. It should be less resource hungry than Kubuntu, and you need that for working with audio.

---

### Post by de Bacon on 2013-01-01
I use the 64 bit system, since I have one!  So what is wrong with the 64 bit system and its ability to do twice as much (at least in theory)?  Are there still too many conflicts with software after all this time?

As to clock speed, I have enough if what you say is the lower limit. I have 2.3 Ghz or something, don't remember.  

To purchase a new system will require months of getting up to speed on new hardware potential and then finding the right combos.  I don't go to the store and buy one for the cheapness in such things that I wish to avoid.  Then there are the compatibility issues which are rather difficult to figure out in new hardware, until it is in your machine that doesn't work due to conflicts and proprietary issues. So that is a whole different ball of wax.  Still this is a rather old machine, 6 years, where my other one is 13 years and still working fine, while never being allowed access to the internet.

Oh thanks for the info file on audio.  It looks like it could be a good thing to understand, maybe even take the mystery out of what I have always seen as the it don't work problem.  Like skype, I can't make the audio work with it either, never needed to use it though so gave up after days of diddling around to no profit.

---

### Post by jejeman on 2013-01-01
64bit OS is slightly faster than 32bit OS. But it uses more RAM than that it is faster. Since you have (only) 2GB, 32bit OS is all you need. Of course, nothing wrong for you to use 64bit OS even that you have just 2GB of RAM.
If you run properitary software, such as skype, or you use WINE, it is better to have 32bit OS, since it is 32bit program etc.

For your PC i would go for 32bit OS with JACK1.
You can find out what CPU you have with this
```
cat /proc/cpuinfo | grep name
```

---

### Post by coldraven on 2013-01-01
I played around with Ubuntu Studio and as the posters above say you will probably need to learn Jack. It took me a few days until I figured it out but if someone were to show you I bet that you would pick it up in half an hour.
So here are my two bits of advice...
Try to hang out with some other Linux based musos :)
Get a PC with two monitors or one really wide one. When learning new software I find it invaluable to have the help screen on one monitor and the program running on the other.
Good luck and have fun.

---

### Post by de Bacon on 2013-01-01
> **coldraven said:**
> if someone were to show you I bet that you would pick it up in half an hour.
I bet you are right!  That is why I write here. I don't know anyone who uses Linux other than myself.

> **coldraven said:**
> 
Try to hang out with some other Linux based musos :)

I have no idea what a "musos" is?  I do imagine you are saying, other like minded folks that use Linux but I stated above I don't know anyone.  When living out in the very rural area, where the largest population base is 700 there is little chance of finding much more than windoze folks, who's sole purpose for that is to use FaceBook or other nonesense.

---

### Post by de Bacon on 2013-01-01
> **jejeman said:**
> 
Read this [http://tuxradar.com/content/how-it-works-linux-audio-explained](http://tuxradar.com/content/how-it-works-linux-audio-explained)

A pretty good article, that becomes even more clear after reading all the comments tacked on to the end.  (clear as mud by completion)  It helped my understanding of the things I need to learn about at best.  It doesn't help for understanding how to configure Studio's component software parts/pieces/programs, so that they will function in a way that will allow a music recording system to work though.  Nor does it say anything about what the functional software components do or how to integrate them as a functioning package for reaching my goal of a computer based recording studio. 

In the end I found value in reading the article.  Thanks for passing it along.  
Thanks for reading the thread also!
Regards

---

### Post by jejeman on 2013-01-02
Musos = musOS = music Operating Systems 
Like: AVLinux - it is really optimised for audio to work "out of the box".

Now that you understand audio layers in linux it is easyer for you to understand what to do, or troubleshoot.

read this
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)
[https://wiki.ubuntu.com/UbuntuStudio/Workflows](https://wiki.ubuntu.com/UbuntuStudio/Workflows)

Basicly, when you setup JACK to work stable, then it all depends on what you want to do.

---

### Post by coldraven on 2013-01-02
Sorry for the confusion but around here the slang for a musician is a muso.
JACK as I'm sure that you know by now is a digital version of the old fashioned patch bay where you can connect inputs and outputs with jack leads.
You can also connect the time-code so that an equalizer, for example, will alter it's settings during the track. Also a virtual drum machine (Hydrogen) will "rewind" as you move through your recording using Ardour.
You will have to experiment.

Again I suggest getting two monitors because you will need all the screen "real estate" that is possible.

---

### Post by lykwydchykyn on 2013-01-02
First, your computer hardware is significantly newer than the hardware I use for Ubuntu Studio, so I think you should be fine there.  No point in upgrading until you hit the limits.

Second, I also used Cakewalk (later Sonar) back in the day, so I think I can appreciate where you're coming from.

If you want to convert your Kubuntu system into a studio system, you'll want both the applications and also the low-latency kernel.  This is critical to getting good audio performance.

I find that Ardour had a much steeper learning curve than Cakewalk, it's a bit more like ProTools.  And like others have said, understanding JACK is essential to everything else.

Unfortunately I haven't had a lot of time to do recording on my system, and it's had some hardware instabilities to boot, but with some dedication it's possible to get comfortable making music on Ubuntu.  I miss some of my old Sonar features like loop clips, and I really miss a lot of my old VST plugins (can't get Wine VST working for anything), but if you're doing very simple audio tracks without a lot of sequencing or heavy production, you should be fine.

---

### Post by de Bacon on 2013-01-02
Thanks for the interest first of all.  I altered my original plan, after burning UStudio 64 bit to disk, I then downloaded the 32 bit version and burned it.  I got the 32 bit version loaded (ha ha) today and am about done fooling with computing for the day. I put it on a separate HDD so when I want to do music I can boot to that drive (until I get the studio version fully functional as my desktop with browser, mail and other functions).  At a glance I didn't notice what I think of as a monster, "Unity", if true, I'll be truly thankful (don't like that at all).   

Anyhow, I'll do more research as per > **jejeman said:**
> 
read this
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)
[https://wiki.ubuntu.com/UbuntuStudio/Workflows](https://wiki.ubuntu.com/UbuntuStudio/Workflows)
 I've sort of looked at the studio community url before.  What I saw was oversimplified to be of much help  IMO of the time.  It is likely worth going back.  The workflows page might also be quite helpful/useful.  I do think I understand the basics of JACK but have yet to actually try putting item of software into and out from it.

No worries about the muse confuse, language is difficult at best, well maybe just for me.

As to cakewalk and what my normal is:
I put songs together by recording actual sound, through my PA system.
1. Inputs of sound (microphone >>>> PA mixer >>>>> computer soundcard >>>> hardware/software interface >>>> digital audio file _.wav) guitars, piano or other instruments along with  vocals, each recorded individually on separate digital tracks.  2.  I add and write midi tracks of bass, drums, individual strings, maybe even woodwinds and horns, (what ever is desired) again in individual tracks ( _.mid).
3.  Adding effects where desired (reverb etc.)  
4.  Then the mixing process.  All those individual tracks need sound level adjustment for the right mixture of tonal quality, in sterio.  
5.  the mixdown conversion the final _.wav or _.mp3 output file. 

6.  I also use the music notation program that interfaces with the midi (as its source to mimic for notation) to make a printable music chart for copyright purposes.  I also sometimes integrate the lyric view (which uses an interface through midi) to write the melody for the lyric and places it in musical score/notation.  

I can only hope at this point, that I can end up with something sort of equivalent.  Being disabled unemployable, money is a big issue.  I both don't want another windoze machine, nor can I afford the $600 or more, for a new equivalent program to cakewalk.  The proprietary get the money stuff that exists, is for other people now. I do so wish I were more of a computer geek, able to write code and or even look at it, knowing what I was seeing!

Again thanks for the interest and tips.  I'll be getting back to it, that is for sure.. :) 
Regards

---

### Post by jejeman on 2013-01-02
Reading at your tasks, and also considering that you are cakewalk user, maybe MusE will be good choice for you, as MIDI + Audio Sequencer.

---

### Post by lykwydchykyn on 2013-01-03
I've found "Muse Score" to be a good program for notation.

---

### Post by de Bacon on 2013-01-03
> **lykwydchykyn said:**
> I've found "Muse Score" to be a good program for notation.

I am really glad to hear this.  I was quit of the thought that I might not find anything for that aspect of the need. 
Onward and upward! 

Thanks

---

### Post by AstroLlama on 2013-01-06
There are some great ardour tutorials online, check those out too!

I pay lots of attention to the notation editors and find that Muse Score definitely the best one, as far as linux boxes go!  :)

---

