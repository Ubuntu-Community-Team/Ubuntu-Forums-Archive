---
title: "My T430 laptop with desktop GPU"
date: 2016-04-28
forum: The Cafe
---

### Post by Konjad on 2016-04-28
At the end of 2013 I have bought T430 laptop with i5-3320m and integrated graphic card which is not powerful enough for someone who enjoys playing computer games, including the new ones. Hence why at the beginning of this year I have assembled external graphic card setup with MSI GTX 560 Ti Twin Frozr II which lets me play games such as Divinity: Original Sin or Alien: Isolation on maximum details. My eGPU kit consists of four parts: the graphic card itself, adapter, ATX power supply and a case to fit it all in for convenience. Of all the adapters I chose PE4L 2.1b as it has a good opinion and was already tested by many people before. For a GPU I bought GTX 560 Ti because it's a powerful but at the same time an inexpensive card. I was limited to Nvidia because ATI doesn't support anything resembling Optimus technology which would allow me to display the output of the eGPU on the laptop's internal screen instead of an external monitor. As the power supply I got Fortron FPS350-60MDN, while it's not very powerful in general, it does have a great 12V line which is all that matters for an eGPU anyway (19.5V, while my GPU is only 170W, so even a 15V would be enough, it leaves space for further upgrade to an even more demanding card in the future). Finally, I got a SilverLight SG05 Lite as the case to put everything inside so as to avoid potential damage to the hardware and a mess on a desk. 

[img]http://i.imgur.com/80tjhma.jpg[/img][img]http://i.imgur.com/ARngqzR.jpg[/img][img]http://i.imgur.com/lrBkEol.jpg[/img]



