---
title: "More thoughts on Audacity"
date: 2012-11-09
forum: Ubuntu Studio
---

### Post by tnob on 2012-11-09
Quote:
1. *Hi, select jackd as the audio device in audacity preferences.*
2. *Select your soundcard in qjackctl. (see recent jackd topics in this forum) *
3. *For now, start a constant sound source, modest volume, and connect it to your soundcard line-in. Start qjackctl, and press the Connect button, on the main screen, lower left. A panel opens with three tabs, select the Audio tab on the left.*
4. *Start Rakarrack, and change it's output preferences to stereo, if desired. (You open its preferences, select by mouseclick the un-highlighted half of the output). Press Rakarrack 'FX On' button under the file menu, to start the fx.*
5. *Back in qjackctl Audio panel, select System on the left half and select Rakarrack on the right half, and press connect, (on this Connection panel, not on the opening GUI) a line is drawn to designate connection. (If you now click the > widget by System, the System outputs will be fully exposed, and you will see lines are displayed for both left and right of stereo signals).*
6. *Select Rakarrack on the left half, and System on the right half, and press connect, again, a line is drawn. (If you clicked the > widget mentioned above, you must now manually connect the other half of the stereo pair).*
7. *Now your constant sound should be played, in stereo, through Rakarrack, into your soundcards speakers or headphones, 4 lines crisscrossing the gui indicating connection.* 
8. *To record, start Audacity, but don't create a track, just press record, and it automatically connects in qjackctl, creates a track, and begins recording the dry, unaffected sound, using the nickname 'portaudio', on the right side of the panel. (Now 6 lines are drawn in the qjackctl gui.)*
9. *To record Rakarrack output, connect Rakarrack on the left, to Portaudio on the right. If you don't want the 'dry' signal also recorded, disconnect System on the left, from Portaudio on the right. The choice is yours.*
10. *Pressing pause in audacity, just pauses recording until you press pause a second time. Pressing 'stop', and pressing record again, launches a new track to record on. Use the option best suited to your work (the latestversion of Audacity I have is 2.02).*

[I]I prefer the simple timemachine for basic high quality recording and import the tm-xx-xx-xx.w64 recordings into audacity, for editing, conversion, and export.

Media players like aqualung, vlc, xmms, xine etc with the jackd module installed by synaptic can play an audio file into timemachine, using the same connections process, while you record a second part, with the first, a simple but quality 24 bit overdub.

Some media players only appear in qjackctl when you press play, so press play, then press pause in the player, make your connections, press Record in timemachine, and press play again (or pause a second time, depending on the players implementation.) and you are rwadt to overdub.

This is all simple, after the third or fourth time, but the results are excellent. Well, 20th and 21st, for me.
[/I]Unquote

Greetings all,

A question I posted some time ago was about **linking Audacity and Rakarrack **(**Audacity 2.0.0 Unicode** and **Rakarrack Audio F/X 0.6.1,** to be exact). In response, sgx contributed the excellent tutorial above, quoted here in full ( I took the liberty to polish it up a bit, graphically, and to add numbering).

At the time, Audacity was still not functioning (my desktop an ancient Dell Optiplex, carrying Ubuntu DreamStudio 12.04 ELT, by the way), due to some annoyingly persistent PC/Audacity input and output issues. It took rather a while to sort these out - and a little help from a friend as well  - but I'm happy to report that, at present, Audacity is fully working.

I haven't yet come around to following up sgx's suggestions, though - partly since a few questions remain:

