---
title: "Can't take much more! CPU Maxxed?"
date: 2010-07-14
forum: Ubuntu Studio
---

### Post by decomp on 2010-07-14
I'm using my computer as effects processor for guitar and as a drum machine. But it seems I require too much CPU power of my little machine. Is it the CPU? The sound card? 

I use a usb preamp to connect my guitar. Then, open rakarrack + jackrack and I'm running at 90% cpu. anything more and programs crash and jack stops. rt kernel or no. But I want to use rakarrack + jackrack + Jamin + Hydrogen.  

I have a sony vaio with a 1.5 g pentium m processor. sound card appears to be intel AC'97. Laptop is from 2005.

I'm using lxde as DE, with mist gtk theme.. close all other programs.. not sure how to shave anymore CPU power off. Am I at the limits of what my little lappy can do? what about logging into a more minimal session that only loads openbox and jack? would it make a difference?

---

### Post by GhostofJohnToad on 2010-07-14
No solution here but I can share in your misery.  I am having major issues with rakarrack.  I am using 0.5.8 in Lucid. Rakarrack tanks my cpu and I get xruns in the 1000s.  It seems to be worse with certain banks.  Maybe certain effects are hogging everything, I don't know.  

This happens if I use my usb audio card or the laptop's internal one.  Jack is working fine with everything else and I don't get xruns except with rakarrack.  Maybe a problem with laptops, I'm clueless but I'm in the same boat as you decomp. I don't think it's an issue of with your DE though.

---

### Post by answer-b on 2010-07-14
:popcorn: relax guys, share my popcorn:)

I am green to ubuntu studio, but slightly more familiar with other stuff.

I have tried 3 different versions:-

    1: amd64 ver on a quad core 2.4ghz, 2g's of mem, great work;  but there are still issues with some of the more, lets say creative banks in rakarrack v0.5.8_Equinox.  I don't think thats to do with system build or configs, that might be more to do with the constructs of the banks.

   2: I installed ubuntu studio alternative on an acer aspire one, I have just noticed it has 2x2.6ghz processors (dual core), i thought this was a single core thing. Anyway, the long and short of it is I could get some good effects and it is functional as a portable effects machine, nothing intricate though.

I compiled the source rakarrack to make sure it was up-to-date with my system and that it was the latest version today.

   3:    Not sure what happend to the wireless module in ubuntu studio, (i know it sounds crazy to want wireless on a studio box), but I wanted a hassell free updateable system, and I didn't want to play around anymore fiddling with proprietary B43xxx wireless drivers, so I scrapped studio and installed Ubuntu 10.04LTS, compiled rakarrack and tested.  Seem to get the same performance as no.2 above.  I also get wireless when I want, plus all the other bits and bobs from this distro.

I miss the logo and startup music theme which takes my breath away! ( I'll transfer them when I get some time)

Configs:

   Jack, Ardour GTK2, rakarrack, Hydrogen, tuxguitar and muse + musescore, PulseAudio volume control

If you want to be sure to give your system the jitters, use RT in Jack otherwise use it on a quad core and it doesn't make any difference that I have noticed; but then I can only go so far with this thing.

If this has been helpful to someone, then I ask that you be helpful; else ?:popcorn:

---

### Post by JosepAndreu on 2010-07-15
Hi

Is true that some effects on rakarrack 0.5.8  use a lot of CPU, all the effects that use Convolution and also the Harmonizer effects, in older versions we always care about the CPU usage of all the effects, but in this version we sacrify that in order to have the best sound as possible.

But ... we provide ways to reduce this CPU usage, read the help ... the trick is in the audio settings .... Downsample  Convolotron, Revertron, Echotron ...  to 22050 Linear Linear, to check if your CPU usage goes down. Even you can Downsample to 16000.

Read the help again and you will find tips of what method of UP/Down sample is better for each case, then you can increase sample rate or resampling quality.

If you do that you will find a good balance between sound quality and CPU usage.

Of course ... a realtime kernel, a ligth desktop, a reasonable number of task running and many other things helps.


Josep
 


Josep

---

### Post by sgx on 2010-07-15
Rakarrack 5.8 is a delight! Having so many fx at hand in a concise gui
simplifies the workflow, while expanding the creative opportunities. 
The big-name windows ampsims, and many quality windows fx freewares, as
good as they are, don't win out in day-to-day usage. For your rakarrack themesong,

Time is short, and
time is money. 
Rakarrack
is golden honey

;)

---

### Post by RaumTrug on 2010-07-15
I guess it's either denormal-problems ([http://en.wikipedia.org/wiki/Denormals](http://en.wikipedia.org/wiki/Denormals), solvable only by knowing & hacking the code yourself), or a version of the software from the repos, which is compiled to run on old processors, too.

I might write **** here, but if I recall correctly, all programs from the standard repos are compiled to be able to run even on real old systems (like pentium II without sse).

now the problem is: on 32bit platforms without sse, floating point dsp code will run slow as **** (yes, I actually typed those stars). so if your platform can handle sse & sse2, either compile the relevant progs/plugins yourself, with the right optimizations, or find a ppa that has the properly optimized code for 686 with sse. if your system can handle 64bit code, run a 64bit os & install 64bit versions of the programs, it will help a lot ("amd64" (includes intel 64bit chips, too) fares even better at dsp than 686 sse). if that still doesn't happen to bring performance increase, then, well...pay the developers to properly optimize their inner loops (and don't donate beer to them, that'd just keep them from optimizing...) ;)

to say it with sgx'ish werds (yah, stop smoking/swallowing that stuff, really!):

"
the mule that surely could go rule,
was outterly just sparklin' kewl,
but fed with rusty irongrinds,
it met the floor in many kinds!

its food had to be bristled fine,
and soaked in very sweetest wine,
when fed with what is proper for:
the mule just could go carry more!
"
(sung with whikey voice & with irish fiddle&pipe in background ;-P)

---

### Post by transmogrifox on 2010-07-15
Another thing I noticed, especially on laptops, is cpu governor.

Unless you compile your own kernel and disable frequency scaling (whose purpose is to save power), it will kill your RT CPU capacity.

Every time I use my Linux Mint partition for RT audio, I run
sudo cpufreq-set -g performance

Any combination of commands that prevent the cpu governor from scaling down the frequency helps.

For Rakarrack, definitely read the help.  We put a lot of work into explaining these kind of things, and it is as easy as pressing F1.

As Josep already explained, we have some presets that will barely work on a 1.5GHz P4 or similar.  Some presets use almost nothing.

You can make your own custom preset banks, so when you find presets that work well with your hardware, save them in your custom bank.  If you take a little time to sort through the presets that work & presets that don't work for you then you will have a bank that is good.

The other thing is you can convert the old default banks from 0.4.2, or 0.3.0, which are all low-cpu FX.  The command is 
rakconvert -c nameofoldbank.rkrb

They don't make use of the new FX, but you are guaranteed low CPU.

As for jackrack + Jamin + Hydrogen...
Hydrogen is not bad on CPU except when opens. Sometimes when I start Hydrogen and is loading on my iBook G4 (1.33GHz), the program will crash and not even start.  Starting Hydrogen is like booting a virtual machine. Once Hydrogen is running, it does not use very much.

Jack Rack, like Rakarrack, CPU usage depends completely upon what you have loaded in the rack.

Finally, I don't think there are any denormal problems remaining in Rakarrack...but I can't speak for the rest of the programs.  We have specifically addressed the denormal problem.

Jack Rack would be the most suspect for denormal problems since that depends on the plugins you are using, who wrote the plugins, and whether they addressed the denormal computation problem.

---

