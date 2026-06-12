---
title: "M-Audio Keystation Pro 88 &amp; Ubuntu DreamStudio 12.04 LTS"
date: 2013-03-16
forum: Ubuntu Studio
---

### Post by tnob on 2013-03-16
[FONT=Arial][SIZE=3][COLOR=#000000]Greetings all,

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=#000000]Can anybody help with getting a M-Audio Keystation Pro 88 to work in Ubuntu DreamStudio 12.04 LTS?

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=#000000]My home studio consists of

[/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Symbol][SIZE=3]-[/SIZE]       [/FONT][FONT=Arial][SIZE=3]an IBM desktop:Intel ® Core (TM) i 5-3470 CPU @ 3.20 GHz 3.20GHz; RAM 4Gb; 500 Gb HDD; 64 bit;
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Symbol][SIZE=3]-[/SIZE]       [/FONT][FONT=Arial][SIZE=3]a Realtek soundcard;
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Symbol][SIZE=3]-[/SIZE]       [/FONT][FONT=Arial][SIZE=3]UbuntuDreamStudio 12.04 as my main platform (with Audacity as sequencer of preference);
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Symbol][SIZE=3]-[/SIZE]       [/FONT][FONT=Arial][SIZE=3]a vintage TascamPorta 2 four-track analogue recorder;
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Symbol][SIZE=3]-[/SIZE]       [/FONT][FONT=Arial][SIZE=3]a GEM (piano)keyboard, small, with MIDI IN and MIDI OUT buses;
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Symbol][SIZE=3]-[/SIZE]       [/FONT][FONT=Arial][SIZE=3]M-AudioKeystation Pro 88: has been purchased second-hand, so original disk and drivers were not included.

