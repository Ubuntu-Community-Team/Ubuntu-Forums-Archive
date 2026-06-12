---
title: "Recording with an Emu-0404 PCI... Help"
date: 2009-11-25
forum: Ubuntu Studio
---

### Post by Sanopaid on 2009-11-25
[B]HI ALL:
[/B]I'm writing here , because i'm new at ubuntu and i have some issues with my sound card.

i have an Emu-0404 PCI, I had been using it to record in windows xp , but now i changed to ubuntu studio, as I've heard it has some great aplications , but i am getting troubles with my sound card.

At first the system wouldn't recognize it, but reading through this forums , i found out it was a firmware problem and  it is solved , now, ubuntu studio recognizes it , and in the sound preferences panel i can select it  and use it to get sound, so as an output it works perfectly. But it wont recognize any input, I tried to plug my guitar , and my mic , but it wont do anything i doesn't report any kind of data , as if I wasn't playing.

I've read that lots of people use this card to record , and have it perfectly functional in ubuntu , so if anyone  is recording like this , please tell me how to configure it or what to do to solve this , if any one that tels me how they set up their system I would be really thankful.

Of course any information is well received , an thanks to all that may help.

Have a Nice Day ;).

---

### Post by sgx on 2009-11-26
Hope I'm wrong, but at least some of the compatibility info pertains to usb versions of E-mu soundcards, but since playback works,

Start qjackctl, click setup in the gui, on the right side, halfway down, are
Input Device / Output Device, click the widgets shaped like >

Clicking these will reveal what sound devices are seen by your system. If your 0404 card is there, select it.

You can install and use timemachine, a one-big-button recording app that
will be listed in qjackctl when started, connect it to zynaddsubfx, hydrogen, or other software instrument to test recording. There will be three tabs in qjackctl, audio, midi, and alsa. The soundcard anf timemachine in the audio tab should be connected.

alsaconf is a command to get the alsa sound system to configure your soundcards, it will ask a few questions, and needs root permissions, so

sudo alsaconf


Cheers

---

### Post by Sanopaid on 2009-11-28
> **sgx said:**
> Hope I'm wrong, but at least some of the compatibility info pertains to usb versions of E-mu soundcards, but since playback works,

Start qjackctl, click setup in the gui, on the right side, halfway down, are
Input Device / Output Device, click the widgets shaped like >

Clicking these will reveal what sound devices are seen by your system. If your 0404 card is there, select it.

You can install and use timemachine, a one-big-button recording app that
will be listed in qjackctl when started, connect it to zynaddsubfx, hydrogen, or other software instrument to test recording. There will be three tabs in qjackctl, audio, midi, and alsa. The soundcard anf timemachine in the audio tab should be connected.

alsaconf is a command to get the alsa sound system to configure your soundcards, it will ask a few questions, and needs root permissions, so

sudo alsaconf


Cheers

well thanks , ill try it and let you know if it works,
really appritiate it . ;)

---

### Post by QwUo173Hy on 2009-12-06
I've just been given one of these cards as a gift and Ubuntu Studio doesn't recognize it. Is the only solution to upgrade the firmware on a windows machine?

---

### Post by sgx on 2009-12-06
back in February, zajaro posted this:

so far as I know there is two different version of the emu 0404 pci, you can tell one from the other by running lspci -nn. the model that works is the one that has identifier [1102:0008]. the other ( the [1102:0004]) is not working right now.

------------------------------------------------------------------------

There may be an alsa-firmware package in the repositories that can help this?
Another hope is to get all the latest distro live dvd/cd, in hopes something is rolled up right in one of those. 

Also, the 0404 pci card is listed in the Alsa soundcard matrix, with directions to get kernel modules working, if you're able to get down that road. The directions are well laid out. I don't know if that overcomes the version differences noted above.

Cheers

---

### Post by QwUo173Hy on 2009-12-06
Excellent, I didn't know about the firmware package and I see it in the repository now. (It's in the Medibuntu repo incase anyone else doesn't see it.)

Thanks sgx.

---

