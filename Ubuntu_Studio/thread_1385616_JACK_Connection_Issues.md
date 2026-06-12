---
title: "JACK Connection Issues"
date: 2010-01-19
forum: Ubuntu Studio
---

### Post by webster922 on 2010-01-19
Hello, I have just installed Ubuntu Studio 9.10 in order to use my piano keyboard with some of the multimedia programs. I have my keyboard (which does not have Linux drivers) set to MIDI output and thought that Ubuntu would take it from there, but unfortunately it was not that easy. From what I understand JACK handles all multimedia inputs and outputs, am I correct? So without JACK I cannot have a connection to my keyboard? I go to see if JACK is running with the qjackctl gui but every time it gives me this message:

 p, li { white-space: pre-wrap; }  [COLOR=#999999]19:39:49.256 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]19:39:49.264 Statistics reset.[/COLOR]
 [COLOR=#999999]19:39:49.315 Startup script...[/COLOR]
 [COLOR=#990099]19:39:49.316 artsshell -q terminate[/COLOR]
 [COLOR=#66cc99]19:39:49.320 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]19:39:49.720 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]19:39:49.720 JACK is starting...[/COLOR]
 [COLOR=#990099]19:39:49.721 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2[/COLOR]
 [COLOR=#999999]19:39:49.754 JACK was started with PID=4419.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot use real-time scheduling (FIFO at priority 10) [for thread -1217161536, from thread -1217161536] (1: Operation not permitted)
 cannot create engine
 [COLOR=#999999]19:39:49.784 JACK was stopped successfully.[/COLOR]
 [COLOR=#999999]19:39:49.785 Post-shutdown script...[/COLOR]
 [COLOR=#990099]19:39:49.785 killall jackd[/COLOR]
 [COLOR=#cccc99]19:39:49.934 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]19:39:50.194 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]19:39:51.941 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

I have reinstalled 'jackd' with Synaptic but did not notice any difference. Any help is appreciated as I have yet to connect my keyboard.

---

### Post by webster922 on 2010-01-19
I just found out that Ubuntu can see my device. Some programs see it without changing settings like Aconnectgui, Seq24, and Linthesia. But others like Ardour and Beast cannot see it. They ask for settings like 'Inbound MMC Device ID', 'Outbound MMC Device ID', 'Startup Program Change', and 'Port Name' in order to even see the device. If somebody could point me to where I can find these settings it would be very helpful. Thanks.

---

### Post by pete25r on 2010-01-20
I had a similar problem. Well I had the same outpout that you listed.

I found a fix. I opened a terminal and typed in jack (maybe jackd), was the other night. It came back to me with some error saying it needed some arguments. Do the --help and it'll give you the arguments.
Final fix was something like >jack -d alsa

hope this helps...

---

### Post by AutoStatic on 2010-01-20
Hello webster922, how is the keyboard connected to your PC? And could you post the outcome of **amidi -l** in a terminal? And you don't need JACK, you've already played around with Aconnectgui and that's good to start with already.

---

### Post by AutoStatic on 2010-01-20
> **pete25r said:**
> I found a fix. I opened a terminal and typed in jack (maybe jackd), was the other night. It came back to me with some error saying it needed some arguments. Do the --help and it'll give you the arguments.
Final fix was something like >jack -d alsaJACK comes with a nice GUI, QjackCtl, you don't need the terminal for that. With QjackCtl you can control all possible JACK settings.

---

### Post by mango42 on 2010-01-20
> cannot use real-time scheduling (FIFO at priority 10) [for thread -1217161536, from thread -1217161536] (1: Operation not permitted)

AutoStatic & Trulan showed us the way around this error. It's to do with system permissions.

To quote from [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) :-

"After you've got the [Real time] kernel you still need to set up real-time access for your applications. 

All you have to do for this is give your audio group permissions to access the rtprio, nice, and memlock limits. To do this, you just need to run these commands, which will add some lines to the file /etc/security/limits.conf:"

```
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'
```

---

### Post by webster922 on 2010-01-20
The output to **amidi -l **is:

Dir Device    Name
IO  hw:1,0,0  CASIO USB-MIDI MIDI 1

---

### Post by AutoStatic on 2010-01-21
Thanks! So it's being properly recognised and its hardware ID is 1 (hw:1). Could you also post a screenshot of aconnectgui with the Casio attached? And maybe this post will help you a bit: [http://ubuntuforums.org/showpost.php?p=8540958&postcount=18](http://ubuntuforums.org/showpost.php?p=8540958&postcount=18)

---

### Post by webster922 on 2010-01-21
Here is a screenshot of aconnectgui running and also qjackctl (although I am starting to think that MIDI does not relate to JACK).

---

### Post by AutoStatic on 2010-01-21
> **webster922 said:**
> Here is a screenshot of aconnectgui runningLooks good, the Casio is there. Now run ZynAddSubFX like in the link to one of my earlier posts and connect it to the Casio input in Aconnectgui. That should get you going.

> **webster922 said:**
> (although I am starting to think that MIDI does not relate to JACK).Yes and no. Yes because JACK does have built-in MIDI support (the MIDI tab in QjackCtl) and no, not all JACK aware apps use it, they (still) use MIDI via ALSA.

---

### Post by webster922 on 2010-01-21
I opened aconnectgui, and instead of typing **pasuspender -- zynaddsubfx**, I typed **pasuspender -- ardour** (because that is the program I would like to try). After opening Ardour it showed up in the menu and I made a connection through aconnectgui. But still when recording under Ardour no noise is recorded. I think it relates to the Add MIDI Port (see screenshot). And also Ardour gives me three options that I am unsure about. Should I choose Internal, MTC, or JACK?

---

### Post by AutoStatic on 2010-01-22
For Ardour to work you need JACK. I thought you wanted to find out if Ubuntu sees your device and if you can use it, ie with a simple softsynth.
Can't help you though with getting Ardour to work, I don't use it.

---

### Post by trulan on 2010-01-22
Ardour is a great program, I use it all the time, but I don't use it for my midi keyboard.  Midi support is coming in Ardour 3.0.  For now, to use your midi keyboard, qsynth, qtractor, zynaddsubfx, or even lmms will handle the midi keyboard much better than Ardour.

Once you've got your midi the way you want it, you can connect the outputs of your midi program to inputs in Ardour and record your audio live (as you play it, or as your midi program plays it back).  For recording the midi stream (as opposed to the audio) I would use qtractor.

---

### Post by webster922 on 2010-01-23
I got the input running with ZynAddSubFX, but why does it sound so synth-y even the program set to no effect?

---

### Post by webster922 on 2010-01-27
Thanks for all the replies. Hopefully it will keep running as it should.

---

### Post by 5hawnk3lly on 2010-03-10
i got this one and messin with /etc/security/limits.conf didn't work.  when when i looked in /etc/group i noticed that my current user wasn't in the audio group.  added myself, restarted, and smacked my head "duh".[http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif](http://ubuntuforums.org/images/smilies/new_popcornsmiley.gif)

---

