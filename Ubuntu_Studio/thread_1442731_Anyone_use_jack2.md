---
title: "Anyone use jack2?"
date: 2010-03-30
forum: Ubuntu Studio
---

### Post by cchhrriiss121212 on 2010-03-30
I wanted to try out the synth phasex on my studio install but it has jack>0.99 as a requirement. I have installed jack2 but cannot get it to run:
   p, li { white-space: pre-wrap; }  ```

15:59:22.116 /usr/local/bin/jackd -P70 -t5000 -dalsa -dhw:0,0 -r48000 -p128 -n2 -s
 /usr/local/bin/jackd: symbol lookup error: /usr/local/bin/jackd: undefined symbol: jackctl_server_create

```

A few questions I haven't been able to search for:
Why does studio not use jack2?
Is it any better/worse than jack (ignoring less support for things like phasex)?
Could someone show me how to get it running?:p

---

### Post by RaumTrug on 2010-03-30
how have you installed it? I had similliar errors when just compiling myself while having old jack installed. my sollution was to lock all old jack packages (so dependant progs will not be uninstalled), delete their files manually, and then installing jack2. some progs (creox from repo, for example) don't seem to like it, but most stuff works fine.

I'm not sure, but I think jack2 has the advantage of being able use multiple threads (i.e. multiple processor cores) for sound processing; I've still got single core, and use jack2 because of the audioadapter (=multiple soundcards in sync in one jack server).

---

### Post by cchhrriiss121212 on 2010-03-30
Update: Now its running even though I have not changed any settings, but latency has to be set at 40ms in order for me to avoid xruns. I have a delta44 card so I used to run at 5ms previously with no trouble.
Phasex is very good btw. Far easier to make new presets than zynsub.

---

### Post by cchhrriiss121212 on 2010-03-30
> how have you installed it?
I compiled it from the newest stable package on the jack website as I did not know of any ppas with it. It installed to /usr/local/bin so I just altered the directory path to that in qjackctl setup, I have done no other configuration.

I think I will go with a clean install of regular ubuntu and install only the bits I would like to use.

---

### Post by AutoStatic on 2010-03-30
PHASEX doesn't need Jack2, at least not the latest version available (which is in my [PPA]("http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/p/phasex/") btw). And the [frasten PPA]("https://launchpad.net/~frasten/+archive/ppa") has Jack2. I don't use Jack2 yet, there are still some issues with it apparently. And I think I'll await what this whole session management discussion leads to.

---

### Post by cchhrriiss121212 on 2010-03-30
> PHASEX doesn't need Jack2, at least not the latest version available

I downloaded the same version that is in your ppa (0.12.0) from their webpage. It has this in the install notes:
> MINIMUM REQUIREMENTS:
-------------------------------------------------------------------------------
    gcc-3.4
    gtk-2.4
    alsa-0.9.0
    jack-0.99.0
    libsamplerate-0.1.2

I tried ./configure out anyway but it needed >0.99.0. How does your ppa get around that?

 > And I think I'll await what this whole session management discussion leads to. 	
What does this refer to?

---

### Post by bobince on 2010-03-30
I'm interested in the status of JACK2. Is it running well, or is there a good stability reason we should be sticking with JACK1?

I'd very much like the multiple sound device support so I don't get ugly-cutout xruns when using my USB mic... does this work reliably? If so, with suitable plugs for ALSA, could JACK2 be a reasonable replacement for Pulse as a main always-on sound server too?

---

### Post by AutoStatic on 2010-03-31
> **cchhrriiss121212 said:**
> I tried ./configure out anyway but it needed >0.99.0. How does your ppa get around that?You probably miss a JACK dev package. Karmic comes with JACK 0.116.x which is a higher version than 0.99.0 so it should work.

 
> **cchhrriiss121212 said:**
> What does this refer to?There's a hefty discussion going on at the moment on multiple mailinglists and IRC channels:
[http://lists.jackaudio.org/listinfo.cgi/jack-devel-jackaudio.org](http://lists.jackaudio.org/listinfo.cgi/jack-devel-jackaudio.org) (you have to be subscribed to access the archives)
[http://lists.linuxaudio.org/pipermail/linux-audio-dev/2010-March/026968.html](http://lists.linuxaudio.org/pipermail/linux-audio-dev/2010-March/026968.html)
[http://lists.linuxaudio.org/pipermail/linux-audio-dev/2010-March/027110.html](http://lists.linuxaudio.org/pipermail/linux-audio-dev/2010-March/027110.html)
IRC: #jack on FreeNode

I'm not really following the discussion but it's all about JACK and session management.

---

### Post by cchhrriiss121212 on 2010-04-01
I've now got a fresh install going now, and I think I'll stick with jack1 for the while.

But phasex is giving out an occasional distorted output. It sometimes goes back to normal after a few minutes without restarting anything but jack does not display anything that looks like an error. 
I don't have this with any other jack using programs that I've been using all morning. I remember having a similar issue with zyn which was solved with an increased timeout setting in jack.
Any ideas?

---

### Post by AutoStatic on 2010-04-01
No not really unfortunately. Maybe if you increase the verbosity in QjackCtl? And what patch causes the distortion? Maybe I could reproduce it.

---

### Post by RaumTrug on 2010-04-01
just for your interest: I've seen/heard a lot softsynths that cause distorted output in different audio environments (win alsa jack whatever...) occasioanally due to internal bugs (overflow, precision etc).

they've seriously bust my ears many times, as they tend to produce output when distorted at maximum possible level.

so don't blame jack for such behaviour as first "enemy", just try other progs, when they run clean, however you abuse them, then some dev probably has overdone optimizations for the synth that explodes.

sad, but true :(

---

### Post by cchhrriiss121212 on 2010-04-02
> they've seriously bust my ears many times, as they tend to produce output when distorted at maximum possible level.

This is what is happening and it is not pretty. It seems odd that it should be working one minute and then just shoot off into noise the next, and then switch back again.

> And what patch causes the distortion? Maybe I could reproduce it. 	

Thanks for the help. It seems to be happening with the industrial chimes patch, but I've also had it happen when making my own. It might be connected with delay somehow but it's mostly just at random intervals. Doesn't seem to be involved with having too much polyphony going on as it happens with 3 note chords and simple melody lines.

---

### Post by cchhrriiss121212 on 2010-04-05
Eliminated the distortion hiccups by lowering the polyphony from 12 notes to 8, if anyone wants to know. A bit disappointing it can't handle 12 notes, but I doubt I'll ever really find it limiting with my meager skills. 
Have also been trying out AMS, some of the presets nearly blew my ears off, but its otherwise a great synth.

---

### Post by carlotheman on 2010-04-08
(sorry this post was kind of misleading, removed)

---

