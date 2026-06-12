---
title: "M Audio Delta 1010lt is not recognized"
date: 2010-08-19
forum: Ubuntu Studio
---

### Post by benjammin105 on 2010-08-19
I've had my delta installed under windows and I've recently changed my system over to studio and I cannot find any mention of it under any menu. I tried the maudio site for drivers but it didnt work. Any suggestions??

---

### Post by sgx on 2010-08-20
Hi, start qjackctl, and press the setup button in the gui,
then at the far right, halfway down, you see > by the lines
reading 

Input Device
Output device

Click the >   and a list of your possible sound sources will drop down,
ICE1712, or M-Audio XXX will be the ones to consider using. ICE1712 is
linux-speak for the the m-audio chipsets. 

From there, back on the main qjackctl gui, press the Connect button.
A three tab gui appears, ignore the middle tab, the Alsa tab will display
your m-audio midi ports, and the Audio tab will have your souncard i/o.
Various hardware/software show up in these, make connections by highlighting an item on each side, and pressing this panels connect button
(not the one on the main gui).
There are  several google hits for 

ubuntu m-audio 1010 lt

if some odd issue is present. Cheers

---

### Post by Pablo_F on 2010-08-20
Hi,

To know for sure if your card is actually being recognized or not, open a terminal and paste the following informative commands:

lspci | grep -i audio

(list the audio pci devices) 

cat /proc/asound/cards

(list the cards that alsa recognises)

cat /proc/asound/modules

(list the modules that alsa has loaded)

Then, before trying to setup jack you should check the "Envy24control" tool. It is similar to the Windows and MacOSX controllers that you will find in the manual. You need to install "alsa-tools-gui" from synaptic and it will show up in Applications -> Sound and Video.  

Roughly, the alsa driver (ice_1712 module) is what talks to your hardware device and you setup the mixer and converter levels via Envy24control. Then, at a higher level, in Ubuntu(studio) there are two sound systems available: pulseaudio and jack.

The first one is the default and most multimedia players use it. It is integrated in gnome, so System -> Preferences -> Sound is a pulseaudio frontend. However, there is a problem with pulseaudio and ICE1712 based soundcards that is documented here:

  [https://bugs.launchpad.net/ubuntu/+s...io/+bug/178442](https://bugs.launchpad.net/ubuntu/+s...io/+bug/178442)

I suggest you try the work around in comment #30. 

The second sound server, jack, is what you will normally use for music creation. You normally set it up via Jack Control.

Cheers! Pablo

---

### Post by benjammin105 on 2010-08-20
Thanks a lot! I found the M Audio Delta options in Jack Control!

---

