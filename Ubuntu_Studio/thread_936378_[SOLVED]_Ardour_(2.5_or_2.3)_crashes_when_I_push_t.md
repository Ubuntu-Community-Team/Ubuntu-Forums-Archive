---
title: "[SOLVED] Ardour (2.5 or 2.3) crashes when I push the &amp;quot;stop&amp;quot; while recording"
date: 2008-10-02
forum: Ubuntu Studio
---

### Post by DARKAD on 2008-10-02
I start to record an audio-track with a mic plugged in my firewire soundcard and I can see the track being recorded and the audio-line-spectrum becomes more fat when I shout... so when I push the "stop" button ardour closes itself automatically and I loose everything.
This is the 5° track of a 3 minutes song.
Sometimes it generates an xrun and sometimes not.

If I try to record a track on a new session / song everything goes well.

Could you please give me any suggestion?

p.s. If I toggle the real-time option on jack it's the same thing.

****** Details ********

Ubuntu studio with 2.6.24-19-rt and 600MB in limits.conf and qjackctl that calls /usr/bin/jackd -R -P60 -t1000 -dfreebob -r44100 -p256 -n3 -D, 1Gb Ram.

I have only one external firewire audiocard running with freebob.

*******************************

Here it&#8217;s my ardour.rc file:
(Ardour)
(MIDI-port tag=&#8221;control&#8221; device=&#8221;ardour&#8221; mode=&#8221;duplex&#8221; type=&#8221;alsa/sequencer&#8221;/)
(MIDI-port tag=&#8221;mcu&#8221; device=&#8221;ardour&#8221; mode=&#8221;duplex&#8221; type=&#8221;alsa/sequencer&#8221;/)
(MIDI-port tag=&#8221;seq&#8221; device=&#8221;ardour&#8221; mode=&#8221;duplex&#8221; type=&#8221;alsa/sequencer&#8221;/)
&#8722;
(Config)
(Option name=&#8221;trace-midi-input&#8221; value=&#8221;0&#8221;/)
(Option name=&#8221;trace-midi-output&#8221; value=&#8221;0&#8221;/)
(Option name=&#8221;use-tranzport&#8221; value=&#8221;0&#8221;/)
(Option name=&#8221;minimum-disk-io-bytes&#8221; value=&#8221;262144&#8221;/)
(Option name=&#8221;track-buffer-seconds&#8221; value=&#8221;5&#8221;/)
(Option name=&#8221;disk-choice-space-threshold&#8221; value=&#8221;57600000&#8221;/)
(Option name=&#8221;xfade-model&#8221; value=&#8221;0&#8221;/)
(Option name=&#8221;auto-xfade&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;destructive-xfade-msecs&#8221; value=&#8221;20&#8221;/)
(Option name=&#8221;mute-affects-pre-fader&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;mute-affects-post-fader&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;mute-affects-control-outs&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;mute-affects-main-outs&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;plugins-stop-with-transport&#8221; value=&#8221;0&#8221;/)
(Option name=&#8221;stop-recording-on-xrun&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;create-xrun-marker&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;stop-at-session-end&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;quieten-at-speed&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;show-track-meters&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;jack-time-master&#8221; value=&#8221;0&#8221;/)
(Option name=&#8221;smpte-format&#8221; value=&#8221;6&#8221;/)
(Option name=&#8221;timecode-source-is-synced&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;no-new-session-dialog&#8221; value=&#8221;0&#8221;/)
(Option name=&#8221;use-vst&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;periodic-safety-backups&#8221; value=&#8221;1&#8221;/)
(Option name=&#8221;periodic-safety-backup-interval&#8221; value=&#8221;120&#8221;/)
(Option name=&#8221;default-narrow_ms&#8221; value=&#8221;0&#8221;/)
(Option name=&#8221;font-scale&#8221; value=&#8221;102400&#8221;/)
(/Config)
&#8722;
(extra)
(RulerVisibility smpte=&#8221;yes&#8221; bbt=&#8221;yes&#8221; frames=&#8221;no&#8221; minsec=&#8221;no&#8221; tempo=&#8221;yes&#8221; meter=&#8221;yes&#8221; marker=&#8221;yes&#8221; rangemarker=&#8221;no&#8221; transportmarker=&#8221;yes&#8221; cdmarker=&#8221;no&#8221;/)
(Keyboard edit-button=&#8221;3&#8221; edit-modifier=&#8221;4&#8221; delete-button=&#8221;3&#8221; delete-modifier=&#8221;1&#8221; snap-modifier=&#8221;32&#8221;/)
(TransportControllables roll=&#8221;0&#8221; stop=&#8221;1&#8221; goto_start=&#8221;2&#8221; goto_end=&#8221;3&#8221; auto_loop=&#8221;4&#8221; play_selection=&#8221;5&#8221; rec=&#8221;6&#8221; shuttle=&#8221;7&#8221;/)
(/extra)
&#8722;
(ControlProtocols)
(Protocol name=&#8221;Generic MIDI&#8221; active=&#8221;no&#8221;/)
(Protocol name=&#8221;Mackie&#8221; active=&#8221;no&#8221;/)
(/ControlProtocols)
(/Ardour)

**************************

Here it is how I run ardour:
/usr/bin/ardour2
&#8230;
Ardour/GTK 2.5
(built using 3525 and GCC version 4.2.3 (Ubuntu 4.2.3-2ubuntu7))
&#8230;
loading default ui configuration file /etc/ardour2/ardour2_ui_default.conf
loading user ui configuration file /home/darkad/.ardour2/ardour2_ui.conf
Loading ui configuration file /etc/ardour2/ardour2_ui_dark.rc
theme_init() called from internal clearlooks engine
ardour: [INFO]: Ardour will be limited to 1024 open files
loading system configuration file /etc/ardour2/ardour_system.rc
loading user configuration file /home/darkad/.ardour2/ardour.rc
ardour: [INFO]: No H/W specific optimizations in use
ardour: [INFO]: looking for control protocols in /home/darkad/.ardour2/surfaces/:/usr/lib/ardour2/surfaces/
ardour: [INFO]: Control surface protocol discovered: &#8220;Generic MIDI&#8221;
ardour: [INFO]: Control surface protocol discovered: &#8220;Mackie&#8221;
powermate: Opening of powermate failed - No such file or directory
ardour: [INFO]: Control protocol powermate not usable
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property &#8216;GtkWidget::cursor-color&#8217; of type &#8216;GdkColor&#8217; from rc file value &#8220;((GString*) 0x8bdbb30)&#8221; of type &#8216;GString&#8217;
loading bindings from /home/darkad/.ardour2/ardour.bindings
Loading session /home/darkad/art/registrazioni/prison/prison using snapshot prison (1)
Loading history from &#8217;/home/darkad/art/registrazioni/prison/prison/prison.history&#8217;.
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property &#8216;GtkWidget::cursor-color&#8217; of type &#8216;GdkColor&#8217; from rc file value &#8220;((GString*) 0x9194310)&#8221; of type &#8216;GString&#8217;

*************************

here it is a log window that i see when i run ardour:

[error] no devices found for driver alsa.

---

### Post by DARKAD on 2008-10-05
I solved exporting the tracks in a new session and now it works.

---

