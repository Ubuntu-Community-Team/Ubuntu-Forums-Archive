---
title: "Rakarrack: using sound effects?"
date: 2009-09-12
forum: Ubuntu Studio
---

### Post by billdotson on 2009-09-12
I have a strange issue where jack won't run without super user privileges so I have to run it and rakarrack as as super user. I connect the line in to the rakarrack in with jackd "connect" window but when I have FX on it doesn't sound any different than it normally would. Now if I go and manually connect rakarrack out 1 to system playback 1 I get the most awful sounds you've ever heard. The sound is different for each effect but they all are just a bunch of very loud interference. I was doing it and launched audacity to try and record the sound to post here but then the sound stopped, jackd crashed and now rakarrack is sitting here on the desktop but it isn't shown in the system monitor as running (and it won't close or be interacted with in any way). Any idea what is going on?

---

### Post by transmogrifox on 2009-09-27
It would be useful to know the following:
What is your sound card?
What is your computer, and what's RAM, CPU and hardware type.  
How is Jackd configured?
 --sample rate
 --buffer size
 --frames per buffer
 --latency
 --what sound card device name is used for input device, output device?
 --are you trying to use different sound cards for inputs and output?

Do other jack applications work properly?  

This can be a problem with your jackd configuration or maybe it's a bug in the current build of rakarrack distributed by Ubuntu.

As for running as root, go here 
[http://jackaudio.org/faq](http://jackaudio.org/faq)

and follow the instructions.  Add your username to group audio:
sudo adduser myusername:audio

If you aren't using qjackctl or patchage to make your jack connections, I highly recommend it.

Make sure you aren't creating a feedback loop or anything like that.  

First, start jackd (don't open rakarrack or any other jack application until after jackd is running).

Connect the output of rakarrack to your system sound card output.  Is there a problem.

Connect the system capture to rakarrack input(s).  Problem now?

If it goes out of control, then connect the input of rakarrack first and see if the volume meter bars are showing noise for both input and output, or only one.  

If there's no noise on the input bar for rakarrack, but noise coming out, then it might be a rakarrack problem.  If there's something happening on both input and output bars, then the problem is likely external.

I'm making a stab in the dark from your description that your problem is related to jack configuration.  Try some different  configuration settings and make sure jackd is running without excessing Xruns before connecting anything.

I hope that gives you some ideas.

---

### Post by kayosiii on 2009-09-27
> **billdotson said:**
> I have a strange issue where jack won't run without super user privileges so I have to run it and rakarrack as as super user.

Yeah the default Ubuntu config for jack control is broken. you need to either configure jack control to not use realtime or you need to configure your system to allow your audio programs realtime access. 
search this forum for /etc/security/limits.conf for details on how to do that. (or purhaps you can install the ubuntustudio-controls package and get it to configure things for you.

>  I connect the line in to the rakarrack in with jackd "connect" window but when I have FX on it doesn't sound any different than it normally would. Now if I go and manually connect rakarrack out 1 to system playback 1 I get the most awful sounds you've ever heard. The sound is different for each effect but they all are just a bunch of very loud interference. I was doing it and launched audacity to try and record the sound to post here but then the sound stopped, jackd crashed and now rakarrack is sitting here on the desktop but it isn't shown in the system monitor as running (and it won't close or be interacted with in any way). Any idea what is going on?

yes the effects in Rakarrack are quite noisy... You really need to be mindful of your gain levels (set the input and output gains down by default). If you haven't already and install patchage (it makes patching between applications much easier). Connect your inputs and your outputs
set the input gain and output gain down quite low, select an preset and turn effects on. Now adjust the gain up to the required level... This is just like you should do with real world audio equipment (maybe too realistic perhaps)...

Probably forget trying to use Audacity to record at the moment purhaps - it's support for jack is not exactly stellar. Install time-machine and wire it to rakarracks outputs. Time Machine has a very simple interface (just a big record button really). It will create wave64 files in your home folder that Audacity will be able to open. The files will start with the letters tm and will be timestamped.

---

### Post by kayosiii on 2009-09-27
It as also worth noting that rakarrack is designed as a guitar fx rack and most of the presets do contain a fair amount of distortion. Using it with other types of signal might require some tweaking - however if are getting horrible noises from something like "soft stereo" then you have a problem.

---

### Post by raboofje on 2009-09-28
> **billdotson said:**
> I have a strange issue where jack won't run without super user privileges

[quote=transmogrifox]As for running as root, go here [http://jackaudio.org/faq](http://jackaudio.org/faq) and follow the instructions.[/quote]

[quote=kayosiii]you need to configure your system to allow your audio programs realtime access. search this forum for /etc/security/limits.conf for details on how to do that. (or purhaps you can install the ubuntustudio-controls package and get it to configure things for you.[/quote]

.. and/or see [http://trac.jackaudio.org/wiki/Troubleshooting](http://trac.jackaudio.org/wiki/Troubleshooting)

---

### Post by billdotson on 2009-10-10
Yeah all of the plugins for rakarrack make these awful noises when turned on. I built rakarrack from the source code and jackd was installed via synaptic.

I am getting really frustrated dealing with sound issues as there are so many different subsystems (ALSA, OSS, etc.) to deal with.

---

### Post by transmogrifox on 2009-10-12
> **billdotson said:**
> Yeah all of the plugins for rakarrack make these awful noises when turned on. I built rakarrack from the source code and jackd was installed via synaptic.

I am getting really frustrated dealing with sound issues as there are so many different subsystems (ALSA, OSS, etc.) to deal with.

I understand the frustration.  I have found that qjackctl really simplifies things.  It's like having a graphical tutorial of jackd. If your sound usually works fine without jackd, then you can pretend the underlying systems are just a "driver" that you don't have to think about.

I'm a debian user, so I'm uncertain whether there's a bug in Ubuntu's current version of jack, or if this is unique to your hardware/software configuration.  For me Rakarrack works wonderfully well, and does not produce unwelcome noise.  The presence of noise indicates a problem with jack configuration in some way.  Are you sure you haven't inadvertently routed a rakarrack output into the input to create a feedback loop?  This kind of thing can certainly ruin your day.  This type of behavior may even be hidden in the form of the devices you selected for input and output channels.  If you selected the same thing for input and output, then you made a feedback loop with Jack.  Have you tried other applications under jack that process input and output...for instance, jack-rack, or guitarix?

I recommend getting source from current CVS.  It's a little frustrating at first when trying to compile CVS source, but it will keep you on the leading edge of features and bug fixes for Rakarrack. When I was using 0.3.0, I did not have any noise issues, however.  MIDI implementation and chord/note recognition has seen some vast improvement in recent CVS, so it will be worth your while if either of those features interest you.

---

