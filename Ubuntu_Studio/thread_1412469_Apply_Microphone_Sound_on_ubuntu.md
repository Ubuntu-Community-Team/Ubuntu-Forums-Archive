---
title: "Apply Microphone Sound on ubuntu"
date: 2010-02-21
forum: Ubuntu Studio
---

### Post by KingOfDeath on 2010-02-21
i just bought a mic and connect it to my pc everything 100% But No Sound While Recording and also no sound in skype.
In RecordMyDesktop i Clicked sound tab and i saw jackd not installed,I Don't Know What The Hell IS Jackd But Where Can I Find It ?and How can I Apply Sound  on skype ?

---

### Post by LuridCinema on 2010-02-21
I'd suggest installing the ALSAMixer .. gamix it is in the Ubuntu Software Center. You will have settings for line in and mics. Give that a go first and you should be on your way.

I have not figured out the sound settings on Record My Desktop yet, but being an Indie Filmmaker, and I have an external device for recording dialog. It is easier for me to sync dialog in a video editor after filtering for noise in Audacity << Which also records

Also go to this forum and check the                  [**Comprehensive Sound Problem Solutions Guide**]("http://ubuntuforums.org/showthread.php?t=205449")

good luck !!

---

### Post by sgx on 2010-02-21
> **KingOfDeath said:**
> i just bought a mic and connect it to my pc everything 100% But No Sound While Recording and also no sound in skype.
In RecordMyDesktop i Clicked sound tab and i saw jackd not installed,I Don't Know What The Hell IS Jackd But Where Can I Find It ?and How can I Apply Sound  on skype ?
Hi, jackd is the soundserver, qjackctl is its gui, where your software and hardware are connected by virtual patch cables, install them via synaptic, turn on a constant sound source for your mic, open the qjackctl
interface and a notebook, click the buttons and widgets, to see what is recognized (soundcards, keyboards, mics etc) take notes, when a panel opens with left/right sides, inputs will be on one side, outputs on the other, select one of each and press the 'connect button, and a line of connection appears between them.

Alsa is your soundcard 'driver' software, jackd/qjackctl is your soundsystem connection software.

Be aware that some mics need a preamp to boost their levels, as usb inputs, mic inputs, and line inputs will not always be equal. Provide specific details of your mic, soundcard, version of ubuntu, and you will get some better detailed help. Cheers: )

---