When I purchased T430 I instantly installed Linux Mint on it and used it ever since. Which is why it was the first operating system I tried to use my eGPU in. Nvidia doesn't make Optimus technology available on GNU/Linux systems, however, there's open-source [Bumblebee](http://bumblebee-project.org/) which serves the same purpose. I followed [the instructions for Ubuntu 13.10](https://wiki.ubuntu.com/Bumblebee#Installation) to install Bumblebee and executed a command: 
*sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic primus-libs-ia32 *
Having open-source drivers Nouveau already installed, I proceeded to test a few games. Unfortunately, the performance in all the games was extremely disappointing, regardless of graphic settings and how demanding the games were. Kerbal Space Program, Left 4 Dead 2 and Depths of Peril all were displayed with only 8-10 frames per second, while Depths of Peril, being a low-demanding game, was running fine on maximum settings on Intel HD 4000. Afterwards I installed the newest Nvidia's linux drivers (340), but there was only a slight improvement of two more frames per second. Then I tried older 331 drivers and when I hadn't seen improvement, I removed all the drivers and libraries and repeated everything with no avail. 


Because I couldn't use my eGPU on Linux Mint, I installed Windows 7 and updated it. Afterwards I installed Nvidia's 347 drivers and tested some games, but this time I had another issue - I had high frame rates but every few seconds the image would freeze for a second. The issue was present in all the games I have tried: Divinity Original Sin, Alien Isolation, Left 4 Dead 2, and so on. I tried all the available settings and nothing would help. Finally, in Killing Floor game and [Valley benchmark](https://unigine.com/products/valley/) I noticed the issue is restricted to DirectX, as in OpenGL I have a stable and satisfying performance. In the Valley I had 40 FPS with drops to 2 FPS in DirectX on Ultra details, while in OpenGL I had stable 30-35 FPS. It was a bit bewildering, but that meant the problem clearly pertains to the software and not the hardware. I installed the 340 drivers and restored the default settings in Nvidia Control Panel, then tried running Valley benchmark again - this time everything worked as it should. I had stable ~35 FPS on Ultra settings with no AA and 1600x900 resolution. Then I tested games and they were also running with high performance. A few days later I tested performance using various versions of the Nvidia's driver and this is what I found out: The best drivers for GTX 560 TI are 331. 340 gives a few FPS less than 331 (in Divinity Original Sin and Fallout New Vegas), 347 there's an issue of freezing every few seconds, and 314 works similarly to linux drivers - performance is extremely low and games run in about 10 FPS. 

[img]http://i.imgur.com/06OBlic.jpg[/img][img]http://i.imgur.com/AXYg8CW.jpg[/img]



I am very happy with this setup as I am able to play modern games in maximum details on my T430. With eGPU it's not really a mobile hardware, but I play games only in my room anyway, when I need to take my laptop with me somewhere else I just disconnect the external GPU and use HD 4000. After all, outside I only need the laptop for simple tasks such as writing. It's just a shame Nvidia's drivers are so useless for Linux, but to be honest, all GPU drivers are disappointing in Linux. Hence why for games I have to dual boot.



Here is a description about how particular games work on my setup:

All of the games were tested on internal monitor in resolution 1600x900 and turned off antialiasing. Frames per second were counted by Steam. The graphic card used with the egpu setup was MSI N560GTX-Ti Twin Frozr II. Windows 7 64bit, Nvidia drivers 340 or 331.

**Alien: Isolation** - works fine
Works on maximum graphic details with about 60 FPS, albeit has infrequent drops, of which the highest ones were to about 35 FPS, so it is the most convenient to play with FPS limited to around 35 FPS for fluent gaming experience.
[http://i.imgur.com/oQ0aZOU.jpg](http://i.imgur.com/oQ0aZOU.jpg)
[http://i.imgur.com/KQhQKFB.jpg](http://i.imgur.com/KQhQKFB.jpg)
[http://i.imgur.com/u7zGLT0.jpg](http://i.imgur.com/u7zGLT0.jpg)

**Anno 2070 **- works great
On maximum graphic settings (without vsync and AA) FPS is within 45-60 range, drops to around 30 FPS when on double speed and far off camera.

**Assetto Corsa **-  works great
On High pre-set the game has >55 FPS during a race with three AI opponents, albeit it had a rare dropdowns to 45 FPS. When racing with a maximum amount of AI, the game's frames annoyingly dropped when multiple AI controlled cars were displayed.

**Armed Assault 2 (aka ArmA 2) **and** ArmA 3** - barely playable
Regardless of graphic settings games have drops to around 20 FPS. The performance is disappointing and playing these games with such low frame rates is inconvenient. The average FPS is about 25.

**Betrayer **- works fine
FPS never goes below 30 on medium-high graphic settings.
[http://cloud-4.steamusercontent.com/ugc/700643653006342052/0A91B29F2BAA5EA824C3A8BDD911ADDD42A7339D/](http://cloud-4.steamusercontent.com/ugc/700643653006342052/0A91B29F2BAA5EA824C3A8BDD911ADDD42A7339D/)
[http://cloud-4.steamusercontent.com/ugc/700643653006342529/D0D98DA31FC9886DCC37BE65303ADC9F3AAA502B/](http://cloud-4.steamusercontent.com/ugc/700643653006342529/D0D98DA31FC9886DCC37BE65303ADC9F3AAA502B/)
[http://cloud-4.steamusercontent.com/ugc/700643653006344907/2F6D97CE7BD5C8F9965A2227CC784B5FA0BC8316/](http://cloud-4.steamusercontent.com/ugc/700643653006344907/2F6D97CE7BD5C8F9965A2227CC784B5FA0BC8316/)

**Cities:Skylines ** -  works fine
FPS never went below 30 FPS on medium graphic settings.

**Divinity: Original Sin** - works fine
The game works on maximum graphic settings with stable 30 FPS and with no drops, which makes it perfectly playable. On the screenshots some effects such as Depth of Field are turned off, but that is only because of my personal preferences as I dislike such effects.
[http://i.imgur.com/gUBDjUm.jpg](http://i.imgur.com/gUBDjUm.jpg)
[http://i.imgur.com/DQFFE9V.jpg](http://i.imgur.com/DQFFE9V.jpg)
[http://i.imgur.com/ltE6BEH.jpg](http://i.imgur.com/ltE6BEH.jpg)

**Dragon Age 3** -  works fine
On medium pre-set the game works fine enough and is playable. The game's benchmark shown average of 33.7 FPS and minimum of 26.8 FPS. I did not measure FPS in-game, but it seemed to me that the FPS was corresponding to the benchmark's results.

**Euro Truck Simulator 2 **- unplayable
On minimum graphic settings the game runs with 15-20 FPS, on maximum with 8-12. Therefore the game is unplayable.

**Fallout: New Vegas **and **The Elder Scrolls series **– works great
Stable 60 FPS on maximum details

**Grim Dawn** -  works great
FPS never went below 40 FPS on maximum graphic settings.

**Hitman: Absolution **-  works fine
FPS never went below 30 FPS on maximum graphic settings.

**Kerbal Space Program** - works fine
The game works fluently on maximum graphic details with around 35-50 FPS. Using integrated Intel HD 4000 the game runs stable on average graphic settings with 60 FPS (but has drops to thirties on Kerbal), whereas on eGPU it never goes beyond ~50 FPS regardless of graphic settings.
[http://i.imgur.com/UNGhVNB.jpg](http://i.imgur.com/UNGhVNB.jpg)
[http://i.imgur.com/UagUeEV.jpg](http://i.imgur.com/UagUeEV.jpg)

**Left 4 Dead 2** - works great
The game works with stable 60 FPS on maximum graphic settings.

**Metro 2033 **- barely playable
Similarly to ArmAs, regardless of graphic settings the game has drops to around 20 FPS, although the average FPS is 30-40 depending on the grapic settings.
[http://i.imgur.com/xzU2Bh7.jpg](http://i.imgur.com/xzU2Bh7.jpg)
[http://i.imgur.com/ncpFBzv.jpg](http://i.imgur.com/ncpFBzv.jpg)

**Pillars of Eternity **-  works okay
FPS around 30 FPS on maximum graphic settings, but there were some drops to about 25 FPS.

**Serious Sam 3 **- works great
On high/high/high settings the game's frame rates never go below 43 FPS.
[http://i.imgur.com/pKdeUZm.jpg](http://i.imgur.com/pKdeUZm.jpg)
[http://i.imgur.com/v5AQPAg.jpg](http://i.imgur.com/v5AQPAg.jpg)

**Starcraft 2**  - works great
Graphic settings:
Textures: Ultra
Pre-set: High
FPS never goes below 45 FOS when playing a 6-player match, including larger battles. 

**The Long Dark**  and  **The Forest **- unplayable
Both games run with about 15-20 FPS regardless of graphic settings. Even lowering the resolution did not give significant boost to performance. They are playable, but with such low FPS it is very inconvenient.

---

### Post by DuckHook on 2016-04-29
*Your thread has been moved to **The Cafe** as the forum more suited to your issue.*

**Not a support request**

---

### Post by Konjad on 2016-08-01
I have upgraded my eGPU setup with GTX 670. I can play Witcher 3 on a mix of ultra and high settings on it ;)

[img]http://i.imgur.com/uIRP3TR.jpg[/img]


here's a firestrike result:

[img]http://i.imgur.com/TLc799L.jpg[/img]

---

