---
title: "Would you believe? Another Jack issue..."
date: 2009-12-02
forum: Ubuntu Studio
---

### Post by lavadisco on 2009-12-02
Last month, after finally getting Jack working perfectly in Jaunty thanks to the fine coaching of AutoStatic and trulan, I turned right around and wiped my machine and installed Karmic 64 bit. Now I have a problem with Jack. I have the realtime kernel installed, I added all the stuff to the end of my limits.conf, and I am a member of the audio group. My Edirol UA-25 audio interface is working great with my machine otherwise. Don't really know what's going on, but any help is appreciated:


```
21:17:50.316 Patchbay deactivated.
21:17:50.320 Statistics reset.
21:17:50.338 Startup script...
21:17:50.338 artsshell -q terminate
21:17:50.341 ALSA connection graph change.
sh: artsshell: not found
21:17:50.740 Startup script terminated with exit status=32512.
21:17:50.740 JACK is starting...
21:17:50.740 /usr/bin/jackd -R -m -dalsa -dhw:2 -r44100 -p128 -n2
21:17:50.743 JACK was started with PID=3067.
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
creating alsa driver ... hw:2|hw:2|128|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:2
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
21:17:50.777 JACK was stopped successfully.
21:17:50.777 Post-shutdown script...
21:17:50.777 killall jackd
21:17:50.942 ALSA connection change.
jackd: no process found
21:17:51.186 Post-shutdown script terminated with exit status=256.
21:17:52.952 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

Do I need to install something called alsa_pcm?

---

### Post by sgx on 2009-12-02
I think something is using sound before you start jackd. 'Hardware 2'
is too far down the list to be lucky. Unplug the edirol, then turn off
sound and networking and acpi etc in the bios (take notes!)reboot,
and run

sudo alsaconf  or whatever your admin audio config program is. This SHOULD
fail, since no sounchips/cards are present, but copy the output for reference. Also, save the output of

lsmod

Now plug in the edirol, and run the sound config program again,
and save the output if possible. Run lsmod again, and look for differences. Also, compare the sound devices in qjackctl before and after.
Cheers

---

### Post by VertexPusher on 2009-12-02
> **lavadisco said:**
> control device hw:2
Soundcard numbers sometimes change, so hw:2 will not always be what you expect it to be.

Enter this:
```
aplay -l
```

You'll see something similar to this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Find out the name of the card that you want Jack to use. In the example above ...
```
card 0: Intel
```
... the name of card #0 is "Intel".

Once you know the name of the card you want to use, enter it in Jack's configuration like this:
```
hw:Intel
```

Now any changes in soundcard numbers won't affect Jack any more.

---

### Post by lavadisco on 2009-12-03
Weird. All I had to do was restart my machine without the UA-25 connected, plug it in after the restart, and now it works. However, Jack keeps on giving me this error:

> subgraph starting at qjackctl timed out (subgraph_wait_fd=16, status = 0, state = Running, pollret = 0 revents = 0x0)

I even got this up at a high latency of 46 ms. Anybody know what this error is? So far Jack and Reaper aren't running nearly as well on my new faster machine as they did on my old one.

---

### Post by VertexPusher on 2009-12-03
> **lavadisco said:**
> Weird. All I had to do was restart my machine without the UA-25 connected, plug it in after the restart, and now it works.
Not weird at all. It works now, and next time it will fail again. That's what I was trying to explain.

Cards are enumerated in the order they are detected. If all cards are present at boot time, the numbering is pretty much random. That's not a problem because you can specify cards by name instead of number. I showed you how to do that in my previous post. If you enter the card name into Jack's configuration, you won't have to unplug the UA-25 to make it work.

However, if you keep using card numbers instead of names, prepare to run into this problem again and again.

---

### Post by lavadisco on 2009-12-03
Thanks, I did change it to hw:UA25 just in case. 

Any idea why I am getting the subgraph error?

---

### Post by AutoStatic on 2009-12-03
What are your current JACK settings? And what sample rate does the UA-25 run on (switch on the back)? And try a Frames/Period of 3.

---

