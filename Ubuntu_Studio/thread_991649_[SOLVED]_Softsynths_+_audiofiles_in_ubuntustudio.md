---
title: "[SOLVED] Softsynths + audiofiles in ubuntustudio"
date: 2008-11-24
forum: Ubuntu Studio
---

### Post by Rubuler on 2008-11-24
Greetings all,

New to linux audio, could use some quick guidance.

Wondering if i can get an environment comparable to logic/cubase going on in linux.

Id like to work with softsynths/samplers in sync with audiofiles. Ardour looks interesting but i see theres no virtual instruments.

I`m assuming I`ll be using some type of ext sequencer to power my synths, and audio from synths will be recorded to an ext DAW (ardour?). From what i gather, JACK is what brings this all together.

I think what im looking for is a little reassurance that learning how to get all this going will give me a practical workstation.


example of what id like to do:

load drumloop, probably change tempo of sample and slice it up

sequence my own drums in sync with loop

sequence synths

use effects plugins


can someone suggest a setup for me to learn that will allow me to use and edit all these elements in realtime?


Thanks in advance.

---

### Post by markbuntu on 2008-11-24
You want ardour/jack. Rosegarden for midi synths. Hydrogen for drums. ZynAddSubFX for a soft synth. Jackrack for effects. These can all be connected together in pathcage and synced up from jack control so you can have your synth and drum loops playing in their own apps but into ardour where you can add your audio tracks. You can hook your midi instuments into rosegarden and play along/record with the tracks in ardour. jackrack can be used anywhere you want on the audio, on indivudual tracks or sub masters or master tracks.

First, you need UbuntuStudio and read all the how tos and tutorials you can find. here are a few links to get you started;


[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

If you are wondering how to sync applications together through jack. 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

---

### Post by Rubuler on 2008-11-25
Thank you very much for the great answer, I love reading audioproduction instruction manuals, been a few years since i curled up with a good one, should keep me busy for a while.

One more question, Im aware of the recording issues and lack of rt kernel in 8.10, do these issues apply to recording live audio only? Im just gonna be using software, is recording softsynths the same as recording live audio? Im running US 8.10 at the moment, will i have to go back to 8.04 to be able to work? and if soo, is there an easier way than doing a clean install? Will just installing the rt kernel in a terminal allow me to work in 8.10? Have I broken the record for most questions ask in a paragraph that starts with the phrase "One more question"?

---

### Post by markbuntu on 2008-11-25
I expect that the rt kernel will be available soon in 8.10 and there is already a patch available. There is a thread about it around here somewhere. The rt kernel is not strictly necessary and your success depends a lot on how you use your applications. If you run into problems then the rt kernel might help.

---

