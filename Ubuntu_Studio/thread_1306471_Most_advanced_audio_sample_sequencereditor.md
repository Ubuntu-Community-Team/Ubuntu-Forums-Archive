---
title: "Most advanced audio sample sequencer/editor"
date: 2009-10-30
forum: Ubuntu Studio
---

### Post by IB1Dance on 2009-10-30
Hi,

As the title suggests I'm looking for the Most advanced audio sample sequencer/editor for my particular way of making music on a computer.

I like to use pre-recorded samples of real instruments mostly percussive instruments.

So which Linux program can play/sequence many different audio samples in the most organised way?.

I know of the DAW's that use Audio tracks like Ardour, but wouldn't it get confusing with many short drum samples.Or does Ardour have a simple way to organise them?.
I've used Hydrogen which is Good but lacking some of the basic features I'd like.

The main features I'd like in order of importance are;-

1. Sequence many audio samples in a efficient organised way.

2. Edit Audio samples non destructively preferably whilst the music plays.

3. Add Effects to a individual sample/groups or Globally .

4. Piano roll so as to accurately alter the pitch of any sample whilst playing the music.

Any suggestions which program could do the above in the most productive and well organised way .

---

### Post by mr.thraz on 2009-10-30
your looking for hydrogen2

---

### Post by IB1Dance on 2009-11-02
> **mr.thraz said:**
> your looking for hydrogen2

OK if that's the case where do I find hydrogen2?

---

### Post by mr.thraz on 2009-11-02
you can find out all about it [here]("http://www.hydrogen-music.org/")


you can dl it in the repos. or get a deb at getdeb.org.

hydrogen has plenty of drum kits at its sorceforge page.

you'll wanna dl freecycle to cut your samples for it, 
otherwise you'll need to use audacity.


hope this helps.

---

### Post by AutoStatic on 2009-11-02
You could also try [LMMS]("http://lmms.sourceforge.net").

---

### Post by IB1Dance on 2009-11-02
> **mr.thraz said:**
> you can find out all about it [here]("http://www.hydrogen-music.org/")


you can dl it in the repos. or get a deb at getdeb.org.

hydrogen has plenty of drum kits at its sorceforge page.

you'll wanna dl freecycle to cut your samples for it, 
otherwise you'll need to use audacity.


hope this helps.

That is Hydrogen 0.9.4 (stable) & I have installed & use  0.9.5-svn1411 -fx-edition, which has some nice features like piano roll and a non destructive editor but is still in a very early stage of development.In fact it's having 'saving' bugs with this program that has led me onto wanting to find a alternative .

You wrote Hydrogen2 ? or was that just a little lead to get me to search thus find your helpful video's ;) ? .

Anyway Hydrogen 0.9.4 is a fine drum machine but hasn't got much advanced audio editing ability yet, which is a shame because out of all the programs I've tried I prefer Hydrogen's simple way of structured pattern editors to organise drum samples.

---

### Post by IB1Dance on 2009-11-02
> **AutoStatic said:**
> You could also try [LMMS]("http://lmms.sourceforge.net").

Thanks I've tried that and though Again a fine looking program it's not got many features when it comes to 'samples' .

---

### Post by mr.thraz on 2009-11-02
hi i just dont feel like writing this.

