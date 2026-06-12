---
title: "Beast BSE - Will not playback"
date: 2010-05-15
forum: Ubuntu Studio
---

### Post by svenskmand on 2010-05-15
Hello, I wanted to learn to use Beast BSE, but when I started it up and loaded the built in demo song "Party Monster" and pressed play I only got the following error:

```

MIDI input or output is not available.

No available MIDI device could be found and opened successfully. Reverting to null device, no MIDI events will be received or sent.

```
Anybody having any idea how to solve this problem, so I can start using Beast BSE :)

PS: I was in doubt where to put this thread, but I hope this was the correct place :)

---

### Post by sgx on 2010-05-16
Hi, here is a link to the quickstart guide.

[http://testbit.eu/wiki/Beast-Quickstart](http://testbit.eu/wiki/Beast-Quickstart)

 I've not used beast, but its not like zynaddsubfx where you load it and start playing. Its a modular
environment, where you build from the ground up, hence the quickstart guide. Screenshots:

[http://beast.gtk.org/screenshots](http://beast.gtk.org/screenshots)

Wish I could be of more help.
Cheers

---

### Post by svenskmand on 2010-05-16
I tried Beast BSE a while a go (a year or two I think) and there it worked fine, I could just load up and example and hit play to hear it :), but I cannot do that now :(

I did try the [quick start guide]("http://testbit.eu/wiki/Beast-Quickstart") and when you get to the section titled "Starting And Stopping Playback" then your supposed to be able to hear the "Custom Synthesizer" you just added in the previous two steps of the guide.

Anybody that actually have Beast BSE working?

PS: Thanks for the quick reply :)

PS^2: This ZynAddSubFx looks pretty cool :)

---

### Post by sgx on 2010-05-16
> **svenskmand said:**
> I tried Beast BSE a while a go (a year or two I think) and there it worked fine, I could just load up and example and hit play to hear it :), but I cannot do that now :(

I did try the [quick start guide]("http://testbit.eu/wiki/Beast-Quickstart") and when you get to the section titled "Starting And Stopping Playback" then your supposed to be able to hear the "Custom Synthesizer" you just added in the previous two steps of the guide.

Anybody that actually have Beast BSE working?

PS: Thanks for the quick reply :)

PS^2: This ZynAddSubFx looks pretty cool :)

How are other midi apps doing on your system? Are they finding the hardware correctly? 

Phasex is another great synth, with the bonus of using your soundcard line-in as sound source, so you can synthesize your wifes vocals,
your guitar, a homeless jazz sax player, along with the synth engine,
much untapped potential. Rakarrack, guitarix, and calf-plugins are
also to be experienced.

Zyn is 16 part multi-timbral, the bottom half of the gui has options,
the Instrument starts as 1, click the widgets on either side of the
number to move up or down thru the 16 possible instruments, click to make 2, then tick the new empty 'Enabeled' box,  and on the bottom right of the screen,
'midi chn rcv' 
should be changed to channel 1 to hear the extra voices you add.

Cheers

---

### Post by svenskmand on 2010-05-16
I do not own any MIDI equipment, I just wanted to use synthesizers (the ones inside of Beast) and then compose the notes in Beast, but I have now dropped Beast as I just discovered Rosegarden :), so now I use Rosegarden to do the composition, then I will use various synthesizers connected to Rosegarden thought JACK, and then record it to wave files using Ardour.

By the way I tried ZynAddSubFx, and I thing it is great, but how do I connect more than one instrument thought JACK? With QSynth I can make as many instruments as I want, but I cannot seem to do that with ZynAddSubFx :S, also can I get the instruments export to a soundfont file? I have not been able to find any documentation for ZynAddSubFx, which annoys med :(

---

### Post by sgx on 2010-05-16
> **svenskmand said:**
> I do not own any MIDI equipment, I just wanted to use synthesizers (the ones inside of Beast) and then compose the notes in Beast, but I have now dropped Beast as I just discovered Rosegarden :), so now I use Rosegarden to do the composition, then I will use various synthesizers connected to Rosegarden thought JACK, and then record it to wave files using Ardour.

