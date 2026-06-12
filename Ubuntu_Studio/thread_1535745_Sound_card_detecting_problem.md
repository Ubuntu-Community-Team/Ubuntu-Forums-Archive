---
title: "Sound card detecting problem"
date: 2010-07-21
forum: Ubuntu Studio
---

### Post by V-music on 2010-07-21
Hello.
I have integrated sound card (disabled in BIOS) and Creative Audigy SE PSI card (Ubuntu studio 10.04 installed).

Why sound system not always detected my Creative card as hw:0 ?
Sometimes (after restarting the computer) card was detected as hw:1 (I use aplay -l ). And i must to change the settings in multimedia soft (jack for example): hw:0 to hw:1.
 
Someone can help ? Thanks.

---

### Post by Pablo_F on 2010-07-21
Hi V-music, 

I don't know the reason why linux changes the indexes but you can:

Either give the card a fixed index number in /etc/modprobe.d/alsa-base.conf

Or, don't use the index ID in qjackctl's settings, but rather, the name of the card, as seen with aplay -l or cat /proc/asound/cards

 This is an example of the second option (my case and what I do):

$ cat /proc/asound/cards

 1 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xbc00, irq 22

So I write down in the interface field of jack the following, even if this doesn't appear as an option:

hw:M2496

And I never again have to worry about jack not choosing the right interface.

HTH, 

Pablo

---

### Post by V-music on 2010-07-22
Thank you Pablo for your informative answer. I used $ cat /proc/asound/cards and than entered in the interface field of jack my card  -  hw:CA0106. It is work very good.

---

