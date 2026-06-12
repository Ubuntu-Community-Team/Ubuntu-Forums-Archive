---
title: "good LADSPA distortion plugin?"
date: 2009-01-19
forum: Ubuntu Studio
---

### Post by cronholio on 2009-01-19
I'm using Ardour for homerecording and I miss some good distortion plugin that can be used on guitar tracks. I've never gotten around to building Ardour with VST support, so I was wondering if anyone can suggest a good LADSPA plugin pack?

---

### Post by eric71 on 2009-01-19
Search for "caps" in synaptic and install the package. The caps ladspa plugins are preamp/amp/cabinet simulations. You should be able to get what you need from those.

You can read about them here:

[http://quitte.de/dsp/caps.html](http://quitte.de/dsp/caps.html)

---

### Post by thorgal on 2009-01-19
you can also try guitarix. It's not yet a plugin as such, more some sort of standalone effect box for realtime playing. But it may sound good enough for you. Just google it.

It also interfaces with jconv, a convolution engine which works really nicely. You just need impulse response files that you can also google around. You can achieve quite good reverbs and crazy distorsions with a bit of tweaking :)

For more info, you can start reading this discussion trhead on linuxmusicians.com :
[http://linuxmusicians.com/viewtopic.php?f=44&t=279&st=0&sk=t&sd=a](http://linuxmusicians.com/viewtopic.php?f=44&t=279&st=0&sk=t&sd=a)

it's a rather long discussion thread but the guitarix main developer is relating his progress. You may find a few interesting links in there as well.

I forgot to mention that using guitarix in ardour is possible as a track insert. Guitarix takes a mono source and outputs in stereo (IIRC).

---

### Post by cronholio on 2009-01-19
Thanks, I'll give those a try!

---

### Post by alanj on 2009-03-11
Quite a nice valve overdrive plugin at [http://www.linuxdsp.co.uk]("http://www.linuxdsp.co.uk") might be worth a look.

---

### Post by Stochastic on 2009-03-12
> **alanj said:**
> Quite a nice valve overdrive plugin at [http://www.linuxdsp.co.uk]("http://www.linuxdsp.co.uk") might be worth a look.

I'd be weary of binary downloads from unknown sources - you don't know what ugly bits of code it's running on your machine.  (after all, how do they pay for their private web host?).... just my 2cents.

---

### Post by alanj on 2009-03-12
As far as I'm aware it's all funded out of the developers own pocket, the guy is just pasionate about Linux audio.

---

### Post by Stochastic on 2009-03-12
> **alanj said:**
> As far as I'm aware it's all funded out of the developers own pocket, the guy is just pasionate about Linux audio.

Fair enough.  I hope that's the case - it would be wonderful.

It'd be even nicer if he opened the source code up and let others distribute it so that it could be added to the Ubuntu repositories. :)

---

### Post by linuxdsp on 2009-03-13
Hi, I gather there's some suspicion that my plugins might contain malicious code because they're binaries - I set up linuxDSP because I believe in linux as a great platform for audio, I wanted to promote its use and I had written some plugins for my own use.  They are not open source at the moment, that is a complex issue I won't go into here, but they are free, the site does cost money to run, so far I have funded that, if you look closely there's a 'Donate' button if anyone feels they could help in that respect. The plugins are provided without waranty but there is nothing malicious about them (it would be somewhat ridiculous to post intentionally malicious code on the site - it would be very easy to trace the owner! Try the plugins, if you like them let me know if you don't, let me know as well :)

[email]mike@linuxdsp.co.uk[/email]

[http://www.linuxdsp.co.uk](http://www.linuxdsp.co.uk)

---

### Post by danflash on 2010-03-14
> **linuxdsp said:**
> Hi, I gather there's some suspicion that my plugins might contain malicious code because they're binaries - I set up linuxDSP because I believe in linux as a great platform for audio, I wanted to promote its use and I had written some plugins for my own use.  They are not open source at the moment, that is a complex issue I won't go into here, but they are free, the site does cost money to run, so far I have funded that, if you look closely there's a 'Donate' button if anyone feels they could help in that respect. The plugins are provided without waranty but there is nothing malicious about them (it would be somewhat ridiculous to post intentionally malicious code on the site - it would be very easy to trace the owner! Try the plugins, if you like them let me know if you don't, let me know as well :)

[email]mike@linuxdsp.co.uk[/email]

[http://www.linuxdsp.co.uk](http://www.linuxdsp.co.uk)

I use Mike's LinuxDSP plugins all the time (even donated a tiny bit couple months back) and they're brilliant.  Prefer them over Jamin for mastering, and the fx are highly effective.  To anyone reading I suggest you test-drive the reverb, overdrive, and dynamics plugs - you'll be pleasently surprised.  Also, give the man a bit of money for his hard work, it's only fair.

---

