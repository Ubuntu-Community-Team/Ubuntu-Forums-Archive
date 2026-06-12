---
title: "Wobble bass in ZynAddSubFX"
date: 2010-02-14
forum: Ubuntu Studio
---

### Post by g-raf on 2010-02-14
Does anyone know how to make a wobble bass in ZynAddSubFX? I'm not sure how to activate a key sync or if it's even possible in ZynAddSubFX.

A "wobble bass" is when the bass changes to different waveforms at every note. This tutorial for a closed-source program gives an example of wobble bass:

[http://www.youtube.com/watch?v=nZYDmw2pYOk](http://www.youtube.com/watch?v=nZYDmw2pYOk)

Please give me some ideas.

---

### Post by hardcopy on 2010-02-14
unfortunately you cant automate things like lfo frequency and waveforms in zyn- you could try automaing the wah effect on an effect insert in zyn but that uses nrpn messages for control so would be quite time consuming to program. your other option would be to setup a different voice for each different wobble so you can trigger them seperately.

at least im not alone in wanting these sorts of parameters automated- zyn can make some amazing sounds i just want more control.

edit: it seems theres some development of midi control in the works, not sure how far along it is though

---

### Post by g-raf on 2010-02-14
> **hardcopy said:**
> unfortunately you cant automate things like lfo frequency and waveforms in zyn

You can change the LFO frequency and waveforms. Go to "edit instrument" and then click on the "addsynth" and edit it. There is an envelope for change the waveform. In the voices list, you can make up to about 10 different waveforms and detune them, etc. I've tried this stuff, but still can't get the bass to wobble and i think it's because there's no key sync - where each note plays a different waveform on each touch of a key. I'm not too knowledgable on these things, but continuing to experiment.

---

### Post by hardcopy on 2010-02-14
yep what i meant is you cant change those controls via midi- only manually

to get the wobble change the amplitude adsr (and filter adsr for that sweeping sound) or use the lfo with depth set to full. the lfo can be synced to start the same with each keypress, or just cycle independantly, this setting is a checkbox

the controls can be a little fiddly to get the right rates but it is possible to make all kinds of dubstep/dnb bass sounds with zyn so just keep fiddling :)

---

### Post by g-raf on 2010-02-15
> **hardcopy said:**
> to get the wobble change the amplitude adsr (and filter adsr for that sweeping sound) or use the lfo with depth set to full. the lfo can be synced to start the same with each keypress, or just cycle independantly, this setting is a checkbox

Thanks. This really helped a lot. I've got somewhat of a wobble now, but it's not the greatest. The checkbox (i think it says "continuous LFO" or something) helps. I got one more little question that i haven't figured out by experimenting yet: there is the global instrument filters/amplitude/frequency and then each "voice" has it's own LFO filters/amplitude/frequencies...were you referring to the global instrument or experimenting with each voice seperately?

---

### Post by hardcopy on 2010-02-15
its probably best to stick with the global instrument until you understand it better and want to make some really complicated patches, they all should work the same (just on a different 'level' of the patch). be careful that your adsr envelopes arent interfering with the lfos (keep the attack short, just enough to stop from getting clicks)

im pretty sure that with lots of voices, and careful programming you could make just one bass that when you hold a key down would go:

wow-wow-wow-waaaaaarrrb-wooow-wooow-warb-warb-wu-wu-wu

etc :D

personally i'd prefer to automate the lfo rate or just use seperate instruments for each type of bass to prevent headaches if you need to alter tempo, or want different notes, or whatever

---

### Post by g-raf on 2010-02-21
> **hardcopy said:**
> im pretty sure that with lots of voices, and careful programming you could make just one bass that when you hold a key down would go:

wow-wow-wow-waaaaaarrrb-wooow-wooow-warb-warb-wu-wu-wu

etc :D

I came up with something like that. If you want to hear it, go to [www.myspace.com/w0rkerant](www.myspace.com/w0rkerant) and listen to the "Fornication Conscious" track. Let me know what you think of that wobble.

I used about 4-5 voices and half of them had different waveforms, all detuned except one. Your advice on the filter & amplitude ADSR, LFO depth and the checkbox really helped me.

After much more experimentation, i hope to make a video tutorial on how to make a wobble bass in ZynAddSubFX and upload it on youtube. Let me know if you're interested in doing it together.

---

### Post by Monona on 2010-02-21
Here's a different tutorial, although for closed source software:

[http://www.mashit.com/2007/10/27/tutorial-bass-research/](http://www.mashit.com/2007/10/27/tutorial-bass-research/)

Might be helpful.  

I'd love to see the zynaddsubfx tutorial, if you get it going!

---

### Post by hardcopy on 2010-02-21
I had a quick listen.. your music is crazy raw, but i think i like it, maybe you're overdoing the samples heh

From what i can hear i think you should be able to focus your sounds more with a little help.

i've made a quick wobble bass patch for you to try out, but rather than just give you the patch file (that would be too easy) i'm attaching a zip with a screenie of the instrument in zyn along with a reference audio mp3....

its a simple patch but i think it shows quite well the different elements to a wobbly bass, here's the notes for the picture:

1: adsynth oscillator editor
I started by making a suitable tone- the waveform looks quite messy, but I find that the sound is more important than the look. The harmonics are very important to bass sounds- it's good to make the high frequency content of a sound dependant on harmonics rather than faking it by overdoing the filter resonance. A great feature here is the waveshaping dropdown box (wsh), the settings give lots of scope for different sounds.

2: ADSR envelopes
To prevent clicks I added a little attack time on the amplitude envelope. The filter envelope is to create the first wow sound.

3: LFO's
First i added a little delay so that the initial envelope wow is not affected by the LFO. I synced (manually) the amp & filter LFO frequencies so that they work together. The amp LFO is at full depth but the filter LFO is quite low, just to add interest. By using a different wave type on the filter LFO the wobble on the bass is very noticable.

4: Distortion
To bring out the nasty side of the bass I added a little distortion. I didnt want to go over the top so i used the gain of the filter section to increase the level going to the distortion, and then added a tiny bit of drive once I had selected the distortion type i wanted.

Tell me what you think :)

