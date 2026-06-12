---
title: "No sound in audio apps!"
date: 2009-12-02
forum: Ubuntu Studio
---

### Post by jitup on 2009-12-02
Hello again,
I just got ubuntu studio 9.10 installed last night and every thing works good except one thing. I cant get jack to work, Ardour dosent recognize any input, and the rest of the audio follow suit. Nothing outputs either. I get sounds from the system on start up and when messages pop up. How do I set up ALSA on this distro? Is it even there? I have no internet on the computer so if I need to download something, can you please point me in the direction? Thanks

Oh, ya, The other thing is I am wondering how do you create deb's  in 9.10? There are some good apps that dont have a deb yet and I would be willing to make them for the programs I intend to put on my box, like Cinelerra 4.1. I am runing 64 bit if that makes any differance. I know there are guides out there, but can some one give me a link to a good one for a non programer?
Thanks!

---

### Post by bigsmitty64 on 2009-12-02
This  [ http://jackaudio.org/]("http://jackaudio.org/")  helped me alot,along with the people on here.
I JUST got it too. Its confusing at first but trust me it's worth it! Good luck.

---

### Post by jitup on 2009-12-03
Please Help!! I cant figure out how to get sound from any of the audio apps!! I cant get alsa to work. I had it all running smooth in 9.04 (but my video card did not like it)

---

### Post by trulan on 2009-12-03
Are you trying to use Jack, or are you trying to work without using Jack?

It sounds like you are having problems getting Jack set up but I am not sure.  If you are having troubles with Jack, please post the errors it it giving so we know how to help you.

---

### Post by jitup on 2009-12-03
Ok, it is a problem with jack. I would paste the results from the msg box but tomboy is not included (no word editro is? why? open office should be included?) so I will try and get the .deb when I go to the library,(I have dial up, download will take too long) in the mean time, what do I need to be able to compile programs?

---

### Post by jitup on 2009-12-03
if there is any way to upload a file, I have a scribus file which I copied the jack msg into

---

### Post by trulan on 2009-12-04
The best way is to paste it into a post right here.  Put code tags around it, like this:

[ C O D E ] paste message here [ / C O D E ]

Eliminate the spaces in the code tags and it will look like this:

```
 paste message here 
```

---

### Post by jitup on 2009-12-04
1

---

### Post by jitup on 2009-12-04
ok, there is a txt editor in studio, thanks for the PM!
here is what jack is putting out
```
20:31:54.743 Patchbay deactivated.
20:31:54.763 Statistics reset.
20:31:54.854 ALSA connection graph change.
20:31:55.050 ALSA connection change.
20:31:58.716 Startup script...
20:31:58.717 artsshell -q terminate
sh: artsshell: not found
20:31:59.120 Startup script terminated with exit status=32512.
20:31:59.120 JACK is starting...
20:31:59.121 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
20:31:59.126 JACK was started with PID=2510.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
20:31:59.403 JACK was stopped successfully.
20:31:59.404 Post-shutdown script...
20:31:59.404 killall jackd
jackd: no process found
20:31:59.822 Post-shutdown script terminated with exit status=256.
20:32:01.266 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```
I don't know what any of this means! please help
thank you for being so patient with my ignorance.

---

### Post by trulan on 2009-12-05
OK, first take care of the "cannot lock down memory" problem.

1. If you have not run Ubuntu Studio Controls, do.  It's in the main menu under system/administration/Ubuntu Studio Controls.  Check the 'enable memlock' box and set it to 50% of system memory.  Click apply, then close.

2. Check if the settings were written properly. In a terminal, run:
```
sudo gedit /etc/security/limits.conf
```At the bottom of the file you should see these two lines:
```
@audio    -    rtprio        99
@audio      -      memlock     (a number equaling half your system memory)
```Some people are reporting that Ubuntu Studio controls does not write the 'memlock' line correctly.

3. Run
```
groups
```Make sure 'audio' is listed in this output.

Then, try starting Jack again and see if anything changed.  You may need to reboot for these settings to take effect but I'm not sure.

If it still doesn't work, but is giving different error messages, post them and we'll go from there.

---

### Post by jitup on 2009-12-05
ok I did what you said and I got the outputs I was supposed to.
now jack is giving me this error
```
20:31:54.743 Patchbay deactivated.
20:31:54.763 Statistics reset.
20:31:54.854 ALSA connection graph change.
20:31:55.050 ALSA connection change.
20:31:58.716 Startup script...
20:31:58.717 artsshell -q terminate
sh: artsshell: not found
20:31:59.120 Startup script terminated with exit status=32512.
20:31:59.120 JACK is starting...
20:31:59.121 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
20:31:59.126 JACK was started with PID=2510.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot lock down memory for jackd (Cannot allocate memory)
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
20:31:59.403 JACK was stopped successfully.
20:31:59.404 Post-shutdown script...
20:31:59.404 killall jackd
jackd: no process found
20:31:59.822 Post-shutdown script terminated with exit status=256.
20:32:01.266 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```

---

