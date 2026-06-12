---
title: "Soundcard Terratec PHASE28 / controlling the 'preamp'? (U.St. 14.04)"
date: 2016-04-26
forum: Ubuntu Studio
---

### Post by Olli_Restgold on 2016-04-26
Hi, I'm a Ubuntu Studio newbe, and I'm using Ubuntu Studio 14.04. I have some sounding trouble with my soundcard Terratec PHASE28. Based on a ICE1724 Cipset, Ubuntu (studio) recognizes the (PCI) card:

> xxx@xxx:~$ cat /proc/asound/cards
 0 [T28            ]: ICE1724 - Terratec PHASE 28
                      Terratec PHASE 28 at 0xdc00, irq 17
xxx@xxx:~$ lspci | grep -i audio
01:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)


The card is working, but the output is somekind of "fuzzy", like a wide open overdrive in front of a power amp. Think, this is not a hardware problem, a have a sound Phase28, and in the result it is the same thing ... :(
The ALSA-System ist running, I use the Qasmixer to control it. But I have to less volume power from my soundsystem, if I like to have a clean sound.

Any ideas, how to fix this? Thx. to all friendly helpers ... O:)

---

