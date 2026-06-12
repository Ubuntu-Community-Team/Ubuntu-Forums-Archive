---
title: "Zoom H2 and Jack"
date: 2010-07-01
forum: Ubuntu Studio
---

### Post by bluesscream on 2010-07-01
I'm going to buy a Zoom H2 and I know that it's easy to import it's recorded files via usb or cardreader. But are there experiences with using the H2 directly as a Jackd input device? This would be the icing on the cake.

---

### Post by sgx on 2010-07-02
> **bluesscream said:**
> I'm going to buy a Zoom H2 and I know that it's easy to import it's recorded files via usb or cardreader. But are there experiences with using the H2 directly as a Jackd input device? This would be the icing on the cake.
Hi, when qjackctl is configured for your soundcard, anything with audio outputs connected to the soundcard 'line-in' is fair game. Jackd makes
no distinction. Sound is sound. Midi devices are different, and must be properly supported to work properly, and software settings configured with
some uniform settings, and optimal choices discovered to fine tune things.
Cheers

---

### Post by AutoStatic on 2010-07-02
bluesscream, afaik the Zoom H2 should just work, it's  a standard compliant device.

---

### Post by bluesscream on 2010-07-02
> **AutoStatic said:**
> ...it's  a standard compliant device.
Tx, I'll buy it and report :)

---

### Post by bluesscream on 2010-07-05
Received it this morning. I read the manual in my breathing pauses, tried the usb cardreader functions - the dealer added a 8g hcsd - but had no more time over the day. 
Now I tested it's pc i/o functions with my laptop. 
It's a facile stereo i/o usb audiodevice  and on the fly a usb stereo microphone of remarkable quality. It appears and connects ootb in jackd. First I had some Xruns until I  noticed that I'd run the device on sr 44100 and jack on 48000.
Even a dual device setting is possible in jack/ardour and audacity: h2 as usb input device and my notebooks internal soundchip for (cheesy) output and monitoring. For getting jack started with this option higher latencies had to be accepted. 
Tomorrow I'll test it's standalone recorder functions in a real jam session. First impression: absolutely useful in a mobile linux audio environment.

---

### Post by RaumTrug on 2010-07-05
you might find the "alsa_in"/"alsa_out" tools, or jack2's "audioadapter" useful for live-monitoring the usb mic with lower latency. I do this (alsa_in/out don't work at my machine, but audioadapter, despite of bugs/flakieness in configurations does) with an usb-condenser and get good results - I'm able to monitor the mic on headphones with ladspa reverb & eq in between without noticing the delay while speaking/singing myself.

just watch that you load the mic as "master interface" in record-only mode and add the monitor output with those tools - this way the recorded signal will be clean, because the adapters resample the devices added to the jack tree.

---

