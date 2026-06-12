---
title: "high CPU usage when JACK and qjackctrl both running"
date: 2009-07-22
forum: Ubuntu Studio
---

### Post by ltwelve2 on 2009-07-22
When I run JACK with the command line, top measures reasonable CPU usage for the jackd process, something like 3%-5%. When I run it with qjackctl, both qjackctl and JACK show usage in the 15%-20% range. Together, they soak up a third or more of my processor cycles and create all kinds of havoc. Any idea why this is? I've tried both dummy and alsa drivers with and without running qjackctl, with the same sample rate and number of frames, and when the GUI is running, both processes go crazy. 

I'm running Ubuntu Studio 9.04, installed and updated just a couple of days ago with the realtime kernel and all that good stuff. Realtime priorities and memlock have been set appropriately, I believe (or at least they are the same whether I'm running qjackctl or not).

---

### Post by kayosiii on 2009-07-23
Are you running both jack from the command line and qjackctl at the same time? If so you would be running two versions of jack at the same time and they would both be competing for resources (is this even possible).

If you mean you are getting much higher cpu usage when using qjackctl then look at the settings used by qjackctl. these are stored in a file called .jackdrc in your home folder. try starting jack from the command line using those options.

---

### Post by raboofje on 2009-07-24
> **kayosiii said:**
> Are you running both jack from the command line and qjackctl at the same time? If so you would be running two versions of jack at the same time and they would both be competing for resources (is this even possible).

I don't think that's a situation that's easy to create - but check with 'ps aux | grep jackd' to see if there's multiple instances of jackd running just to be sure.

> If you mean you are getting much higher cpu usage when using qjackctl then look at the settings used by qjackctl. these are stored in a file called .jackdrc in your home folder. try starting jack from the command line using those options.

Good idea. If that doesn't explain it: is pulseaudio running? PA seems to be a common cause of puzzling situations, though I don't directly see how it could cause this particular behavior.

---

### Post by iammatthew2 on 2009-07-29
I'm a bit new around here, but I've spent a bit of time with qjackctl.
 
If the advice above didn't solve your problem, have you checked your Sample Rate and Frames/Period? Mine are set to 44100 and 128 respectively.

---

### Post by ltwelve2 on 2009-07-29
Yeah, Pulseaudio keeps popping up, even though I keep killing it.  I'll see if I can figure out how to disable it, and maybe that will help.  Thanks!

---

### Post by ltwelve2 on 2009-07-30
I killed Pulseaudio--by removing it entirely--and that helped a tiny bit.  The real problem was apparently that my computer was configured to automatically scale CPU frequency by demand, and that didn't go over so well with Jack.  Once I used:

cpufreq-selector --governor performance

the problem was solved.  I can now run Jack at 64 frames, <3 msec latency, with no difficulty.

---

### Post by HaightsW on 2012-02-24
> **ltwelve2 said:**
> 
cpufreq-selector --governor performance


So simple, yet that makes all the difference!
Thanks

---

