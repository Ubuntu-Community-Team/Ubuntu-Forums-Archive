---
title: "Question, help with Jack"
date: 2010-07-07
forum: Ubuntu Studio
---

### Post by raymondvillain on 2010-07-07
Used Jack to connect Virtual MIDI Keyboard with ZynAddSubFX Software Sythesizer, and was able to get sound out of my speakers.  

The question I have is this:  The JACK connections window has 3 tabs, Audio, MIDI, and ALSA.  In my setup, the Audio and MIDI tabs do not show anything.  The ALSA tab shows 14:Midi Through and 129:Virtual Keyboard in the Output Ports (left side), and 14:Midi Through, 128:TiMidity, and 130:ZynAddSubFX in the Input Ports (right side).

I was expecting to see something in the MIDI tab, after reading the tutorial.

Is there something I need to do so my setup can work like the examples in the tutorial?

This is the output of cat .jackdrc:
/usr/bin/jackd -P10 -p128 -dalsa -dhw:0,1 -r44100 -p1024 -n4 -S -M

This is the output of cat /proc/asound/cards:
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdffc000 irq 19

This is the output of aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is the output of ps ax | grep alsa:
 3779 pts/1    S+     0:00 alsamixer
 4009 pts/0    S+     0:00 grep --color=auto alsa

This is the output of  ps ax | grep pulse:
 1959 ?        S<sl   0:01 /usr/bin/pulseaudio --start --log-target=syslog
 1975 ?        S      0:00 /usr/lib/pulseaudio/pulse/gconf-helper
 4011 pts/0    R+     0:00 grep --color=auto pulse

This is the output of ps ax | grep jackd:
 4013 pts/0    S+     0:00 grep --color=auto jackd

---

### Post by AutoStatic on 2010-07-07
> **raymondvillain said:**
> Used Jack to connect Virtual MIDI Keyboard with ZynAddSubFX Software Sythesizer, and was able to get sound out of my speakers.  

The question I have is this:  The JACK connections window has 3 tabs, Audio, MIDI, and ALSA.  In my setup, the Audio and MIDI tabs do not show anything.If the Audio tab doesn't show anything then jackd isn't running. The MIDI tab is for applications that support JACK MIDI (like Yoshimi, guitarix, arpage and rakarrack). JACK MIDI is something different than the ALSA MIDI drivers. The apps that support ALSA MIDI are in the ALSA tab.

> **raymondvillain said:**
> Is there something I need to do so my setup can work like the examples in the tutorial?Which tutorial?

> **raymondvillain said:**
> This is the output of cat .jackdrc:
/usr/bin/jackd -P10 -p128 -dalsa -dhw:0,1 -r44100 -p1024 -n4 -S -MPrio 10 is way too low, then it' s better to use JACK's default setting. And a periods/buffer setting of 4 is unusual too, most soundcards are happy with 2 and USB1 cards with 3.

---

### Post by Pablo_F on 2010-07-07
Also, hw:0,1 is your digital I/O. From aplay -l: "card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]". So device 1 is digital, not analog. You need the analog outputs. 

The interface should be hw:0,0 or just hw:0, or, better, use the alphamumeric ID 

hw:SB

 (you have to write it down in the "interface" field despite not showing up as an option).

More comments:

Afaik, force 16 bit (-S option) doesn't make much sense either unless you have a 24 bit capable card and for some reason (e.g., saving space) you want to force it to 16 bit. If the card is not 24 bit capable you don't need to force to 16 bit either.

Definitely, you need to see in the Audio TAB at least the system: playbacks and zynaddsubfx or some other app that you can connect to them (in case they don't autoconnect)

Cheers! Pablo

---

### Post by raymondvillain on 2010-07-08
Thanks so much, Pablo_F.

I found the examples for Rosegarden.  The other matters I'm still working on.

If I open "Virtual MIDI Keyboard" and "ZynAddSubFX Software Sythesizer" I'm expecting to have some MIDI inputs and outputs to use with JACK.  But then I open JACK, click on "Connections", and there are no entries under the audio or MIDI tabs.  Only on the ALSA tab do I have choices.

Any ideas?

Thanks again for your help.

---

### Post by Pablo_F on 2010-07-08
Hi, 

Auto gave you the answer. "Alsa" and "Midi" tabs are both for midi connections. In this context, alsa means alsa midi and midi means jack midi. Some apps support jack midi but most support alsa midi only. 

What is really weird is that you don't have any connections in the audio tab, which needless to say, you need to have sound from your speakers.

Oh, wait, you have to push the start button! This starts the jack server. If not, there is no jack audio connections, of course. However, there are alsa midi connections. These don't have anything to do with the jack server but they appear in qjackctl for convenience.

You should see "system" in both columns. This is your audio card. Then launch the apps, connect the midi and connect the audio output of the app to the system_playbacks.

---

### Post by AutoStatic on 2010-07-09
> **Pablo_F said:**
> Auto gave you the answer. "Alsa" and "Midi" tabs are both for midi connections. In this context, alsa means alsa midi and midi means jack midi. Some apps support jack midi but most support alsa midi only

...

However, there are alsa midi connections. These don't have anything to do with the jack server but they appear in qjackctl for convenience.Yup, ALSA MIDI is also available when jackd isn't running. QjackCtl offers an extra tab to control these connections (the ALSA tab) but these connections can also be managed with **aconnectgui** for example or with the **aconnect** command in a terminal.

So it is possible to connect a virtual MIDI keyboard with ZynAddSubFX in the ALSA tab of QjackCtl and get sound out of ZASFX. If jackd isn't started you can still make ALSA MIDI connections and ZynAddSubFX will use ALSA as its audio backend.

---

