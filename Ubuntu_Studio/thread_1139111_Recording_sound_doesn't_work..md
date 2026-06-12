---
title: "Recording sound doesn't work."
date: 2009-04-26
forum: Ubuntu Studio
---

### Post by Master-of-None on 2009-04-26
Recording sound via a microphone, record-my-desktop, and rendering video with audio doesn't work on my laptop, or our desktop computer. Help?

---

### Post by B4RR13N705 on 2009-04-27
Did you check volume settings? maybe Mic is muted.

---

### Post by Master-of-None on 2009-04-27
No mic/capture isn't muted.

---

### Post by elliotn on 2009-05-01
I have the same problem, I can hear myself on the speaker when I talk over the mic but When I record the sound doesnt get recorded

---

### Post by B4RR13N705 on 2009-05-01
I used to have the same problem with a Realtek audio card. I didnt found any solutions. I have tried all. So, i bought a Genius sound-card and now it works perfectly.
Is your sound card Realtek?
Is a IN-MOTHERBOARD card?

---

### Post by elliotn on 2009-05-02
Mine is a pci Crystal Fusion which works in windows. It seems as its some that need to b workd on

---

### Post by flaviocpontes on 2009-05-02
I have the same problem here.

My sound card is an onboard HDA Intel with Realtek ALC888 codec.
I had audio recording until I upgraded to Jaunty. Now it doesn't work anymore.:cry:

Any hints on what can be wrong?
](*,)

---

### Post by B4RR13N705 on 2009-05-02
I have the same onboard realtek, and i never could capture anything. I had to buy a new one, a genius, this sounds and record like heaven :guitar:

---

### Post by d_in_Conduct on 2009-05-03
Flavio,
I'm running Jaunty with that same audio device.  There are several places where you can play with the configuration.  I've had to go through all three several times until I got the right combination of settings.

My main needs are recording from Line-in and, of course, playback.

First check System > Preferences > Sound.  There are several settings with test buttons to see if they work.

Then go to the little loudspeaker icon in the upper-right corner and select volume control.  Make sure the stuff you want is turned on and has the gains up.

Then from a terminal run alsamixer.  If you have it,  it will show what's on and what the levels are on those.

I had to go back through all of those things several times before I got sound working.

---

### Post by josefg on 2010-01-09
Open Alsamixer and uncheck the "Mic bypass" box, that worked for me.

---

