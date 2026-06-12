---
title: "Music applications that rock"
date: 2009-02-24
forum: Ubuntu Studio
---

### Post by StephenOK on 2009-02-24
As a musician/composer I have two macs: A macbook pro core duo and a Quad G5. I bought these machines for running a variety of programs like Logic, Pro-Tools, Sibelius, Max/Msp, etc.
I'm curious to find applications in Linux that are really worth the time and effort to learn. 
I'd love to see Sibelius ported to Linux. It's bar-none, the best notation software out on the market - although you will find some really hard-core Finale users.
What I'm most interested in are programs that allow you to mess around with frequency modulation, granular synthesis, ring modulation, Physical modeling, etc.
Does anyone know of any programs like that? Of course, you can do this all in Max/Msp, but I'm sure there are some Linux programs that
have similar functions. 
Depending on your level of expertise in programming in Max, it could take quite some time to create a patch that you're happy with.

Thanks in advance for any thoughts,

Steve

---

### Post by Stochastic on 2009-02-24
Well, first, Pro Tools can be replaced with Ardour.
Logic, might be replaceable by Rosegarden (maybe even LMMS in newer versions), or maybe you should just wait until Ardour releases its 3.0 version with MIDI features.

Sibelius is a wonderful program and some people have been able to get it running in Wine.  But I prefer to code into Lilypond - there's a lot that you can do, but it has a steep learning curve.  Denemo is a nice GUI frontend for Lilypond.  There's also a new editor with syntax highlighting for Lilypond called Frescobaldi - but this requires compiling it from source.  Sadly no exact Sibelius replacement exists.

As for Max/MSP, I'm surprised that you've not hear about Pure Data.  Miller Puckette - the guy who started Max/MSP before Cycling '74 took it over - decided a long long time ago that the internal engine had some major issues, so he re-wrote it, put it out under a GPL license, and called it Pure Data.  There are two versions around, the standard, and the extended (includes a bunch of community-built objects) - most people prefer the extended version.  First, a quick warning that it's not a pretty as Max/MSP, but beyond that, it's a direct equivalent (some could argue that the internal engine improvements make it better).

But if you're into Max/MSP, then there's no reason to stop with Pure Data and call it a day, you should also look into Beast, SuperCollider, CSound, Chuck, and a number of other musical programming tools floating around.  Not a requirement, PD will get you by just fine, but why not?

