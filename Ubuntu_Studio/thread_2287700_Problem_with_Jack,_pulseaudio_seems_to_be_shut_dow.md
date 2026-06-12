---
title: "Problem with Jack, pulseaudio seems to be shut down?"
date: 2015-07-21
forum: Ubuntu Studio
---

### Post by adam155 on 2015-07-21
Hello, I am new to Ubuntu, however I've tried everything before I posted this thread. I tried to figure out the problem which is very similar to those which other users have experienced. So I tried their solutions but it doesn't help at all so I ask for help. 
First of all, my Jack used to work with no problems but yesterday I've tried to record guitar and vocals, at the same time. Guitar was plugged in Line-in and Mic was plugged in front MIC socket (I have to sockets, rear and front, though I am sure I haven't missed them). It didn't record any sound and... where there is the most sorry part of the story... I tried to change something in jack setup and I have no idea what I've done but I screwed it... However all settings seems to be as before now, and it still doesn't work. When I launch it, this is the message:

```
 [COLOR=#999999]20:19:04.036 Logging started --- wt. lip 21 20:19:04 2015 ---[/COLOR]
 [COLOR=#999999]20:19:04.048 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]20:19:04.059 Statistics reset.[/COLOR]
 [COLOR=#cccc99]20:19:04.067 ALSA connection change.[/COLOR]
 [COLOR=#999999]20:19:04.072 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#999999]20:19:04.126 D-BUS: JACK server is starting...[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#999999]20:19:04.153 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#9999cc]20:19:04.344 JACK connection change.[/COLOR]
 [COLOR=#999933]20:19:04.345 Server configuration saved to "/home/adam/.jackdrc".[/COLOR]
 [COLOR=#999999]20:19:04.345 Statistics reset.[/COLOR]
 [COLOR=#999999]20:19:04.351 Client activated.[/COLOR]
 [COLOR=#cc9966]20:19:04.358 JACK connection graph change.[/COLOR]
 Tue Jul 21 20:19:04 2015: Starting jack server...
 Tue Jul 21 20:19:04 2015: JACK server starting in realtime mode with priority 10
 Tue Jul 21 20:19:04 2015: self-connect-mode is "Don't restrict self connect requests"
 Tue Jul 21 20:19:04 2015: Acquired audio card Audio0
 Tue Jul 21 20:19:04 2015: creating alsa driver ... hw:PCH,0|hw:PCH,0|256|2|48000|0|0|nomon|swmeter|-|16bit
 Tue Jul 21 20:19:04 2015: configuring for 48000Hz, period = 256 frames (5.3 ms), buffer = 2 periods
 Tue Jul 21 20:19:04 2015: ALSA: final selected sample format for capture: 16bit little-endian
 Tue Jul 21 20:19:04 2015: ALSA: use 2 periods for capture
 Tue Jul 21 20:19:04 2015: ALSA: final selected sample format for playback: 16bit little-endian
 Tue Jul 21 20:19:04 2015: ALSA: use 2 periods for playback
 Tue Jul 21 20:19:04 2015: graph reorder: new port 'system:capture_1'
 Tue Jul 21 20:19:04 2015: New client 'system' with PID 0
 Tue Jul 21 20:19:04 2015: graph reorder: new port 'system:capture_2'
 Tue Jul 21 20:19:04 2015: graph reorder: new port 'system:playback_1'
 Tue Jul 21 20:19:04 2015: graph reorder: new port 'system:playback_2'
 Tue Jul 21 20:19:04 2015: New client 'qjackctl' with PID 3348
 Tue Jul 21 20:19:05 2015: Saving settings to "/home/adam/.config/jack/conf.xml" ...


```

I start guitarix and it says that the jack server isn't running... I thought that maybe it's hardware. but when I switched to Windows ... Line-in and other sockets works fine. 


Please help

I use latest Ubuntu Studio

---

### Post by jejeman on 2015-07-22
Guess you are using onboard sound card.
You can not record from two different inputs. Use only line in or mic. The card has only two input channels.

---

### Post by adam155 on 2015-07-22
Yes, but now I can't even record from one input. Sorry I didn't mention that I've already figured out what you said but thx anyway;)

Is it possible that after reboot, system still thinks that I have two inbputs pluged in? And there is another thing I didn't mention. When I start jack, pulseaudio isn't visible in conection menu. I used command ```
pulseaudio --start
``` and with another command I get message from terminal that pulseaudio deamon is already running and still jack is not working and there is no pulse audio in conection menu.

---

### Post by jejeman on 2015-07-22
I never use pulseaudio-jack module, it only breaks down JACK. That is the first thing I purge from the system. 
Never use pulseaudio ports for recording, only system ports.
> Is it possible that after reboot, system still thinks that I have two inbputs pluged in?No. And, it doesn't matter if you have.
Can you record without JACK? With Audacity, for example.

---

