---
title: "Making ubuntu recognize &quot;microphone&quot; as MIDI keyboard"
date: 2010-01-08
forum: Ubuntu Studio
---

### Post by Affrikka on 2010-01-08
Hey everyone!

I am running ubuntu 9.10

I have a Yamaha Clavinova digital piano, and my dad said that with this certain cord I can run the piano into the microphone jack of my computer and it will register it as a MIDI keyboard.

Well I moved my entire computer setup downstairs next to my piano and plugged it all in and nothing.
I want to have ubuntu recognize that the piano is a "midi keyboard" so I can record stuff and use it in Rosegarden and Reason 4.

The only other thing I can think of is to get something like [this](http://www.amazon.com/External-Microphone-Adapter-Dongle-Notebook/dp/B001MW92AE) and plug it in through a USB.

My dad says I need a special sound card to do it, but the computers we have a school (where we use miniature midi keyboard that run into a usb jack) I'm almost positive don't have "special sound cards" because they're really cheaply made :P


So what do I need to do?


Thanks!


Mathieu

---

### Post by RaumTrug on 2010-01-08
I doubt the mic-in sollution/the sollution with that mini-usb soundcard would work on linux, as I guess you'll need a special driver that decodes the midi signals that'd be encoded to analog soundwaves. most probably such a driver won't exist for linux, but I could be wrong...

what kind of outputs does your piano have? if there's the standard midi in/out ports, you could try a "dongle" similliar to the one you've shown above, but with midi input/output! you can get one for like 20 €.

or, if you've got some game port, you could try to find a breakout cable for it, that used to be the standard midi connection in the 90's, but I think to recall that stuff is buggy somehow with current alsa, so it's also disabled by default. so best would be a soundcard with good midi reportedly working under linux (expensive), or a midi-usb adaptor that needs no special drivers (they exist, and I think they work under ubuntu)!

---

### Post by sgx on 2010-01-08
Hi, pitch-to-midi is complex, and supported by only a few apps.
Some free, some expensive. Not worth your efforts.

Good news, find a used older maudio 24/96 pci soundcard, or another
that is well supported, check here:

[http://www.alsa-project.org/main/index.php/Matrix:Main#ALSA_SoundCard_Matrix](http://www.alsa-project.org/main/index.php/Matrix:Main#ALSA_SoundCard_Matrix)

Cheers

---

### Post by RaumTrug on 2010-01-09
heh, yeah, an used m-audio soundcard is probably twice or more the price of a new usb midi connector, but you'll get some dope audio quality, too, from the same thing ;) - it'd just be some hassle to get the thing into the pc & running, driver config etc.

no, seriously, does the keyboard have midi in/out ports? look at that picture & compare with the back of your keyboard:
[http://commons.wikimedia.org/wiki/File:Midi_ports_and_cable.jpg](http://commons.wikimedia.org/wiki/File:Midi_ports_and_cable.jpg)
if your digital piano has such ports, you'll be able to interface it midiwise with your computer!

otherwise I don't see "much light" for you, as sgx said, plugging audio output to mic in would mean that audio'd need to be analyzed to be converted to note data, and that'd mean it would be glitchy & have some nasty delay! pure midi is much better as it sends only note-on, note-off, velocity & such as numbers directly, that the computer can use to control a synth, record to some sequencer/notation software, and also for playing back midi stuff from your computer on the piano!

easiest to set up & cheapest would be a simple usb-midi connector, something like this:
[http://www.thomann.de/gb/esi_midi_mate.htm](http://www.thomann.de/gb/esi_midi_mate.htm)
(not meant as advertisement, just as sample of what you need, you'll probably find it somewhere else cheaper, or another model, that works, too!)

don't be shocked too much if all shops won't state wether it works with linux, just make sure it needs no drivers (i.e. plug&play), and google for the name of the product + linux to see if it worked without hassles on linux for other people (the thing from the link above, for example, should work I think)!

"good luck"!

---

### Post by Affrikka on 2010-01-09
hey everyone,

I got the problem solved, I got an M-Audio UNO cord and I'm currently using it for MuseScore, now if only I could get it recognized in my virtual windows 7....


thanks though guys!

---