By the way I tried ZynAddSubFx, and I thing it is great, but how do I connect more than one instrument thought JACK? With QSynth I can make as many instruments as I want, but I cannot seem to do that with ZynAddSubFx :S, also can I get the instruments export to a soundfont file? I have not been able to find any documentation for ZynAddSubFx, which annoys med :(

Hi, using qjackctl, the gui for jackd, each zyn (or other instrument) that you start, should appear separately, and you need to make each connection. Press the connect button in the lower left of qjackctl, and a
3 tabbed panel opens, Audio and Alsa are the ones to check. Each will have two sides, System in and out in the audio tab, for your soundcard,
and in the alsa tab, your system midi devices. When zyn appears on one side, connect it to the opposite side, by selecting both items, and clicking the connect button in this panel (not the main window). This
holds true for other instruments and fx, some of which connect automatically.

[http://www.kvraudio.com/forum/viewforum.php?f=47](http://www.kvraudio.com/forum/viewforum.php?f=47)

 is a zyn forum, with some useful links and discussion. There are several youtube videos, some are quite good, a couple are just noodlers.

You'll find youtube videos of ardour and hydrogen, some of them also cover qjackctl, since it is a fundamental tool for many people connecting their gear.

Soundfonts would require both recording the zyn sounds as .wav files, then converting those to soundfonts, it can be done, but its tedious.
The linux version of Highlife is an excellent sampler for such recording, or try the windows version using wine and wineasio.

An older linux app, smurf, is a soundfont editing program, I don't know if it will work in the newer linux versions, its based on vienna, a windows soundfont editor, related links are here

[http://soundfonts.homemusician.net/](http://soundfonts.homemusician.net/)

Cheers

---

### Post by svenskmand on 2010-05-16
After 5-10 minutes of playing around with Jack I figured it out :) (how to connect stuff and such), but in some documentation for Rosegarden it mentioned that QSynth could be used with Rosegarden, but when I open it I do not have any sound banks, and therefore no sound :( So I tried you suggestion (ZynAddSubFx) which worked in first try. Then I noticed that in QSynth I could load multiple (Here I actually only use one instance of QSynt, even though I have many instruments) instruments and have them appear in Jack, but in ZynAddSubFx I can only load up one instrument per ZynAddSubFx program instance I have running, so I just wanted to hear if I could load many instruments in one instance of ZynAddSubFx?

By the way I also found some other nice Synths, called Bristol Audio Synthesis, they have modeled real synthesizers in software for use with Jack :)

Do you know QSynth/FluidSynth? As I understand I need SoundFonts to use it right? There also seems to be no documentation for these two tools :(

---

### Post by sgx on 2010-05-16
OOPs, Forgot the sound loading tip, see below

Hi, look at the bottom half of the zyn screen, for the number one, flanked by black triangle widgets. Click the one on the right,
the number changes to 2. Tick the box by 'Enabled'. Now go to the lower right, 'midi chn rcv' it will say channel 2, switch it back to channel one.
 Now load a different sound in zyn, and OOPs, its not obvious how to do that, sorry I forgot in the previous post.
-------------------------------------------------------------------------
To load sounds:

In zyn, use the menu Instrument-->Show Instrument Bank.

A big empty bank appears, at the top of this, click the black triangle widget by the phrase 'Refresh bank list' and the list of sound folders appears, each will have about 10 to 20 sounds, so click on one, and a large but partially filled bank of sounds appears, just click them to try different ones. There is a small dotted-line highlite on the selected item. So you can have 16 separate sounds from these, in each instance of zyn, but your cpu will decide the final number, I often use 3 or 4 to make custom sounds. You can save these multi-sounds as nameUchoose.xmz, to be reloaded. Use the
File-->Open Parameters    option to reload them. 
Cheers

---

### Post by svenskmand on 2010-05-16
If I do that then both instruments will be playing the same notes as they will receive the same notes from Rosegarden, I would like to have to (or more) instruments playing different nodes, loaded at the same time in one instance of ZynAddSubFx, is this not possible?

---

### Post by sgx on 2010-05-16
> **svenskmand said:**
> If I do that then both instruments will be playing the same notes as they will receive the same notes from Rosegarden, I would like to have to (or more) instruments playing different nodes, loaded at the same time in one instance of ZynAddSubFx, is this not possible?
I think by having each track in rosegarden on a separate midi channel,
and having each zyn sound on a different midi channel, they would play together, and that would be possible. But I have not used rosegarden,
so have some experiments. If you start zyn a second time, does it show up in qjackctl? It should.
Cheers

---

### Post by svenskmand on 2010-05-17
> **sgx said:**
> I think by having each track in rosegarden on a separate midi channel,
and having each zyn sound on a different midi channel, they would play together, and that would be possible. But I have not used rosegarden,
so have some experiments. If you start zyn a second time, does it show up in qjackctl? It should.
Cheers

Nice I will see if I can make it do that right away :)

By the way (ZynAddSubFx may be able to do this, but I do not know :S, it would suspect it be able to do additive and subtractive synths off course) do you know of any FOSS synthesizer that can make all or most/many of these types of synthesis?:
[LIST]
[*]Sample-based synthesis
[*]ADSR envelope
[*]Additive synthesis
[*]Subtractive synthesis
[*]FM synthesis
[*]Phase distortion synthesis
[*]Granular synthesis
[*]Physical modeling
[/LIST]
I have taken these categories from [this]("http://en.wikipedia.org/wiki/Synthesizer#Types_of_synthesis") wiki page.

Also do you know of any cheap Midi keyboard that is compatible with Ubuntu? I am on the lookout for one :) It should preferably not be too large.

---

### Post by sgx on 2010-05-18
Hi, if you click the Edit Instrument button in zyn,
The popup has additive, subtractive, and padsynth. Enable these, and click on each one. ADSR controls for amp and filter will be there
among multitudes of options. Take notes as you click on all buttons
anywhere, as quite a few lead to more control screens.

Most keyboards will work, em-u xboards, maudio axiom/keyrig,
various edirol, so the features you want may be on quite a few models and brands.

[http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)  good spot to start shopping :)
Cheers

