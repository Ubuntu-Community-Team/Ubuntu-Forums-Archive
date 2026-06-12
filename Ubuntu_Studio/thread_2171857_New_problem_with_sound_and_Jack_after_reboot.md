---
title: "New problem with sound and Jack after reboot"
date: 2013-09-02
forum: Ubuntu Studio
---

### Post by louh2 on 2013-09-02
Got everything working fine earlier today and gave myself and the  computer a break.  After turning back on and starting Jack I get the  following error:

d-bus: setparametervalue('driver:inchannels','2'):

Parameter value type mismatch: was expecting 'i', got 'u'.
(org.jackaudio.error.invalidargs)

I also noticed that I wasn't able to hear input while playing back  output in Ardour.  I thought I had fixed this by selecting PCM Out for  IEC958 and Digital Mixer  for the H/W in the ALSA mixer utility.  This  allowed me full duplex operation with my M-Audio Delta 2496 soundcard  when Digital Mix L and R was selected in the patchbay/router tab of the  Envy24 control utility.  However now when I start Jack it changes all of  the input and output to PCM Out, changing it back works for a few  seconds and then it automatically changes back.  WTH?  I know there is  some details for you guys to ponder over but I don't know the commands  well enough to cough it up for you.  I can include the Jack message  table if that will help:

  [COLOR=#999999]20:59:34.918 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]20:59:34.920 Statistics reset.[/COLOR]
 [COLOR=#cccc99]20:59:34.936 ALSA connection change.[/COLOR]
 [COLOR=#999999]20:59:34.960 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]20:59:34.980 ALSA connection graph change.[/COLOR]
 [COLOR=#ff0000]20:59:37.471  D-BUS: SetParameterValue('driver:inchannels', '2'): Parameter value  type mismatch: was expecting 'i', got 'u'.  (org.jackaudio.Error.InvalidArgs)[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Sun Sep  1 20:59:37 2013: [1m[31mERROR: Parameter value type mismatch: was expecting 'i', got 'u'[0m
 Sun Sep  1 20:59:39 2013: Saving settings to "/home/lou/.config/jack/conf.xml" ...
 [COLOR=#ff0000]20:59:40.259  D-BUS: SetParameterValue('driver:outchannels', '2'): Parameter value  type mismatch: was expecting 'i', got 'u'.  (org.jackaudio.Error.InvalidArgs)[/COLOR]
 Sun Sep  1 20:59:40 2013: [1m[31mERROR: Parameter value type mismatch: was expecting 'i', got 'u'[0m
 [COLOR=#999999]20:59:41.449 D-BUS: JACK server is starting...[/COLOR]
 [COLOR=#999999]20:59:41.458 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
 Sun Sep  1 20:59:41 2013: Starting jack server...
 Sun Sep  1 20:59:41 2013: JACK server starting in realtime mode with priority 10
 Sun Sep  1 20:59:41 2013: control device hw:0
 Sun Sep  1 20:59:41 2013: control device hw:0
 Sun Sep  1 20:59:41 2013: Acquired audio card Audio0
 Sun Sep  1 20:59:41 2013: creating alsa driver ... hw:0,0|hw:0|128|2|44100|0|0|hwmon|hwmeter|-|32bit
 Sun Sep  1 20:59:41 2013: control device hw:0
 Sun Sep  1 20:59:41 2013: configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 2 periods
 Sun Sep  1 20:59:41 2013: ALSA: final selected sample format for capture: 32bit integer little-endian
 Sun Sep  1 20:59:41 2013: ALSA: use 2 periods for capture
 Sun Sep  1 20:59:41 2013: ALSA: final selected sample format for playback: 32bit integer little-endian
 Sun Sep  1 20:59:41 2013: ALSA: use 2 periods for playback
 Sun Sep  1 20:59:41 2013: scan: added port hw:0,0,0 in-hw-0-0-0-M-Audio-Audiophile-24-96-MIDI
 Sun Sep  1 20:59:41 2013: scan: added port hw:0,0,0 out-hw-0-0-0-M-Audio-Audiophile-24-96-MIDI
 Sun Sep  1 20:59:41 2013: scan: opened port hw:0,0,0 in-hw-0-0-0-M-Audio-Audiophile-24-96-MIDI
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_1'
 Sun Sep  1 20:59:41 2013: New client 'system' with PID 0
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_2'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_3'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_4'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_5'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_6'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_7'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_8'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_9'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_10'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_11'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:capture_12'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_1'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_1'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_2'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_2'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_3'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_3'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_4'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_4'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_5'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_5'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_6'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_6'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_7'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_7'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_8'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_8'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_9'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_9'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:playback_10'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:monitor_10'
 Sun Sep  1 20:59:41 2013: graph reorder: new port 'system:midi_capture_1'
 Sun Sep  1 20:59:41 2013: New client 'PulseAudio JACK Sink' with PID 1847
 Sun Sep  1 20:59:41 2013: scan: opened port hw:0,0,0 out-hw-0-0-0-M-Audio-Audiophile-24-96-MIDI
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:rear-left' to 'system:playback_3'
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:rear-right' to 'system:playback_4'
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:front-center' to 'system:playback_5'
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:lfe' to 'system:playback_6'
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:side-left' to 'system:playback_7'
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:side-right' to 'system:playback_8'
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:aux0' to 'system:playback_9'
 Sun Sep  1 20:59:41 2013: Connecting 'PulseAudio JACK Sink:aux1' to 'system:playback_10'
 Sun Sep  1 20:59:41 2013: New client 'PulseAudio JACK Source' with PID 1847
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_3' to 'PulseAudio JACK Source:rear-left'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_4' to 'PulseAudio JACK Source:rear-right'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_5' to 'PulseAudio JACK Source:front-center'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_6' to 'PulseAudio JACK Source:lfe'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_7' to 'PulseAudio JACK Source:side-left'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_8' to 'PulseAudio JACK Source:side-right'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_9' to 'PulseAudio JACK Source:aux0'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_10' to 'PulseAudio JACK Source:aux1'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_11' to 'PulseAudio JACK Source:aux2'
 Sun Sep  1 20:59:41 2013: Connecting 'system:capture_12' to 'PulseAudio JACK Source:aux3'
 [COLOR=#9999cc]20:59:43.698 JACK connection change.[/COLOR]
 [COLOR=#999933]20:59:43.703 Server configuration saved to "/home/lou/.jackdrc".[/COLOR]
 [COLOR=#999999]20:59:43.706 Statistics reset.[/COLOR]
 [COLOR=#999999]20:59:43.714 Client activated.[/COLOR]
 [COLOR=#cc9966]20:59:43.727 JACK connection graph change.[/COLOR]
 Sun Sep  1 20:59:43 2013: Saving settings to "/home/lou/.config/jack/conf.xml" ...
 Sun Sep  1 20:59:43 2013: New client 'qjackctl' with PID 3095
 [COLOR=#cc66cc]20:59:49.237 XRUN callback (1).[/COLOR]
 [COLOR=#cc66cc]21:00:05.229 XRUN callback (2).[/COLOR]

---

### Post by louh2 on 2013-09-04
Seems I have fixed this by setting input and output channels to default.

---