[http://www.youtube.com/watch?v=_9Hgt5Y5550]("http://www.youtube.com/watch?v=_9Hgt5Y5550")

---

### Post by bear24rw on 2009-11-02
you can also try out audacity

$ sudo apt-get install audacity

---

### Post by mr.thraz on 2009-11-03
what is he going to do with audacity?

he said he needs a piano roll and sequencer.

what he needs is to connect rosegarden together with hydrogen via jack.


if not that, then he'll need to buy energyxt, or install wine and work with windows daws + vsts/vsti's.

---

### Post by paulmerchant on 2009-11-03
You might want to look at Renoise. I currently use Renoise to do exactly what you are looking to do. The license is reasonable, the free version can do almost everything you need, and it has a strong community.

Renoise currently doesn't have a piano roll, but the tracker interface is quite fun once you spend some time with it. Everything else, like the sampling and effect routing, is intuitive and almost exactly as you described in your post.

---

### Post by IB1Dance on 2009-11-03
> **mr.thraz said:**
> w


what he needs is to connect rosegarden together with hydrogen via jack.


if not that, then he'll need to buy energyxt, or install wine and work with windows daws + vsts/vsti's.

I will take a good look at rosegarden. But still their seems to be a shortage on linux for being able to do much real time editing of samples as they are playing within a track/song.

Hydrogen is great for playing lots of short audio clips ( drums ) and being able to organise them without using loads of power.
When or if the hydrogen Fx edition ever gets to be stable or it's features are merged onto the stable release it will have most of the features I need.But Hydrogens development is frustratingly slow.

THe only other program that I have tried that fits what I want and does it in a clear enough way is windows Ableton Live .I've just tried to give this a test run with wine but I keep getting a blank configuration window in Ableton.

Anyway don't get me wrong, using Hydrogen as I do now and pre-editing Audio samples using Rezound does give me plenty of editing variation.

But to be able to simply sequence lots of short audio clips and have 'real time'  editing of them whilst the music plays, is the next best thing for 'feeling the music' as actually playing the drums my self.

---

### Post by IB1Dance on 2009-11-03
> **paulmerchant said:**
> You might want to look at Renoise. I currently use Renoise to do exactly what you are looking to do. The license is reasonable, the free version can do almost everything you need, and it has a strong community.

Renoise currently doesn't have a piano roll, but the tracker interface is quite fun once you spend some time with it. Everything else, like the sampling and effect routing, is intuitive and almost exactly as you described in your post.

I think this program as more features than I need. I've used a similar tracker like prog before.I'm not that keen on that style of organising the music.
For me the less I have to stare at the screen to get the music produced the better for me and my eyes.

---

### Post by VertexPusher on 2009-11-04
If you don't like Rosegarden, take a look at Qtractor. It's in the repositories, too.

---

### Post by IB1Dance on 2009-11-04
> **VertexPusher said:**
> If you don't like Rosegarden, take a look at Qtractor. It's in the repositories, too.

Just had a little play with Qtractor 0.4.2 & I'm liking it.

So far I've only added a few samples which it plays & edits well .

(What is missing though is being able to 'pitch shift' the wave samples as the music is playing.

& besides do I really want to use Alpha software with little documentation and possible loss of work just like I had with hydrogen?.

---

### Post by VertexPusher on 2009-11-04
> **IB1Dance said:**
> What is missing though is being able to pre-listen to samples before loading them up & editing the samples 'pitch shift' etc as the music is playing.
The Qtractor project page lists this feature:

*Audio clip time-stretching (WSOLA-like or via librubberband), pitch-shifting (via librubberband) and seamless sample-rate conversion (via libsamplerate).*

> & besides do I really want to use Alpha software with little documentation and possible loss of work just like I had with hydrogen?.
Yes, because it's the only way to have a free lunch. Keep in mind that if no one uses the program, it may remain alpha forever and never get the features that you want. Low version numbers don't necessarily mean that the software is unstable, only that some planned features have not yet been implemented.

---

### Post by IB1Dance on 2009-11-04
> **VertexPusher said:**
> The Qtractor project page lists this feature:

*Audio clip time-stretching (WSOLA-like or via librubberband), pitch-shifting (via librubberband) and seamless sample-rate conversion (via libsamplerate).*

Yes and they work fine though not in real time.I.E - you set the parameters press ok and then the clip is changed.It would be nice to pitch shift like in hydrogen, for example as the music is playing so as to match your editing exactly with the music.




> **VertexPusher said:**
> Yes, because it's the only way to have a free lunch. Keep in mind that if no one uses the program, it may remain alpha forever and never get the features that you want. Low version numbers don't necessarily mean that the software is unstable, only that some planned features have not yet been implemented.

A fair point and I may use this software if it's stable enough to make music with.

---

### Post by IB1Dance on 2009-11-05
Just to bring this thread to some kind of conclusion I think I've found the program for me.

[http://qtractor.sourceforge.net/qtractor-index.htm](http://qtractor.sourceforge.net/qtractor-index.htm)

If you like using samples,mix & matching beats,stretching boundaries as well as loops, qtractor has many tools to make music making on a PC almost...?well.....? ok it's still allot of sitting on your *** but because of it's ease of use less time sitting and more time moving to the sounds I make.

And because you can load up plug-in synths like Fluid Synth soundfont player,edit them in a piano roll,this neat program is quite capable of an entire production. :D

---

### Post by AutoStatic on 2009-11-05
Personally I really like Qtractor. And little documentation? [http://downloads.sourceforge.net/qtractor/qtractor-0.3.0-user-manual.pdf](http://downloads.sourceforge.net/qtractor/qtractor-0.3.0-user-manual.pdf)

Ok, lots of features were added after the 0.3.0 release but the manual is a good starting point. Unfortunately 0.4.3 came too late to be included in Karmic. But if I have time I'll build some 9.10 debs.

---

### Post by IB1Dance on 2009-11-06
> **AutoStatic said:**
> But if I have time I'll build some 9.10 debs.

I'm just reading up on how to compile and install 0.4.3.

compiling on ubuntu [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

It would be very helpful having the 0.4.3 in debs as allow people to check qtractor out quickly and easily.

And it's certainly nice having a half decent manual.Let hope the manual can keep up to speed with the program.

---

### Post by Stochastic on 2009-11-06
Hmm, most advanced audio sample sequencer/editor?

ChucK  [http://chuck.cs.princeton.edu/](http://chuck.cs.princeton.edu/)
or
SuperCollider  [http://supercollider.sourceforge.net/](http://supercollider.sourceforge.net/)

Though it sounds like you want something a little more structured and 'out-of-the-box'.

---

### Post by IB1Dance on 2009-11-07
> **Stochastic said:**
> 

Though it sounds like you want something a little more structured and 'out-of-the-box'.

Well yes and well not really.True I want a well structured sequencer so as to keep track of the audio samples I use.
But I can't get a more 'out of the box' sound or variation,fluidness I.e - humanness than the sound that real instruments produce.

Sound has a infinite, not random structure & Audio software can reproduce these sounds using random variables.
But these seemingly random variables are not truly random or chaotic ( chance ).Naturally occurring sound in the world or real instruments being played , just like sound produced on a PC have parameters or laws (code) that govern how it sounds.no system could be developed or indeed evolve with pure chance for then chaos would prevail and who'd use some Audio software called 'Chaos' you'd forever be trying to find a file.

Sound is shapes/patterns/vibration/rhythms and these processors ( that are all 1) are the building blocks of existence.

So keeping this in mind the software I am looking for to suit my own particular circumstances is a package that can allow me to sequence the 'seemingly' complexities of music production so as simplify music and let it be heard for all it actually is sound/vibration/rhythm etc etc etc.
Just as life is extremely varied and complex yet can be broken down layer by layer revealing it's roots or building blocks .I.E - D.N.A - until what is revealed is the more complex system must be simple in order to achieve such variation without breaking down.

So while I do like to use software that Evolves whilst also using software that has direction and vision.This way any improvements do not come about by mere chance but by a organised system that enables the most 'Adaptable' features to survive.
Using this model it can be seen that eventually something will come about that will surpass all that came before.
Call it 'self realisation' , call it good programming,call it anything but divine intervention.

I call it Dancing in this 'your rhythm of life'.

So essentially I want a Audio program that allows me to make the kind of music in a synthetic way, that one day I will have the means to do in a more natural or a way in which I have evolved to do.

I want to play Drums,instruments,music and dance in a Society that is founded on It's Rhythm for then it will be a community at peace & harmony with it's natural 'self'. :D

Having said all that qtractor is a very nice program indeed .

You won't know it until you try it out for yourself.

---

### Post by Stochastic on 2009-11-07
> **IB1Dance said:**
> So essentially I want a Audio program that allows me to make the kind of music in a synthetic way, that one day I will have the means to do in a more natural or a way in which I have evolved to do.

I want to play Drums,instruments,music and dance in a Society that is founded on It's Rhythm for then it will be a community at peace & harmony with it's natural 'self'. :D

Having said all that qtractor is a very nice program indeed .

Sounds like you should use any one of the following (maybe more than one):
Qtractor
MusE
Renoise
LMMS
Hydrogen (if you start editing the samples in the drum editor and saving your kit afterward, you can use it for more than just drums - this can be tedious)

You might also find these fun:
Sooper Looper
Freewheeling (sorta hard to learn this one)
Mixxx
Freebirth
MuSe

Hope that helps. :D

---

### Post by IB1Dance on 2009-11-08
> **Stochastic said:**
> 
Hydrogen (if you start editing the samples in the drum editor and saving your kit afterward, you can use it for more than just drums - this can be tedious)


Hope that helps. :D

Besides using rezound for pre-editing & jamin for mastering the track available via the below link was entirely made with hydrogen.

In fact I have entitled it 'Shaping sound (evolved using hydrogen drum machine) to give hydrogen much needed promotion.

[http://www.sectionz.com/detail.asp?rType=mp3&SZID=30044]("http://www.sectionz.com/detail.asp?rType=mp3&SZID=30044")

---

### Post by Cool Surfer on 2009-11-10
> **IB1Dance said:**
> Just to bring this thread to some kind of conclusion I think I've found the program for me.

[http://qtractor.sourceforge.net/qtractor-index.htm](http://qtractor.sourceforge.net/qtractor-index.htm)

If you like using samples,mix & matching beats,stretching boundaries as well as loops, qtractor has many tools to make music making on a PC almost...?well.....? ok it's still allot of sitting on your *** but because of it's ease of use less time sitting and more time moving to the sounds I make.

And because you can load up plug-in synths like Fluid Synth soundfont player,edit them in a piano roll,this neat program is quite capable of an entire production. :D


Thanks for this info....

---

