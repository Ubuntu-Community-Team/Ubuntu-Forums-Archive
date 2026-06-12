---
title: "multiple cartes son jack config probleme"
date: 2014-03-06
forum: Ubuntu Studio
---

### Post by axiome23 on 2014-03-06
Bonjour à tous  ; 
Linuxien depuis 2 ans , je tourne avec une machine de recup mais de bonne facture je crois .
Je suis artiste musicien et travaillais auaparavant depuis 1995 sur windoz95 cubase 3.0  , synthe hardware et sampler.
Depuis je tourne sur artistix et sur une machine hardware faites en diy toute analo. Voila pour la prez. 
 Mon souci ? mettre en place ma machine avec jack et ma carte son externe maudio delta44 , donc je poste le resultat
 d un script alsa project  ici que vous puissiez me faire un diagnostic .

[http://www.alsa-project.org/db/?f=42d3ac4f7ceebd7761731d0f58cb1a5027ec2974](http://www.alsa-project.org/db/?f=42d3ac4f7ceebd7761731d0f58cb1a5027ec2974)


Si du monde veut des conseils en diy sur des synthe ect n hesitez pas 
 projet kontaktor visible à [https://www.facebook.com/media/set/?set=a.399050846851502.93575.100002397718794&type=1&l=27457300da](https://www.facebook.com/media/set/?set=a.399050846851502.93575.100002397718794&type=1&l=27457300da)

status/ vener fatigue decouragé on arretera pas ce qu on a commence tant qu on aura pas terminé .

---

### Post by brianmc on 2014-03-08
I've had to resort to Google translate, but let me give this a go:

> **axiome23 said:**
> 
[http://www.alsa-project.org/db/?f=42d3ac4f7ceebd7761731d0f58cb1a5027ec2974](http://www.alsa-project.org/db/?f=42d3ac4f7ceebd7761731d0f58cb1a5027ec2974)


Firstly, you're not running a lowlatency kernel:
> ```

[FONT=courier new]!!Kernel Information
!!------------------

Kernel release:    3.8.0-35-**generic**
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes[/FONT]
```

You should see something like:
```

[FONT=courier new]!!Kernel Information
!!------------------

Kernel release:    3.11.0-18-**lowlatency**
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes[/FONT]
```

If - since you're running a generic kernel - you've not installed all  the Ubuntu Studio stuff, there are various meta packages you can quickly  update with.
```

[FONT=courier new]sudo apt-get install ubuntustudio-desktop ubuntustudio-audio linux-lowlatency[/FONT]
```

Your Delta 44 card is recognised, as-seen in this section:
> ```
[FONT=fixedsys]
[FONT=courier new]!!Loaded ALSA modules
!!-------------------

**snd_ice1712**
snd_hda_intel[/FONT][/FONT]
```

The **[FONT=fixedsys]*snd_ice1712*[/FONT]** is the Delta 44 card. But, you would be advised to avoid trying to combine it with the Intel HDA card. You *could*  use one as input, and another as output. That's something to set up in  the JACK setup.

Seen below; jack isn't running, or you are using *[FONT=fixedsys]jackdbus[/FONT]*.
> ```

[FONT=courier new]!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - **No**[/FONT]
```

You can check for jackdbus with *[FONT=courier new]ps aux | grep jackdbus[/FONT]*, you should see a line for *[FONT=courier new]/usr/bin/jackdbus[/FONT]*. If it's not running, best to start that via **[FONT=fixedsys]*QJackCtl*[/FONT]**.

I wouldn't try any of the ALSA hacking possible to combine these into a single virtual card, but you might try the [FONT=courier new]*alsa_in*[/FONT] or [FONT=courier new]*alsa_out*[/FONT] commands in a terminal. These may help you get one card running properly under JACK, and a second as a 'supplement' for extra input or output. For that, you want to use *[FONT=courier new]**QJackCtl**[/FONT]* against one card. 

For example, I've just set up my AMD box here to use my ICE1712 card (Edirol 2496) as the master card in JACK (The hw:<name> is DA2496, whereas you seem to have M44). I can then use [FONT=courier new]***alsa_out***[/FONT] to run the PC's outputs as an additional monitor output. 
```

[FONT=courier new]alsa_out -j onboard -d hw:SB[/FONT]
```

Obviously, this isn't the same onboard card as you've got, but you may be able to substitute [FONT=fixedsys]*hw:1*[/FONT] or [FONT=fixedsys]***hw:Intel***[/FONT] in-place of [FONT=fixedsys]*hw:SB*[/FONT] to get the same result. I then found myself having to go into the Alsa mixer and crank up the volume on its master output. You'll probably need to tweak the volume, mute, and patchbay, controls for your Delta 44 via the Mudita24/Envy24 mixer.

Longer-term [FONT=courier new]*alsa_out*[/FONT] is something you'd build into scripts ***[FONT=courier new]QJackCtl[/FONT]*** runs on startup/shutdown. For example, this oneliner will start both [FONT=courier new]*alsa_in*[/FONT] and *[FONT=fixedsys]alsa_out[/FONT]*; I do find running both is quite a noticeable CPU hog.
```

[FONT=courier new]*(alsa_out -j onboard-out -d hw:SB) & (alsa_out -j onboard-in -d:hw:SB) &*[/FONT]
```

Lastly, the oneliner can even be placed in the "[FONT=fixedsys]*Execute script after Startup:*[/FONT]" field on **[FONT=fixedsys]*QJackCtl*[/FONT]**'s Options tab in [FONT=fixedsys]*Setup*[/FONT]. What to watch there is making sure you save any customisations by going back to the Settings tab. If the [FONT=fixedsys]*Save*[/FONT] button is greyed-out, just check and uncheck one of the options to make sure you save setting changes on other tabs.

---

