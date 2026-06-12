---
title: "software synthesizer"
date: 2011-10-25
forum: Ubuntu Studio
---

### Post by Chiel92 on 2011-10-25
Hello everyone,

I am looking for a way to play music via my computer. I want to connect a keyboard to my computer and convert the midi signal realtime into sound using a software program. I know it is possible, but I don't know how to do it. Can anyone point out good software and hardware to do this?

regards

---

### Post by jejeman on 2011-10-25
There are many software synthesizers. By default in ubuntu studio you have
Yoshimi, Zynaddsubfx, phasex, to name a few. It depends what version of studio you have installed. Most of them works only with jack. You should first learn jack.
If your keyboard has usb connection which transfers midi, you can try that.

---

### Post by sgx on 2011-10-25
Hi, study these pics and details for connecting a great synthesizer

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

and more details about the system connection settings:

[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

and a nice magazine article:

[http://w3.linux-magazine.com/issue/67/JACK_Audio_Server.pdf](http://w3.linux-magazine.com/issue/67/JACK_Audio_Server.pdf)

Use synaptic package manager to install zynaddsubfx and qjackctl
if you don't yet have them. To load its soundbanks

menu Instrument --Show instrument bank

then at the empty banks panel that opens, at the top, click the little black triangle widget by the 'Refresh Bank List' button, and select from the list that appears. The default location for zyn
soundbanks is

/usr/share/zynaddsubfx.


Phasex is another good synthesizer
to install. Hexter is a Yamaha DX7 sound player, loads of DX7 sysex
soundsets for it are on the net. Install dssi and Hexter from synaptic. Use qjackctl for connections.

There are a nice mono-synth and organ in the Calf plugins,
and the mda lv2 plugins have an e-piano and more.
Install calf and lv2-core and all the lv2 plugins google will reveal in various PPAs like Falk and Autostatic.
Cheers
To use a midi keyboard, plug it into either usb, or a soundcard/interface with 5-pin midi ports, and use the alsa tab in qjackctl to connect to your hardware to your software, as in the links above.

---

### Post by Chiel92 on 2011-10-26
Thanks for the replies!
I tried a little bit around with ZynAddSubFX and monoBristol, but the sound was really bad. When touched more than 3 keys with monoBristol, the sound almost dissapeared.
Do you know if I will need an external sound card or similar?

---

### Post by sgx on 2011-10-26
Hi, did you load sounds from the zynaddsubfx sound banks?
The default sound is just a sine wave. Try the pads, choirs,
arpeggios, fantasy and other banks sounds, usually about 8% of sounds have some appeal to average users. Very few folks love all the sounds
of any instrument.

Bristol is not noted for great sound, more for the variety of
old synth gui. The Calf monosynth and organ, routed to
rakarrack or calf/lv2 fx plugins, should sound very nice,
as would phasex. Fx in small doses would help Bristol, as well.
Cheers

In qjackctl, change the audio tab synth connection from
synth to soundcard, to synth to fx, then connect fx to soundcard.
Look up rakarrack on youtube, for the visuals.

---

### Post by jejeman on 2011-10-26
> **Chiel92 said:**
> I tried a little bit around with ZynAddSubFX and monoBristol, but the sound was really bad. When touched more than 3 keys with monoBristol, the sound almost dissapeared.
Do you know if I will need an external sound card or similar?
I've just tried bristol, never use it before, and sound is normal. I'm using jack for sound.
Do you need external sound card? It depends what you want to do. Just to hear normal sound you don't need it.

---

### Post by Totalchaos on 2011-10-26
> **Chiel92 said:**
> Thanks for the replies!
I tried a little bit around with ZynAddSubFX and monoBristol, but the sound was really bad. When touched more than 3 keys with monoBristol, the sound almost dissapeared.
Do you know if I will need an external sound card or similar?

it's possible that the problem is in monobristol itself, it's on my opinion poorly maintained and resource eating program. My suggestion is to remove it and learn to start Bristol synths from terminal. Here you have one nice command to start with 

~$ startBristol -v -h

ps: Did you find out that most of your midi controller faders are active? ;)
ps..2:I just remembered that Klaudia (a KXStudio application) has a nice bristol launcher

---

### Post by Chiel92 on 2011-10-26
> **Totalchaos said:**
> it's possible that the problem is in monobristol itself, it's on my opinion poorly maintained and resource eating program. My suggestion is to remove it and learn to start Bristol synths from terminal. Here you have one nice command to start with 

~$ startBristol -v -h


ps..2:I just remembered that Klaudia (a KXStudio application) has a nice bristol launcher

Thanks. I didn't know monoBristol and bristol were different things.

> ps: Did you find out that most of your midi controller faders are active? ;)
What do you mean by that? What are midi controller faders exactly?

---

### Post by sgx on 2011-10-26
> **Chiel92 said:**
> Hello everyone,

I am looking for a way to play music via my computer. I want to connect a keyboard to my computer and convert the midi signal realtime into sound using a software program. I know it is possible, but I don't know how to do it. Can anyone point out good software and hardware to do this?

regards
On the hardware side, an maudio pci soundcard, with real midi ports,
is an excellent simple to set up linux choice, and most name-brand midi controllers will work by usb, or the 5 pin connectors. A vintage e-mu pk6, kawai K3/4/5 or yamaha sy55/77/99 and their variants are good for midi controllers, having good keybeds, and have the bonus of a fine hardware synthesizer under the hood.

