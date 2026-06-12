---
title: "Edirol FA-66 works compiled from source"
date: 2009-01-17
forum: Ubuntu Studio
---

### Post by arachnegl on 2009-01-17
I got Edriol FA-66 to work using FFADO with Ubuntu Studio 8.04 RT

I bought it on reports that people had got it working out of box. It didn't for me... I have been struggling with this for the best part of two months.

Go to the trac website and follow instructions. The only thing I did different from the instructions is that when compiling FFADO from source with the scons command, add the enable all option:

ENABLE_ALL=true

The dawn of an Xrun free era arrived. I had Ardour, Renoise, ZynAddSubFX, Pure Data, AMS... all running, recording, communicating without a single Jack complaint. A beautiful mayhem!!!

Hope this helps someone.

---

### Post by ushimitsudoki on 2009-01-17
Well I'm glad to hear it because my Edirol UA-25 is xrun-o-riffic. I'm seriously looking at better interface and it's good to know what my options are!

---

### Post by bageh on 2010-01-28
How did you do that? You removed ffado and jack from synaptic then compiled both?

You tried this [http://subversion.ffado.org/wiki/InstallingFfadoFromSource](http://subversion.ffado.org/wiki/InstallingFfadoFromSource) ?
Or did you try the Beta 6 installation on ffado site?

I'd appreciate your help, cause I also have and Edirol FA-66, but jack crashes when try to open PureData and, after that, I receive message  "could not connect to jack server as a client" and so on.


> **arachnegl said:**
> I got Edriol FA-66 to work using FFADO with Ubuntu Studio 8.04 RT

I bought it on reports that people had got it working out of box. It didn't for me... I have been struggling with this for the best part of two months.

Go to the trac website and follow instructions. The only thing I did different from the instructions is that when compiling FFADO from source with the scons command, add the enable all option:

ENABLE_ALL=true

The dawn of an Xrun free era arrived. I had Ardour, Renoise, ZynAddSubFX, Pure Data, AMS... all running, recording, communicating without a single Jack complaint. A beautiful mayhem!!!

Hope this helps someone.

---

### Post by robeast on 2010-01-28
> **ushimitsudoki said:**
> Well I'm glad to hear it because my Edirol UA-25 is xrun-o-riffic. I'm seriously looking at better interface and it's good to know what my options are!

That USB connection is not super reliable :(

If you have stuff like a USB mouse and keyboard or other USB peripherals try unplugging those and see if it improves your performance. The 66 is firewire which is a lot less likely to get xruns than USB, although they are entirely possible.

arachnegl, I assume you are using FFADO 2? I just compiled that from source last night along with jackdmp a.k.a jack 1.9.2 and the most recent Ardour release on Ubuntu 9.10. Many long hours were spent installing the right dependencies and compiling in the right order but it works amazingly well with my Presonus Firepod!

---

### Post by AutoStatic on 2010-01-28
> **robeast said:**
> That USB connection is not super reliable :(

If you have stuff like a USB mouse and keyboard or other USB peripherals try unplugging those and see if it improves your performance.That was quite an old post ;) And the UA-25 works really well with Ubuntu, I have no problems whatsoever with the device.

> **robeast said:**
> arachnegl, I assume you are using FFADO 2? I just compiled that from source last night along with jackdmp a.k.a jack 1.9.2 and the most recent Ardour release on Ubuntu 9.10. Many long hours were spent installing the right dependencies and compiling in the right order but it works amazingly well with my Presonus Firepod!There are PPA's with debs, that could've saved you a lot of time ;)

---

### Post by robeast on 2010-01-28
> **AutoStatic said:**
> That was quite an old post ;) And the UA-25 works really well with Ubuntu, I have no problems whatsoever with the device.

There are PPA's with debs, that could've saved you a lot of time ;)

Whaaaa??? I see that now...about a year ago...and bageh revived it. No wonder they were talking about FFADO beta6 ;) 