---

### Post by svenskmand on 2010-05-18
Thanks for the many great answers :guitar:

---

### Post by sgx on 2010-05-18
> **svenskmand said:**
> Thanks for the many great answers :guitar:
Remember the old guys when you go Platinum :)
(I forget it all by friday, if I don't type it
by thursday ;)

---

### Post by svenskmand on 2010-05-18
> **sgx said:**
> remember the old guys when you go platinum :) ...
Heh :D

---

### Post by svenskmand on 2010-05-22
I have been looking through you link regarding midi instruments and linux, I found that the CME UF 50, 60, 70 and 80 series of keyboards should be supported by ALSA, but they are a bit expensive, at least for a total newbie with regards to music.

Do you own a Midi keyboard, and if which model? Also which keyboard would you recommend if I have these requirements: 1) 100 % compatible with ubuntu, 2) should be able to work as a normal keyboard/piano without the use of the pc, 3) preferably a 88-key version so I can also use it to practice playing the piano on it :), 4) preferably cheap and small.

These four requirements are listen in non-increasing order of importance for me.

---

### Post by sgx on 2010-05-22
Hi, are you able to shop in a pro music store to test? It is truly worth
a weekend or overnight vacation to travel to a city, test, and lay down the plastic, items you use every week are the ones that justify credit-card interest fees

size: 88 keys are not small, and you must choose a stand, a convenient desk placement, or a freestanding unit. Weight may be a factor if you
want portability, length will not vary greatly.

Sounds: General Midi Romplers can be bargains, Yamaha and Casio have models to fit any budget, and used models can be considered. 

A Yamaha MM8 is 88 keys, very light in weight, has a large soundbank, and any 2 sounds can be layered, with separate volume, reverb, and chorus. It has midi and usb connections, and many percussion/arpeggio options, (rakarrack EQ and filters do great things for drums!) It includes a 6 track hardware sequencer, and some basic synth control functions. Used with a great stereo, or above average headphones, the sounds are excellent, instantly available, and you can use them with linux sound apps in many ways. Its simple to record a sequence of drum, bass, arp, and rythym instrument in the yamaha sequencer, record it as an audio track in audacity/ardour/reaper, then add leads, harmonies and extra percussion using linux apps and vsts. Look for sales, and rebates on
this model, usually a 20% price variance can be discovered!

(you may have to tazer the wife/girlfriend/kids to keep them from dominating usage of the instrument.) 

Cheers

---

### Post by svenskmand on 2010-05-23
Thanks for the advice, although I think the Yamaha MM8 is a bit too expensive for me :S, I found that it costs around 900 USD, my budget is around 200-250 USD. I found this [M-AUDIO KEYSTATION 88ES]("http://www.m-audio.com/products/en_us/Keystation88es.html") it costs 175 EUR which is approx 220 USD. And I have seen people use use other M-Audio keyboards in videos showing music production in Ubuntu, so I hope that this is compatible. But I need to research that a little more :) Do you know this one?

PS: Thanks for all the great advice :)

By the way you should be able to use this keyboard without the computer right?

---

### Post by sgx on 2010-05-24
> **svenskmand said:**
> Thanks for the advice, although I think the Yamaha MM8 is a bit too expensive for me :S, I found that it costs around 900 USD, my budget is around 200-250 USD. I found this [M-AUDIO KEYSTATION 88ES]("http://www.m-audio.com/products/en_us/Keystation88es.html") it costs 175 EUR which is approx 220 USD. And I have seen people use use other M-Audio keyboards in videos showing music production in Ubuntu, so I hope that this is compatible. But I need to research that a little more :) Do you know this one?

