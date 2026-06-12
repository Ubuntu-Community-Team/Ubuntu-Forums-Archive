---
title: "getting jack started"
date: 2010-05-09
forum: Ubuntu Studio
---

### Post by artyone on 2010-05-09
Howdy Folks, absolute beginner here and I've got 10.04 installed.

I've got sounds on startup, the CD's play in movie player, as well as DVD's, and can play sounds on the net, .flv's on youtube. These play over the onboard speaker

My problem occurs with jack which will not start. Everything is set to default in it and the error message always comes up cannot connect to server.

In terminal asking for devices I get this as the soundcard
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device 0001
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 4a000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

This is a screen shot of Alsamixer, sorry about the screenshot window being in front (might be a bug!), but I'm wondering about the MUX bar... what is that? do I need it? And what about the line input which hasn't even a bar. I've tried all kinds of stuff but can't find a strategy to work through to get jack going. Do you want a screen shot of Jack and the message and the options in setup for devices?

[IMG]http://i4.photobucket.com/albums/y115/quickkiwi/Screenshot.jpg[/IMG]

---

### Post by artyone on 2010-05-09
So I'm reading the post below and following up.

In /etc/security/limits.conf

                             @audio - rtprio 99
@audio - memlock 509380

And after typing cat ~/.jackdrc  
/usr/bin/jackdrc -p128 -t5000 -dalsa -dhw:0 -r44100 -p64 -n2 -5

And now, for some weird reason I can't understand, I reloaded Jack and reset all the defaults and quit then started it again and it stated up fine then I loaded Hydrogen and now that works too!

I just hope it all stays this way

---

### Post by hxcobd on 2010-05-11
Reasons people typically can't start JACK:

1.) You have another program using audio already open. This includes audio/video players, web browsers, etc. Close EVERYTHING USING AUDIO BEFORE STARTING JACK.

2.) Your settings are incorrect. Tweaking the buffer, samplerate, and periods normally fixes this.

---