Thing is with the PPAs is that I ONLY wanted ffado2, jackdmp and ardour's newest releases. It's always a learning experience compiling from source, so the time wasn't wasted!

Anyway, to respond to bageh, I had installed qjackctl and jackd from the repos first. Then I found out that it is best to install ffado first...then I found jackdmp...it was a rabbit hole. So I uninstalled qjackctl and jackd then compiled ffado2 and then jackdmp and then ardour. So I'm running jackd from the command line with -dfirewire. So you can remove your existing jackd and I'm also assuming ffado and compile them both from source. I didn't have any conflicts.

---

### Post by AutoStatic on 2010-01-29
> **robeast said:**
> It's always a learning experience compiling from source, so the time wasn't wasted!200% true :D

---

### Post by bageh on 2010-01-29
Thanks robeast!

More questions: here - [http://www.grame.fr/~letz/jackdmp.html](http://www.grame.fr/~letz/jackdmp.html) - there are two possible jackdmp downloads, jackdmp_0.71.tgz and a svn one.
Which is better? I'm guessing the first - looks more simple - but I'm not sure.
Another question: when trying to remove jackd, other applications will be removed as well. Is it possible to uninstall just jackd and keep the others?


> **robeast said:**
> Whaaaa??? I see that now...about a year ago...and bageh revived it. No wonder they were talking about FFADO beta6 ;) 

Thing is with the PPAs is that I ONLY wanted ffado2, jackdmp and ardour's newest releases. It's always a learning experience compiling from source, so the time wasn't wasted!

Anyway, to respond to bageh, I had installed qjackctl and jackd from the repos first. Then I found out that it is best to install ffado first...then I found jackdmp...it was a rabbit hole. So I uninstalled qjackctl and jackd then compiled ffado2 and then jackdmp and then ardour. So I'm running jackd from the command line with -dfirewire. So you can remove your existing jackd and I'm also assuming ffado and compile them both from source. I didn't have any conflicts.

---

### Post by robeast on 2010-01-29
Don't get the old versions! Use the first link under the JACK2 header to download jack-1.9.4.tar.bz2 for linux.

As far as uninstalling jackd ONLY, I don't think you can do it from apt-get or synaptic. It will automatically uninstall at least qjackctl. This is probably really bad advice, but you may be able to install jackdmp OVER jackd, because it will replace pretty much all the same files that jackd uses and it will still use /usr/bin/jackd to run the server. I haven't gotten qjackctl going yet so I'm just running it from the command line.

---

### Post by AutoStatic on 2010-01-30
FYI, there's also a PPA which has JACK 1.9.4: [https://launchpad.net/~frasten/+archive/ppa](https://launchpad.net/~frasten/+archive/ppa)
Make sure to remove everything related to JACK1 (0.116.x) first.

---

### Post by bageh on 2010-02-01
Now things are going really weird...

I did nothing different, I swear. In fact, I've done 1 good session on jack + PureData, but on the next day started to get this:
jackd: symbol lookup error: jackd: undefined symbol: _jack_get_microseconds

Then I decided to install jack2, as you told me.
Now I'm getting this:
bageh@bageh-laptop:~$ jackd -d 
alsa       coreaudio  dummy      oss        portaudio  

If I try with "jackd -d firewire" I get:
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Unkown driver "firewire"

I reinstalled all ffado things from synpatic, but didn't work. What else can I do? I have no idea.

---

### Post by bageh on 2010-02-01
Folks, back to old Jack I returned with the old problems.

I realized that with jack2 I didn't find how to enable firewire (libffado was not in /local, so I didn't get it).

I expected also that jack2 would override my old jack: that was true when "jackd --version" but false in synaptic.

So back to the begining, think I sould try compiling jack2, but what should I do with the firewire option (remember that I installed libffado from a ppa).




> **bageh said:**
> Now things are going really weird...

