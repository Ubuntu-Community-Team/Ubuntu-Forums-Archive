---
title: "Jack ignores MobilePre, just keeps using onboard sound"
date: 2013-11-12
forum: Ubuntu Studio
---

### Post by linuxmart on 2013-11-12
Hello there,
I recently installed Ubuntu Studio 13.10 and want to connect an electric guitar to an M-Audio MobilePre, use Jack to send the sound to Rakarrack and from there back to the MobilePre.

I had it working once, after a lot of playing around with settings, but it wasn't easy to get it to work. Today, I wanted to do the same thing again, but can't get it to work.

I select (from the side arrow) the MobilePre (hw:MobilePre) as Interface in QjackCtl, also tried hw:2, restart Jack, but no change, Jack keep using the onboard mic and speaker as input and output.

cat /proc/asound/cards
```
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf2300000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf2210000 irq 19
 2 [MobilePre      ]: USB-Audio - MobilePre
                      M-Audio MobilePre at usb-0000:00:12.0-1, full speed
```

lsmod | grep snd
```
snd_usb_audio         149162  2
```

Is there anything I am doing wrong?

---

### Post by jejeman on 2013-11-12
Give
```
arecord -l
```

---

### Post by linuxmart on 2013-11-12
This is what I have:

arecord -l && aplay -l
```
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: MobilePre [MobilePre], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: MobilePre [MobilePre], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I also tried **hw:MobilePre,0** with the same results, Jack only uses onbaord sound.

This is Jack's message. As far as I can tell, the "failed" message is a minor UI problem and not related to the sound:
```
13:01:21.879 Patchbay deactivated.
13:01:21.880 Statistics reset.
13:01:21.908 ALSA connection change.
13:01:21.920 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
13:01:21.980 JACK connection change.
13:01:21.992 Client activated.
(qjackctl:2761): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2761): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2761): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2761): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
```

---

### Post by jejeman on 2013-11-12
Now tell me, does JACK won't start when you select hw2 or what?
Give
```
cat .jackdrc
```

---

### Post by linuxmart on 2013-11-12
> **jejeman said:**
> Now tell me, does JACK won't start when you select hw2 or what?
Give
```
cat .jackdrc
```

I thought it had been running, but now I find out it does. When I open Rakarrack first, then it looks like it runs, but it just uses the onboard sound, but now when it start QjackCtl first, I get this:
```
18:10:35.116 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:1873): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:1873): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
Tue Nov 12 18:10:34 2013: Starting jack server...
Tue Nov 12 18:10:34 2013: JACK server starting in realtime mode with priority 10
Tue Nov 12 18:10:35 2013: Acquired audio card Audio2
Tue Nov 12 18:10:35 2013: creating alsa driver ... hw:MobilePre|hw:MobilePre|16|2|22050|0|0|nomon|swmeter|-|32bit
Tue Nov 12 18:10:35 2013: configuring for 22050Hz, period = 16 frames (0.7 ms), buffer = 2 periods
Tue Nov 12 18:10:35 2013: ALSA: final selected sample format for capture: 24bit little-endian
Tue Nov 12 18:10:35 2013: ERROR: ALSA: cannot set period size to 16 frames for capture
Tue Nov 12 18:10:35 2013: ERROR: ALSA: cannot configure capture channel
Tue Nov 12 18:10:35 2013: ERROR: Cannot initialize driver
Tue Nov 12 18:10:35 2013: ERROR: JackServer::Open failed with -1
Tue Nov 12 18:10:35 2013: ERROR: Failed to open server
Tue Nov 12 18:10:36 2013: Saving settings to "/home/myname/.config/jack/conf.xml" ...
(qjackctl:1873): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:1873): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
18:11:50.120 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

I then "quit" QjackCtl and start it again, and this is what I get:
```
18:13:00.887 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:1907): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:1907): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
Tue Nov 12 18:13:00 2013: Starting jack server...
Tue Nov 12 18:13:00 2013: JACK server starting in realtime mode with priority 10
Tue Nov 12 18:13:00 2013: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio2": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio2
Tue Nov 12 18:13:00 2013: ERROR: Failed to acquire device name : Audio2 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio2
Tue Nov 12 18:13:00 2013: ERROR: Audio device hw:MobilePre cannot be acquired...
Tue Nov 12 18:13:00 2013: ERROR: Cannot initialize driver
Tue Nov 12 18:13:00 2013: ERROR: JackServer::Open failed with -1
Tue Nov 12 18:13:00 2013: ERROR: Failed to open server
Tue Nov 12 18:13:02 2013: Saving settings to "/home/myname/.config/jack/conf.xml" ...
18:13:08.407 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

---

### Post by linuxmart on 2013-11-12
Got it to work. I set the Frames/Period to 512. That did the trick.

---

### Post by mauro80m on 2013-11-24
Can you help me?
my cat .jackdrc

Code:
> cat .jackdrc
/usr/bin/jackd -P10 -dalsa -r48000 -p64 -n3 -H -M -D -Chw:MobilePre -Phw:MobilePre,0 -zr

---

### Post by jejeman on 2013-11-25
As linuxmart said
> I set the Frames/Period to 512. That did the trick. 
Your setting is to low (64), raise it to 512.

---

