---
title: "Live-CD: Jack not working"
date: 2013-05-14
forum: Ubuntu Studio
---

### Post by planktomas on 2013-05-14
Hi,
I've tried UbuntuStudio in my normal environment, 13.04 Gnome, and couldn't start jack. So I tried the Live-CD. There happened the same error:
After "Start" from qjackctl I get the following messages:
```
 [COLOR=#999999]05:48:16.818 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]05:48:16.821 Statistics reset.[/COLOR]
 [COLOR=#cccc99]05:48:16.824 ALSA connection change.[/COLOR]
 [COLOR=#999999]05:48:16.857 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = Connection refused
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]05:48:16.865 ALSA connection graph change.[/COLOR]
 (qjackctl.real:4359): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:4359): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]05:48:58.599 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Tue May 14 05:48:33 2013: Starting jack server...
 Tue May 14 05:48:33 2013: JACK server starting in realtime mode with priority 10
 Tue May 14 05:48:33 2013: Acquired audio card Audio0
 Tue May 14 05:48:33 2013: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Tue May 14 05:48:33 2013: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 Tue May 14 05:48:33 2013: ALSA: final selected sample format for capture: 32bit integer little-endian
 Tue May 14 05:48:33 2013: ALSA: use 2 periods for capture
 Tue May 14 05:48:33 2013: ALSA: final selected sample format for playback: 32bit integer little-endian
 Tue May 14 05:48:33 2013: ALSA: use 2 periods for playback
 Tue May 14 05:48:38 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Tue May 14 05:48:38 2013: [1m[31mERROR: Driver is not running[0m
 Tue May 14 05:48:38 2013: [1m[31mERROR: Cannot open client name = dbusapi[0m
 Tue May 14 05:48:38 2013: [1m[31mERROR: failed to create dbusapi jack client[0m
 Tue May 14 05:48:38 2013: [1m[31mERROR: Unknown request 4294967295[0m
 Tue May 14 05:48:38 2013: [1m[31mERROR: CheckSize error size = 0 Size() = 12[0m
 Tue May 14 05:48:38 2013: [1m[31mERROR: CheckRead error[0m
 Cannot connect to server socket err = Connection refused
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:4359): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:4359): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]05:49:07.679 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 Cannot read socket fd = 23 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 Tue May 14 05:49:07 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
 Tue May 14 05:49:07 2013: [1m[31mERROR: Driver is not running[0m
 Tue May 14 05:49:07 2013: [1m[31mERROR: Cannot create new client[0m
 Tue May 14 05:49:07 2013: [1m[31mERROR: Unknown request 4294967295[0m
 Tue May 14 05:49:07 2013: [1m[31mERROR: CheckSize error size = 0 Size() = 12[0m
 Tue May 14 05:49:07 2013: [1m[31mERROR: CheckRead error[0m


```

Is there a problem with my hardware?

Ciao
Tom

---

### Post by zequence on 2013-05-14
1. Make sure you don't have any application using desktop audio, including any web pages with audio content (like a paused hmlt5 or flash video).

2. Make sure you select the right audio device, if you have more than one (hdmi is also an audio device) before starting jack.

The order of the cards may change at each boot.

---

### Post by planktomas on 2013-05-14
Hi zequenze,
I think the problems is already caused by ALSA. There are no soundcards! I expected that a Live-CD could fix such problems.
[http://www.alsa-project.org/db/?f=013f155ac9c47f6dbbc2c1aa6d378f69fed8111f](http://www.alsa-project.org/db/?f=013f155ac9c47f6dbbc2c1aa6d378f69fed8111f)

Ciao
Tom

---

### Post by Sylos on 2013-05-14
Hello.

The dmesg section of your alsa output suggests some form of bug going on that goes well beyond alsa (and for that matter my knowledge). Have a google and check it out.

Out of interest, what MOBO are you using?

Cheers

---

### Post by planktomas on 2013-05-14
Hi Sylos,
it's H77-D3H.
Ciao
Tom

---

### Post by Sylos on 2013-05-15
If your using a PCIe graphics card perhaps you could try removing it an testing using the onboard GPU (the intel chip). I only suggest this because I had trouble with a gigabyte Z68 board and interference between the my Graphics card and sound card.

Failing that you could try some different kernels. Try installing the latest upstream kernel and see if that fixes the issue.

Cheers

---

