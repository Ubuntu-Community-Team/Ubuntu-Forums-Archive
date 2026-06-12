---
title: "Harmonizer / Scale Pitch Shifter"
date: 2008-11-23
forum: Ubuntu Studio
---

### Post by rekado on 2008-11-23
Aloha,
when I was using Windows mainly years ago I had a little VST plugin called DecaBuddy which was an okayish vocal harmonizer (or intelligent pitch shifter).
In Linux I figured making live music with the laptop is really convenient as all separate programs can be linked together without the need for one  platform that hosts everything. Unfortunately, I haven't any vocal harmonizer yet that would be more than just a simple (and I mean simple) pitch shifter. DecaBuddy fails to work in Linux, I've tried all methods to use VST dlls in Linux but it always crashed when trying to draw drop down menus or something.

All pitch shifters I've found miss feature of mapping to a scale, so they are useless for live usage. What I mean is: I cannot say that the pitch shifter should not simply shift my vocal input by 4 semitones but decide by itself if it needs to shift 3 or 4 semitones to correctly intonate a diatonic third. I would like to provide a lookup table, that the program would respect when shifting.

Do you know any pitch shifter that would allow scripting or even has a mappable output or something similar?

I've tried writing my own pitch shifter in PureData but failed (of course). Has anyone figured out a way to set up a vocal harmonizer? I would be very interested to know and try by myself.

---

### Post by rekado on 2008-12-02
Bump.

---

### Post by Stochastic on 2008-12-03
I'd say Rakarrack is your best bet: [http://rakarrack.sourceforge.net/](http://rakarrack.sourceforge.net/) as version 0.3.0 was just released, and it supports MIDI control of parameters.  It has a harmonizer, so all you need to do is feed the harmonizer value with an intelligent number from PureData's midi output... and voila!

or

There's also the Jost (vst / ladspa / dssi) host [http://www.anticore.org/jucetice/?page_id=4](http://www.anticore.org/jucetice/?page_id=4) that can accept MIDI messages as controller signals for plugins.  So a LADSPA pitch shifter, jost, and PureData patch would do it too.

---

