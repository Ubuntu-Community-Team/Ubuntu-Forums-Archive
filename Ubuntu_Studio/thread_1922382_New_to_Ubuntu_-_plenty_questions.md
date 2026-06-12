---
title: "New to Ubuntu - plenty questions"
date: 2012-02-08
forum: Ubuntu Studio
---

### Post by Noobuntu79 on 2012-02-08
Ok so here's the deal.  I've started using Ubuntu literally today after many years of limited Vista adequacy and I'd like to link up my happy hardware family of Edirol PCR300 and Edirol FA66.  

I've installed the Qjack audio server and I've read in many places that things will 'just work' in this environment.  After a few hours of headscratching, post reading, video watching, I've finally got the PCR talking to AMsynth via Jack and lots of pretty noises are coming from the laptop's own soundcard.  Smashing!!  

As for the FA66, it has no idea what one of those is even though a few pages I've read suggest it's one of the squillions of firewire soundcards in the Jackd library.  About the best I've managed to do whilst trying to configure a firewire output is to crash Jack.

I'm kinda digressing though, you see with all this connecting and not-connecting going on I've now discovered something quite annoying - once I start/stop using Jack, Ubuntu wont allow me to play media of any format.  Banshee will not play audio, audio from Soundcloud will not play, video files wont play, Youtube videos have no sound....  Something to do with Jack seems to be upsetting simple media playback whenever I've tried using Jack.

Is this a known problem?  I've hunted around but haven't found anyone else experiencing it or any insight as to why this might happen.  It'd be great if I could just connect every last bit of multimedia through Jack once it's running (which I thought I might be able to do especially once the FA66 is running) but this doesn't seem to be the case......yet......

Many thanks in advance for your help & patience,

Steve

---

### Post by jejeman on 2012-02-09
Forums work best If you ask one question at the time.

I use Edirol FA-66, in my studio, with out problems on Ubuntu Studio 10.04. I can say that it gives really steady performance.

Did you install plain Ubuntu or Ubuntu Studio?
Do you have ffado drivers installed?

---

### Post by Noobuntu79 on 2012-02-09
Hi thanks for the reply...  After posting I've done a little more reading and as it happens I just have Ubuntu desktop - I first thought Studio was just an app rather than a separate instance entirely of Ubuntu...  I have ffado, and here are the first few lines of ffado-diag...

=== CHECK ===
 Base system...
  kernel version............ 3.0.0-15-generic
  old 1394 stack present.... False
  old 1394 stack loaded..... False
  old 1394 stack active..... False
  new 1394 stack present.... True
  new 1394 stack loaded..... True
  new 1394 stack active..... True
  /dev/raw1394 node present. False
 Prerequisites (dynamic at run-time)...
   gcc ............... gcc (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1
   g++ ............... sh: g++: not found
   PyQt4 (by pyuic4) . sh: pyuic4: not found
   jackd ............. no message buffer overruns
     path ............ /usr/bin/jackd
     flags ........... Package jack was not found in the pkg-config search path.

...so the first issue seems to me that I have the 'new stack' and no legacy, which from what I've been reading I don't think I'm the first person to have had this, though I'm uncomfortable with knowing what to do about it due to my noob-ness, and am massively in need of some authoritative guide on rectification.

The second issue that jumps out at me from ffado-diag is the last few lines:
  g++ not found,
  pyuic4 not found,
  package jack not found...

Is this something wrong with my Jack configuration?


Thanks again for your reply,

Steve

---

### Post by jejeman on 2012-02-09
I have never tried this soundcard on the new firewire stack. So I don't now does/how it works. Well, I vaguely remember I tried it on 10.10 which was the first version to introduce new stack, and it didn't work, so I installed old stack. As far as I know, this is not possible with 3.x kernels.
> g++ not found,
pyuic4 not found,This is not important.> package jack not found...

Is this something wrong with my Jack configuration?I don't know about this. You probably did install jack.
Because you didn't install ubuntu studio you need to do this steps
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
you don't need to do, all just the Real-time Support.

If you can install ubuntu studio 10.04, it's, at the moment, best choice for audio production.

---

### Post by Noobuntu79 on 2012-02-10
Cool, so I haven't put Studio on my lappy yet as I have some clearing out to do before I'm prepared to commit to it, but I've tried it out on my desktop dual-booting with XP....

So far so good - Jack talks to my Delta 1010 card with no hiccups although it names all the IO in a surround capacity (left-centre, right-centre, left-rear, right-rear etc.) which isn't an issue really, I just have to translate that into the simple 1,2,3,4.... that I'm familiar with.

As for linking up the PCR300 controller, it wont let me patch any connections to any software in Jack like I was able to using U-11.10 on my lappy, but there might just be something simple in the setup I've overlooked.

My next step is to get the PCR talking to my MicroKorg via the Delta 1010 MIDI, and be able to audition/record it's output via the soundcard....

Once that is all done, I reckon I should be 100% fluent with Jack patching :)

Thanks for the help dude

---

### Post by cfhowlett on 2012-02-11
Jack prioritizes audio handling.  It SHOULD release audio once it's shut down.  Then audio can be piped into other apps.

---

