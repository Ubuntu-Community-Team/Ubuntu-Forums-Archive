---
title: "General Question About Plugins"
date: 2011-05-13
forum: Ubuntu Studio
---

### Post by xwindowsfan on 2011-05-13
what type synth or plugin would i need to make a guitar sound like other instruments, violin, piano, ect? I assume it would be audio or input triggered. free or commercial. 

as I am new to doing music with a PC, I find synth's the most confusing thing to work with. i Know a lot of them rely on MIDI. some are for post processing, some only do effect type synth. but I read some work with input and do specific instruments. i have yet to find an actual example of it.

I have yet to learn MIDI. my lack of knowledge as far as how synth's are routed and how they work can be summed up like this. when i run a synth with jack I notice under connections there is output but no input for the synth plugin. I assume therefore it's for post processing, or it must also be routed through MIDI.

so to narrow it down a, synth plugin or software that is audio triggered would be ideal. so I can just plug in the guitar and play with the knobs and presets.
if there is anything available or any knowledge of this is appreciated,

thank you. :rolleyes:

---

### Post by sgx on 2011-05-13
For now, this works ONLY with the great Yoshimi synthesizer, and for creative multi-timbral use, not 'shredding'!
Properly connect guitar to line in, preamp guitar as needed, get the cleanest signal possible

install

qjackctl
a2jmidid
libaubio
aubio-tools
yoshimi

start jackd similar to this 

 jackd -d alsa -r 44100 Chw:1 Phw:0,0 
 
(note, some setups may have  different capture/playback devices, or unique settings required)

run these commands

a2jmidid -j default

aubionotes -v -o -j

qjackctl

yoshimi

in the audio tab of qjackctl, connect

capture 1 + 2 --> aubio

yoshimi left + right --> playback 1 + 2

in the midi tab of qjackctl

(expand a2j) connect

aubio:aubio port --> yoshimi

now the crucial, and tricky part, in yoshimi gui, turn the yoshimi 'Velocity Sens' knob left, to about 20, 
and the 'Velocity Offset' knob slightly left, to about 56

now choose a sound you really like in yoshimi, because one must adjust these two knobs
slightly, to get the cleanest sound from each chosen sound, and write their settings down for future remembrance.

(change the Mode setting from Poly to Mono if needed)

enable more yoshimi sounds if your computer is powerful enough,
and put them all on midi channel one.

You can also learn to change the yoshimi envelope adsr settings to your guitar advantage, and resave a group of special presets.

Anyone discovering, or knowing of equivalent velocity controls on other instruments, may get usable results.

