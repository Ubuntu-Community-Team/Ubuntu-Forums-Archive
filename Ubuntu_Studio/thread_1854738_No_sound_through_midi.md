---
title: "No sound through midi"
date: 2011-10-05
forum: Ubuntu Studio
---

### Post by blackone86 on 2011-10-05
So, i just installed studio and have my akaimpk connected through usb. In jack connections there is nothing under the audio tab or midi but, Alsa recongnizes the akaimpk. I connected it and opened a synth program and it seems to be responding but with no sound??? Im assuming this has to do with nothing being located in the audio tab in jackd??

thanks

---

### Post by sgx on 2011-10-05
Hi, try installing a2jmidid and use the command

a2jmidid -j default

this should open a midi port in the qjackctl midi tab.
In the alsa tab, you, or others with differing setups,
may need or want to connect any midi-through
ports to your soundcard midi where a midid keyboard is recognized. 

Yoshimi requires a2jmidid, phasex and zynaddsubfx do not.
Cheers

---

### Post by jejeman on 2011-10-05
> **blackone86 said:**
> So, i just installed studio and have my akaimpk connected through usb. In jack connections there is nothing under the audio tab or midi but, Alsa recongnizes the akaimpk. I connected it and opened a synth program and it seems to be responding but with no sound??? Im assuming this has to do with nothing being located in the audio tab in jackd??

thanks
That akai mpk is midi controler not a synth, right? If that is true it sends just midi data thru usb. So there would not be any instance in audio tab, just in Alsa. Or in midi tab if you use what sgx said.
You need to connect audio output of soft synth to audio card's playback in audio tab to get sound from it.

---

### Post by sgx on 2011-10-05
> **blackone86 said:**
> So, i just installed studio and have my akaimpk connected through usb. In jack connections there is nothing under the audio tab or midi but, Alsa recongnizes the akaimpk. I connected it and opened a synth program and it seems to be responding but with no sound??? Im assuming this has to do with nothing being located in the audio tab in jackd??

thanks
Here are the connections docs/pics:
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

and more : [http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

Cheers

---

### Post by blackone86 on 2011-10-11
Thanks for that link. I understand now how to connect them the problem is i dont have those options. 

[ATTACH]204065[/ATTACH]

I have nothing under midi or audio only under alsa?

---

### Post by blackone86 on 2011-10-12
The only thing that seems to be working with my midi keyboard is hydrogen and it isnt fully functional

---

### Post by sgx on 2011-10-12
edit: just in case, check the midi tip on page 5 of the akai manual

Hi, try installing phasex and yoshimi, which can be had here

[https://launchpad.net/~autostatic/+archive/ppa/+packages](https://launchpad.net/~autostatic/+archive/ppa/+packages)

install with    sudo dpkg -i yoshimixxxx.deb

in case their midi setup is better than zynaddsubfx. Phasex auto-connects in the audio tab, and needs manual connection to your midi keyboard in the alsa tab.

for yoshimi, run  a2jmidid -j default, after qjackctl starts, then start yoshimi, I connect both midi-through ports in the alsa tab,
connect the a2jmidi port to the midi keyboard in the midi tab,
and yoshimi to system, in the audio tab
---------------------------------------------------------------------

In the hydrogen menu
tools-->preferences-->audio system-->restart output

use this to restart the jackd connection if needed. When Hydrogen is connected to your akai keyboard in the alsa tab, and connected to
'system' in the audio tab, you should be able to load a kit, and play the beats on the keyboard. (kit mapping varies, lower octave notes usually.
Load a demo song from the menu, to play, which includes a kit. 

The akai usb midi connection may fail if you also have the 5 pin cables connected. I would think the 5 pins would be better, but not
when usb is also connected.

If you have a fancy new video chipset with audio as a subset, or hdmi, that may be a problem. In general, with odd problems, it's lucky to disable everything network/comms/bluetooth/power-management related in the bios (take notes what you turn off) and boot with no other usb devices, especially no usb hubs. Even a humble usb keyboard has been a culprit in rare setups. The power supply should be used, usb power is not trustworthy with complex devices.

You should google you usb and motherboard chipsets against linux,
some are not cooperating. I would also try other distros, as different
kernels cam make a difference. AVLinux, RemixOS, and Puppy Studio
are a good variety. Post computer details here for others to consider.
Cheers

---

### Post by jejeman on 2011-10-12
> **blackone86 said:**
> Thanks for that link. I understand now how to connect them the problem is i dont have those options. 

[ATTACH]204065[/ATTACH]

I have nothing under midi or audio only under alsa?On the screenshot one can see that jack is stopped. You need to have jack server running in order to have ports in audio and midi tab.

---

### Post by blackone86 on 2011-10-12
with jack running i get options under midi. I have been able to connect and get response of midi keyboard in zynaddsubfx. When i press down the keys on my midi keyboard it shows in the sound bar at the bottom of zynaddsubfx that the keys beeing pressed are recongnized.. still no sound. ill figure it out one of these days lol

---

### Post by jejeman on 2011-10-12
Than you just need to connect ZynAddSubFx's audio ports to soundcards' playback ports in audio tab.
Also ZynAddSubFx can work eather with jack or just alsa.
If you first start jack, than it uses jack, and you have to connect it like in the picture. If you do not start jack, than you don't have to connect it in audio tab, just in alsa tab for midi.

---

### Post by sgx on 2011-10-12
some zyn versions don't properly place themselves in the audio tab, so try phasex and hydrogen, which automatically connect in the audio tab,
and just need manual connection in the alsa tab.
Cheers

---