The faders are the mouse-controllable knobs on the softsynth gui,
also used with gear like the korg nanocontrol, and various midi hardware controllers utilizing 'midi learn'  where a mode allows you to select a knob on screen, then move a control on your hardware, to create a learned link, so you always can turn that software knob with the hardware.
Cheers

Cheers

---

### Post by Chiel92 on 2011-10-26
> **Totalchaos said:**
> 
ps: Did you find out that most of your midi controller faders are active? ;)

Yes, they are active.

---

### Post by Totalchaos on 2011-10-26
> **Chiel92 said:**
> Thanks. I didn't know monoBristol and bristol were different things.

monobristol is actually the (semi-official) GUI for bristol

---

### Post by Chiel92 on 2011-10-26
> **sgx said:**
> Hi, did you load sounds from the zynaddsubfx sound banks?
The default sound is just a sine wave. Try the pads, choirs,
arpeggios, fantasy and other banks sounds, usually about 8% of sounds have some appeal to average users. Very few folks love all the sounds
of any instrument.

Ah, so zynaddsubfx has more than sine :) I already wondered...
> 
Bristol is not noted for great sound, more for the variety of
old synth gui. The Calf monosynth and organ, routed to
rakarrack or calf/lv2 fx plugins, should sound very nice,
as would phasex. Fx in small doses would help Bristol, as well.
Cheers

In qjackctl, change the audio tab synth connection from
synth to soundcard, to synth to fx, then connect fx to soundcard.
Look up rakarrack on youtube, for the visuals.

It is indeed a pro that bristol has the GUI's. I would be cool if i could get hold of some touchscreen-supporting laptop and combine it with the GUI's (though they are graphically not that splendid). Graphically I think of something like apple's garageband on an iPad. But I fear that is not yet possible :)

---

### Post by Chiel92 on 2011-10-26
> **jejeman said:**
> I've just tried bristol, never use it before, and sound is normal. I'm using jack for sound.
Do you need external sound card? It depends what you want to do. Just to hear normal sound you don't need it.

I use jack in combination with alsa.

My soundcard is quite bad. When I listen to music through a headphone, there is noise in the background and the low frequenties sound awful. Besides, I am also experimenting with recording raw audio. So for that reason too I want a way to bypass my internal soundcard :). But I have zero experience with soundcards and similar, so I don't know if a cheap 30$ soundbox is sufficient to get normal soundquality for both aims.

---

### Post by sgx on 2011-10-27
To load soundbanks in zynaddsubfx, choose
menu  Instrument --Show Instrument Bank

The empty panel opens, and click the little black triangle widget by the Refresh Bank List button, and the list of banks will open.

Try and find a used mAudio 24/96 pci soundcard, for $40-$50
The quality is excellent, and no magic is needed to use it.

Cheers

---

### Post by beefheartvliet on 2011-10-31
> **sgx said:**
> 

Try and find a used mAudio 24/96 pci soundcard, for $40-$50
The quality is excellent, and no magic is needed to use it.

Cheers

I have to agree, it's a great card, that has midi in/out/ and stereo in and out. 
M-audio, are well supported with Linux. I have used this card myself for about the last 5 or so years with no prolems.

---

### Post by sgx on 2011-11-25
> **Manuel. said:**
> Hello my friend,
For the instruments area i will try using the software of Native instruments.
Good luck !

Manuel
spam snip
Hi, Warning!!! With Native Instruments,

Always run the standalone version once, before you use the plugin!

Problems sometimes occur if you don't!

I have had most success using most Native Instruments demos
with wine/wineasio in stand-alone mode, and Reaper as vst host
for the plugin versions. The installers sometimes open an important
window behind others, so the user thinks it has failed, so move
or minimize windows if there is a long pause during the installation.

For the plugins, I create the folders needed for the defaults
that are offered, just to be safe.

If you dual-boot, you can carefully copy the all files, especially
Service Center, to the matching locations in the .wine folder, and
your /home/username folder. You may need to create some of them,
And the file structure of the N.I. software is like the wreckage
of a hurricane, scattered everywhere. Better to just use the installers a second time.
Cheers:)

---

### Post by Chiel92 on 2012-01-29
Hey,
I haven't had time for this for a while. Now I do again :-({|=

Just to make sure:
Do I get it right if I say that I need to do the following steps?
- Buy a MIDI controller (keyboard) with an USB out port, and link it to the pc
- install the synthsoftware
- Buy an external usb soundcard/interface
- link the output of the synthsoftware via usb to the external soundcard
- connect the soundcard with a speaker of a headphone

Are these steps everything I need to do?

Thanks in advance once more!

---

### Post by jejeman on 2012-01-29
> **Chiel92 said:**
> Do I get it right if I say that I need to do the following steps?
- Buy a MIDI controller (keyboard) with an USB out port, and link it to the pc
- install the synthsoftware
- Buy an external usb soundcard/interface
- link the output of the synthsoftware via usb to the external soundcard
- connect the soundcard with a speaker of a headphone

Are these steps everything I need to do?1. if you want/need
2. you must
3. if you want/need
4. This is confusing. The usb card is already connected to PC with usb cable, or you ment to say: to connect usb card with usb cable to pc. You just need to tell softsynth to send audio to usb card.
5. you must

---

### Post by Chiel92 on 2012-01-30
Thanks for your quick reply!
> 
You just need to tell softsynth to send audio to usb card.I indeed meant this with my question.

I guess this is everything one needs to know to play keyboard on a software synthesizer.
Thread solved.
:popcorn:

---