PS: Thanks for all the great advice :)

By the way you should be able to use this keyboard without the computer right?
Hi, Keystations are midi controllers, a class of instrument that lack built-in sounds, and this model has mixed reviews about quality. Some like some don't, but true about every midi controller, so a personal test
is the safe way, rather than rumours.

My daughter has one of these, very similar sounds like the MM8, 61 keys, and $230

[http://www.sweetwater.com/store/detail/PSRE423/](http://www.sweetwater.com/store/detail/PSRE423/)

If 88 keys are a must, there are many used Yamahas with
DGX, YPG, or PSR prefixes, but little in the way of internal
differences, usually standard are XG-lite soundset, around 500 sounds,
a 5 track sequencer, reverb, chorus, and 100+ drum patterns.

A DGX 500 or 76 key DGX 300, is a jewel, as they has a much nicer FX section than later models.

Cheers

[http://www.youtube.com/watch?v=7ndP8d4gWBc](http://www.youtube.com/watch?v=7ndP8d4gWBc) video of $230 yamaha

---

### Post by svenskmand on 2010-05-24
The Yamaha PSR-E423 looks very good, I think I will grab one of them :) Have you tried hooking it up to a Ubuntu box, is it just plug-n-play? Does it connect with USB? I have no Midi-ports as it is a laptop I am running on.

---

### Post by sgx on 2010-05-24
> **svenskmand said:**
> The Yamaha PSR-E423 looks very good, I think I will grab one of them :) Have you tried hooking it up to a Ubuntu box, is it just plug-n-play?
No personal experience, but usually new usb devices are class compliant, in order to work on a Mac, and then not by design, also work in linux. If
you can take your laptop to a store, or a private seller of a similar used model, you can see firsthand. I have an older Yamamha, with the 5pin midi ports instead of usb midi, and it works fine. Bring your own usb cable, for luck :)

---

### Post by svenskmand on 2010-05-24
But your daughters PSR-E423 was not with USB then, but only Midi?

As far as I can [read here (link)]("http://www.thomann.de/dk/yamaha_psre423.htm") it has USB, this is for midi right? EDIT: I read the manual and saw that it was for Midi :)

---

### Post by svenskmand on 2010-06-12
Hey SGX, I just wanted to tell you that I have just bought the Yamaha PSR-E423, I went to one of the local music stores and tried it out with Ubuntu, the personnel was very helpful :) And the keyboard worked with Ubuntu and JACK straight out of the box, it was just plug and play :) This was a very good buy, thank you very much for you advice :)

---

### Post by sgx on 2010-06-13
Hi, glad you are enjoying the Yamaha. Layering of two sounds, with
individual volume/fx on each is great. I layer acoustic bass at
around 60% volume to the Grand Piano, and add some chorus fx to the
piano, this gives extra lows and highs to the already nice piano.

I also enjoy using the harmony (variable echo) effect on steel drums,
at about 70% volume layered with a Vibraphone, and one of the tropical
rythms, flamenco, rmbIslnd hawaiian etc.

The many epianos and synth sounds also team up for layers, and using
the best sax, flute and brass sounds, layered with themselves, or similar sounds, but with different fx, octave, and volume settings, can get you
added realism with little effort.

I believe you will also be able to layer the different drum kits, and by
using a different octave on one of them, you will offset the individual
instruments giving 2 sounds per keypress, some very unique percussion lines are available for experimenters, and the harmony can be put to use also and colored sticky dots to label distant combos across the keyboard are a must! And processing the output with rakarrack EQ and fx can give your beats and songs yet another boost when desired 

Cheers

---

### Post by Xavier Oddmon on 2010-06-14
Is anyone still interested in BEAST? I used galan a while ago, but the version in the repositories conflicts with ubuntu-desktop, and I can't compile a version which doesn't crash constantly. I'd like to use BEAST, but cannot for the life of me get it to produce sound. What's more, if I right click on a source, like an oscillator, and choose "Output signal monitor", there is no output. If I am running jack, there are no connections to make (none are registered). If not, nothing happens. The only output I get is about midi device, which I'm not using, and the FAQ says shouldn't be a problem. Is there any hope for this program?

---

### Post by svenskmand on 2010-06-14
I am beginning to suspect that the error is caused by a bug in the release, and cannot be fixed by changing the configuration of Beast. You could try to build it from source from the Beast webpage, and if the error is not there you should contact the package maintainers.

---