### Post by rekado on 2008-12-03
Thanks for you input! I will check it out.
I just figured out that for PureData there is an object called plugin~ which enables the user to import a LADSPA plugin. In PureData I could measure the input frequency (monophonic as it's my voice), calculate the diatonic shifts according to scales and set parameters of several instances of imported LADSPA plugins.

Just need to find a fast LADSPA plugin that manages to shift a pitch and correct the formant in real-time at higher quality, but this shouldn't be too difficult. If I succeed one day I will share my results at this place.

---

### Post by Stochastic on 2008-12-03
There are quite a few different LADSPA pitch shifters.  I think the purely PureData route would be the best option as it would require the least setup every time you want to use it.

Where did you find the plugin~ object?  Is it part of pd-extended?

---

### Post by rekado on 2008-12-09
I found it here:

[http://quicktoots.linuxaudio.org/toots/pd-ardour/](http://quicktoots.linuxaudio.org/toots/pd-ardour/)

However, I haven't been able to test it as I was setting up my new Arch system the last few days (did it several times to learn more...). I will try it soon, though.

EDIT:
plugin~ seems to be a bit old and not so widely available. There is said to be an alternative which hosts both DSSI (virtual instruments similar to VSTi) and LADSPA plugins in PD:

[http://puredata.info/Members/jb/dssi%7E/view](http://puredata.info/Members/jb/dssi%7E/view)

I will try both soon.

---

### Post by rekado on 2008-12-25
Recently I checked out if pd + plugin~ + LADSPA pitch shifter would work for me. It actually did but was far away from a solution that could be considered anything near usable.
First I tried both pitch shifters that are contained in the SWH plugin collection from plugin.org.uk. There is a fast one and a slower one which offers better sound quality. Unfortunately neither of these worked well enough as they apparently do not offer formant correction. Doesn't go well for realistic choirs.

So I installed the TAP LADSPA plugins. Unlike the pitch shifters from plugin.org.uk the shifter contained in the TAP plugin collection ([http://tap-plugins.sourceforge.net/](http://tap-plugins.sourceforge.net/)) has no decimal pitch factor input but instead offers a simple semitone-based approach. You can simply feed a 4 to it's input to make it shift the input stream by a major third. The sound quality is surprisingly good and yet is not terribly hard on the CPU.

Unfortunately I couldn't get the logic around the plugin to work well. Basically, for a single-voice-harmonizer you just need a third added to the orginal signal. This means: either 3 or 4 semitones shifts according to a musical scale. Nothing too fancy. However, when I set it up just like that it reacted way too harsh, sometimes bouncing back and throw between a minor and a major third. Not quite musical. Anyway, I added the pd file so you have something to start a harmonizer patch with. I'd love to hear what you come up with.


Recently I tried to install the DecaBuddy VST once again and it worked with Savihost and wine. Really simple! Savihost is actually a Windows application but runs perfectly with Wine (you will need to copy two or three DLLs to the directory ~/.wine/drive_c/windows/system32). I just put the executable in the same directory as the DecaBuddy DLL and renamed *savihost.exe* to *DecaBuddy.exe*. The plugin doesn't crash anymore but the sound is horrible choppy and the microphone input is either distorted or simply ignored... yet have to work on it.



EDIT:
I managed to get DecaBuddy to work! It just seemed that my cheapo microphone for phone calls was not quite powerful enough. Feeding my soundcard with an AUX-way of my mixer works much better, the harmonizer seems to track the signal much better. Alternatively it also works to pump up the microphone signal by first feeding it to a tube amp simulation in VSTHost and then connect the "roasted" signal to the harmonizer.
It also was necessary to install the wineasio driver.

I sometimes experience some dropouts as if the CPU couldn't handle the load (actually it is as low as 7%) but that might be due to the non-realtime kernel I use.

---

### Post by JasonSilver on 2010-12-04
Do you mind describing a bit of a step by step on how to do this? I can't find anything using Google that will show me how to use PD with this harmonizer. I opened Jack, opened Puredata, then opened the harmonizer.pd in PD, but then what? What connections should I be making in Jack?

Thanks!

---

### Post by raboofje on 2011-01-15
> **rekado said:**
> I found it here:

[http://quicktoots.linuxaudio.org/toots/pd-ardour/](http://quicktoots.linuxaudio.org/toots/pd-ardour/)

EDIT:
plugin~ seems to be a bit old and not so widely available.

FYI, pd-plugin is packaged in [Debian Sid](http://packages.debian.org/search?keywords=pd-plugin&searchon=names&suite=all&section=all) and [Ubuntu Natty](http://packages.ubuntu.com/search?keywords=pd-plugin&searchon=names&suite=all&section=all).

---

### Post by raboofje on 2011-01-15
> **rekado said:**
> Unfortunately I couldn't get the logic around the plugin to work well. Basically, for a single-voice-harmonizer you just need a third added to the orginal signal. This means: either 3 or 4 semitones shifts according to a musical scale. Nothing too fancy. However, when I set it up just like that it reacted way too harsh, sometimes bouncing back and throw between a minor and a major third. Not quite musical. Anyway, I added the pd file so you have something to start a harmonizer patch with. I'd love to hear what you come up with.

Nice work!

I haven't had a chance to test with live input yet, but testing with a qsynth piano i noticed a bug in your patch that could explain this: the difference to the root note is is always rounded downwards. This means intonating only slightly too low will make the patch trigger the wrong interval.

Trivial fix attached.

---

### Post by raboofje on 2011-01-15
x

---

### Post by raboofje on 2011-01-15
> **JasonSilver said:**
> Do you mind describing a bit of a step by step on how to do this? I can't find anything using Google that will show me how to use PD with this harmonizer. I opened Jack, opened Puredata, then opened the harmonizer.pd in PD, but then what? What connections should I be making in Jack?
Select 'jack' in the pd 'Media' menu and check the 'compute audio' option on the main pd window. A pure_data input and output will appear in the 'Audio' tab of the qjackctl 'Connections' window. Route your audio into pure_data and pure_data's output to the soundcard (or your DAW or whatever you want).

---

