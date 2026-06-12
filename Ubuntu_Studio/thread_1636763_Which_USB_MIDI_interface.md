---
title: "Which USB MIDI interface?"
date: 2010-12-03
forum: Ubuntu Studio
---

### Post by mtdnelson on 2010-12-03
Hi all,

I installed Ubuntu 10.04 on a fouryear-old HP PC which I was donated recently, and have since added the Ubuntu Studio packages. Until a couple of years ago, I used to use Fedora and PlanetCCRMA. I have a couple of old second-hand RME DIGI soundcards.

Now, I'd like to start using my MIDI controller keyboard to write some tunes, and I might buy a MIDI sound module later. I've been asked what I would like for Christmas, and I have decided to ask for a USB MIDI interface... Working with a budget of £30-£60, and a deadline of Christmas eve, what do you recommend? I'd like 2-4 inputs and outputs. I need it to play nicely with Linux. If it works out-of-the-box, so much the better.

There's the MidiSport 2x2 20th anniversary edition, which I've seen on [www.dv247.com]("http://www.dv247.com") for £60 -- conveniently, they have an actual real-world shop near me. Do I remember something from a few years ago about using a special utility to load firmware to it?

Any thoughts? Any other suggestions?

Thanks,
Michael

---

### Post by SleepWalkerX on 2010-12-03
I just bought a cheap usb midi cable from ebay.  Midi is just an interface so I don't think you really have to look for "quality"..

---

### Post by mtdnelson on 2010-12-06
Thanks for your advice.

However, I was more concerned with the availability of a decent stable Linux driver than with quality, and I thought this might be the place to ask! I know that there are some devices which conform to a USB MIDI standard, and some that do not, but which might have a dedicated driver already...

Has anyone got any advice?

Thanks,
Michael

---

### Post by babarosa on 2010-12-06
I am using a "M-Audio Midisport 2x4" since v8.04 and it works perfectly, even with an inserted USB-hub.

Regards,
Michael

---

### Post by bikodog on 2010-12-11
You can pick up a used midisport 2x2 for ~ $30 on ebay.

works perfect for me in any *nix setting.

---

### Post by bluesscream on 2010-12-11
e-mu xmidi 2x2 does the job for me. Working ootb. For time critical live performances it might reasonable to use a rt-kernel and adjust device's irq priorities.

---

### Post by calande on 2012-06-23
Hello,

I'm searching for a 8-IN 8-OUT MiDi interface that is Linux compatible. Some people are struggling with the MIDI Motu express 128 interface and I wouldn't like to go through the same hassle. My VSTis don't work with Linux so I have to at least be able to use my hardware synths, sampler and effect processors...What interface do you suggest? Thanks.

---

### Post by sgx on 2012-06-23
Experiments needed. A non-motu, mac compatible device,
may be needed, and though hubs are not recommended,
a very high quality powered usb hub, with a pair of

[http://www.thomann.de/gb/maudio_midisport_4x4_ae_usb.htm](http://www.thomann.de/gb/maudio_midisport_4x4_ae_usb.htm)

or some e-mu 2X2

[http://www.ebay.com/sch/i.html?_nkw=E+MU+2x2](http://www.ebay.com/sch/i.html?_nkw=E+MU+2x2)

may be in the ballpark. The e-mu are built like
little tanks, and show up in qjackctl.

Someone was successful with a motu midi device in the
last year or so, a thorough google search should turn it up. It was pretty easy, once the magic was discovered.
Cheers

---

