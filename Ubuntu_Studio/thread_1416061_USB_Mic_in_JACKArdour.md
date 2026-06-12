---
title: "USB Mic in JACK/Ardour?"
date: 2010-02-25
forum: Ubuntu Studio
---

### Post by Tahakki on 2010-02-25
Hey guys,

Does anyone know how to get Ardour or Jack to recognise a USB Logitech microphone?

Cheers.

---

### Post by markbuntu on 2010-02-25
Does the mic work in other apps?
Is it listed when you run lsusb?
If so then all you need to do is change the input setting in jack control/setup/input device and restart jack.

---

### Post by Tahakki on 2010-02-25
Did that, but on connecting system -> Ardour the only input working is the other microphone, the webcam.

---

### Post by fauzie on 2010-02-26
You may want to try this

[http://ubuntuforums.org/showthread.php?t=1348604](http://ubuntuforums.org/showthread.php?t=1348604)

Once you're done, you should be able to choose your soundcard. It worked for me.

---

### Post by Tahakki on 2010-02-26
I only have one sound card...unless you're suggesting the mic has one built-in? Will I still be able to use other inputs, such as USB MIDI?

---

### Post by markbuntu on 2010-02-26
The usb mic can be considered as a sound card/device and so can a webcam with a mic. When you go to jack/setup/input device > what is listed there?

---

### Post by Tahakki on 2010-02-26
Here's a screenshot:

[IMG]http://www.majhost.com/gallery/kixo/Ubuntu/screenshot-setup_-_jack_audio_connection_kit.png[/IMG]

---

### Post by Tahakki on 2010-02-28
Bump.

---

### Post by AutoStatic on 2010-02-28
Select the Logitech USB Mic as the Input device and you should be good to go.

---

### Post by Tahakki on 2010-02-28
Tried that, but the only input Ardour accepts is still the webcam mic. Unplugging this achieves nothing.

---

### Post by AutoStatic on 2010-02-28
What's the output of **aplay -l** ?

---

### Post by Tahakki on 2010-02-28
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by AutoStatic on 2010-02-28
Where's the USB mic? Is it plugged in? If not, could you plug it in and do an **aplay -l** again?

---

### Post by Tahakki on 2010-02-28
It's plugged in. GNOME Sound recognises it.

---

### Post by markbuntu on 2010-02-28
Did you restart jack? Ardour should complain when your stop jack to make the changes. You then need to tell ardour to reconnect to jack to see the new connection. If that does not work then try closing ardour, making the change in jack control and starting jack and then opening ardour in a new session.

---

### Post by Tahakki on 2010-02-28
To get those results I opened Jack Control, made the changes, quit Jack then started Ardour. No dice.

---

### Post by AutoStatic on 2010-03-01
> **Tahakki said:**
> It's plugged in. GNOME Sound recognises it.Oops, my bad. The command should be **arecord -l** :oops:

---

### Post by Tahakki on 2010-03-01
```
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Microphone [Logitech USB Microphone], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

As you can see, the USB Mic shows up. :)

---

### Post by AutoStatic on 2010-03-01
And it's called unequivocally 'Microphone' :)
If you enter *hw:Microphone* in the Input Device field you're 100% sure that JACK always uses your USB microphone, no matter in which USB port you plug it in.
Unless your webcam mic is also a Logitech USB device. What does **lsusb** say with the USB microphone plugged in?

---

### Post by Tahakki on 2010-03-01
Bus 006 Device 002: ID 046d:0a03 Logitech, Inc. Logitech USB Microphone

---

### Post by AutoStatic on 2010-03-02
Is that all **lsusb** returns? I'd like to know more about the webcam, why it gets in the way.

---

### Post by Tahakki on 2010-03-02
No, sorry. lsusb returns:

Bus 004 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 004 Device 002: ID 04ca:0027 Lite-On Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1871:01f0 Aveo Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 046d:0a03 Logitech, Inc. Logitech USB Microphone
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 03f0:0304 Hewlett-Packard DeskJet 810c/812c
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The camera seems to be used in Jack. It's connected by USB, but only for video - for sound it has a standard mic connector.

---

### Post by AutoStatic on 2010-03-03
> **Tahakki said:**
> The camera seems to be used in Jack. It's connected by USB, but only for video - for sound it has a standard mic connector.Thanks! I now also reread some of your posts and I misunderstood you, especially now you say that the webcam mic has to be plugged in before you can use it. If you select the Logitech USB Mic as the Interface (enter 'hw:Microphone' instead of '(default)') and set it to Capture only, does it work then?

---

### Post by Tahakki on 2010-03-03
If I set it to capture only, I cannot choose an input device.

Setting either 'USB Mic' or 'Logitech USB Mic' still recieves input only from the microphone in the webcam.

---

### Post by AutoStatic on 2010-03-03
And if you try according to the screenshot I've added? You have to enter 'hw:Microphone' manually, you can't select it.

---

### Post by Tahakki on 2010-03-03
No. It still accepts input only from the webcam.

---

### Post by AutoStatic on 2010-03-03
But does JACK start with the settings I've indicated?

---

### Post by Tahakki on 2010-03-03
No. Jack normally refuses to start for me - it only starts when something uses it, like Ardour. I had previously assumed this was normal.

---

### Post by AutoStatic on 2010-03-03
What messages do you get when you start JACK? Did you untick the Realtime option?

---

### Post by Tahakki on 2010-03-03
I unticked realtime. Still gives:

```
21:48:43.576 Patchbay deactivated.
21:48:43.577 Statistics reset.
21:48:43.594 ALSA connection graph change.
21:48:43.794 ALSA connection change.
21:48:55.944 Startup script...
21:48:55.945 artsshell -q terminate
sh: artsshell: not found
21:48:56.347 Startup script terminated with exit status=32512.
21:48:56.347 JACK is starting...
21:48:56.347 /usr/bin/jackd -dalsa -dhw:Microphone -r44100 -p1024 -n3 -C
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
21:48:56.362 JACK was started with PID=10028.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... -|hw:Microphone|1024|3|44100|0|0|nomon|swmeter|-|32bit
control open "hw:Microphone" (No such device)
ALSA lib pcm_hw.c:1435:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
cannot load driver module alsa
21:48:56.372 JACK was stopped successfully.
21:48:56.373 Post-shutdown script...
21:48:56.373 killall jackd
jackd: no process found
21:48:56.782 Post-shutdown script terminated with exit status=256.
21:48:58.467 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by AutoStatic on 2010-03-03
```
control open "hw:Microphone" (No such device)
ALSA lib pcm_hw.c:1435:(_snd_pcm_hw_open) Invalid value for card
```

And what if you try 'hw:1' ?

---

### Post by Tahakki on 2010-03-04
```
09:31:51.724 Patchbay deactivated.
09:31:51.727 Statistics reset.
09:31:51.819 ALSA connection graph change.
09:31:52.017 ALSA connection change.
09:32:00.635 Startup script...
09:32:00.636 artsshell -q terminate
sh: artsshell: not found
09:32:01.038 Startup script terminated with exit status=32512.
09:32:01.038 JACK is starting...
09:32:01.038 /usr/bin/jackd -dalsa -dhw:1 -r44100 -p1024 -n3 -C
09:32:01.041 JACK was started with PID=2540.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... -|hw:1|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
control open "hw:1" (No such file or directory)
ALSA lib pcm_hw.c:1435:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
cannot load driver module alsa
09:32:01.222 JACK was stopped successfully.
09:32:01.223 Post-shutdown script...
09:32:01.223 killall jackd
jackd: no process found
09:32:01.649 Post-shutdown script terminated with exit status=256.
09:32:03.091 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
09:33:20.809 Startup script...
09:33:20.810 artsshell -q terminate
sh: artsshell: not found
09:33:21.211 Startup script terminated with exit status=32512.
09:33:21.211 JACK is starting...
09:33:21.211 /usr/bin/jackd -dalsa -dhw:1 -r44100 -p1024 -n3 -C
09:33:21.213 JACK was started with PID=2639.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 44100
creating alsa driver ... -|hw:1|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
impossible sample width (1) discovered!
09:33:21.234 JACK was stopped with exit status=1.
09:33:21.234 Post-shutdown script...
09:33:21.235 killall jackd
jackd: no process found
09:33:21.642 Post-shutdown script terminated with exit status=256.
09:33:23.417 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

---

### Post by AutoStatic on 2010-03-04
```
impossible sample width (1) discovered!
```

Maybe someone else can tell more about this, I can only guess it has got something to do with the USB mic being capture only and jackd maybe has a problem with it. If that is the case, you've ran into a bug: [https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/494223](https://bugs.launchpad.net/ubuntu/+source/jack-audio-connection-kit/+bug/494223)

What you could try is setting different cards for Playback (Output) and Capture (Input), so your onboard card for Playback and the USB mic for Capture.

---

### Post by RaumTrug on 2010-03-04
yep, I ran into that one some time ago with my usb-mic, and filed it slopily as a bug some time later (yep, that traumflug stuttering on launchpad in the link above is me) just to find someone else had already made up a cleaner fix for jack2 ;)

it's really just some refactoring bug, that prevents jack loading cap.only devices, with the patch it should work, at least it does with my mic.

have you already tried using your mic as capture device, and your soundcard as playback like autostatic suggested above? also try to alternate one of them as main "interface" above the capture/playback? i.e. hw:0 or hw:1 as "interface", and hw:1 for capture and hw:0 for playback...

for me that kind of "worked" in the beginning, _but_ only at very high latency! no use for other things than simple recording without hearing oneself while doing so; anything below 40ms latency would give me horrible numbers of x-runs and freezes my system in rt-mode.

so it depends on what you're trying to actually do with that mic. do you wish to monitor what you record in "realtime"?

---

