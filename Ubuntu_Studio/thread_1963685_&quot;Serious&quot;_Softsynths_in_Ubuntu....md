---
title: "&quot;Serious&quot; Softsynths in Ubuntu..."
date: 2012-04-22
forum: Ubuntu Studio
---

### Post by sirriffsalot on 2012-04-22
Hello!

I've gotten very much into recording with Linux, and am more or less satisfied with the overall gist, but what is tempting me to go the easy road and get involved with Pro Tools et cetera instead is that all the synth sounds I can come across anywhere are just too silly or unsuited for what I want to do... Some suggest, to get what I'm after, that I program things myself, but frankly I lack as much interest as effort and prioritizing for that..

In other words this is a last attempt to see if there are some quality synths out there for a  guy sitting with a midi-keyboard at his disposal and Ubuntu, haha :-) In the beginning of the song "Celestial Furnace" by Disarmonia Mundi, there are synths going on which are an example of what I would be after.. Calm, unscreeching and mellow synths in many varieties is what I'm after.

Any suggestions that won't take weeks to master are more than welcome, and I appreciate your time!!

---

### Post by sgx on 2012-04-22
zynaddsubfx and the newer yoshimi version, world class in the
opinion of many windows zealots. Get extra banks at

[http://www.kvraudio.com/banks.php](http://www.kvraudio.com/banks.php) (click 'choose product'
and scroll to Z section)

Whysynth  use the many included Kawai K4 sounds 

Hexter  great fm synth sounds, get the sysex banks 'deckard.zip'

