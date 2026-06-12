---
title: "jackd 4 channel with alsa"
date: 2008-08-03
forum: Ubuntu Studio
---

### Post by bernt_ on 2008-08-03
Hello,

Is there a solution for this:

Ubuntu 8.04
jackd 0.109.2
Soundcard C-Media CMI8738-MC6 (model 55)

By default there is only playback_1 and playback_2 in the connection window.
But the soundcard has 6 output channels.
Setting the output channels to 4 with qjackctrl gives:

```

23:39:48.522 /usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw:1,0 -Phw:1,0 -S -o4
23:39:48.524 JACK was started with PID=10999.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1,0|hw:1,0|1024|2|44100|0|4|nomon|swmeter|-|16bit
control device hw:1
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: cannot set channel count to 4 for playback
ALSA: cannot configure playback channel
cannot load driver module alsa
no message buffer overruns
23:39:48.545 JACK was stopped successfully.
23:39:48.545 Post-shutdown script...
23:39:48.546 killall jackd
jackd: no process killed
23:39:48.956 Post-shutdown script terminated with exit status=256.
23:39:50.643 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

What shell I put into .asoundrc for telling alsa to has 4 playback channels?

Bernt

---

### Post by monstara on 2011-01-14
I am trying to do the same.
I have already created a .asoundrc file with a definition for a four-channel device. Instructions for this here: [http://alsa.opensrc.org/SurroundSound](http://alsa.opensrc.org/SurroundSound)
However, it still does not work. I am trying to start jack with this definition, but get the same error:
ALSA: cannot set channel count to 4 for playback

The card is cheapo USB (C-Media Electronics, Inc. CM106 Like Sound Device), but I thought this would work anyway...

Maverick 10.10
Jackdmp 1.9.6

---

### Post by cchhrriiss121212 on 2011-01-14
Try setting channels to default, jack will pick up how many inputs or outputs you have automatically. If the default does not match the number of channels, then the problem lies with ALSA and not jack. 

Try opening alsamixer from a terminal, you should be able to see all the available channels. If ALSA does not see them, then jack will not see them.

---

### Post by Pablo_F on 2011-01-14
Hi, 

It is possible that the default device only has two playback ports but there could be a device with multichannel playback. If so, I don't think you need a .asoundrc file. What does "aplay -l" say?

You can select different devices for capture and playback. 

Cheers, Pablo

---

### Post by monstara on 2011-01-14
Hmm strange things are happening.

ALSA sees front, rear, center, woofer and side speakers.

However, now I am not able to start Jack with this card at all (I think it worked in the past), with this error:
```

ALSA: could not start playback (Broken pipe)

```If I start Jack with the built-in Intel card, and then add the external card with jack_load, it is added successfully, but no sound comes out of this card.

In .asoundrc I have created a definition "jack40" as instructed on the site I posted earlier. If I start Jack with it, sound comes out of the built-in card, even though I have specified card 1 in the definition (perhaps it falls back because of a failure?). The strange thing is, according to Jack output the proper card was picked up:
```

Using ALSA driver USB-Audio running on card 1 - USB Sound Device         at usb-0000:00:1d.0-1.1, full speed

```No errors in this case...

I'm puzzled and annoyed, cause I need this for a school project.
I'm going to try creating an ALSA multi plugin, if I can use both cards, then it still suits me.

---

### Post by Pablo_F on 2011-01-14
lspci |grep -i usb
lsusb

?

---

### Post by monstara on 2011-01-14
Yes, sorry. Find them attached
The only external devices are the audio card and the mouse. The wacom device is a touchscreen.

Update:
if I do 
speaker-test -c4 -D hw:1 -t wav
then I get output from 4 channels, which is filling me with hope :)

---

### Post by Pablo_F on 2011-01-14
Hi, 

Read this:

[http://www.pubbs.net/201009/linuxaudio/8244-lau-usb-audio-interface-and-a-buggy-usb-controller.html](http://www.pubbs.net/201009/linuxaudio/8244-lau-usb-audio-interface-and-a-buggy-usb-controller.html)

It seems impossible to have duplex mode with that USB controller. You will have to set jack to playback only mode.

I encountered the same issue in my sister's notebook. Many people is affected by this. 

EDIT: 
With jack2 (jackdmp) I could use capture only mode. With jack1, only playback only mode. 

Cheers! Pablo

---

### Post by monstara on 2011-01-14
Wow, amazing, it worked! Thank you.:popcorn:
I am even able to start in playback mode with jack2.
Nasty problem though.

---

### Post by monstara on 2011-01-14
Wow, amazing, it worked! Thank you.:popcorn:
I am even able to start in playback mode with jack2.
Nasty problem though.

---

