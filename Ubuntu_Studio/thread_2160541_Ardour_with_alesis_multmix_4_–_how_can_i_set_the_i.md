---
title: "Ardour with alesis multmix 4 – how can i set the interface as input?"
date: 2013-07-07
forum: Ubuntu Studio
---

### Post by ihnc on 2013-07-07
I've tried to use my alsesis multimix 4 with ardour for some homerecording, but the problem is that jack won't recognize the interface. under sound>hardware>input i cant't select the pcm2900 audio codec because everytime i do so, it just closes and nothing happens....
what can i do about it?

---

### Post by jejeman on 2013-07-07
Give
```
aplay -l
arecord -l
```

---

### Post by ihnc on 2013-07-07
im sorry im not that familiar with ubuntu since i only got it a week...how do i that?

---

### Post by jejeman on 2013-07-07
Plug in the soundcard, open terminal, copy/paste commands - one by one - pressing "enter" to run 'em, paste back here the output, put it in CODE tags.

---

### Post by ihnc on 2013-07-08
Like this?


riedl@Laptop:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC268 Analog [ALC268 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: HDMI [HDA ATI HDMI], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 2: CODEC [USB Audio CODEC], Gerät 0: USB Audio [USB Audio]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
riedl@Laptop:~$ arecord -l
**** Liste der Hardware-Geräte (CAPTURE) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC268 Analog [ALC268 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 2: CODEC [USB Audio CODEC], Gerät 0: USB Audio [USB Audio]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
riedl@Laptop:~$

---

### Post by jejeman on 2013-07-08
I guess you are using Qjackctl for starting JACK.
First start JACK, then open Ardour.
You need to setup JACK to use USB audio card.
" sound>hardware>input" is not important for JACK, that's PulseAudio setting.
In Qjackctl choose for interface: hw:2,0

---

### Post by ihnc on 2013-07-12
yes i'm using qjackctl
i've put hw:2,0 (input and output - or just input?)
now i don't know which connection to choose in ardour, master in for input or audio in or....because i can't get a signal from my guitar (which is shown on the interface) into ardour...?

---

### Post by jejeman on 2013-07-12
>  i've put hw:2,0 (input and output - or just input?)Both, if you need it.

In Ardour add audio track, rename it to something more convinient, e.g. "guitar". Then you will connect system>guitar_in.

But first, check if everything is okay. Connect directly capture>playback in Qjackctl. There should be sound form hardware input.

---

### Post by Grafens on 2013-07-13
[COLOR=#000000]Hello ihnc
I've got one of these 'alsesis multimix 4' sound cards running. If your still having issues I can take you through how I set it up.[/COLOR]

---

### Post by ihnc on 2013-07-14
Hi Grafens
still need some help with this, now i can't start ardour because a window pops up which says that I chose the wrong audio settings...

---

### Post by Grafens on 2013-07-14
OK I'll try and help, I'm no sound engineer/linux guru so all I can do is tell you what I've done.
1 - I disabled the integrated sound card on the mainboard through the BIOS.
2 - In 'jackctl > Setup > settings' where it says 'interface' next to that you have an option to choose your sound card (for me it's hw:1,0) and next to that is a '>' if you select the '>' you can then choose additional soundcard options from there(for me it's hw:1,0 USB Audio), everything else is left as default.


From your original question you said you want to use the multimix as 'input' is there a specific reason for this? if not disabling the mainboard sound card through the BIOS maybe a good idea. But try step 2 first and see if ardour starts.

---

