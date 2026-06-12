---
title: "Jack won't start"
date: 2010-03-25
forum: Ubuntu Studio
---

### Post by hudsonryde on 2010-03-25
well, the title basically says it all... when i open Jack and try and start the server I get the Jack won't start error(that's a paraphrase, i don't remember the exact wording)

anyway, I'm using an m-audio fast track pro, and as far as I can tell, it's at hw:2, but I could be mistaken. I am by no means a Linux pro, but I have been using it for about 6 months so I understand the basics.

any info you need from the terminal I'd be ready to post, but I don't really no where to start, any guidance would be beautiful.

I have attempted various other fixes I've read in other forums, adding myself to the audio group, editing limits.conf etc. And I'm running an rt kernel and karmic

---

### Post by mango42 on 2010-03-25
No doubt someone competent will be along shortly but for now it would be useful to post the Jack error messages in full.

---

### Post by hudsonryde on 2010-03-25
it's just a window that comes up and says "could not start Jack. Sorry."

---

### Post by AutoStatic on 2010-03-25
Hello hudsonryde, please provide the output of the terminal command **aplay -l** and if it outputs anything **cat ~/.jackdrc**
And when you start JACK with QjackCtl, could you try clicking on the Messages button and copy/paste what JACK is spitting out?

---

### Post by hudsonryde on 2010-03-25
thanks for the quick reply AutoStatic, here's the info:

output of aplay -l:

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Generic [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Generic [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

output of cat ~/.jackdrc:

/usr/bin/jackd -p 128 -T -d oss -n 2 -r 48000 -p 512 

and Jack messages: 

15:27:24.586 Patchbay deactivated.
15:27:24.613 Statistics reset.
15:27:24.978 Startup script...
15:27:24.979 artsshell -q terminate
15:27:24.982 ALSA connection graph change.
sh: artsshell: not found
15:27:25.575 Startup script terminated with exit status=32512.
15:27:25.575 JACK is starting...
15:27:25.575 jackd-realtime -R -p128 -t5000 -dalsa -r48000 -p64 -n2 -D -Chw:2 -Phw:2 -S -i2
15:27:25.581 Could not start JACK. Sorry.
15:27:25.777 ALSA connection change.
15:27:26.844 JACK was stopped successfully.
15:27:26.845 Post-shutdown script...
15:27:26.845 killall jackd
jackd: no process found
15:27:27.267 Post-shutdown script terminated with exit status=256.

---

### Post by AutoStatic on 2010-03-25
You're using the wrong server path, it should be */usr/bin/jackd*, not *jackd-realtime*. And I would also not set a specific number of input and output channels, just leave them default. And in the Interfaces field you could manually enter ```
hw:Pro
```This way JACK will always use the Fast Track Pro, no matter which hardware index number it has.

---

### Post by hudsonryde on 2010-03-25
awesome! it worked thanks! but there's one thing... I can only get recorded sound output through outputs 3/4 not 1/2 and i can only get monitor sound through outputs 1/2 not 3/4... so i can either hear the music and not hear myself, or hear myself and not hear the music. haha this could pose a problem...

---

### Post by hudsonryde on 2010-03-25
okay nevermind, I spoke too soon, got it solved, thank you sir!

---

### Post by Shtrk on 2010-11-12
Can you please help me too?
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SIS966 [HDA SIS966], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Jack error:
20:16:05.913 Startup script...
20:16:05.914 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
20:16:06.317 Startup script terminated with exit status=32512.
20:16:06.318 JACK is starting...
20:16:06.319 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n3
20:16:06.348 Could not start JACK. Sorry.
20:16:09.485 JACK was stopped with exit status=255.
20:16:09.486 Post-shutdown script...
20:16:09.487 killall jackd
jackd: no process found
20:16:09.900 Post-shutdown script terminated with exit status=256.

Thx

---

