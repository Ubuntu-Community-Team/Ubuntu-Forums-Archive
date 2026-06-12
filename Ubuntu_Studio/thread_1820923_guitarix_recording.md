---
title: "guitarix recording?"
date: 2011-08-08
forum: Ubuntu Studio
---

### Post by kaizen666 on 2011-08-08
[LEFT]Hi,

I have been looking to find an answer to a problem I have with my guitarix...probabky just me not doing something correctly.

I keep trying to record and it shuts straight away:

[15:42:57]  Record  ***   Trying to run jack_capture
[15:42:57]  Record  ***  Started jack_capture, session file #1
[15:42:57]  Jack Capture  ***  jack_capture terminated
[15:43:03]  Record  ***   Trying to run jack_capture
[15:43:03]  Record  ***  Started jack_capture, session file #1
[15:43:03]  Jack Capture  ***  jack_capture terminated

Sound comes out fine. Using a behringer USB UCG102(see previous posts).
I can now get guitarix, rakkarak, and calf plugins to work (none of the synths do so i have to use lmms)
It seems guitarix will be my best option for recording?  Is there any way to get it to work or is there another app in the ubuntu studio I should be using to record playing live through guitarix or rakkarak?
I tried to do it with audacity and it doesn't pick up anything though.

thanks for helping this noob :D
:KS
[/LEFT]

---

### Post by jejeman on 2011-08-08
I didn't understand what is your setup.
I usually use ardour to record from guitarix or anything else. Traverso will also work. I use it regulary for sketches.
Here is one recording I made with guitarix and ardour
[http://soundcloud.com/dzoni-promis/scream-in-doubt](http://soundcloud.com/dzoni-promis/scream-in-doubt)

Please explain your jack setup.

---

### Post by kaizen666 on 2011-08-08
Hi,

sorry, I have set up my guitar through a USB/soundcard.  The soundcard is part of the Behringer UCG102.

I was trying to use the record button in the bottom right of the guitarix interface.

Is this enough info to see what the setup is?

---

### Post by jejeman on 2011-08-08
I don't know of that recording button inside gutarix, I never used it. I'm using latest version of guitarix, which I compiled my self, and it does not have that button.
Nevertheless, it's better to use another program to record sound, like ardour or traverso. Did you tried these programs to use for recording?

In youre jack setup you need to use 3 periods/buffer because it is USB card. It will give you better performance.

When I said setup in my pervious message first of all I meant what are connections (beetwen programs) in jack.

You should setup something like this

---

### Post by sgx on 2011-08-08
> **kaizen666 said:**
> Hi,

sorry, I have set up my guitar through a USB/soundcard.  The soundcard is part of the Behringer UCG102.

I was trying to use the record button in the bottom right of the guitarix interface.

Is this enough info to see what the setup is?
Hi, from the looks of the screenshot, you may need the Output device
to be your motherboard soundchip, or another installed souncard.

My usb amp is also an Input only device,
so I choose something else as the Output device. Beyond that,
Guitarix has lots of on/off switches, and it's easy enough to
miss something in a complicated/full featured gui. I've given it
lot's of 'deer in the headlights' :guitar: sessions.

timemachine is a great simple recording app, use qjackctl to connect
guitarix on the left panel, to timemachine on the right, press the
record button when ready.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl) good links with screenshots, articles etc

Aqualung audio player, among others, can load recorded audio files, 
connect to timemachine, which will record your first track while you overdub and craft the next part. timemachine default file format
is excellent .w64, and audacity imports those for edit/convert/export.

timemachine -f wav    will record regular .wav files. (most players
don't support .w64, but I like it's quality, and put off conversion
until it's really needed.

To record in audacity with jackd/qjackctl, you must specify jackd as
the audacity recording device, push record in audacity, then pause, then look in qjackctl, and 'portaudio' should appear, which will be audacity. Make the connections, and press pause again, to resume recording.
Cheers

---

### Post by kaizen666 on 2011-08-15
thanks for the help and the screenshots, how do you get those screens on guitarix?

going to try and play about a little more, starting to realise there is a sequence to opening this stuff up now.

---

### Post by jejeman on 2011-08-15
> thanks for the help and the screenshots, how do you get those screens on guitarix?Not shure what you mean. As I said it's new version form their site. Version guitarix2-0.17.0. So thats why it is different from yours.

---

### Post by sgx on 2011-08-16
> **kaizen666 said:**
> thanks for the help and the screenshots, how do you get those screens on guitarix?

going to try and play about a little more, starting to realise there is a sequence to opening this stuff up now.

There are screens that open when you click a certain widget. The screen fills fast when you open up all the modules. Click everything that isn't shooting sparks :)

---

### Post by SatanSpawn on 2011-08-27
Just use ```
jack_capture_gui2
```

---

