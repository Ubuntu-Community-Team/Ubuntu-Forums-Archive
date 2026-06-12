---
title: "Recording a band help"
date: 2008-05-21
forum: Ubuntu Studio
---

### Post by amazedd on 2008-05-21
Hey im new to ubuntu studio figured i give it a try
here is my problem
1. which is the best to record with (ive used garage band from mac) and i dont see any choices like guitar bass vocals
2. lowjack is that ran through line in?
3. any additional help

---

### Post by amazedd on 2008-05-21
ive just found 

[http://www.jokosher.org/](http://www.jokosher.org/)

hows the sound quality

---

### Post by Drunky on 2008-05-21
1.  Jokosher may not be that stable.  It's been awhile since I've delved into it though.  If you like Jokosher then you will like...

Audacity.  It is very simple to use, but not that feature rich when compared to...

Ardour2.  Ardour2 is comparable to Pro Tools on some facets.  While it is very feature rich, it also includes a rather step learning curve.  Good news is there are tutorials available.

2.  Lowjack?  I've never heard of it, maybe I'm missing something good.

3. Google 'linux music' and learn how to use Jack.  [https://help.ubuntu.com/community/HowToQjackCtlConnections]("This is a good place to start for Jack.")

---

### Post by Stochastic on 2008-05-22
If you're recording a band, I'd highly recommend Ardour2 as it is designed for professional multi-track recording, so you'll be able to get the vocals on one track, guitar on another, mandolin on another, erhu on another still etc...  There are other multi-track apps out there, but Ardour is much much stronger.

[http://www.ardour.org](http://www.ardour.org)
[Detail heavy official manual](http://ardour.org/files/manual/index.html)
[Beginner friendly tutorial](http://www.out-of-order.ca/tutorials/ardour/)

---

### Post by amazedd on 2008-05-22
thanks and yeah i ment jack not lowjack ha
low latency ima dummy.

dumb question ive been trying to get jack to work all night with just a headset mic.

can you not use jack through your line-in / mic port?

if so i could post my hardware and could you possibly help me

---

### Post by amazedd on 2008-05-22
ook well i got it to record.
but i dont see much mixing options in ardour

---

### Post by Stochastic on 2008-05-22
Hit alt+m and you'll see your mixing board.  There's also the volume level automation for each track in the main window.  Take a look through the Beginner's Tutorial link I gave before and you should quickly see the main features of ardour.

---

### Post by thorgal on 2008-05-22
"I don't see much mixing options in ardour" ... oh my! newbies' candor is always refreshing :lol:
Actually, I will keep this statement as the best quote of the week :lolflag:

---

### Post by Stochastic on 2008-05-22
Actually I recently started a new audio production job and some of my co-workers claimed they had tried ardour (all on windoze or mac systems) but didn't see anything special in it.  I think everyone forgets to mention the LADSPA plugins when talking about ardour - these may be what amazedd means by "mixing options" as adding the plugins aren't immediately obvious to those used to other interfaces.

---

### Post by Drunky on 2008-05-22
> **amazedd said:**
> ook well i got it to record.
but i dont see much mixing options in ardour

While this is really your next step, you should also look into JAMin.  Quoted from it's website ... [http://jamin.sourceforge.net/en/about.html](http://jamin.sourceforge.net/en/about.html)

> JAMin is the JACK Audio Connection Kit (JACK) Audio Mastering interface. JAMin is an open source application designed to perform professional audio mastering of stereo input streams. It uses LADSPA for digital signal processing (DSP). JAMin is licensed under the GPL.

---

### Post by amazedd on 2008-05-22
ha yes that is more what i was looking for.
man im starting to think its worth the 25$+ an hour to get someone to do it
or i need to watch someone do it first

---

### Post by zettberlin on 2008-05-22
> **amazedd said:**
>  ...im starting to think its worth the 25$+ ... 

Stay cool ;-) no need to touch any money just to learn how Ardour works for you ;-)

The Ardour people learned how to make an interface that just works for starters and still can do much much more if you are ready to lern a bit.

3 simple rules to start with Ardour:

1: The most important Tools besides the main editor-window are to be found in "Windows" (upper right end of the Menu) it holds the Mixer and Track/Bus Inspector - the Connections Tool. Both are the most important parts of the GUI.

2: All FX is made by plugins (LADSPA for now) right-click in the head or bottom of the mixerstrip to insert some.

3: Use the right-click - many functions hide behind it.

Plus: save often, save early - Ardour is a big beast, though its performance and stability has been hugely improved, it still can bring your machine to its knees. Being somewhat carefull  wont hurt ;-)

good luck :-)

---

### Post by robeast on 2008-05-23
Check out the guide in my sig for a description of most of the interface elements in Ardour. It's actually a quick glaze over a bunch of apps meant to give people a look into what Linux Audio has to offer.

---

### Post by warbread on 2008-05-23
> **amazedd said:**
> ha yes that is more what i was looking for.
man im starting to think its worth the 25$+ an hour to get someone to do it
or i need to watch someone do it first

And if you want quality recordings, you **will** end up spending money. 

Apprenticing someone isn't a bad idea, and if there are any studios in your area, I suggest you go watch them work, if they let you.  They probably won't be using any Linux apps, but there is more to recording than the software you use.  Learning to configure Jackd, work Ardour and use LADSPA plugins are all easy compared to everything you need to learn about outside of the computer.  Mic placement, acoustical treatment, eqing... there's a lot to recording that transcends computer platforms.

That said, once you get the basics of getting the software running down, learning the rest is not only easy and natural, but a lot of fun!  So, be patient with yourself and your software.  While you really don't *need* to spend any money to learn this stuff, I have a couple of suggestions.  For one, I suggest you get a decent sound card.  I love the [M-Audio Delta 24/96]("http://www.musiciansfriend.com/product/MAudio-Audiophile-2496-PCI-Digital-Audio-Card?sku=701341").  It's got the quality I need for a low price and it works beautifully in Jack.  Second, I recommend getting a small hardware mixer.  I started with an [Alesis Multimix 8]("http://www.musiciansfriend.com/product/Alesis-MultiMix-8USB-Mixer-with-USB-and-DSP?sku=630166").  The USB works, but it's not too useful.  Still, it's cheap and it gets the job done.  That will get nice stereo sound into your computer for under $300.  

Another option is a USB interface, which I haven't tried.  This [M-Audio USB interface]("http://www.guitarcenter.com/M-Audio-MobilePre-USB--No-Software--102212776-i1154077.gc") works in Linux out of the box, from what I've read.  At about half the price of the above suggestion, I'd say that's a good way to go for small recordings.  Still, it would be very difficult to record a whole band playing without a separate mixer.  

As long as you can record something, you have what you need already. As with all other projects, though, better tools makes doing what you want to do easier.  Take your time, decide what it is you want to do and for how long, and plan accordingly.

 Just don't plug any guitar amps strait into your computer/mixer and you'll do fine.

---

