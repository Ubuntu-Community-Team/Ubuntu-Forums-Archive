---
title: "Can't get Alsa working with Jack - ubuntu studios, edirol ua25"
date: 2009-06-11
forum: Ubuntu Studio
---

### Post by Dhjengis on 2009-06-11
Hi

I am trying to get jack running, it worked two days ago, but now it don't seem to do that anymore.
When i go to the setup - interface in Jack i can't find the right one, there use to be options hw:1 - UA 25 and hw:1.0 Usb audio device, it worked fine whith hw:1.0, but somehow the option disapeared. I think it has something to do with Alsa not detecting it right, but apart from that, i havent got a clue, here is the mesage window:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]14:34:46.432 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:34:46.791 Statistics reset.[/COLOR]
 [COLOR=#66cc99]14:34:47.291 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]14:34:51.412 ALSA connection change.[/COLOR]
 [COLOR=#999999]14:34:55.112 Startup script...[/COLOR]
 [COLOR=#990099]14:34:55.115 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]14:34:55.543 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]14:34:55.545 JACK is starting...[/COLOR]
 [COLOR=#990099]14:34:55.547 /usr/bin/jackd -R -dalsa -dhw:1 -r96000 -p256 -n10[/COLOR]
 [COLOR=#999999]14:34:55.554 JACK was started with PID=7105.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot lock down memory for jackd (Cannot allocate memory)
 loading driver ..
 apparent rate = 96000
 creating alsa driver ... hw:1|hw:1|256|10|96000|0|0|nomon|swmeter|-|32bit
 control device hw:1
 ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 configuring for 96000Hz, period = 256 frames (2.7 ms), buffer = 10 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: use 10 periods for capture
 impossible sample width (1) discovered!
 [COLOR=#999999]14:34:56.092 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#999999]14:34:56.094 Post-shutdown script...[/COLOR]
 [COLOR=#990099]14:34:56.095 killall jackd[/COLOR]
 [COLOR=#ff0000]14:34:56.125 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 jackd: no process killed
 [COLOR=#999999]14:34:58.472 Post-shutdown script terminated with exit status=256.[/COLOR]

Help is very welcome!
/Torben

---

### Post by benbriedis on 2009-10-11
Hi Torben -

Did you find a solution to this?  I have a UA-25 too and have the same problem.  The problem only occurs at 96000kHz, not at 44100kHz.

Thanks,
Ben

---

### Post by raboofje on 2009-10-11
I have a UA25-EX, which is almost identical.

> **Dhjengis said:**
> When i go to the setup - interface in Jack i can't find the right one, there use to be options hw:1 - UA 25 and hw:1.0 Usb audio device, it worked fine whith hw:1.0, but somehow the option disapeared.

Strange, I do see it.

> cannot lock down memory for jackd (Cannot allocate memory)

I think you can fix this warning by increasing the 'memlock' value for the audio group in /etc/security/limits.conf, but this is probably not your problem.

> ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode

What does 'aplay -l' show? Is the device in 'Advanced driver' mode? 'sudo fuser /dev/dsp1'? 'sudo fuser /dev/snd/*'? Which kernel are you running?

---

### Post by AutoStatic on 2009-10-20
> configuring for 96000Hz, period = 256 frames (2.7 ms), buffer = 10 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 10 periods for capture
impossible sample width (1) discovered!96000Khz and 10 periods as buffersize? That's a really weird combination an jackd obviously chokes on it. Did you try different settings?

---

### Post by Papa_Smurf on 2009-10-23
the very first error message about artsshell not found means that you do not have audio permissions, and thus nothing will work right if at all. To give yourself permissions, go to System->Administration->Users and Groups. Select and Unlock your user name. In your Properties, in the User Privileges tab, check "Use audio devices". Save your changes and re-boot (I select the RT kernel from Grub). Now Jack runs for me.:popcorn:

---

### Post by AutoStatic on 2009-10-23
artsshell is part of [aRts]("http://www.arts-project.org/doc/mcop-doc/artsd-faq.html"). aRts is an old sound server for KDE, it has nothing to do with this issue. Jack will run despite of this warning.

---

### Post by Eiffelben on 2009-11-04
> **Dhjengis said:**
> 
impossible sample width (1) discovered!
 [COLOR=#999999]14:34:56.092 JACK was stopped with exit status=1.[/COLOR]
 [COLOR=#999999][/COLOR]

I had the same problem and solved it by defining the Input and Output devices separatley. As my USB audio device is hw0 I use "hw0,0" as Output device and "hw0,1" as Input device.
Jack runs nicely with this config.
My current problem is I can't get the audio input to Ardour but the list of possible failure-sources in this case is far longer...

---

### Post by RaumTrug on 2009-11-06
Hello there...so that "bug" in jack is not fixed yet?

I've been having the same problems lately with an usb-mic which supplies only input channels, no output: whenever trying to select it as master source, without an output source given: impossible sample width (1) (selecting both the mic for input and the independently timed soundcard for output led to either big latency or x-run nightmare!).

however, I wished for my mic to be master source, and output with as little latency as possible (via jack_load audioadapter, so only the monitor sound gets resampled, not the input which I wished to record directly) processed by reverb&eq on my soundcard!

I've found, researching the jack sourcecode, that jackd's alsa driver at some part tries to assign dithering routines to an "output handle", even if there's no output device present: then it fails in some routine with "sample width (1)" and exits the whole jackd daemon!!

the only way to fix this is to recompile whole jack with fixed sourcecode (either deleting/uncommenting the "impossible sample width -> exit" passage in the alsa driver (which might be unsafe), or encapsulating the output part with an "if(output_handle) { ...code... }", like it's done all over the alsa driver's code, btw, but was apparently forgotten in that special routine!

sadly I've wiped the install with the fix (was on 8.10 and worked well, just overinstalling broke whole jack on 9.04!), but if anyone's interested in how to do it, and somebody else even helps by telling me how to "replace"  & lock the jackd & libjack packages with the recompiled without having to uninstall all other apps that depend on them, I'd be happy to tell you exactly how to fix it - I'm eager as well to use my usb mic with 'buntu again!

I'll install 9.10 in the next days, and then I'll give jack another chance!

-Peace!

---

