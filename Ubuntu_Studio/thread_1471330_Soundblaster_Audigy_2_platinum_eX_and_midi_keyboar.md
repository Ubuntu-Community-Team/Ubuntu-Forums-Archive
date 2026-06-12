---
title: "Soundblaster Audigy 2 platinum eX and midi keyboards"
date: 2010-05-03
forum: Ubuntu Studio
---

### Post by Hardtoid on 2010-05-03
Hello everyone. I am a fresh Ubuntu Studio user. I find it kind of tricky to setup my sound card (the Audigy2), but it seems to work fine (playback, midi files etc). Problem is that I can't get signals from my Midi Keyboard. It is connected to the external module of the Audigy2 cause I use midi cable connection. I have read that there might be an isuue with these external modules. Is this true? Should I give up trying to get this issue fixed for my PC? Or am I just doing something wrong? Thank you for your time :)

---

### Post by sgx on 2010-05-03
> **Hardtoid said:**
> Hello everyone. I am a fresh Ubuntu Studio user. I find it kind of tricky to setup my sound card (the Audigy2), but it seems to work fine (playback, midi files etc). Problem is that I can't get signals from my Midi Keyboard. It is connected to the external module of the Audigy2 cause I use midi cable connection. I have read that there might be an isuue with these external modules. Is this true? Should I give up trying to get this issue fixed for my PC? Or am I just doing something wrong? Thank you for your time :)
At worst, there are several $30 usb midi interfaces, and a closeout of
E-mu Proteus X2 softsynth is often $50 or less, and includes a great 2X2 usb midi interface (it doubles as a copy protection dongle needed to use the software)
I recall reading of the issues you mention, a focused google search will likely get you some discussions.

You can install qjackctl

sudo apt-get install qjackctl

or use the synaptic package manager gui

Press the qjackctl Start button, and click the Setup button on the right

On the panel that appears, on the right side you'll see

Output Device >
Input Device  >

Click the  >  widget, and a list of the names, and hardware identity numbers will appear. One of them will be your soundcard. emu-10k or similar will be its name. Choosing the name, rather than HW:0 or HW:1
will prevent qjackctl from possibly picking the wrong number.

to find the one you need in qjackctl, install and start zynaddsubfx
as you did with qjackctl,
and press the Connect button on the main qjackctl screen. A three tabbed panel opens, zynaddsubfx appears in the right and left tabs. The alsa tab
on the rightmost panel has your selected midi ports. Connect to zyn by selecting it, and the midi port on the opposite side, and pressing the connect button on this same panel (not the one on the main qjackctl screen) so you can send midi from your keyboard

The Audio tab has your soundcard inputs and outputs, called 'System'. Connect zyn to the system audio port on the opposite side, so you can hear this instrument while you play. 

You must stop qjackctl each time you change settings, and press the Start button again, so choose the available possibilities from the   > widget until you find the correct one. Use The HW:0 etc if thats all thats available.

This might get things rolling :D

---

### Post by sgx on 2010-05-03
There are some usb midi interfaces here:

[http://www.linuxstudiopro.com/](http://www.linuxstudiopro.com/)

Cheers

---

### Post by Hardtoid on 2010-05-04
That's a nice tutorial! Thank you very much. You really made jackcntrl look easier. For some funny reason Jack control won't start today (Could not connect to JACK server as client.) and I am too tired to fix it right now (just got home). So I 'm just going to get some rest and then hopefully get all issues fixed. Thank you again for your time!

---

### Post by sgx on 2010-05-04
> **Hardtoid said:**
> That's a nice tutorial! Thank you very much. You really made jackcntrl look easier. For some funny reason Jack control won't start today (Could not connect to JACK server as client.) and I am too tired to fix it right now (just got home). So I 'm just going to get some rest and then hopefully get all issues fixed. Thank you again for your time!

Hi, if Realtime is ticked, and you don't have a realtime kernel,
untick it for now. If you have an RT kernel, you can add yourself
to the audio group and edit 

/etc/security/limits.conf

Add this to the end of the file, and edit the spacing as per the exixting columns in the file,
the forum compacts the spaces

@audio          -       rtprio           99
@audio          -       nice             -19
@audio		soft	memlock		unlimited
@audio		hard	memlock		unlimited

This should  give the needed RT permissions to the non-root user.

A web browser with a flash/shock plugin might steal the audio device,
so try a reboot, with qjackctl the only thing you start.

You can manually start jackd with a simple, or more complex command

jackd -d alsa -r 44100   (is the simple form)

and then start qjackctl.

Cheers

---

