---
title: "Can't find JACK Audio Connection Kit at applications menu"
date: 2008-11-03
forum: Ubuntu Studio
---

### Post by groundnut on 2008-11-03
I have installed JACK Audio Connection Kit in order to communicate between Rosegarden and a soft synth.

After starting Rosegarden it says that the JACK server is not active.

I can't find JACK at the applications menu.

How can I activate JACK?

---

### Post by paulmerchant on 2008-11-03
The best thing to do is to install the QT Jack Control Interface to control your Jack sound server. You'll find it as qjackctl in the repositories.

---

### Post by groundnut on 2008-11-03
I have installed the QT Jack Control Interface.
After pushing the start button of the control interface, Rosegarden starts up without complaining about JACK. 

Very nice.

However now I get a new message about audio file import.

It says I need sox OR sndfile-resample.

Which one of the two programs should I use?
Where can I find it?

---

### Post by barisurum on 2008-11-03
Hi groundnut. I suggest installing sox because I couldn't find sndfile-resample in sndfile-programs package. Perhaps its in another package. But no need to bother, sox is found as sox in repositories. Install it with synaptic or in a terminal enter:

> sudo apt-get install sox

---

### Post by groundnut on 2008-11-04
I've installed sox. No more comments from Rosegarden.

Now the next step.

I don't want external instruments / controllers for my Ubuntu-Rosegarden setup. So I need software synthesizers or software samplers in order to be able to program music.

Any suggestions for software synthesizers / samplers?

---

### Post by markbuntu on 2008-11-04
ZynAddSubFX is what you want, Hydrogen for drums.

---

### Post by paulmerchant on 2008-11-04
You'll probably want to look closely at DSSI synths. They'll integrate most easily with Rosegarden.

I don't use Rosegarden or DSSI. The Linux softsynths that I enjoy are ZynAddSubFx, Qsampler, and Hydrogen. They can all be used with Rosegarden as external synths.

---

### Post by barisurum on 2008-11-04
> Any suggestions for software synthesizers / samplers?

For synths:
 
Alsa Modular Synth: good and flexible modular synth app
AmSynth: fat sounding analog modelling synthesizer with 2 oscs. Lacks some flexibility though, must combine with other plugins through jack.
Hexter: Yamaha dx7 modelling synth. Sounds good but you cant tweak anything, just use the sounds n thats all.
Bristol: Good project, bad implementation. Worth taking a look at though.
Aeolus: Superb sounding organ synth. Has lots of features.
Zynaddsubfx: Astonishing sounds! But unfortunately uses oss and doesn't work well with jack. There is a project that ports this to lv2. [http://home.gna.org/zyn/](http://home.gna.org/zyn/) Didn't try that.

For samplers:

Qsynth: Is a fluidsynth frontend which is a sf2 (soundfont) sampler. So you need fluidsynth too. Handy.
Linuxsampler/Qsampler: These two open gig files which are production grade quality. After all vienna symphonic library is gig!! ;)
Hydrogen: Drum machine and sampler that kicks *ss.

---

### Post by groundnut on 2008-11-06
Thank you very much guys for your comprehensive overview.

I've made the kick-off with hydrogen. The rest will follow.

In that process I lost the Rosegarden Transport bar. I could not fine it in the menu.

How can I restore the Rosegarden transport bar?

I managed to create patterns with Hydrogen. I can also stop and start them from the Rosegarden transport bar. But when I change the tempo in Rosegarden, Hydrogen will not follow. Also a change in tempo in Hydrogen is not reflected in Rosegarden. I guess I have to learn some more of 
Rosegarden first.

---

### Post by barisurum on 2008-11-06
> In that process I lost the Rosegarden Transport bar. I could not fine it in the menu. Just press T on the main project window and it will be visible.

> But when I change the tempo in Rosegarden, Hydrogen will not follow. Also a change in tempo in Hydrogen is not reflected in Rosegarden.

You have to sync the tempo between the two applications somehow. Like MMC it must be done with a midi message. Can't help you on this couse I never tried that between the two. If you find a solution please post it here.

---

### Post by markbuntu on 2008-11-06
You can sync the transport with jackcontrol, that's what its for. More on that here:

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

---

### Post by barisurum on 2008-11-06
I choose jack transport option in both applications. Yes rosegarden sends start/stop messages. But even if I make rosegarden as MTC and MMC master in preferences/MIDI/MIDI sync its not reflected to hydrogen's tempo. Its the same as MTC and MMC slave too. Hydrogen's tempo doesn't change rosegarden's. I connect the sync out of rosegarden to hydrogen MIDI in. But I think there must be a sync in port of hydrogen to be able get those tempo change messages and there isn't. Perhaps its the problem we have here.

---

### Post by groundnut on 2008-11-07
thanks markbuntu,

I succeeded the tutorial of your first link: HowToQjackCtlConnections.
However the second link does not work.

I made all possible connections between Hydrogen and Rosegarden (both the audio and the alsa tab of the connections window).
However it did not work. I can't change the tempo from one of the application into the other.

---

### Post by markbuntu on 2008-11-07
I'm sorry about that link, I have not checked those in a while, try these:

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

---

### Post by groundnut on 2008-11-09
thanks markbuntu,

I've read the three links. At this time I'm not able to solve the tempo problem. So I leave the topic for the time being. Instead I will study Rosegarden itself first.

---

