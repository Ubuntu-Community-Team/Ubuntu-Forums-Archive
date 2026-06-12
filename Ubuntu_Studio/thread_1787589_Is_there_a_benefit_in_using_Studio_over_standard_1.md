---
title: "Is there a benefit in using Studio over standard 11.04"
date: 2011-06-21
forum: Ubuntu Studio
---

### Post by Red62 on 2011-06-21
Hi.. I have been a ubuntu user for many years....currently running 11.04 on a Thinkpad laptop.  I play and record music and want to use Ardour, Audacity, Hydrogen, soft synths etc.  I understand that Studio 11.94 does not have a rt kernel and uses the same generic kernal as 11.04.

Which begs the question - what is the benefit of running ubuntu studio?

Will 11.04 standard ubuntu be able to record to ardour with hydrogen thro jack ok?

At the moment I am getting lots of xruns in jack - not sure whether that is my jack setup or because I am running standard ubuntu.

Any guidance would be appreciated.

Cheers

---

### Post by cchhrriiss121212 on 2011-06-21
There would be no difference in performance when using Studio, the distro has no extra tweaks, it is just a collection of software packages. The point of Studio is to showcase the latest audio/video/graphical software, it has no advantage in practical terms over any other OS.

If you want better performance look at an rt or low latency kernel, or look at changing your settings. Increasing the latency will reduce xruns, as will using a dedicated soundcard.

---

### Post by dFlyer on 2011-06-21
+1. I use Studio in the past and figured there was no different in performance other than more graphic and multimedia software install by default, all of which can be added from the archives using synaptic or ubuntu software center. It's also a larger download and requires a dvd or at least in the past it did.

---

### Post by bluesscream on 2011-06-21
here you'll find the authoritative lowlatency kernel:

[https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa)

but don't forget to scale your cpu frequencies at "performance" as long as you need stable audio performance. "ondemand" will cause xruns by interrupting your audio work for up- and downshifting cpu-frequency at many system operations independent from subsequent priority settings.

---

### Post by Red62 on 2011-06-22
Thanks all.... at the moment I am still struggling to get Jack running  without xruns with the -generic kernal.

---

### Post by Pablo_F on 2011-06-22
> I am still struggling to get Jack running without xruns with the -generic kernel

I suggest you should try the low latency kernel from [Alessio's PPA]("https://launchpad.net/~abogani/+archive/ppa")

---

### Post by Red62 on 2011-06-22
It seems that the best Frames/Sec I can get is 2048...giving a latency of 92.9msec... also notice I can tick the Realtime option with the -generic kernal and the RT lights up ok on the control panel as if RT is working... does that sound right?

Any suggestions (apart from installing RT kernal) whether latency can be improved? 

cheers

---

### Post by Pablo_F on 2011-06-22
> I can tick the Realtime option with the -generic kernal and the RT lights up ok on the control panel as if RT is working... does that sound right?

[Quite right]("http://www.jackaudio.org/realtime_vs_realtime_kernel").

Did you try abogani's kernel? It is not a realtime kernel, but for audio work it is better tweaked than the generic one.

---

### Post by Pablo_F on 2011-06-22
Another suggestion, synchronous mode (only applicable to jackd2, the default ubuntu >=10.10 jackd implementation).

You do it by writing in the server path field:

/usr/bin/jackd --sync

---

### Post by bluesscream on 2011-06-22
> **Red62 said:**
> 
Any suggestions (apart from installing RT kernal) whether latency can be improved? 


have a look at my screenshot, this setting works nice here with usb midicontroller keyboard,  lmms-zynaddsubfx, vsti-synth in reaper, 2 instances of phasex and hydrogen simultaneously

---

### Post by Totalchaos on 2011-06-23
> **Red62 said:**
> It seems that the best Frames/Sec I can get is 2048...giving a latency of 92.9msec... also notice I can tick the Realtime option with the -generic kernal and the RT lights up ok on the control panel as if RT is working... does that sound right?

Any suggestions (apart from installing RT kernal) whether latency can be improved? 

cheers

Check it out here  [http://wiki.linuxmusicians.com/doku.php?id=system_configuration](http://wiki.linuxmusicians.com/doku.php?id=system_configuration)

---

### Post by Red62 on 2011-06-24
Thanks all.... I havent had a chance to try the suggested new kernal yet.... I think one of my issues is that I have to run ubuntu on my Thinkpad t400 with noapic and nolapic in the boot paremeters.. this seems to only use one of the 2 cores in the thinkpad, so suspect my machine is not providing all the power it could...

---