I did nothing different, I swear. In fact, I've done 1 good session on jack + PureData, but on the next day started to get this:
jackd: symbol lookup error: jackd: undefined symbol: _jack_get_microseconds

Then I decided to install jack2, as you told me.
Now I'm getting this:
bageh@bageh-laptop:~$ jackd -d 
alsa       coreaudio  dummy      oss        portaudio  

If I try with "jackd -d firewire" I get:
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Unkown driver "firewire"

I reinstalled all ffado things from synpatic, but didn't work. What else can I do? I have no idea.

---

### Post by bageh on 2010-02-01
AutoStatic, thanks for the tip, but aren't these repos for 9.04 e 9.10.
I'm afraid if they'll work in 8.04.

> **AutoStatic said:**
> FYI, there's also a PPA which has JACK 1.9.4: [https://launchpad.net/~frasten/+archive/ppa](https://launchpad.net/~frasten/+archive/ppa)
Make sure to remove everything related to JACK1 (0.116.x) first.

---

### Post by robeast on 2010-02-01
I think you have to install libffado before installing JACK. It was definitely not installed when you ran jackd -d and it printed the available drivers (minus firewire). libffado is available in the synaptic, you can install from there and then try JACK2. Of course, you can just ride with the JACK version in synaptic, in which case still install libffado first.

Also, run JACK with the -R option to enable realtime processing if you are using a realtime kernel (which you should be). I believe the package is something like linux-rt.

---

### Post by bageh on 2010-02-01
I figured what I needed: installing libffado*-dev

Then, firewire was "yes" ate configure but, after installing jack2, I couldn't even start jackd.

bageh@bageh-laptop:~/jack-1.9.4$ jackd 
jackdmp 1.9.4 
Copyright 2001-2005 Paul Davis and others. 
Copyright 2004-2009 Grame. 
jackdmp comes with ABSOLUTELY NO WARRANTY This is free software, and you are welcome to redistribute it under certain conditions; see the file COPYING for details jackd: symbol lookup error: jackd: undefined symbol: jackctl_server_create

"sudo ldconfig" after installation solved that. Now jackd starts, but it still doesn't work with pd: instead of crashing, it keeps skiping cycles. It gaves me that forever: 
firewire ERR: wait status < 0! (= -1)
JackAudioDriver::ProcessAsync: read error, skip cycle


Jack's version output:
bageh@bageh-laptop:~/jack-1.9.4$ jackd --version
jackdmp 1.9.4
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
could not open driver .so '/usr/lib/jack/jack_oss.so': /usr/lib/jack/jack_oss.so: undefined symbol: _jack_get_microseconds
no message buffer overruns
could not open component .so '/usr/lib/jack/jack_oss.so': /usr/lib/jack/jack_oss.so: undefined symbol: _jack_get_microseconds
jackdmp version 1.9.4 tmpdir /dev/shm protocol 7

Any idea?


> **robeast said:**
> I think you have to install libffado before installing JACK. It was definitely not installed when you ran jackd -d and it printed the available drivers (minus firewire). libffado is available in the synaptic, you can install from there and then try JACK2. Of course, you can just ride with the JACK version in synaptic, in which case still install libffado first.

Also, run JACK with the -R option to enable realtime processing if you are using a realtime kernel (which you should be). I believe the package is something like linux-rt.

---

### Post by AutoStatic on 2010-02-02
> **bageh said:**
> AutoStatic, thanks for the tip, but aren't these repos for 9.04 e 9.10.
I'm afraid if they'll work in 8.04.They probably won't work. I wasn't aware that you were using 8.04.

---

### Post by bageh on 2010-02-02
I don't know exactly why, but it seems to work now.

In resume, as Robeast said, I installed liffado* (and -dev) from the repository, then compiled jack-1.9.4 with the --prefix=/usr option.

Then "sudo ldconfig" (I don't remember if after or before installation).

So, it worked with PD. I think that it can work with Ardour too.

One more question: how to hear midi through Edirol using jack?

Thanks to all!

---