[/SIZE][/FONT][/COLOR][FONT=Arial][SIZE=3][COLOR=#000000]Normally ,the Tascam Porta 2 four-tracker is my first port of call &#8211; in order to put in a provisional click track and guiding chords (usually with the GEM). These will then be transferred to Audacity and further tracks are added there.

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=#000000]I'm using electric (flat-body) versions of traditional instruments &#8211; banjo, guitar,uke, amongst others &#8211; with the Tascam Porta 2 four-tracker doubling as amp here. However, I'd very much like to expand my instrumental palette; and it is with this in mind that I purchased the M-Audio Keystation Pro 88. 

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=#000000]I'm hoping to use it as a tool for accessing MIDI musical instrument banks 0 &#8211; 127 as integrated in the Realtek soundcard of the IBM desktop computer. The musical instrument sounds generated from there could then be led to the Tascam four-tracker and/or Audacity, I imagine, for further processing. This would be the easiest method &#8211; and the one most comfortable for me.

[/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT=Arial]In other words: I'd need to program the Keystation Pro 88, in some way or other, in order to create a connection with those MIDI banks 0-127 as incorporated in the Realtek sound card of my computer. But rather than continuing in MIDI &#8211; and all the unwanted complications thereof &#8211; I just wish, plain and simple, to ***capture*** musical instrument sound, coming from Realtek MIDI banks 0-127, on the Tascam or in Audacity. Thus, my preferred routing would be: M-Audio Keystation Pro 88 [/FONT][FONT=Wingdings][FONT=Wingdings]à[/FONT][/FONT][FONT=Arial]Realtek sound card on IBM desktop [/FONT][FONT=Wingdings][FONT=Wingdings]à[/FONT][/FONT][FONT=Arial] audio line-out from IBM to Tascam four-tracker/to Audacity on spare deskop.

[/FONT][/COLOR][/SIZE][FONT=Arial][SIZE=3][COLOR=#000000]Is this feasible? And if yes, how? Besides, I&#8217;m also wondering if Jackctl has any role to play in this setup.

[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=#000000]tnob[/COLOR][/SIZE][/FONT]

---

### Post by jejeman on 2013-03-16
JACK could help for feeding both Audacity and TascamPorta 2.

You should check if MIDI bank of Realtek is supported by ALSA driver. I doubt. I have onboard Realtek, and it is not shown as MIDI device, like Audigy2 is where you can load GM sounds in it.

But, you can use software as GM bank. Mybe the easyest way is to use Qsynth (frontend of fluidsynth), it comes with sf2 GM bank (FluidR3_GM.sf2). Or you can load any other sf2 GM bank you can find.

You can use Qjackctl to connect ALSA MIDI ports or patchage.

---

### Post by CrocoDuck on 2013-03-16
Hi. I'm not sure I have properly understood what you are going to do... I have a keystation 88es and it works just out of the box with linux. If you are going to plug the usb cable into your computer then you will not encounter any issue. So, it seems to me that you would like to use your soundcard as a sound module, playing with the keyboard the built-in sound banks. Can you repost your soundcard model?

---

### Post by tnob on 2013-03-16
[FONT=Times New Roman][SIZE=3][COLOR=#000000]
[COLOR=#222222][FONT=Verdana]Hi Crocoduck,

Thanks for your reply. 

I'll try to explain once again. It's very simple really.

I have heard it rumoured that in every sound card MIDI musical instrument banks (0-127) have been integrated. The sound card on my IBM desktop is from Realtek (can't give you any more details right now,unfortunately, since the IBM is being serviced at the moment).

Based on this information, I'd like to use my M-Audio Keystation Pro 88 to access these MIDI musical instrument patches on my sound card. Now, let's say I'd need a double bass in my score: I want my M-Audio Keystation Pro 88 to produce a double bass sound - but I'd treat this _as if it were **[FONT=Verdana]analogue[/FONT]**_[FONT=Verdana], [/FONT]leading it on to my (analogue) Tascam four-track recorder or to Audacity (via an audio cable from my computer).

To put it in a different way: the general idea is to add this double bass (or any other instrument I don't play myself) to my score (either on the Tascam orin Audacity) **[FONT=Verdana]as[/FONT]** **[FONT=Verdana]a "live" instrument [/FONT]**(i.e. directly from the Keystation keys). At the moment, though, I don't get any sound at all from my Keystation Pro 88. Hence, I'd need to find some way of linking up Pro 88 with General Midi. And I just don't know how to do that.

I hope this will clarify things a bit.

tnob

[/FONT][/COLOR]
[/COLOR][/SIZE][/FONT]

---

### Post by tnob on 2013-03-16
Thanks to Jejeman, too, of course. Your suggestions are very helpful.

tnob

---

### Post by CrocoDuck on 2013-03-16
Ok, I think I got it... What you are trying to do depends on how the Realtek is made and how ALSA support it (as jejeman said). Let's try to learn some info about your system, this could give us some answers:

```
lspci
```
```
cat /proc/asound/cards
```
```
cat /proc/asound/devices
```
```
cat /proc/asound/pcm
```
```
aconnect -i
```
```
aconnect -o
```

Repost the output of those guys. Keystation 88es, you know, is a mute midi controller. If you want you can plug it into your computer with usb and use any synthetizer or software that can menage soundfonts (as jejeman said). With Jack you can connect the output of those programs to the soundcard output and then record with your analog recorder. You can also connect the output of those programs to Audacity running on your IBM, in order to record at the same time both ways. You see, going through this way is not using the banks of your soundcard, but probably in the banks of your soundcard there are general midi sounds... that are not the most nice... With Qsynth you can load any sound you want... Or maybe there is a way to deeply manage the Realtek's banks? It depends on support.

---

### Post by jejeman on 2013-03-16
I will just illustrate here how it is with Audigy2
```
amidi -l
Dir Device    Name
IO  hw:0,0    Audigy MPU-401 (UART)
IO  hw:0,1    Audigy MPU-401 #2
IO  hw:0,2    Emu10k1 Synth MIDI (16 subdevices)
IO  hw:0,3    Emu10k1 Synth MIDI (16 subdevices)
```We can see that we have MIDI devices from the soundcard. 0,0 & 0,1 are MIDI ports. 0,2 & 0,3 are wavetable device.
Now I can load soundbank in the wavetable
```
asfxload CT4MGM.SF2
```CT4MGM.SF2 is default soundfont which comes on CD for the soundcard.
Now I can play the Audigy2's wavetable device when I connect MIDI keyboard to it
[ATTACH=CONFIG]240251[/ATTACH]
I never saw a Realtek onboard card to show MIDI devices, as Audigy2 does.

---

### Post by tnob on 2013-03-19
[SIZE=3][FONT=arial]Hi Jejeman and Crocoduck[/FONT][/SIZE], 

[SIZE=3]Your suggestions are definitely very helpful. Thanks very much for that, guys! However, I'll have to wait for another week for a follow-up, since my IBM desktop is away for some necessary modifications. 

In the meanwhile, I have another question. This came up after reading a SoundOnSound review (from 2004, I think) on the M-Audio Keystation Pro 88 (on the web). 

 Allegedly, a guitar can be connected as well - and now I'm wondering if you guys have any experience in this area. And just out of curiosity: what extras does the 88ES bring in (since it's an improved version of the Pro 88, I take it...)

tnob[/SIZE]

---

### Post by tnob on 2013-03-19
[SIZE=3]Another question to Jejeman too: is Audigy2 a sound card, like Realtek in my IBM? And is it internal or external?

tnob[/SIZE]

---

### Post by tnob on 2013-03-19
[SIZE=3]Another question to Jejeman too.

I don't know what Audigy2 is (or does). Is it a sound card (internal or external) - like Realtek on my IBM? Or is it an dependent MIDI device?

tnob[/SIZE]

---

### Post by jejeman on 2013-03-19
You colud just search the web to find out about Audigy2
Here it is:
[http://www.ixbt.com/multimedia/audigy2-value/a2cardb.jpg](http://www.ixbt.com/multimedia/audigy2-value/a2cardb.jpg)
It is a plain old (2004.) PCI soundcard. (I have this one in the picture: Creative SoundBlaster Audigy2 Value). Maybe stiil a little bit advanced than onboard HDA cards.

But, the main thing here is that it is supported by ALSA as wavetable (MIDI) device.

Now, I'm at different PC where I have Realtek ALC888
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC888
```

And we can see, no MIDI devices related to it
```
$ amidi -l
Dir Device    Name
$ 
```Also, in alsamixer there is no "Synth" fader like for Audigy2. So, if the onboard HDA cards actually have MIDI chip & bank inside them, I really doubt that they are supported by ALSA. I have to admit that I didn't go to find out if one could "activate" MIDI chip & bank, so I really don't know if it can be done or not.

I suggest that you try to go the software way with Qsynth. It has default sf2 which is 140MB, and that kind of bank surely will sound better than any potential bank in onboar chip. Also, with Qsynth you don't need to use JACK for audio. It can play as just ALSA application, although you will need to connect MIDI ports with "aconnect" or similar.

---