[LIST]
[*]Audacity is not a Qjackctl client, to my understanding, so I don't quite get why Qjackctl is still required to link Rakarrack to it. Because Rakarrack is one, presumably?
[/LIST]
[LIST]
[*]Does the tutorial quoted also apply to Drumstick Virtual Piano and Hydrogen? Piano and drums, in addition to bass already available in Rakarrack, would be really handy to have!
[/LIST]
[LIST]
[*]As to 2., in the tutorial: where should I go to in order to find out what sound card I have?
[/LIST]
[LIST]
[*]As to 6., in the tutorial: is the choice between stereo *or* mono? Or could it also be stereo *[I]as well as*[/I] mono, depending on requirements?
[/LIST]
[LIST]
[*]If I opt for stereo here, which set of icons will represent *the other half of the stereo pair*?
[/LIST]
[LIST]
[*]As to 8., in the tutorial: Qjackctl **GUI** is mentioned here, but even after some quick research, I still don't quite grasp what GUI actually refers to, in this context.
[/LIST]
[LIST]
[*]As to 9. but also related to 6., in the tutorial: Audacity will be in use as either a] an auxiliary to incredibly sturdy analogue four-track hardware (Tascam Porta 2) of more than 25 years old, newly restored (in order to preserve my four-track audio cassette archive for posterity, amongst others); b] as a multitrack device in its own right; or c], to transfer other stereo audio content to .wav or .mp3. With this in mind, FX from Rakarrack may be added during recording, in mono - a] & b] - during mixing, in stereo - c] - or in view of sprucing up standard stereo audio content - also c] - depending on requirements. Accordingly, I'll probably be toggling between mono and stereo all the time. So once more thinking of 6., in the tutorial: how now to avoid mono and stereo connections in Qjackctl "biting" each other (if this is indeed the case)?
[/LIST]
[LIST]
[*]How do I upgrade Audacity to the latest version available?
[/LIST]
[LIST]
[*]I may need Audacity too on a separate Windows unit (with some essential music notation software not available on Ubuntu in mind). Which makes me wonder: are Ubuntu and Windows versions compatible?
[/LIST]
 
In my experience, Audacity is certainly not the 'plug'n play' miracle as I've seen advertised on the web, in various places. But once it's up and running, I find it most pleasingly versatile and - even more importantly - far more user-friendly, essentially, than Ardour, for instance (as far as I'm concerned, anyway). Ardour is the other DAW I tried to get to grips with - and it caused me some pretty bad headaches indeed, in the not so distant past.

The factor Ardour and Audacity seem to have in common, in my opinion, is that setting up audio is so dreadfully complicated to begin with. And maybe this applies to Ubuntu in its entirety as well: it's crammed to the rafters with stuff to a musician's heart's content - but it usually takes some considerable sweat before it'll be seeing action for real, I'm not surprised that many people not too well versed in IT jargon, like myself, will be looking elsewhere before soon - which is a pity, really, since Ubuntu is excellent in almost every other respect (another major pain in the backside video capturing devices, now I come to think of it).

