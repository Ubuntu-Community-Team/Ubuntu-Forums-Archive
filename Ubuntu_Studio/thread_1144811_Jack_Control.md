---
title: "Jack Control"
date: 2009-05-01
forum: Ubuntu Studio
---

### Post by shanehaua on 2009-05-01
Hi, I am trying to configure Jack Control. I am a biginner so it doesn't make sense to me. Heeeeeeeeelp!

---

### Post by af20001 on 2009-05-01
It might take some trial an error to get the settings right. Try following the setup shown in the link below as a starting point:

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/")

Make sure you have the correct soundcard selected in the 'Interface' drop down.

---

### Post by kayosiii on 2009-05-01
It would be much easier to help you if you gave some specific information about what you are trying to do. :)

With what I have to go on I can give you a few basic pointers. The setup button is on the right hand side of the main interface in about the middle that is where you put most of your settings. Out of the settings there 
Realtime is nice to have set - but that requires extra setup so try and get things working without that at the moment.

Near the top on the first tab there should be a section called Server. It has an option called Driver - This will be set to alsa you will want to change this to freebob or firewire if you have a firewire soundcard. Otherwise it is best left as is.

The main performance settings are Frames/Period (this determines the size of the buffers - the smaller this size the less latency but you are more likely to get glitches(xruns)) Periods/Buffer -- Change this setting if somebody recommends it for your hardware.

Finally the Sample Rate determines what rate your jack audio is working at. 

You can pretty much ignore most of the other settings for the time being. And even the ones I mentioned above should have fairly sensible defaults.
There are also some options you may wish to set in the misc tab

Once you are set you can start jackd by hitting the Start button.

I also can recommend installing and using patchage to connect apps together as it is easier to use than jack control for this purpose.

---

### Post by shanehaua on 2009-05-01
Hi again, I am wanting to do music production. I am used to using a hard disc recorder (Korg 888D) but I want to move to computer based recording. I have Jaunty Ubuntu Studio. I tried setting Jack to realtime but then it would not connect to the server.

---

### Post by kayosiii on 2009-05-01
Can you get Jack running without realtime privileges?
What sort of soundcard are you using?

To use realtime privileges you need to let the security system know that you want our audio programs to access to resources that they otherwise wouldn't have access to. I was under the impression that this was set up by default under the studio version of Ubuntu. :confused:
You can use the ubuntustudio-controls application to tweak some of the stuff. This may help. 

Also the Messages window (press the messages button in the main interface) can be helpful to figure out what is going on.
You could try pasting the output of that here

---

### Post by Stochastic on 2009-05-01
I'd like to be able to refer you to [https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration) but I think that page is one of the community documentation pages that has been sorely neglected.  It does have a little bit of good info on it though.

---

### Post by shanehaua on 2009-05-01
I got it running but I think it is have an x run nightmare. Here is the output from the message window.

09:42:11.269 Patchbay deactivated.
09:42:11.426 Statistics reset.
09:42:11.508 Startup script...
09:42:11.509 artsshell -q terminate
09:42:11.523 ALSA connection graph change.
sh: artsshell: not found
09:42:11.911 Startup script terminated with exit status=32512.
09:42:11.911 JACK is starting...
09:42:11.912 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p32 -n2 -m
09:42:11.914 JACK was started with PID=19933.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|32|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
09:42:11.945 JACK was stopped successfully.
09:42:11.945 Post-shutdown script...
09:42:11.946 killall jackd
09:42:12.114 ALSA connection change.
jackd: no process killed
09:42:12.356 Post-shutdown script terminated with exit status=256.
09:42:14.129 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
09:43:05.883 Startup script...
09:43:05.885 artsshell -q terminate
sh: artsshell: not found
09:43:06.288 Startup script terminated with exit status=32512.
09:43:06.288 JACK is starting...
09:43:06.289 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p32 -n2 -m
09:43:06.291 JACK was started with PID=19975.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|32|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 32 frames (0.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
09:43:08.463 Server configuration saved to "/home/shane/.jackdrc".
09:43:08.467 Statistics reset.
09:43:08.473 Client activated.
09:43:08.481 JACK connection change.
09:43:08.493 JACK connection graph change.
09:43:08.495 XRUN callback (1).
09:43:10.492 XRUN callback (82 skipped).
09:43:12.498 XRUN callback (83 skipped).
09:43:14.518 XRUN callback (82 skipped).
09:43:16.524 XRUN callback (83 skipped).
09:43:18.531 XRUN callback (82 skipped).

---

### Post by shanehaua on 2009-05-01
mmm how do I find out which sound card I have?
In the Studio Controls window it has these settings ticked.

Enable Nice -10%

None of the other controls are ticked.

Thanks.

---

### Post by shanehaua on 2009-05-01
Sorry forgot to mention I got Jack running without realtime ticked.

---

### Post by shanehaua on 2009-05-01
The sound card might be an HDA Intel STAC92xxAnalog hope thats right.

---

### Post by thorgal on 2009-05-02
you have set an ultra low buffer size (-p32) for your onboard card. It will not cope with it easily without a realtime kernel.

Try this jack setting:
- frames per period = 1024
- number of periods per buffer = 3

see if you get this torrent of xruns.

For your information, under the realtime kernel 2.6.29.2-rt10 (not in ubuntu, mind you, but debian sid and home-compiled), I run jackd (in fact, jack2, the next generation jack) on my old laptop with this setting:
- frames per period = 64
- number of periods per buffer = 3
- RT mode ticked

I have no xruns and can run ardour with a few tracks on this old 1.6GHz pentium M machine :D

---

### Post by Stochastic on 2009-05-02
Good to see it's up and running.  
XRuns can be reduced by running in realtime (linux-rt kernel required).  
XRuns can also be reduced by increasing the buffer size.  That can be done by increasing the Frames/period setting, increasing the samplerate (your card probably won't allow this), or increasing the periods/buffer number.

Edit: darn, thorgal beat me to the response.

---

