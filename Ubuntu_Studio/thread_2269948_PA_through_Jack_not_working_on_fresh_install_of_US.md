---
title: "PA through Jack not working on fresh install of US14.04.2/5"
date: 2015-03-19
forum: Ubuntu Studio
---

### Post by kazakore on 2015-03-19
Recently reinstalled Ubuntu Studio 14.04, the latest version (I believe is Studio 14.04.02 bassed on main Ubuntu 14.04.5...)

I double click an audio file and it opens and plays in Audacious fine.
Start Jack via qjackctl
Try and play in Audacious and no audio and the play position doesn't move.
Change output to Jack and audio plays.
Change back to PA (or ALSA) and audio stops.
Also tested with Audacity and Rhythmbox with the same result.

PulseAudio JACK Sinc is present under Jack Connections as you would expect.


Anybody know what the problem may be or how to fix it? Previously I completely disable PA by removing the Executable flag but thought I'd give it another chance on this install...


Partially SOLVED:
Follow the set-up here, which should be set as default (and used to be) but for some reason wasn't for me. The setting are in PulseAudio Volume Control, not in the standard PA audio mixer.
[https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204#The_Pulse_Audio_to_Jack_Bridge_-_using_both_at_once](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204#The_Pulse_Audio_to_Jack_Bridge_-_using_both_at_once)
This setting is not remembered between sessions though! As soon as you disconnect from Jack the Sinc option disappears and it doesn't remember to use it again when you next start connect to Jack.

---

### Post by Sean_Britton on 2015-03-21
Hi There,
I have had this problem too and learned that if you want ALSA working again under Ubuntu Studio without restarting your computer you must:
1. Quit QJackCtl
2. Open Task Manager
3. Right-click on "jackdbus auto", and click "kill" and sound should come through ALSA instantly

---

### Post by kazakore on 2015-03-21
How does quitting QJackCtl help me get Pulse Audio through Jack? If I do that jack is no longer running to send PA to! Defeats the whole purpose!! (Yes I use QJackCtl to start the Jack session, not commandline arguments. Could try that I guess...)

Quitting Jack and PA instantly starts playing again, if that's what you mean was your problem. As far as I understand it ALSA is still the final (application?) layer before the actual audio interface, so both PA and Jack interact with ALSA to get sound to your card (although I may be wrong.) Both Jack and PA work in isolation, switching between pure use of either is fine, but the Pulse/Jack Source/Sinc are not working!

This worked as expected when I installed Ubuntu Studio 14.04 initially, which would have been very slightly after the .1 release for Ubuntu main. It doesn't work with the latest version though, on the same hardware though.

---

### Post by kazakore on 2015-03-21
Additional. Messages from a basic session.  

Session actions: 
Start QJackCtl from commandline. (Auto start Jack server option is enabled.) 
Stop Jack Session. 
Start Jack Session (again.)  

Messages:
 ```
  [COLOR=#999999]11:02:51.750 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]11:02:51.752 Statistics reset.[/COLOR]
 [COLOR=#cccc99]11:02:51.762 ALSA connection change.[/COLOR]
 [COLOR=#999999]11:02:51.768 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#999999]11:02:51.892 D-BUS: JACK server is starting...[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]11:02:51.894 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]11:02:51.920 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
 (qjackctl:3887): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3887): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 Sun Mar 22 11:02:51 2015: Starting jack server...
 Sun Mar 22 11:02:51 2015: JACK server starting in realtime mode with priority 10
 Sun Mar 22 11:02:51 2015: self-connect-mode is "Don't restrict self connect requests"
 Sun Mar 22 11:02:51 2015: Acquired audio card Audio0
 Sun Mar 22 11:02:51 2015: creating alsa driver ... hw:0|hw:0|512|3|48000|0|0|nomon|swmeter|-|32bit
 Sun Mar 22 11:02:51 2015: Using ALSA driver HDA-Intel running on card 0 - HDA Intel PCH at 0xf2530000 irq 48
 Sun Mar 22 11:02:51 2015: configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 3 periods
 Sun Mar 22 11:02:51 2015: ALSA: final selected sample format for capture: 32bit integer little-endian
 Sun Mar 22 11:02:51 2015: ALSA: use 3 periods for capture
 Sun Mar 22 11:02:51 2015: ALSA: final selected sample format for playback: 32bit integer little-endian
 Sun Mar 22 11:02:51 2015: ALSA: use 3 periods for playback
 Sun Mar 22 11:02:51 2015: graph reorder: new port 'system:capture_1'
 Sun Mar 22 11:02:51 2015: New client 'system' with PID 0
 Sun Mar 22 11:02:51 2015: graph reorder: new port 'system:capture_2'
 Sun Mar 22 11:02:51 2015: graph reorder: new port 'system:playback_1'
 Sun Mar 22 11:02:51 2015: graph reorder: new port 'system:playback_2'
 Sun Mar 22 11:02:51 2015: graph reorder: new port 'system:playback_3'
 Sun Mar 22 11:02:51 2015: graph reorder: new port 'system:playback_4'
 Sun Mar 22 11:02:51 2015: New client 'PulseAudio JACK Sink' with PID 1579
 Sun Mar 22 11:02:51 2015: port 'PulseAudio JACK Sink:front-left' created
 Sun Mar 22 11:02:51 2015: port 'PulseAudio JACK Sink:front-right' created
 Sun Mar 22 11:02:51 2015: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
 Sun Mar 22 11:02:51 2015: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
 Sun Mar 22 11:02:51 2015: New client 'PulseAudio JACK Source' with PID 1579
 Sun Mar 22 11:02:51 2015: port 'PulseAudio JACK Source:front-left' created
 Sun Mar 22 11:02:51 2015: port 'PulseAudio JACK Source:front-right' created
 Sun Mar 22 11:02:51 2015: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
 Sun Mar 22 11:02:51 2015: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
 Sun Mar 22 11:02:53 2015: Saving settings to "/home/dale/.config/jack/conf.xml" ...
 [COLOR=#9999cc]11:02:54.127 JACK connection change.[/COLOR]
 [COLOR=#999933]11:02:54.127 Server configuration saved to "/home/dale/.jackdrc".[/COLOR]
 [COLOR=#999999]11:02:54.128 Statistics reset.[/COLOR]
 [COLOR=#999999]11:02:54.142 Client activated.[/COLOR]
 [COLOR=#cc9966]11:02:54.156 JACK connection graph change.[/COLOR]
 (qjackctl:3887): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3887): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 Sun Mar 22 11:02:54 2015: New client 'qjackctl' with PID 3887
 [COLOR=#999999]11:02:59.299 Client deactivated.[/COLOR]
 [COLOR=#999999]11:02:59.390 D-BUS: JACK server is stopping...[/COLOR]
 [COLOR=#999999]11:02:59.396 D-BUS: JACK server was stopped (org.jackaudio.service aka jackdbus).[/COLOR]
 (qjackctl:3887): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3887): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3887): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3887): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 Sun Mar 22 11:02:59 2015: Client 'qjackctl' with PID 3887 is out
 Sun Mar 22 11:02:59 2015: Stopping jack server...
 Sun Mar 22 11:02:59 2015: Client 'system' with PID 0 is out
 Sun Mar 22 11:02:59 2015: Client 'PulseAudio JACK Sink' with PID 1579 is out
 Sun Mar 22 11:02:59 2015: Client 'PulseAudio JACK Source' with PID 1579 is out
 Sun Mar 22 11:02:59 2015: ERROR: Cannot write socket fd = 12 err = Broken pipe
 Sun Mar 22 11:02:59 2015: ERROR: CheckRes error
 Sun Mar 22 11:02:59 2015: ERROR: Could not write notification
 Sun Mar 22 11:02:59 2015: ERROR: ClientNotify fails name = system notification = 1 val1 = 0 val2 = 0
 Sun Mar 22 11:02:59 2015: ERROR: Cannot write socket fd = 14 err = Broken pipe
 Sun Mar 22 11:02:59 2015: ERROR: CheckRes error
 Sun Mar 22 11:02:59 2015: ERROR: Could not write notification
 Sun Mar 22 11:02:59 2015: ERROR: ClientNotify fails name = system notification = 1 val1 = 0 val2 = 0
 Sun Mar 22 11:02:59 2015: Released audio card Audio0
 Sun Mar 22 11:02:59 2015: ERROR: Cannot write socket fd = 12 err = Broken pipe
 Sun Mar 22 11:02:59 2015: ERROR: CheckRes error
 Sun Mar 22 11:02:59 2015: ERROR: Could not write notification
 Sun Mar 22 11:02:59 2015: ERROR: ClientNotify fails name = freewheel notification = 1 val1 = 0 val2 = 0
 Sun Mar 22 11:02:59 2015: ERROR: Cannot write socket fd = 14 err = Broken pipe
 Sun Mar 22 11:02:59 2015: ERROR: CheckRes error
 Sun Mar 22 11:02:59 2015: ERROR: Could not write notification
 Sun Mar 22 11:02:59 2015: ERROR: ClientNotify fails name = freewheel notification = 1 val1 = 0 val2 = 0
 [COLOR=#999999]11:03:01.720 D-BUS: JACK server is starting...[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#999999]11:03:01.724 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
 Sun Mar 22 11:03:01 2015: Starting jack server...
 Sun Mar 22 11:03:01 2015: JACK server starting in realtime mode with priority 10
 Sun Mar 22 11:03:01 2015: self-connect-mode is "Don't restrict self connect requests"
 Sun Mar 22 11:03:01 2015: Acquired audio card Audio0
 Sun Mar 22 11:03:01 2015: creating alsa driver ... hw:0|hw:0|512|3|48000|0|0|nomon|swmeter|-|32bit
 Sun Mar 22 11:03:01 2015: Using ALSA driver HDA-Intel running on card 0 - HDA Intel PCH at 0xf2530000 irq 48
 Sun Mar 22 11:03:01 2015: configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 3 periods
 Sun Mar 22 11:03:01 2015: ALSA: final selected sample format for capture: 32bit integer little-endian
 Sun Mar 22 11:03:01 2015: ALSA: use 3 periods for capture
 Sun Mar 22 11:03:01 2015: ALSA: final selected sample format for playback: 32bit integer little-endian
 Sun Mar 22 11:03:01 2015: ALSA: use 3 periods for playback
 Sun Mar 22 11:03:01 2015: graph reorder: new port 'system:capture_1'
 Sun Mar 22 11:03:01 2015: New client 'system' with PID 0
 Sun Mar 22 11:03:01 2015: graph reorder: new port 'system:capture_2'
 Sun Mar 22 11:03:01 2015: graph reorder: new port 'system:playback_1'
 Sun Mar 22 11:03:01 2015: graph reorder: new port 'system:playback_2'
 Sun Mar 22 11:03:01 2015: graph reorder: new port 'system:playback_3'
 Sun Mar 22 11:03:01 2015: graph reorder: new port 'system:playback_4'
 Sun Mar 22 11:03:01 2015: New client 'PulseAudio JACK Sink' with PID 1579
 Sun Mar 22 11:03:01 2015: port 'PulseAudio JACK Sink:front-left' created
 Sun Mar 22 11:03:01 2015: port 'PulseAudio JACK Sink:front-right' created
 Sun Mar 22 11:03:01 2015: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
 Sun Mar 22 11:03:01 2015: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
 Sun Mar 22 11:03:01 2015: New client 'PulseAudio JACK Source' with PID 1579
 Sun Mar 22 11:03:01 2015: port 'PulseAudio JACK Source:front-left' created
 Sun Mar 22 11:03:01 2015: port 'PulseAudio JACK Source:front-right' created
 Sun Mar 22 11:03:01 2015: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
 Sun Mar 22 11:03:01 2015: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
 Sun Mar 22 11:03:03 2015: Saving settings to "/home/dale/.config/jack/conf.xml" ...
 [COLOR=#9999cc]11:03:03.826 JACK connection change.[/COLOR]
 [COLOR=#999933]11:03:03.827 Server configuration saved to "/home/dale/.jackdrc".[/COLOR]
 [COLOR=#999999]11:03:03.827 Statistics reset.[/COLOR]
 [COLOR=#999999]11:03:03.842 Client activated.[/COLOR]
 [COLOR=#cc9966]11:03:03.856 JACK connection graph change.[/COLOR]
 Sun Mar 22 11:03:03 2015: New client 'qjackctl' with PID 3887



```

---

### Post by marseille2 on 2015-03-23
You're system is actually working fine. Some programs -- like Audacity, Audacious, Rhythmbox, and streaming audio from a browser -- don't need Jackd to run. ALSA is enough. They work great by themselves, or with a generic kernel. And if you have a bunch these programs running ... then PulseAudio (PA) is a half-way decent, consumer-grade mixer to control their individual volume levels. But it doesn't get much deeper than that.

Jackd is it's own animal. Once you turn it on, PA has to give Jackd the sound card, and quit... until Jackd is turned off. That means you have to route the audio through Jackd, as you successfully did the first time... since PA is intentionally shut off. 

That's where the modules come in... Because it's the only way to get Jackd and PA to talk to each other. This becomes essential when we want to listen to streaming audio in the browser, while doing audio work in applications  -- like Ardour -- that only work with Jackd.

---

### Post by kazakore on 2015-03-24
> **marseille2 said:**
> You're system is actually working fine. Some programs -- like Audacity, Audacious, Rhythmbox, and streaming audio from a browser -- don't need Jackd to run. 


Sorry but you clearly don't know what you're talking about!! I know it doesn't NEED Jack (which I have made very clear by stating sound is fine while Jack is not running) but since some point in the 12.04LTS cycle Ubuntu introduced the pulseaudio-module-jack to connect PA through Jack if desired.

[https://help.ubuntu.com/community/UbuntuStudioPreparation#PulseAudio_and_Jack_working_together](https://help.ubuntu.com/community/UbuntuStudioPreparation#PulseAudio_and_Jack_working_together)

This worked perfectly without me having to do a thing when I initially installed Ubuntu Studo 14.04 about 9 months ago. It doesn't work with the fresh install of the new, updated image!

According to this there might be a PA setting I have to change but I've not managed to find that setting yet...

[https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204#The_Pulse_Audio_to_Jack_Bridge_-_using_both_at_once](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204#The_Pulse_Audio_to_Jack_Bridge_-_using_both_at_once)

EDIT: Found the setting. Used Application Finder to search for (PulseAudio) Volume Control and the setting is in there. It's not the same as the options you get opening the standard audio mixer and selecting the PulseAudio output mixer, which is where I was looking before.

EDIT2: This setting is not remembered between sessions though! As soon as you  disconnect from Jack the Sinc option disappears from the PA settings and it doesn't remember  to use it again when you next start connect to Jack. Previously it Just Worked(tm) when I tested it. But at least I can get the audio through it now, even if it seems I have an extra hoop to jump through to do so...

---

### Post by marseille2 on 2015-03-24
Oh... sounds like your sinks are flaky. If that's what you're talking about, then you aren't alone.

---

### Post by danilo-bs on 2015-04-01
You need to assign Jack sink as your default audio output.
Click on volume indicator on top bar and go to settings...
Under "output" tab, you should see a "jack sink" output
(presuming jack has started).
Click on the third icon (a green one, on the right side of the jack sink). 
By pressing it, this output now should become default for your system.
If you use your soundcard as only output to your system, i'd recommend creating a good playback
profile in jack (and another for recording, if you plan on doing it). Go to options section and check that jack
connects on aplication startup, and you should assign qjackctl as program that should initialize with the system...
also, in audacious, just leave with the default config (pulse audio output), since with jack sink, it'll work on the fly.
hope this will help

---

