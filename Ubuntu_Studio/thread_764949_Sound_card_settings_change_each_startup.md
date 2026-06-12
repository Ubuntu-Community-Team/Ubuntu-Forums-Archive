---
title: "Sound card settings change each startup"
date: 2008-04-24
forum: Ubuntu Studio
---

### Post by garyed on 2008-04-24
I originally posted this in the beginners group & I hope tihs is not a no-no  but i think this is probably a better group for my question.  
My problem is every time I boot up I never know what my sound cards place will be given, 0,1, or 2. I have three sound devices.
1 - Onboard - disabled in bios but still shows up in Ubuntu studio Gusty
2 - M-audio 2496
3 - Sound Blaster Live

I mainly use just the M-audio but sometimes I might want some sound out of the SBlive. Anyways everytime I boot up I have to check "/proc/asound/cards"
to find the number of my M-audio card to set up Jack for recording. Is there any way to keep the card numbers constant on every boot?
__________________
I found this solutution in another forum so i figure I'n post it here:

To solve multiple sound cards order from changing on boot-up take the output  of:

cat /proc/asound/modules
(Should look something like this)
 0 snd_ice1712
 1 snd_emu10k1
 2 snd_via82xx
--------------------
Then edit "/etc/modprobe.d/alsa-base" file & add the following lines to the end of the file in the order you want the cards to be using the results of your output like this:

options snd-ice1712 index=0
options snd-emu10k1 index=1
options snd-via82xx index=2
-----------------------------------
Note: The spacing has to be exact with special notice to no spaces between "=" sign.

---

### Post by zequence on 2013-04-04
What I would do is set jack to start by the name ID instead of the number ID. To get the name ID, do:
```
$ cat /proc/asound/cards 
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe300000 irq 16
 1 [M66            ]: ICE1712 - M Audio Delta 66
                      M Audio Delta 66 at 0xd040, irq 21
 2 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe080000 irq 24
```

The name ID I like to use here, is "M66". So, to start jack, I do:
```
jackd -d alsa -d hw:M66
```

This also works in qjackctl. You just need to enter the name manually in the "interface" field.

---

### Post by wildmanne39 on 2013-04-05
Thanks for sharing! Thread closed. Please do not post in old threads.

---

