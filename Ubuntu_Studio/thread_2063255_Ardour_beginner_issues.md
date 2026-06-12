---
title: "Ardour: beginner issues"
date: 2012-09-26
forum: Ubuntu Studio
---

### Post by tnob on 2012-09-26
Greetings all,

Because of an ongoing technical glitch at the heart of the system in use at my workplace (not Linux, obviously...), I unexpectedly had a day off. I thought this a good moment to test out **Ardour (2.8.14)**. 

For your information: I'm an absolute newbie to it. And before I forget: I'm running it in **Ubuntu Dream Studio 12.04** (more detailed specs at the end of this Thread).

I never even really got Ardour going, in the past, to tell you the truth. But sometime in July of this year (2012, for the record) , a friend of mine (far more of an Ubuntu expert than I ever can be) agreed to help me out: he spent the larger part of an evening configuring Ardour. Afterwards, I didn't have much opportunity to check it out properly - until now, that is; and I'm pleased that arming a track, hitting the record button and strumming my electric guitar produces a clear signal now - visually at least (in Record as well as in Playback mode). 
 
Nothing whatsoever is coming from my headphones, though. And this fault may well be somewhere in **Jackctl Connections**, I figure - if I only knew where to look. I even haven't got a blooming clue as to what to connect with what there, in order to generate some sound from my speakers/headset. So what to do now?

One more remark regarding the subject: I find **Patchbay** and **Connections**, in **Jackctl** rather confusing, since they seem to be based on the same principle, And there are even more questions on my mind. To stick with sound and volume a little longer: 

- How best to set the signal level, prior to recording?
- And how to control the volume in Playback?
- I expected waves, like in Audacity. Is that an option in Ardour as well?

And if you allow me one more,  about effects:

- I'd like to use the effects of **Rakarrack** in Ardour. How do I link up those two?

Then in more general terms, to conclude with:

- Where do I find an up-to-date online manual for Ardour 2.8.14? I'm aware of the Floss PDF, on the web, but under the impression that the information provided therein is not quite the bee's knees any more.

Finally the specs, as promised at the beginning:

Ubuntu:

Release: 12.04 (precise) 32 bit
Kernel Linux 3.2.0-23-lowlatency-pae
GNOME 3.4.1.
Memory: 3.7 Gb
Processor: AMD Athlon (tm) II P380 Dual Core Processor x 2

I'd really appreciate your help in bringing actually playing and recording my instruments on my PC a little bit closer!

tnob

---

### Post by CrocoDuck on 2012-09-26
Hi. You should be able to control playback levels with the volume controls for tracks and master in Ardour. I'm not sure to have properly understood what you mean with waves, but Ardour can export in the .wav format. Use "connections" to connect inputs and outputs of each program you want to use (for example, system inputs into Rakarrack, Rakarrack outputs into the guitar track in Ardour and to system output too). When using jack programs are like guitar stompboxes. You could also have a try with Patchage. I'm usually calibrate the input level by strummg and trying to get the louder sound from instrument: the appropriate level is the one that avoids clips (you notice a clip when the level meter in a mixer, audio device, program or Ardour track becomes red).

For what I know, the manual at floss is the best. [http://en.flossmanuals.net/ardour/](http://en.flossmanuals.net/ardour/) (as you know)

---

### Post by Sylos on 2012-09-27
hello there.

In addition to the good advice given br CroCoDuck I would suggest having a look in the connections window of Qjackctl (the jack GUI) to see if ardour is connected to your system outputs.

In the "Connections" window you should have 3 Tabs - "audio", "MIDI" and "alsa". In the "Audio" tab you should see Ardour on the left side. There should also be an entry on the right hand side for "system". If they are connected then you should have a line drawn between the two. If not, highlight both and then press the "connect" button.

If you still arent getting sound with them properly connected you might want to look in the Qjackctl "Setup" window and make sure that the correct soundcard is selected, its in Duplex mode, and that hardware monitoring isnt enabled. If you need help with the settings then post up a screenshot of it.

Cheers

---

### Post by fedexnman on 2012-09-27
1. On Qjackctrl make sure you have DUPLEX marked in the settings
2. With Ardour go to the top and look at the menus up there   choose OPTION > MONITORING > ARDOUR DOES MONITORING 
3. TRACK > ADD TRACK/BUS  plug your guitar in arm the track are you getting sound ?
Now launch RAKARRACK 
1. it should connect already to QJACKCTRL  dont mess with it .
2. got to the top of Ardour menus   . VIEW > SHOW EDITOR MIXER . make sure editor mixer has a check by it ,
3.  That little track buss mixer  to the far left on Ardour  lets say it says audio 1 ,    below where it say audio 1 click that little grey rectangle , click edit  . You see a window pop up audio 1 input       inputs      available connections   , under available connections click rakarrack  , then click out 1 and out 2 .   
4  click on your RAKARRACK  GUI    see the top menu FILE BANK SETTINGS HELP , below FILE dont click on file . there is a grey square that says fx on , click on it , itll lite up red , you should hear your guitar being processed . to the right of that is the presets   click the arrow    <  1  >   to got through the  presets .

---