[http://www.abdn.ac.uk/~mth192/html/dx7.html](http://www.abdn.ac.uk/~mth192/html/dx7.html) scroll down some

Deckard should have most in one archive, loads in hexter in 32
sound groups.

qsynth gui for fluidsynth, and quality soundfonts from e-mu and other sources.

phasex -read up and experiment using audio input as oscillators!

Calf Monosynth, a real jewel when used with FX

FalkTX will be releasing TAL Noismaker and others in LV2,
real soon, great instruments/fx

Spend a week, take notes of great sounds, and make use of
the rakarrack multi-fx app, and calf plugins etc

Combined with bass runs and drums done in Hydrogen, you can
do it all.

Pro-Tools can be a freaking nightmare, Reaper works as a
daw with wine and wineasio, alongside the above. There really are
no shortcuts, 5% of commercial presets will be to your liking.

Often the most expensive commercial synths are packed with many
proof-of-concept presets that are unusable in songs you will create.
Save your money, by thorough demo testing before $$$.

Native Intruments synths have generous
30 minute demos, just restart for more 30 minute demos,
and the installers work in wine.
Cheers

---

### Post by sgx on 2012-04-22
[http://www.kvraudio.com/forum/viewtopic.php?t=347569](http://www.kvraudio.com/forum/viewtopic.php?t=347569)

[http://www.kvraudio.com/forum/viewtopic.php?t=347569](http://www.kvraudio.com/forum/viewtopic.php?t=347569)

Read these two topics, about Omnisphere, some crucial composing advice,
and pro/con opinions, that serve well, applied to all instrument
choices, purchases, and production attempts.

Cheers

---

### Post by sirriffsalot on 2012-04-23
Hello again sgx, thanks for pitching in once again, I appreciate it!

Great package of suggestions there, looking into them now. Only trouble is, I am about as fresh as can be involving this, so while I can more or less use ZynAddSubFX with the mentioned extra packages, I am still quite unsure as to where the rest of the packages should go, what programs to be used, how to use it (having difficulty finding manuals for a lot) and the terminology in the first reply. Thanks for everything and anything beyond!! 

--> Leo

Edit: also, since you mentioned I will probably only find 5% of the preset synths to be what I want, is there somewhere I can learn to program synths...? I might as well try to learn how.. I hope it isn't too hard :-)

---

### Post by Sylos on 2012-04-23
Hello there.

A lot of the time you wont find a great deal of documentation on using the applications - a lot is just trial and error for the uninitiated. I would recommend just hooking up your Midi keyboard and then loading hexter or whatever and then just link it in Qjackctl and give it a bash.

As for information on how to fiddle with synths - sound on sound had some good articles you should have a read of.

[http://www.soundonsound.com/sos/allsynthsecrets.htm](http://www.soundonsound.com/sos/allsynthsecrets.htm)

I've only just started fiddling with synths myself so will soon also be trying out hexter, calf organ etc etc. I have found Zynaddsubfx to pretty awesome but I really dont understand how to get the best out of it. I normally just pick a preset and then start twiddling knobs and adding/subtracting stuff. The great thing with Zynn is you can use multiple presets at once and mix them together.

Happy synthing. :guitar:

---

### Post by Precipitous on 2012-04-23
> **LeoTB said:**
> Hello!

I've gotten very much into recording with Linux, and am more or less satisfied with the overall gist, but what is tempting me to go the easy road and get involved with Pro Tools et cetera instead is that all the synth sounds I can come across anywhere are just too silly or unsuited for what I want to do... Some suggest, to get what I'm after, that I program things myself, but frankly I lack as much interest as effort and prioritizing for that..

In other words this is a last attempt to see if there are some quality synths out there for a  guy sitting with a midi-keyboard at his disposal and Ubuntu, haha :-) In the beginning of the song "Celestial Furnace" by Disarmonia Mundi, there are synths going on which are an example of what I would be after.. Calm, unscreeching and mellow synths in many varieties is what I'm after.

Any suggestions that won't take weeks to master are more than welcome, and I appreciate your time!!
I work on highly textural dark ambient music and also had a hard time finding Linux soft synths that were as powerful as I wanted... 

I solved the "problem" by using [SAVIHost]("http://www.hermannseib.com/english/savihost.htm") to run Windows VST's using Wine/WineASIO. It is incredibly simple to set up, works with everything I have thrown at it, and most importantly - works with Jack!

---

### Post by sgx on 2012-04-24
> **LeoTB said:**
> I am still quite unsure as to where the rest of the packages should go, what programs to be used,

is there somewhere I can learn to program synths...? I might as well try to learn how.. I hope it isn't too hard :-)
Use synaptic to install dssi, hexter and whysynth. Then look in
/usr/bin for

jack-dssi-host and look in

/usr/lib/dssi for whysynth.so and hexter.so
note 'whysynth' is not 'wysynth'

In the main menus, look for entries for hexter and whysynth.
If there are no entries, open a terminal, and type

jackd -d alsa -r 44100
In another terminal type

/user/lib/dssi/hexter.so

Now start qjackctl, jackd is already running, open the Connections panel, hexter should be in the Audio tab, and the alsa tab. Select it, and the desired connection on the opposite
side of that panel.

Phasex, when installed, should be in a menu, or start by

/usr/bin/phasex

Calf plugins can start with /usr/bin/calfjackhost
(to access calf monosynth)
rakarrack with /usr/bin/rakarrack  etc etc look in /usr/bin,
it's like C:\Program Files in windows.

for sound design, join [www.kvraudio.com](www.kvraudio.com) and use this forum

[http://www.kvraudio.com/forum/viewforum.php?f=100](http://www.kvraudio.com/forum/viewforum.php?f=100)

and the modular synthesis forum to ask, and study.

The pdf ebook 'how to make a sound', holds a link to a pdf book on sound design, go the link below, and scroll down a bit

[http://noisesculpture.com/how-to-make-a-noise-a-comprehensive-guide-to-synthesizer-programming](http://noisesculpture.com/how-to-make-a-noise-a-comprehensive-guide-to-synthesizer-programming)  (Trade email address for the download link) Much of the example content will apply to linux synths, whysynth and monosynth can both be open while you
follow along turning knobs in careful amounts.

Savihost with wine/wineasio is a good approach, like
making standalone versions of windows plugins! I use reaper,
but will follow Precipitous lead, on some favorites.

---

### Post by sirriffsalot on 2012-04-28
If it works for me too, I am sure that'll be just splendid! Thanks a lot for the tip!

---

### Post by sirriffsalot on 2012-04-28
Gotta love the ubuntu/linux community... All I can say is thanks times however the end-result of my linux-musical ventures turn out :-)

---

### Post by sirriffsalot on 2012-05-13
Hey!

Finally gotten around to try your suggestion, but I'm a bit stuck at getting the connections right... Not a lot of coverage on the Internet as far as I have found, could you summarize what you did from after installing to playing the keyboard happily?:)

--> Leo

Edit: In fact, I was running the wrong one... SAVIhost as you mentioned I can't even get running with wine, haha! :)

---

### Post by sgx on 2012-05-13
Hi,
open qjackctl  (jackd autostart is turned off in my prefs)
choose settings (different ones for guitar Vs keyboard)
and press start

I have the reaper folder in the /home/Leo folder, and start it from a terminal command:

wine reaper/reaper.exe

this sometimes gives a clue to a missing .dll file, or missing font etc

Asio, and asio driver (wineasio) must be chosen in reaper
Device prefs

midi ports must be activated in reaper midi prefs

vsts must have their path chosen, then scanned, in reaper Vst prefs.
Separate different paths with a semi-colon, but no spaces.
The reaper Vst prefs dialogue will do that,
for each extra path you add

Reaper scans again on startup. if any change is detected,
so quit and restart, or double click the 'clear cache and rescan'
button. A few bad apples vsts will hang the scan process, just
restart reaper, and it will skip the bad apple.

Reaper should auto-connect to your soundcard in the
qjackctl Audio tab. 

Asio_reaper---Asio_reaper
System----------System

a big  X  will be drawn, to cross-connect System to the Asio_reaper in and out ports.  System is your soundcard

You can send Asio_reaper on the left, to a linux fx app input you open, which will appear on the right,
highlight both choices, and press Connect

Then connect the fx output on the left side, to System on the right side.

If you want to record, run Timemachine, and connect reaper and or the fx outputs to it,
then press its giant record button when ready to make history.

Same process to use hydrogen drum machine, or a linux synth with fx,
multiple Hexter (yamaha DX7 clone) are awesome with rakarrack

So you could record guitar with both Guitar Rig (via reaper)
and Rakarrack (via linux) using the one qjackctl gui.

When recording usb guitar, choose qjackctl Periods/Buffer of 3,
for non-usb midi keyboard, 2 or 4 

Rakarrack has an unobtrusive 'fx_on' button, that is off by default,
so make sure its on, or you'll only get an old Simon & Garfunkle song

Feeding constant sound to the computer during the connections process means you will hear success, so a loudly humming guitar amp, etc should be audible at the magic click :popcorn:

Cheers

---

### Post by Precipitous on 2012-05-14
> **LeoTB said:**
> Hey!

Finally gotten around to try your suggestion, but I'm a bit stuck at getting the connections right... Not a lot of coverage on the Internet as far as I have found, could you summarize what you did from after installing to playing the keyboard happily?:)

--> Leo

Edit: In fact, I was running the wrong one... SAVIhost as you mentioned I can't even get running with wine, haha! :)
To use [SAVIHost]("http://www.hermannseib.com/english/savihost.htm") you MUST have the Wineasio driver installed and registered. Depending on the version of Wine/Wineasio you are running you may need to open the Wine Configuration tool and set the audio output to Jack (this is not necessary on the latest versions to my knowledge). After this follow the instructions on the [SAVIHost ]("http://www.hermannseib.com/english/savihost.htm")website to get it set up for a specific soft synth...  

To run the synth start Jack, then run the soft synth .exe file. When the synth opens (in a SAVIHost window) check to make sure it is available to Jack. If it is, check to make sure you get audio output from it. If you do not get any audio output, go to the Device menu (in the SAVIHost window) and set the MIDI input and the WAV output. The MIDI input will be whatever device you are using to transmit MIDI data to it. The WAV output should probably be set to MME Default (at least that works for me). If the synth is not available to Jack at all, you probably do not have the Wineasio driver installed and registered properly.

---