For synth knowlege, find a list of most popular synths on google,
and search youtube them, Massive, FM8, and linux zynaddsubfx, and dozens of others have tutorial videos. Joining
kvraudio.com is good if this will be a lifelong pursuit,
many specific forums there.
Cheers
(of course, a roland GR-55, or ztar, are the best options, $800
very well spent, I'm saving up for one)

---

### Post by barisurum on 2011-05-13
As I mostly play my synths with keyboard I've no idea on how to control them with audio but for a quick tour on some of the best linux synths, you may have a look at a video I made about some of KXStudio's audio plugins here:

[http://www.youtube.com/watch?v=l6ftjmyjQW4](http://www.youtube.com/watch?v=l6ftjmyjQW4)

The apps shown are:

Yoshimi (ZynAddSubFx based software synth with better JACK compatibility)
LinuxSampler-Qsampler (Software sampler with GIG and Akai format engines)
FeSTige (Frontend to FST, a program that makes VST plugins work under linux)
Aeolus (Very realistic chruch organ simulator)

---

### Post by xwindowsfan on 2011-05-14
:-({|=  "pardon me, would you have any shredding synths"? 

I saw an Al Di Meola concert on tv once about 20+ yrs ago. he was doing the whole "guitar sounds like bells" thing. he also had a sustainer strapped to the back of his neck. he definitely did some shredding with it and he was able to mix the sound of the bells with the guitars own sound. I'm sure there is hardware that can do this and it's certainly nothing new. it seems it never became very common in professional recordings. maybe more of a novelty.

perhaps I should have worded my question differently. I am looking for a software solution in whatever form it comes in, synth plugin, or a full program or what ever type app can do this. i just cant seem to narrow it down with google. Native Instruments has a bunch of synth programs but I have no idea where to start. it looks like the *KONTAKT* 4 PLAYER which does samples might do it. I'm sure there is something that will accept the input, synthesize it (effect or instrument), then output.

I'm sure i will try your suggestion sgx and thank you for such a detailed response. I also like Festige, barisurum. I watched the video and thank you as well.

---

### Post by sgx on 2011-05-14
> **xwindowsfan said:**
> :-({|=  "pardon me, would you have any shredding synths"? 

I saw an Al Di Meola concert on tv once about 20+ yrs ago. he was doing the whole "guitar sounds like bells" thing. he also had a sustainer strapped to the back of his neck. he definitely did some shredding with it and he was able to mix the sound of the bells with the guitars own sound. I'm sure there is hardware that can do this and it's certainly nothing new. it seems it never became very common in professional recordings. maybe more of a novelty.

perhaps I should have worded my question differently. I am looking for a software solution in whatever form it comes in, synth plugin, or a full program or what ever type app can do this. i just cant seem to narrow it down with google. Native Instruments has a bunch of synth programs but I have no idea where to start. it looks like the *KONTAKT* 4 PLAYER which does samples might do it. I'm sure there is something that will accept the input, synthesize it (effect or instrument), then output.

I'm sure i will try your suggestion sgx and thank you for such a detailed response. I also like Festige, barisurum. I watched the video and thank you as well.

Hi, if you want the audio notes you play on a guitar, to trigger
midi data that is then performed by a sound module, or software synthesizer, with bells, brass, strings, mood/arp/synth sounds yada yada, then my answer is accurate.

The Gr-55 is a fine audio2midi convertor, midi sound module,
guitar fx module, and audio interface all in one device. ztars are
a different type of midi controller, and require hardware or software
midi instruments or sound modules, to make music from the midi data.
 
If you want to play software synthesizers from a midi input device,
anything from mouse/qwerty to akai wind-controllers to 88key workstations, then you can choose from among hundreds of vst plugins, and several nice linux native synthesizers, yoshimi and phasex, are common.

I recommend Reaper, if you choose to use vst instruments in linux. It uses wine and wineasio for the framework of windows, and offers a full feature set, for using multiple instruments, and complex projects. Festige by design, is a usable, but very limited option.

I should mention, that in the aubio/a2jmidid/qjackctl setup, you can have both yoshimi, and a separate guitar fx processor, like rakarrack
or guitarix, connected in qjackctl, and play traditional guitar sounds with each note you pick, while yoshimi plays the synth sounds.

This is a rudimentary but free and useful way to do some of what the Roland engineers/coders, have spent so many years implementing in their new GR-55 and the earlier GR models.

A windows audio2midi app is at the link in the first post here

[http://www.kvraudio.com/forum/viewtopic.php?t=257146&postdays=0&postorder=asc&highlight=bertant&start=0](http://www.kvraudio.com/forum/viewtopic.php?t=257146&postdays=0&postorder=asc&highlight=bertant&start=0)

and can be used to play most any vst synth using a guitar. It's noisegate is important to adjust for optimum results. You could load this in Festige, maybe it will be a better option. 

Cheers

---

### Post by cchhrriiss121212 on 2011-05-14
You can use pure data to convert audio to midi:
[http://www.youtube.com/watch?v=OTl3C26v29s](http://www.youtube.com/watch?v=OTl3C26v29s)
PD is native on linux and works with jack, so you could hook up whatever synths you like.

---

### Post by Pablo_F on 2011-05-14
Rackarrack also has an (experimental as they say) audio to MIDI converter. In the example below you can use PureData or Aubio instead of rackarrack. And you can use any other synth instead of yoshimi.

Example jack connections:

Audio:
System.capture -> rakarrack input

MIDI:
rackarrack output -> Yoshimi input

Audio:
Yoshimi output -> System.playbacks


So, basically, you need an audio to MIDI converter and a synth. If they come together as a stand-alone app, or embedded in hardware, or as plugins that you can use in a DAW... is another question. 

BTW, I don't know if there is a good audio-to-MIDI LADSPA or LV2 plugin.

Cheers, Pablo

---

### Post by xwindowsfan on 2011-05-14
thank you for the invaluable information and the quick replies.

i will study it and experiment over the next few days, and let you know what I come up with.

thanks

---

### Post by sgx on 2011-05-14
I tried the rakarrack midi convertor for 'too long',
and was not able to attain anything a recording musician would find useful.

The Pure Data video example should also eliminate it from consideration. Floundering on a Macbook :confused:

Using the windows plugin from bertant in XP, I can record a nice synthpad or lead accompanying my guitar, in xp, choosing from among the many instruments, Synth1 being a favorite due to the great sounds available, and low cpu usage.

Using yoshimi, I can have several simple synth parts in mono mode
played by the guitar, and the guitar also sending to rakarrack, or
choose fewer, but more complex synth patches. I believe it is ram
and cpu limits kicking in, as the audio/midi conversion should benefit from a faster chip, and more crawl space. 

To get the most from yoshimi, one must spend a few hours with a notebook, choosing a 'top 100' type of sound list. There are banks
from Cormi, Laba170, Will Godfrey, and a fine and large unsorted batch of presets from the zynaddsubfx author, Paul Nasca, to be loaded using the 'parameters --> open' menu option.

[http://www.kvraudio.com/banks.php?s=list&what=1187&format=&order=date](http://www.kvraudio.com/banks.php?s=list&what=1187&format=&order=date)

 And then when
the jewels have been sorted, using the multi-timbrality to make
some nice layered sets, and save them using
Parameters --> save  menu.

Sloppily played guitar will be rewarded with merciless quantities
of blips and thuds, you can reduce these by using a custom set of strings, as uniform in size as possible, and by tuning the guitar higher, and grueling hours of practicing 'clean' picking. For melodies, one could even have an extra guitar with just 3 optimum strings with safety gaps in between. There are no rules in creativity. :o

---