Lastly, any musician on Ubuntu should not be without UbuntuStudio [http://www.ubuntustudio.org](http://www.ubuntustudio.org)  and anyone new to the game would probably gain from a read through of their community documentation [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

Hope that helps.  Welcome to the community, and have fun!

---

### Post by StephenOK on 2009-02-24
> **Stochastic said:**
> Well, first, Pro Tools can be replaced with Ardour.
Logic, might be replaceable by Rosegarden (maybe even LMMS in newer versions), or maybe you should just wait until Ardour releases its 3.0 version with MIDI features.

Sibelius is a wonderful program and some people have been able to get it running in Wine.  But I prefer to code into Lilypond - there's a lot that you can do, but it has a steep learning curve.  Denemo is a nice GUI frontend for Lilypond.  There's also a new editor with syntax highlighting for Lilypond called Frescobaldi - but this requires compiling it from source.  Sadly no exact Sibelius replacement exists.

As for Max/MSP, I'm surprised that you've not hear about Pure Data.  Miller Puckette - the guy who started Max/MSP before Cycling '74 took it over - decided a long long time ago that the internal engine had some major issues, so he re-wrote it, put it out under a GPL license, and called it Pure Data.  There are two versions around, the standard, and the extended (includes a bunch of community-built objects) - most people prefer the extended version.  First, a quick warning that it's not a pretty as Max/MSP, but beyond that, it's a direct equivalent (some could argue that the internal engine improvements make it better).

But if you're into Max/MSP, then there's no reason to stop with Pure Data and call it a day, you should also look into Beast, SuperCollider, CSound, Chuck, and a number of other musical programming tools floating around.  Not a requirement, PD will get you by just fine, but why not?

Lastly, any musician on Ubuntu should not be without UbuntuStudio [http://www.ubuntustudio.org](http://www.ubuntustudio.org)  and anyone new to the game would probably gain from a read through of their community documentation [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

Hope that helps.  Welcome to the community, and have fun!

Hey, Stochastic:

Thanks for all the information, man. Yeah, I would have figured Puckette would have come up with something. I used Csound for a few years, but now find it a bit anachronistic for my own needs.
I've checked out SuperCollider, but I have to get a bit better at the programming language before taking full advantage of it.
I know that I've heard of Pure Data before, so that's something that I'll have to check. I still haven't upgraded from Max/Msp version 4.6.2. The only difference that I've heard is that GUI is a bit better and the layout is a bit more intuitive. 
I'll have to look into Chuck and Beast, and, of course, Ubuntu Studio, as I've never heard of it before. With all the proprietary iLok b.s. with Pro-tools, I often become fed-up and find myself trying to create patches to fit my needs in Max, and I'm still really not that good at it.
Thanks again for all of your advice, and I look forward to checking out these softwares!

Best,

Steve

B.T.W.- Stochastic - you wouldn't happen to be a Xenakis fan, would you?

---

### Post by rbolio on 2009-02-24
Oh wow , i really had underestimated linux's power!.... so the question now  is..... is there a easy way to switch from ubuntu 8.10 to ubuntu studio (is it 8.10 aswell?) i mean i saw it on synaptic, but it can't be so simple....can it?

---

### Post by markbuntu on 2009-02-24
Yes, it is a simple as that. Just get the ubuntustudio audio packages with synaptic. It is a big download though and there is a lot to learn. Here are a few links for that

If you are having basic jack setup problems, or you just want to know where to start:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

If you are having trouble setting up jack in UbuntuStudio:

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

For basic sound troubleshooting and set up:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by StephenOK on 2009-02-24
> **markbuntu said:**
> Yes, it is a simple as that. Just get the ubuntustudio audio packages with synaptic. It is a big download though and there is a lot to learn. Here are a few links for that

If you are having basic jack setup problems, or you just want to know where to start:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

If you are having trouble setting up jack in UbuntuStudio:

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

If you are wondering how to sync applications together through jack:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

For basic sound troubleshooting and set up:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Awesome. Thanks for all the links. There may be a bit of a learning curve, but it can't be nearly as complicated as Logic, which took me a fair amount of time to learn. The title of the software doesn't seem appropriate. LOL But it's a very powerful tool for doing a variety of different types of Audio work.

Look forward to jumping into Ubuntu Studio tomorrow!

Thanks again,

Steve

---

### Post by trlkly on 2009-02-24
There's also a Linux program similar to Sibelius called MuseScore. The last time I checked, it wasn't quite up to snuff, but maybe it's gotten better. Just something you may want to try.

ETA: It's called mscore in your package manager. Newer versions are available at [https://launchpad.net/~mscore-ubuntu/+archive/ppa](https://launchpad.net/~mscore-ubuntu/+archive/ppa)

---

### Post by StephenOK on 2009-02-24
> **trlkly said:**
> There's also a Linux program similar to Sibelius called MuseScore. The last time I checked, it wasn't quite up to snuff, but maybe it's gotten better. Just something you may want to try.

ETA: It's called mscore in your package manager. Newer versions are available at [https://launchpad.net/~mscore-ubuntu/+archive/ppa](https://launchpad.net/~mscore-ubuntu/+archive/ppa)

Yeah, I've looked into Lilypond, too, after a couple of members mentioned it. I'm really at home with Sibelius and my Finale chops are pretty decent. But I've become a monster at Sibelius from doing a lot of copyist work and copying such composers as Ferneyhough and Finnissy into Sibelius. The former probably writes the most abstract, complicated scores on the planet. I can't believe the man does all of that in Finale! But its a great exercise to push your notational skills to the edge by copying such difficult scores into that program.
I know you can input a bunch of varying nested tuplets in Lilypond, but I'm looking forward to finding the extent to one  can notate new-complexity types of music into that program.
The Logic score feature isn't really that good for this; however,
the latest Pro-Tools release has Sibelius features integrated into its score editor, which is amazing for me.
Now I just have to fork over the cash to by another HDD for my Quad and install Leopard - which I'm not all too fond of - on the drive to run Pro-Tools.
I'm so fed-up with these companies and their proprietary fascism.
It's not that I'm against anyone making a good living, but Digidesign is off the wall. 
So, yeah, I'm really excited about checking out Ubuntu Studio and all these other cool software packages.
I'm so grateful that I've found Linux and found this forum. 

Thanks for all the info,

Steve

---

### Post by kayosiii on 2009-02-26
Ardour is well worth the effort. And will serve well depending on how Effect/Plugin/Softsynth driven your recording work is. I am a big fan of Freewheeling,Hydrogen, Rakarrak and ZynAddSubFX... and on the Utilities front I am quite fond of Patchage. 

I am not 100% happy with any of the midi editors out there... Rosegarden would suffice if it had automation and was a bit more stable. If Muse 2.0 was ever to get out the door it might do it for me. Or maybe Ardour 3.0 will be released first. Since I deal mostly with physical instruments  this hasn't bothered me a great deal.

---

### Post by StephenOK on 2009-02-26
> **kayosiii said:**
> Ardour is well worth the effort. And will serve well depending on how Effect/Plugin/Softsynth driven your recording work is. I am a big fan of Freewheeling,Hydrogen, Rakarrak and ZynAddSubFX... and on the Utilities front I am quite fond of Patchage. 

I am not 100% happy with any of the midi editors out there... Rosegarden would suffice if it had automation and was a bit more stable. If Muse 2.0 was ever to get out the door it might do it for me. Or maybe Ardour 3.0 will be released first. Since I deal mostly with physical instruments  this hasn't bothered me a great deal.

My electroacoustic stuff is pretty driven by various plug-ins, patches and D.A.E. However, Ardour looks too good to pass up on. The fact that it has automation is really helpful, too.

Thanks for passing this on,

Steve

---

### Post by osterchrisi on 2009-02-28
Hey guys and girls,

seems like some of you really know of what they are speaking ;) So I have a question: I also want to make my Linux PC a small DAW and I have a lot of experiences on Windows and Mac. I already know all the programs, you're talking about here.

Fact is, I discovered Ubuntu Studio to exist AFTER I already installed Jack, the RT-Kernel, Ardour, Rosegarden, PD, ...
So where's the difference between Ubuntu Studio and installing the (audio-)packages of your need manually to your system?

I just don't want to 'overload' my system with any stuff I don't need, but I also don't want to miss something useful, so here's my question:
Shall I install Ubuntu Studio now, although I already have a nice working setup set up on my machine?

Thanks!

---

### Post by thorgal on 2009-02-28
> **osterchrisi said:**
> 
So where's the difference between Ubuntu Studio and installing the (audio-)packages of your need manually to your system?

none, except for the time invested :)