---

### Post by g-raf on 2010-02-24
> **hardcopy said:**
> Tell me what you think :)

I took your patch and used something similar. Maybe i experimented with it too much. I used diode waveforms and created a oscilator waveform similar to yours, but then i added 3 more voices (power, sine and plain diode) and detuned all of them. I used no insert effect, but i did use phaser 3 in the main zynaddsubfx effect panel. 

This is my first time putting an attachment on an ubuntu forums message. I think the mp3 of what i got is attached though.

Your wobble sounded great. 

The one thing i really wanna do is make the wobble change with each hit of a key. Do you know how to do that? I tried using the "continuous LFO" checkboxes this time, but it didn't work. Each key hit gave me the same sound (but in different notes of course). 

It seems possible to create wobbles with any kind of waveform too. I'm going to keep experimenting to see what kind of sounds each waveform gives me.

---

### Post by g-raf on 2010-02-24
Here's another wobble experiment. Included a screen this time.

---

### Post by neu2buntu on 2010-02-26
HI, I too have been trying to get the "Wobble Bass" using ZASF and i think i am getting very close, i will be working on this until i perfect it. I have came to the conclusion that you must draw in your own filter envelope and the modulator is set to PM with a sine wave as its oscillator, there are loads of ways of fattening the sound up, by detuning and also using unison for each separate wave... i will attach the files (im doing this in LMMS so not sure which format yous are using, i will just put them both up .xpf opens in LMMS directly and .xiz will open with both LMMS and in ZASF)

---

### Post by neu2buntu on 2010-02-27
@HARDCOPY  your method is perfect, i just read through this last night briefly and posted my patch , which is not great, one thing however that you can add to your tutorial is that using the ADDsynth Global - Filter envelope (press button E in Filter Envelope and click freemode *screenshot*), you can add more points here and shift them on the envelope timeline to give an automated type of effect to the wobble... thanks for the great tutorial by the way! 

I,m now actually making good wobbles in ZASF  !!!


i just cant get your exact patch which is good you could perhaps post it up ;)

---

### Post by g-raf on 2010-03-04
@neu2buntu - I took a look at your screen and made something similar. I used ZynAddSubFX with 4 voices (you can see them in the screen) and the Phaser 4 effect. Also, i used JAMin to raise the lows and lower the highs to some degree. I'm attaching a zip file with a screen of my ZynAddSubFX setup, my JAMin set up and an mp3 of what the wobble sounds like. 

Tell me what you think.

---

### Post by g-raf on 2010-03-10
I made a tutorial on wobble bass in zynaddsubfx. Check it out here:

[http://www.youtube.com/watch?v=wohjJNMC_Uc](http://www.youtube.com/watch?v=wohjJNMC_Uc)

---

### Post by AutoStatic on 2010-03-10
Just to let you know that I'm reading along. Interesting stuff! And g-raf, you're setting the new standard for recording a YouTube howto video ;)
Funny that I was thinking about doing it this way too, but then with a lot of pitch shifting or a vocoder/autotuner.

---

### Post by AutoStatic on 2010-06-02
I've attached my attempt to create a dubstep like bass instrument for ZynAddSubFX/Yoshimi.

Best,

Jeremy

---

### Post by sgx on 2010-06-02
> **AutoStatic said:**
> I've attached my attempt to create a dubstep like bass instrument for ZynAddSubFX/Yoshimi.

Best,

Jeremy
Hi, I notice this in synaptic after adding your nice PPA,

Failed to fetch [http://ppa.launchpad.net/autostatic/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/autostatic/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

Maybe a typo crept in somewhere? Thats a great selection you have, after
seeing nanonoise, I may go pick up one of those gizmos!
Cheers :)

---

### Post by AutoStatic on 2010-06-02
Hello sgx,

My PPA has no Lucid packages as I don't use Lucid (yet). nanonoise is a really handy app, not only usable together with the Korg nanoKONTROL but also with other MIDI controllers because it is one of the very few apps I know that do MIDI to keystroke translation in realtime.
And thanks for the props, I should really install Lucid and start packaging for it. 

Best,

Jeremy

---

### Post by sgx on 2010-06-02
Hi, thanks for setting me straight.
I did manually install several of your packages, after changing them
to rpms using  alien, and also use them as-is in Mint9 with the
Ubuntu Studio meta-package installed. 
Guitarix
Rakarrack
Calf-Plugins
Bristol
Gigedit
Phasex
Nanonoise
and more...

Now I am greatly in need of 30 hour days, but no download is available :)
Cheers

---

