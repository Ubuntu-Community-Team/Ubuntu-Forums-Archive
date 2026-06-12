---
title: "Jack issues"
date: 2015-02-08
forum: Ubuntu Studio
---

### Post by chkneater on 2015-02-08
Hi, my name is Bobby.. I am having a problem with QjackCtrl... at first it slowed down and eventually stopped playing Clementine altoget.. I noticed it had an insane amt of Xruns... I closed jack and opend Audacious just for some playback.,, it too did the same thing after a  few mins.... ever since then I cant get jack to work at all.  Here is a copy of the message I get on start up:

[QUOTE]02:42:47.922 Patchbay deactivated.
02:42:47.982 Statistics reset.
02:42:47.995 ALSA connection change.
02:42:48.011 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
02:42:48.025 ALSA connection graph change.
02:43:03.901 D-BUS: SetParameterValue('driver:inchannels', '2'): Parameter value type mismatch: was expecting 'i', got 'u'. (org.jackaudio.Error.InvalidArgs)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Sun Feb  8 02:43:03 2015: [1m[31mERROR: Parameter value type mismatch: was expecting 'i', got 'u'[0m
Sun Feb  8 02:43:05 2015: Saving settings to "/home/hellkiller/.config/jack/conf.xml" ...
02:43:08.184 D-BUS: SetParameterValue('driver:outchannels', '2'): Parameter value type mismatch: was expecting 'i', got 'u'. (org.jackaudio.Error.InvalidArgs)
Sun Feb  8 02:43:08 2015: [1m[31mERROR: Parameter value type mismatch: was expecting 'i', got 'u'[0m
02:43:09.562 D-BUS: JACK server is starting...
02:43:09.572 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Sun Feb  8 02:43:09 2015: Starting jack server...
Sun Feb  8 02:43:09 2015: JACK server starting in non-realtime mode
Sun Feb  8 02:43:09 2015: control device hw:0
Sun Feb  8 02:43:09 2015: control device hw:0
Sun Feb  8 02:43:09 2015: Acquired audio card Audio0
Sun Feb  8 02:43:09 2015: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Sun Feb  8 02:43:09 2015: control device hw:0
Sun Feb  8 02:43:09 2015: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Sun Feb  8 02:43:09 2015: ALSA: final selected sample format for capture: 16bit little-endian
Sun Feb  8 02:43:09 2015: ALSA: use 2 periods for capture
Sun Feb  8 02:43:09 2015: ALSA: final selected sample format for playback: 16bit little-endian
Sun Feb  8 02:43:09 2015: ALSA: use 2 periods for playback
Sun Feb  8 02:43:09 2015: scan: added port hw:0,0,0 in-hw-0-0-0-C-Media-CMI8738-MIDI
Sun Feb  8 02:43:09 2015: scan: added port hw:0,0,0 out-hw-0-0-0-C-Media-CMI8738-MIDI
Sun Feb  8 02:43:09 2015: scan: opened port hw:0,0,0 in-hw-0-0-0-C-Media-CMI8738-MIDI
Sun Feb  8 02:43:09 2015: graph reorder: new port 'system:capture_1'
Sun Feb  8 02:43:09 2015: New client 'system' with PID 0
Sun Feb  8 02:43:09 2015: graph reorder: new port 'system:capture_2'
Sun Feb  8 02:43:09 2015: graph reorder: new port 'system:playback_1'
Sun Feb  8 02:43:09 2015: graph reorder: new port 'system:playback_2'
Sun Feb  8 02:43:09 2015: graph reorder: new port 'system:midi_capture_1'
Sun Feb  8 02:43:09 2015: scan: opened port hw:0,0,0 out-hw-0-0-0-C-Media-CMI8738-MIDI
Sun Feb  8 02:43:09 2015: New client 'PulseAudio JACK Sink' with PID 2025
Sun Feb  8 02:43:09 2015: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
Sun Feb  8 02:43:09 2015: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
Sun Feb  8 02:43:09 2015: New client 'PulseAudio JACK Source' with PID 2025
Sun Feb  8 02:43:09 2015: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
Sun Feb  8 02:43:09 2015: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
Sun Feb  8 02:43:10 2015: Saving settings to "/home/hellkiller/.config/jack/conf.xml" ...
02:43:11.841 JACK connection change.
02:43:11.846 Server configuration saved to "/home/hellkiller/.jackdrc".
02:43:11.848 Statistics reset.
02:43:11.858 Client activated.
02:43:11.892 JACK connection graph change.
Sun Feb  8 02:43:11 2015: New client 'qjackctl' with PID 7005 [QUOTE]


Thanx for your help!!

---

### Post by chkneater on 2015-02-08
Okay, after turning off Realtiem Mode, the only change I made besides checking the correct card was outputting and it jack has been working fine now... with Hydrogen, Ardour and Clementine... no Xruns at all... I always ran Jack in RT mode tho... I need to be able to use it...  here is the output after turning RT off:

```

03:10:12.111 Patchbay deactivated.
03:10:12.162 Statistics reset.
03:10:12.180 ALSA connection change.
03:10:12.202 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
03:10:12.220 ALSA connection graph change.
03:10:26.419 D-BUS: SetParameterValue('driver:inchannels', '2'): Parameter value type mismatch: was expecting 'i', got 'u'. (org.jackaudio.Error.InvalidArgs)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Sun Feb  8 03:10:26 2015: [1m[31mERROR: Parameter value type mismatch: was expecting 'i', got 'u'[0m
Sun Feb  8 03:10:28 2015: Saving settings to "/home/hellkiller/.config/jack/conf.xml" ...
03:10:28.442 D-BUS: SetParameterValue('driver:outchannels', '2'): Parameter value type mismatch: was expecting 'i', got 'u'. (org.jackaudio.Error.InvalidArgs)
Sun Feb  8 03:10:28 2015: [1m[31mERROR: Parameter value type mismatch: was expecting 'i', got 'u'[0m
03:10:30.494 D-BUS: JACK server is starting...
03:10:30.505 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Sun Feb  8 03:10:30 2015: Starting jack server...
Sun Feb  8 03:10:30 2015: JACK server starting in non-realtime mode
Sun Feb  8 03:10:30 2015: control device hw:0
Sun Feb  8 03:10:30 2015: control device hw:0
Sun Feb  8 03:10:30 2015: Acquired audio card Audio0
Sun Feb  8 03:10:30 2015: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Sun Feb  8 03:10:30 2015: control device hw:0
Sun Feb  8 03:10:30 2015: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
Sun Feb  8 03:10:30 2015: ALSA: final selected sample format for capture: 16bit little-endian
Sun Feb  8 03:10:30 2015: ALSA: use 2 periods for capture
Sun Feb  8 03:10:30 2015: ALSA: final selected sample format for playback: 16bit little-endian
Sun Feb  8 03:10:30 2015: ALSA: use 2 periods for playback
Sun Feb  8 03:10:30 2015: scan: added port hw:0,0,0 in-hw-0-0-0-C-Media-CMI8738-MIDI
Sun Feb  8 03:10:30 2015: scan: added port hw:0,0,0 out-hw-0-0-0-C-Media-CMI8738-MIDI
Sun Feb  8 03:10:30 2015: scan: opened port hw:0,0,0 in-hw-0-0-0-C-Media-CMI8738-MIDI
Sun Feb  8 03:10:30 2015: graph reorder: new port 'system:capture_1'
Sun Feb  8 03:10:30 2015: New client 'system' with PID 0
Sun Feb  8 03:10:30 2015: graph reorder: new port 'system:capture_2'
Sun Feb  8 03:10:30 2015: graph reorder: new port 'system:playback_1'
Sun Feb  8 03:10:30 2015: graph reorder: new port 'system:playback_2'
Sun Feb  8 03:10:30 2015: graph reorder: new port 'system:midi_capture_1'
Sun Feb  8 03:10:30 2015: scan: opened port hw:0,0,0 out-hw-0-0-0-C-Media-CMI8738-MIDI
Sun Feb  8 03:10:30 2015: New client 'PulseAudio JACK Sink' with PID 2025
Sun Feb  8 03:10:30 2015: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
Sun Feb  8 03:10:30 2015: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
Sun Feb  8 03:10:30 2015: New client 'PulseAudio JACK Source' with PID 2025
Sun Feb  8 03:10:30 2015: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
Sun Feb  8 03:10:30 2015: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
Sun Feb  8 03:10:31 2015: Saving settings to "/home/hellkiller/.config/jack/conf.xml" ...
03:10:32.770 JACK connection change.
03:10:32.774 Server configuration saved to "/home/hellkiller/.jackdrc".
03:10:32.776 Statistics reset.
03:10:32.790 Client activated.
03:10:32.848 JACK connection graph change.
Sun Feb  8 03:10:32 2015: New client 'qjackctl' with PID 7148
03:10:53.706 JACK connection graph change.
03:10:53.778 JACK connection graph change.
03:10:53.942 JACK connection graph change.
03:10:54.133 JACK connection change.
Sun Feb  8 03:10:53 2015: New client 'Clementine' with PID 7168
Sun Feb  8 03:10:53 2015: Connecting 'Clementine: out_jackaudiosink-1_1' to 'system:playback_1'
Sun Feb  8 03:10:53 2015: Connecting 'Clementine :out_jackaudiosink-1_2' to 'system:playback_2'
```  

Thanx for your help... I have moar than enuff RAM and SWAP to handle RT mode btw...

---

### Post by chkneater on 2015-02-08
the last lines I had to go back and edit cuz the reader thot they were emoticons, that's why the last two lines look weird.  Why didn't the  quotes work??

---

### Post by chkneater on 2015-02-08
> 

D-BUS: SetParameterValue('driver:inchannels', '1'):

Parameter value type mismatch: was expecting 'i', got 'u'.
(org.jackaudio.Error.InvalidArgs)

This is the prompt I get whenever I just try to turn on RT.

---

### Post by sudodus on 2015-02-08
I could help you get rid of the emoticons: use [noparse]```
tags
```[/noparse] (mark and use the # icon in advanced mode).

But I have no experience of jack, so you must wait for somebody else to help you with the real problem.

---

