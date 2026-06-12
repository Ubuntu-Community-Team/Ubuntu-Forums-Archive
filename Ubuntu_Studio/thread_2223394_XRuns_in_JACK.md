---
title: "XRuns in JACK"
date: 2014-05-10
forum: Ubuntu Studio
---

### Post by RideTheSpiral on 2014-05-10
I'm having trouble figuring out how to run JACK with a low enough latency that I can monitor / use effects in JACK Rack. I'm really confused as to why I'm getting XRuns because my hardware is quite capable (I think...)

The USB interface I'm using is an RME Babyface in class compliant mode. My laptop is a Lenovo Y560 that is 3 years old. CPU is a Nehalem core i5 (2.53GHz boost). I have Ubuntu studio installed on a 32GB SSD with a 500GB HDD for /home. It has 4GB of ram. 

When using 192khz, I cannot get clean output, it sounds absolutely terrible, distorted, and tiny. Really buzzy and glitchy sounding. I'm currently running jack with the -S command, cpu governor set to performance, 256 frames a period, 96khz sample rate, 3 periods a buffer. I get clean sound through this and can run effects with 8ms latency. Every 30 - 60 seconds of playing I'll get a quick crackle, but sometimes it glitches out for few seconds and sounds terrible. 

I'm not sure what I can post here to help but here's my JACK message log when I've had JACK running for about 20 minutes.