Finally, I'd like to draw your attention to a wonderfully educational blog on all things Audacity. Andrew Mercer's is now the first I'll turn to for many a subject I'd like to learn more of (go to [http://www.andrewmercer.ca](http://www.andrewmercer.ca) or [http://www.freeaudacitytutorial.com/](http://www.freeaudacitytutorial.com/)). I think he is a great teacher, his video tutorials invariably classy, to the point and very helpful.

The latter are also available on YouTube. Just type in 'audacity' - or, better still, 'audacity andrew mercer' - to have all those neatly together, over three pages. 

I'm not sure there'll be much for the (super) advanced amongst us in those, but they are certainly worth a look!

tnob

---

### Post by tnob on 2012-11-09
[FONT="Arial"] A small addition - or correction, if you like -to sgx's tutorial (under 1.), from another post related to this discussion: I noticed it only after placing my longer contribution above. [/FONT]

[FONT="Arial"]Quote:
1. [I]Hi, select jackd as the audio device in audacity preferences.
Start jackd first, so it can be seen in the device options. If it is not running, alsa and oss are the choices. In my case, when jackd is already running, and I start audacity, it is chosen as default, and shows no other options. Then, press record button in audacity, and it appears in qjackctl as 'portaudio', on the right side of the Audio tab.
This is using V2.02 of audacity, and libportaudio.so.2 One must admit, this all seems a bit too convoluted. But there may be a purpose to the madness, from the coders' point of view, that we musicians do not know.[/I]
2. *Select your soundcard in qjackctl. (see recent jackd topics in this forum) *
3. *For now, start a constant sound source, modest volume, and connect it to your soundcard line-in. Start qjackctl, and press the Connect button, on the main screen, lower left. A panel opens with three tabs, select the Audio tab on the left.*
4. *Start Rakarrack, and change it's output preferences to stereo, if desired. (You open its preferences, select by mouseclick the un-highlighted half of the output). Press Rakarrack 'FX On' button under the file menu, to start the fx.*
5. *Back in qjackctl Audio panel, select System on the left half and select Rakarrack on the right half, and press connect, (on this Connection panel, not on the opening GUI) a line is drawn to designate connection. (If you now click the > widget by System, the System outputs will be fully exposed, and you will see lines are displayed for both left and right of stereo signals).*
6. *Select Rakarrack on the left half, and System on the right half, and press connect, again, a line is drawn. (If you clicked the > widget mentioned above, you must now manually connect the other half of the stereo pair).*
7. *Now your constant sound should be played, in stereo, through Rakarrack, into your soundcards speakers or headphones, 4 lines crisscrossing the gui indicating connection.* 
8. *To record, start Audacity, but don't create a track, just press record, and it automatically connects in qjackctl, creates a track, and begins recording the dry, unaffected sound, using the nickname 'portaudio', on the right side of the panel. (Now 6 lines are drawn in the qjackctl gui.)*
9. *To record Rakarrack output, connect Rakarrack on the left, to Portaudio on the right. If you don't want the 'dry' signal also recorded, disconnect System on the left, from Portaudio on the right. The choice is yours.*
10. *Pressing pause in audacity, just pauses recording until you press pause a second time. Pressing 'stop', and pressing record again, launches a new track to record on. Use the option best suited to your work (the latestversion of Audacity I have is 2.02).*

[I]I prefer the simple timemachine for basic high quality recording and import the tm-xx-xx-xx.w64 recordings into audacity, for editing, conversion, and export.

Media players like aqualung, vlc, xmms, xine etc with the jackd module installed by synaptic can play an audio file into timemachine, using the same connections process, while you record a second part, with the first, a simple but quality 24 bit overdub.

Some media players only appear in qjackctl when you press play, so press play, then press pause in the player, make your connections, press Record in timemachine, and press play again (or pause a second time, depending on the players implementation.) and you are rwadt to overdub.

This is all simple, after the third or fourth time, but the results are excellent. Well, 20th and 21st, for me.
[/I]Unquote[FONT="Arial"][/FONT]

---

### Post by jejeman on 2012-11-09
> I may need Audacity too on a separate Windows unit (with some essential music notation software not available on Ubuntu in mind). Which makes me wonder: are Ubuntu and Windows versions compatible?They should be.
>    As to 2., in the tutorial: where should I go to in order to find out what sound card I have?In Qjacktl open settings. On the far right column you choose sound card.
command 
```
aplay -l
```
list you playback devices
 >    Audacity is not a Qjackctl client, to my understanding, so I don't quite get why Qjackctl is still required to link Rakarrack to it. Because Rakarrack is one, presumably?Qjacktl is GUI for JACK server. So Audacity can be JACK client not Qjacktl's. Only way to link Rackarrack and Audacity is thru JACK server, even that Rackarrack can work with just ALSA, which of course can't.
>     Does the tutorial quoted also apply to Drumstick Virtual Piano and Hydrogen? Piano and drums, in addition to bass already available in Rakarrack, would be really handy to have!If you refer on connecting applications, then yes.
>     As to 6., in the tutorial: is the choice between stereo or mono? Or could it also be stereo as well as mono, depending on requirements?You connect what you need. You can expand the view to see the list of all available inputs/outputs for speciffic application. Then, you connect what you need, like in real studio.
    > If I opt for stereo here, which set of icons will represent the other half of the stereo pair?All ports in JACK are mono (1 channel). Looking at their names you can see which are (stereo) pairs.
>     As to 8., in the tutorial: Qjackctl GUI is mentioned here, but even after some quick research, I still don't quite grasp what GUI actually refers to, in this context.It is the Qjackctl it self, the connections window.
>     How do I upgrade Audacity to the latest version available?1. Upgrading Ubuntu version, if it holds new Audacity version
2. compiling the source code by your self.
3. find already compiled version in some PPA on launchpad.

---

