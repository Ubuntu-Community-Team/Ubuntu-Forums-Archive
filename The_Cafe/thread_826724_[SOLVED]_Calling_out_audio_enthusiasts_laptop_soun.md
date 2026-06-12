---
title: "[SOLVED] Calling out audio enthusiasts: laptop sound card hunt"
date: 2008-06-12
forum: The Cafe
---

### Post by blueturtl on 2008-06-12
Hi all.

I've recently been considering replacing my desktop system with a laptop. Problem is I am a bit of an audio enthusiast and cannot cope with integrated sound of any type.

Can someone recommend a good sound card for laptops? USB is not out of the question, but I'd prefer if the card had a FireWire or PC-card interface. I don't do recording so many inputs or outputs are not necessary, I'm really just interested in a card with good quality output (DACs) and that is Linux compatible, or reasonably easy to set up under Ubuntu.

Price can be up to a 100 €, but if the card really is awesome I suppose I could go over that to 150 €.

---

### Post by mips on 2008-06-12
See,

[http://www.emu.com/products/](http://www.emu.com/products/)
[http://www.m-audio.com/index.php?do=products.family](http://www.m-audio.com/index.php?do=products.family)
[http://www.digidesign.com/index.cfm?navid=2&langid=100&itemid=22700](http://www.digidesign.com/index.cfm?navid=2&langid=100&itemid=22700)

If you see something you fancy then go and look up the linux driver support. I know support in emu & m-audio is good in linux for some of their products.

---

### Post by blueturtl on 2008-06-12
Thank you for the product links.

However it turns out buying something that is ear-marked Linux compatible is not necessarily the safest bet. I've bought a printer and a wireless card based on supposed Linux support, and both had issues when I was expecting pretty much plug-and-play operation.

That is why I'd very much like contributions from someone who actually owns the kind of card I'm looking for and can recommend it based on experience.

I do not mind if I have to go through trouble to set the card up as long as it works!

Anyone?

---

### Post by smbm on 2008-06-12
I would also like a decent quality sound card for my laptop.

I was looking at the M-Audio ones but it seems like they're a lot of hassle to set up, you need a script to inject the firmware in when you connect them etc. Then you've got to configure Pulseaudio to switch to the USB one when you plug it in.

Has anyone got any positive experiences with this?

---

### Post by blueturtl on 2008-06-12
After an afternoon of browsing different products I'm now looking more closely at the Echo Corporation Indigo IO.

This is a PC-card with just one set of i/o connections.
Sound quality is supposed to be good based on multiple online reviews. Also the [ALSA project page]("http://www.alsa-project.org/main/index.php/Matrix:Module-indigoio#The_module_options_for_snd-indigoio") lists the card as supported.

Anyone have a say about this card?

Still taking suggestions for other cards as well...

---

### Post by blueturtl on 2008-06-15
Bump. Can anyone confirm the Echo Indigo IO working with any version of Ubuntu?

---

### Post by ish4269 on 2008-06-26
> **blueturtl said:**
> Bump. Can anyone confirm the Echo Indigo IO working with any version of Ubuntu?

I have The Echo Indigo DJ working in gusty 7.10, I can't give you a step-by-step because I did a few things randomly.

However, I think all I had to do was use adept_manager to install alsa-firmware*, alsa-tools*, alsa-utils, insert the card, restart the computer it should work, fingers crossed

Intially I went to the ALSA website and looked at the info there
[http://www.alsa-project.org/main/index.php/Matrix:Module-indigoio](http://www.alsa-project.org/main/index.php/Matrix:Module-indigoio)

Also, when you've installed the above packages look out for a program called echomixer.

Try this site [http://www.geocities.com/rburra/echo.html](http://www.geocities.com/rburra/echo.html)

---

### Post by blueturtl on 2008-06-26
Thank you for your contribution!

I already bought my Indigo I/O and am now just waiting for it to arrive.

I will post later on how the set up process went.

---

### Post by blueturtl on 2008-07-07
Finally received my Indigo I/O today and this is how it all went:

I unwrap it to find a very neat looking PCMCIA card, a driver CD and a set up note. The note says to install drivers first and plug in the card before starting the computer. Having already installed the alsa-firmware package from the Medibuntu repositories I just plugged the card in and fired up. During the boot process the light on the card lit up which I considered a good sign. After booting ```
cat /proc/asound/cards
``` shows the Indigo IO as detected and configured.

Excited I plug in my wife's iPod headphones (speakers still packed away from the trip) and start Frozen Bubble. The sound comes out of the laptops on speakers. Following my hunch I try to set the Indigo as the default device in several places:

System->Preferences->Sound and Pulse Audio Device chooser. Neither of them work. I use the mixer to play with the volume levels, I fire up Echo mixer also. None of this works, but knowing it's probably just a matter of getting the right audio device to ouput I head to Google in search of answers.

I find a page on the Linux forums that has to do with audio card selection in ALSA. Turns out I have to edit the file /etc/modprobe.d/alsa-base and make sure the laptop integrated audio hardware does not come first.

So adding a simple line
```
options snd_atiixp index=1
```

and a reboot later I now get sound from the Indigo. Although the headphones I have to test with are crappy the sound is very clear and distortion free. I will post an evaluation of the sound quality once I get my speakers hooked up. :)

Anyway, looks like a total success. The set up part was not hard at all, so I totally recommend this card for any Linux audio enthusiasts!

---

### Post by blueturtl on 2008-07-12
Final post. This is the review I posted on eBay after some more listening experiments:

Having recently changed over to a notebook pc I was looking for a high quality replacement of my old desktop audio system. There are a lot of big bulky external cards with many inputs and outputs that are well suited to amateur musicians. With just one input and one output plug this card has the perfect feature set for a person like me. I mostly just listen to music through high quality speakers. To me, the only thing that matters is high quality output of sound. In that regard this card is the best I've heard on a portable system, but comes a bit short of my old desktop system which was powered by the M-Audio Revolution 5.1. The Revolution has very high quality DACs so it's sound was a bit more detailed in the mid-to-high range of sound. The only reason this is significant to me is because I'm replacing the Revolution with the Indigo I/O. For those of you looking for good on-the-road sound and who have trouble coping with integrated sound cards, this is the card you're looking for.

A subjective analysis of it's sound follows: Very clean and distortion free sound. In fact the sound stage is so clean it almost sounds clinical, like someone is cutting noise away with a filter or something. The card is at it's best with music where the sound stage is clean and there is a clear focus on a specific instrument. If the Revolution was rich in detail, the Indigo I/O seems more like the revealing sort. There are things you notice because the sound is so clean rather than because they're being put forth. The low-end seems rather warm, but is thankfully well defined and not boomy. This slight lean towards the low-end might upset some who expect perfect tonal balance though. Even if slightly colored, the sound is still pleasant and does not cause fatigue immediately as the volume increases.

As a note to those with headphones, the card boasts a powerful amplifier with an external volume control.

The software included was left untested as I am using the card with Ubuntu Linux. The card should work with any modern Linux-based operating system as long as the alsa-firmware package is installed (this package contains the firmware for Echo Indigo I/O as well). For Windows support is guaranteed, though I have not tested to see how well it works.

If I were to rate this sound card purely on it's own basis and not against my old set up, I would give it an excellent rating.

(Rated 4/5, Good)

---

### Post by 23meg on 2008-07-12
It's a good idea to search the archives of the [Linux Audio Users mailing list]("http://lad.linuxaudio.org/subscribe/lau.html"), and ask there if you can't find relevant information.

---

