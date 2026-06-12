---
title: "Lexicon Alpha and Ubuntu Studio"
date: 2014-11-20
forum: Ubuntu Studio
---

### Post by ignazio2 on 2014-11-20
Hi there,
I'm Iggy and I've just bought The Lexicon Alpha USB  Audio Interface. I spent the last two days trying to figure out how to  hear my plugged guitar on my PC, but i failed. The thing I cannot get is  the Alpha showing up on the Jack windows in order to make some  connections input->output.
Here it is my system:
Packard Bell DOT-SE
Ubuntu Studio 14.04.1 Tusty Tahr LTS 

The system recognize the device, here it is in fact the output of 
/proc/asound/cards
arecord -l && aplay -l

[INDENT]diocanissimo@diocanissimo-DOT-SE:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x58200000 irq 44
 1 [Alpha          ]: USB-Audio - Lexicon Alpha
                      Lexicon Lexicon Alpha at usb-0000:00:1d.0-1, full speed
diocanissimo@diocanissimo-DOT-SE:~$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Alpha [Lexicon Alpha], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Alpha [Lexicon Alpha], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

[/INDENT]

In Jack Setup, everytime I select Alpha as Input Device, the Jack server cannot be started.
[INDENT]21:30:32.487 Patchbay deactivated.
21:30:32.618 Statistics reset.
21:30:32.897 ALSA connection change.
21:30:32.965 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:2601): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2601): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
21:31:04.162 D-BUS: JACK server could not be started. Sorry
Thu Nov 20 21:30:39 2014: Starting jack server...
Thu Nov 20 21:30:39 2014: JACK server starting in realtime mode with priority 10
Thu Nov 20 21:30:39 2014: Acquired audio card Audio1
Thu Nov 20 21:30:39 2014: Acquired audio card Audio0
Thu Nov 20 21:30:39 2014: creating alsa driver ... hw:0|hw:Alpha|256|2|44100|0|0|nomon|swmeter|-|32bit
Thu Nov 20 21:30:39 2014: configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
Thu Nov 20 21:30:39 2014: ALSA: final selected sample format for capture: 24bit little-endian
Thu Nov 20 21:30:39 2014: ALSA: use 2 periods for capture
Thu Nov 20 21:30:39 2014: ALSA: final selected sample format for playback: 32bit integer little-endian
Thu Nov 20 21:30:39 2014: ALSA: use 2 periods for playback
Thu Nov 20 21:31:01 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 20000000 err = Connection timed out
Thu Nov 20 21:31:01 2014: ERROR: JackEngine::ClientActivate wait error ref = 2 name = dbusapi
Thu Nov 20 21:31:01 2014: ERROR: failed to activate dbusapi jack client. error is -1
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:2601): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2601): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
21:31:18.412  Could not connect to JACK server as client. - Overall operation failed.  - Server communication error. Please check the messages window for more  info.
Thu Nov 20 21:31:09 2014: ERROR: CheckSize error size = 32 Size() = 12
Thu Nov 20 21:31:09 2014: ERROR: CheckRead error
Thu Nov 20 21:31:09 2014: ERROR: CheckSize error size = -1 Size() = 4
Thu Nov 20 21:31:09 2014: ERROR: CheckRead error
Thu Nov 20 21:31:09 2014: ERROR: CheckSize error size = 0 Size() = 12
Thu Nov 20 21:31:09 2014: ERROR: CheckRead error
Thu Nov 20 21:31:13 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 4000000 err = Connection timed out
Thu Nov 20 21:31:13 2014: ERROR: JackEngine::ClientCloseAux wait error ref = 2
Cannot read socket fd = 21 err = Success
CheckRes error
JackSocketClientChannel read fail
Cannot open qjackctl client
Thu Nov 20 21:31:18 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
Thu Nov 20 21:31:18 2014: ERROR: Driver is not running
Thu Nov 20 21:31:18 2014: ERROR: Cannot create new client
Thu Nov 20 21:31:18 2014: ERROR: CheckSize error size = 32 Size() = 12
Thu Nov 20 21:31:18 2014: ERROR: CheckRead error
Thu Nov 20 21:31:18 2014: ERROR: CheckSize error size = -1 Size() = 4
Thu Nov 20 21:31:18 2014: ERROR: CheckRead error
Thu Nov 20 21:31:18 2014: ERROR: CheckSize error size = 0 Size() = 12
Thu Nov 20 21:31:18 2014: ERROR: CheckRead error
Thu Nov 20 21:31:19 2014: Released audio card Audio1
Thu Nov 20 21:31:19 2014: Released audio card Audio0
Thu Nov 20 21:31:19 2014: Saving settings to "/home/diocanissimo/.config/jack/conf.xml" ...
[/INDENT]

I'm not a newbye of Ubuntu but I cannot get past this first hurdle.
Any suggestions?
Thanks,
Iggy

---

### Post by CrocoDuck on 2014-11-21
> **ignazio2 said:**
> [INDENT]...diocanissimo@diocanissimo...[/INDENT]


:lolflag:

Well... Your device should work. Can you please repost the output of these commands?

```

cat /proc/asound/devices
cat .jackdrc
groups

```

Have a look at [this]("http://linuxmusicians.com/viewtopic.php?f=6&t=10118").

---

### Post by jejeman on 2014-11-22
Does device work with just ALSA? (It should). First try that.
Use Audacity to playback and record.

---