```

[COLOR=#999999]16:47:31.754 Patchbay deactivated.[/COLOR]
[COLOR=#999999]16:47:31.761 Statistics reset.[/COLOR]
[COLOR=#cccc99]16:47:31.786 ALSA connection change.[/COLOR]
[COLOR=#999999]16:47:31.812 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
[COLOR=#999999]16:47:35.434 D-BUS: JACK server is starting...[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
[COLOR=#999999]16:47:35.453 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
Sat May 10 16:47:35 2014: Starting jack server...
Sat May 10 16:47:35 2014: JACK server starting in realtime mode with priority 70
Sat May 10 16:47:35 2014: Acquired audio card Audio1
Sat May 10 16:47:35 2014: creating alsa driver ... hw:Babyface2362742,0|hw:Babyface2362742,0|256|3|96000|0|0|nomon|swmeter|-|32bit
Sat May 10 16:47:35 2014: configuring for 96000Hz, period = 256 frames (2.7 ms), buffer = 3 periods
Sat May 10 16:47:35 2014: ALSA: final selected sample format for capture: 32bit integer little-endian
Sat May 10 16:47:35 2014: ALSA: use 3 periods for capture
Sat May 10 16:47:35 2014: ALSA: final selected sample format for playback: 32bit integer little-endian
Sat May 10 16:47:35 2014: ALSA: use 3 periods for playback
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_1'
Sat May 10 16:47:35 2014: New client 'system' with PID 0
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_2'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_3'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_4'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_5'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_6'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_7'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_8'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_9'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:capture_10'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_1'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_2'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_3'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_4'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_5'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_6'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_7'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_8'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_9'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_10'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_11'
Sat May 10 16:47:35 2014: graph reorder: new port 'system:playback_12'
Sat May 10 16:47:35 2014: New client 'PulseAudio JACK Sink' with PID 1550
Sat May 10 16:47:35 2014: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
Sat May 10 16:47:35 2014: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
Sat May 10 16:47:35 2014: New client 'PulseAudio JACK Source' with PID 1550
Sat May 10 16:47:35 2014: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
Sat May 10 16:47:35 2014: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
Sat May 10 16:47:36 2014: Saving settings to "/home/justin/.config/jack/conf.xml" ...
[COLOR=#9999cc]16:47:37.682 JACK connection change.[/COLOR]
[COLOR=#999933]16:47:37.683 Server configuration saved to "/home/justin/.jackdrc".[/COLOR]
[COLOR=#999999]16:47:37.683 Statistics reset.[/COLOR]
[COLOR=#999999]16:47:37.687 Client activated.[/COLOR]
[COLOR=#cc9966]16:47:37.689 JACK connection graph change.[/COLOR]
Sat May 10 16:47:37 2014: New client 'qjackctl' with PID 8004
[COLOR=#cc66cc]16:47:40.815 XRUN callback (1).[/COLOR]
Sat May 10 16:47:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:47:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:47:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:47:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:47:41.694 XRUN callback (6 skipped).[/COLOR]
Sat May 10 16:47:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:47:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:47:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:47:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:47:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:47:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:47:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:47:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:47:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:47:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:47:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:47:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:47:43.697 XRUN callback (9 skipped).[/COLOR]
Sat May 10 16:47:43 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Sink finished after current callback
Sat May 10 16:47:43 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:47:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc9966]16:47:51.904 JACK connection graph change.[/COLOR]
Sat May 10 16:47:51 2014: New client 'jack_rack' with PID 8024
[COLOR=#66cc99]16:47:51.941 ALSA connection graph change.[/COLOR]
[COLOR=#9999cc]16:47:52.106 JACK connection change.[/COLOR]
[COLOR=#cccc99]16:47:52.108 ALSA connection change.[/COLOR]
[COLOR=#9999cc]16:47:59.431 JACK connection change.[/COLOR]
Sat May 10 16:47:59 2014: Connecting 'system:capture_2' to 'jack_rack:in_2'
[COLOR=#9999cc]16:48:01.179 JACK connection change.[/COLOR]
Sat May 10 16:48:01 2014: Connecting 'system:capture_2' to 'jack_rack:in_1'
[COLOR=#9999cc]16:48:10.295 JACK connection change.[/COLOR]
Sat May 10 16:48:10 2014: Connecting 'jack_rack:out_1' to 'system:playback_1'
[COLOR=#9999cc]16:48:13.685 JACK connection change.[/COLOR]
Sat May 10 16:48:13 2014: Connecting 'jack_rack:out_2' to 'system:playback_2'
[COLOR=#cc66cc]16:49:40.822 XRUN callback (18).[/COLOR]
[COLOR=#cc99cc]16:49:41.819 XRUN callback (6 skipped).[/COLOR]
Sat May 10 16:49:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:49:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:49:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 16:49:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:49:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:49:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:49:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:49:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:49:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:49:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:49:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:49:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:49:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:49:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:49:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:49:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:49:43.821 XRUN callback (9 skipped).[/COLOR]
Sat May 10 16:49:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:49:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 16:49:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:49:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:49:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 16:49:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc66cc]16:51:40.825 XRUN callback (35).[/COLOR]
Sat May 10 16:51:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:51:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:51:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:51:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:51:41.888 XRUN callback (5 skipped).[/COLOR]
Sat May 10 16:51:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:51:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:51:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:51:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:51:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:51:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:51:43.890 XRUN callback (6 skipped).[/COLOR]
Sat May 10 16:51:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:51:43 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:51:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 16:51:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc66cc]16:53:40.814 XRUN callback (48).[/COLOR]
Sat May 10 16:53:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:53:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:53:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:53:41.951 XRUN callback (6 skipped).[/COLOR]
Sat May 10 16:53:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Sink finished after current callback
Sat May 10 16:53:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:53:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 16:53:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:53:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:53:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:53:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:53:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:53:43.953 XRUN callback (4 skipped).[/COLOR]
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
[COLOR=#cc66cc]16:55:40.813 XRUN callback (60).[/COLOR]
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:55:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:55:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:55:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Sink finished after current callback
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:55:40 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 16:55:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:55:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:55:41 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:55:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:55:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:55:41 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:55:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:55:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:55:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 16:55:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:55:42.081 XRUN callback (35 skipped).[/COLOR]
Sat May 10 16:55:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:55:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:55:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:55:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 16:55:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:55:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 16:55:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:55:44.084 XRUN callback (5 skipped).[/COLOR]
[COLOR=#cc66cc]16:57:40.820 XRUN callback (102).[/COLOR]
Sat May 10 16:57:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:57:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:57:41 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:57:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:57:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:57:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:57:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 16:57:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:57:42.158 XRUN callback (15 skipped).[/COLOR]
Sat May 10 16:57:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:57:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:57:42 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:57:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:57:43 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Sink finished after current callback
Sat May 10 16:57:43 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:57:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:57:43 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Sink finished after current callback
Sat May 10 16:57:43 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:57:43 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
[COLOR=#cc99cc]16:57:44.160 XRUN callback (36 skipped).[/COLOR]
[COLOR=#cc66cc]16:59:40.820 XRUN callback (155).[/COLOR]
Sat May 10 16:59:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:59:40 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:59:40 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 16:59:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:59:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:59:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 16:59:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:59:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:59:41 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:59:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:59:42.262 XRUN callback (17 skipped).[/COLOR]
Sat May 10 16:59:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:59:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:59:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:59:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:59:42 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:59:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Sink finished after current callback
Sat May 10 16:59:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:59:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 16:59:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 16:59:43 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 16:59:43 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 16:59:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:59:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 16:59:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 16:59:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]16:59:44.264 XRUN callback (14 skipped).[/COLOR]
[COLOR=#cc66cc]17:01:40.823 XRUN callback (188).[/COLOR]
Sat May 10 17:01:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Sink finished after current callback
Sat May 10 17:01:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:01:41 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 17:01:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:01:42.346 XRUN callback (13 skipped).[/COLOR]
Sat May 10 17:01:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 17:01:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:01:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 17:01:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:01:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 17:01:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:01:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 17:01:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:01:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 17:01:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:01:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:01:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 17:01:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:01:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:01:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 17:01:43 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:01:43 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 17:01:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:01:44.347 XRUN callback (9 skipped).[/COLOR]
[COLOR=#cc66cc]17:03:40.812 XRUN callback (212).[/COLOR]
Sat May 10 17:03:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:03:40 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:03:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:03:40 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:03:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:40 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:03:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:40 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:03:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 17:03:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 17:03:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Sink finished after current callback
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 17:03:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:03:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 17:03:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:03:42.431 XRUN callback (19 skipped).[/COLOR]
Sat May 10 17:03:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:03:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:03:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 17:03:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:03:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 17:03:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 17:03:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:03:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 17:03:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:03:43 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 17:03:43 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:03:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 17:03:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:03:44.433 XRUN callback (9 skipped).[/COLOR]
[COLOR=#cc66cc]17:05:40.813 XRUN callback (242).[/COLOR]
Sat May 10 17:05:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 17:05:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:05:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:05:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Triggered
Sat May 10 17:05:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:05:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:05:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:05:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:05:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:05:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:05:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:05:42.514 XRUN callback (9 skipped).[/COLOR]
Sat May 10 17:05:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 17:05:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Running
Sat May 10 17:05:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 17:05:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:05:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:05:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:05:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:05:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:05:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:05:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:05:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:05:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:05:44.516 XRUN callback (7 skipped).[/COLOR]
[COLOR=#cc66cc]17:07:40.822 XRUN callback (260).[/COLOR]
Sat May 10 17:07:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:07:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:07:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:07:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:07:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:07:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:07:42.596 XRUN callback (8 skipped).[/COLOR]
Sat May 10 17:07:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:07:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:07:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:07:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:07:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:07:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:07:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:07:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:07:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:07:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:07:44.598 XRUN callback (3 skipped).[/COLOR]
[COLOR=#cc66cc]17:09:40.814 XRUN callback (273).[/COLOR]
Sat May 10 17:09:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:09:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:09:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:09:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:09:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:09:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:09:42.682 XRUN callback (8 skipped).[/COLOR]
Sat May 10 17:09:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:09:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:09:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:42 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not finished, state = Running
Sat May 10 17:09:42 2014: ERROR: JackEngine::XRun: client jack_rack finished after current callback
Sat May 10 17:09:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Sink finished after current callback
Sat May 10 17:09:42 2014: ERROR: JackEngine::XRun: client PulseAudio JACK Source finished after current callback
Sat May 10 17:09:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Running
Sat May 10 17:09:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:09:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:09:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:09:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:09:44.684 XRUN callback (7 skipped).[/COLOR]
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
[COLOR=#cc66cc]17:11:40.814 XRUN callback (290).[/COLOR]
[COLOR=#cc99cc]17:11:40.822 XRUN callback (1 skipped).[/COLOR]
Sat May 10 17:11:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:11:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:40 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:11:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:40 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:40 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:40 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:11:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:41 2014: ERROR: JackEngine::XRun: client = PulseAudio JACK Source was not finished, state = Triggered
Sat May 10 17:11:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:41 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:41 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:11:42.824 XRUN callback (9 skipped).[/COLOR]
Sat May 10 17:11:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:42 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:42 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
Sat May 10 17:11:43 2014: ERROR: JackEngine::XRun: client = jack_rack was not finished, state = Triggered
Sat May 10 17:11:43 2014: ERROR: JackAudioDriver::ProcessGraphAsyncMaster: Process error
[COLOR=#cc99cc]17:11:44.825 XRUN callback (2 skipped).[/COLOR]
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:8004): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
```

---

### Post by jejeman on 2014-05-11
First try to turn off wireless, on the driver level if necessary, best way by hardware switch.

If that is not enough, disable pulseaudio.

---

### Post by RideTheSpiral on 2014-05-11
I've been using 44khz / 128 frames / 3 periods for ~8ms latency to see if it was the sampling rate. The xruns slowed down but didn't stop. I turned wifi off with the hardware switch, restarted my laptop and opened up jack + jackrack and a reverb / tube amp. Let it sit for a good 5 minutes and at 13% cpu usage there were no xruns. Switched wifi back on and the xruns started pouring in.

Shouldn't setting "nice" to -19 have helped solve that problem? Anyway it's good that I'm making some progress. I'm going to do a bunch more testing once I do a fresh install of 14.04

Edit: Yup it has to be the wifi. 96khz/256 frames/3 periods @ 8ms latency has no xruns after disabling wifi and restarting. That's a shame that I have to have wifi disabled, but at least I'm getting somewhere.

---

### Post by jejeman on 2014-05-13
It is known that wifi interferes with RT operations. That is "normal".
Use the cable.

---