> **osterchrisi said:**
> 
I just don't want to 'overload' my system with any stuff I don't need, but I also don't want to miss something useful, so here's my question:
Shall I install Ubuntu Studio now, although I already have a nice working setup set up on my machine?

Thanks!

if it's working nicely, why do you need to change it ? :D
to be frank, if you are at that level of control of your DAW, just keep on maintaining it this way. That's what I also do with my debian sid based DAW.

---

### Post by StephenOK on 2009-03-01
> **osterchrisi said:**
> Hey guys and girls,

seems like some of you really know of what they are speaking ;) So I have a question: I also want to make my Linux PC a small DAW and I have a lot of experiences on Windows and Mac. I already know all the programs, you're talking about here.

Fact is, I discovered Ubuntu Studio to exist AFTER I already installed Jack, the RT-Kernel, Ardour, Rosegarden, PD, ...
So where's the difference between Ubuntu Studio and installing the (audio-)packages of your need manually to your system?

I just don't want to 'overload' my system with any stuff I don't need, but I also don't want to miss something useful, so here's my question:
Shall I install Ubuntu Studio now, although I already have a nice working setup set up on my machine?

Thanks!

Did you install and start tinkering with U.S. yet? If so, what are your thoughts. I've been too damn busy fixing PC's and teaching instrumental lessons to install the software yet. I have downloaded it and burnt it to a DVD .iso. I'll probably get to it sometime today.
Just curious to hear your thoughts.

---

### Post by rookworm on 2009-03-06
I have installed Ubuntu-Studio, and I can't seem to find packages for PD-extended or Supercollider......  are these in the works, or do i have to do all the work myself?

---

### Post by skullmunky on 2009-03-07
> **rookworm said:**
> I have installed Ubuntu-Studio, and I can't seem to find packages for PD-extended or Supercollider......  are these in the works, or do i have to do all the work myself?

For Pd-extended, go to [http://www.pure-data.info/downloads]("http://www.pure-data.info/downloads")

You can just download the package and double-click to install, or follow the instructions to add a repository for it.

For SuperCollider, apparently you can get packages here:

[http://artfwo.blogspot.com/2008/05/supercollider-for-human-beings.html]("http://artfwo.blogspot.com/2008/05/supercollider-for-human-beings.html")

which I got to from [http://supercollider.sourceforge.net//]("http://supercollider.sourceforge.net//")

enjoy!

---

