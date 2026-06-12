---
title: "Controlling ALSA volume with ALSA+JACK+PA"
date: 2011-07-10
forum: Ubuntu Studio
---

### Post by bezeek on 2011-07-10
Under the 'Studio variant of Natty, I've configured JACK to squeeze its way in between PulseAudio and ALSA very nicely. QJACKCtl is configured with the following "Scripting" options so that launching or exiting JACK is nearly seamless:

Execute on startup > pacmd suspend true
Execute after startup > pactl load-module module-jack-sink channels=2; pactl load-module module-jack-source channels=2; pacmd set-default-sink jack_out; pacmd set-default-source jack_in
Execute on shutdown > pactl unload-module `pactl list | grep -B 1 "Name: module-jack-sink" | grep Module | sed 's/[^0-9]//g'`; pactl unload-module `pactl list | grep -B 1 "Name: module-jack-source" | grep Module | sed 's/[^0-9]//g'`; sleep 5
Execute after shutdown > pacmd suspend false

(I would love to credit the individual who came up with this method of integration, however I've long lost the source...)

My problem is that I am forced to adjust the volume through PulseAudio, although the situation clearly calls for control at the lowest level, ALSA. For example, many applications will connect to PulseAudio by default, via. GStreamer. Performance-critical applications will use JACK, and some legacy applications will route to ALSA directly. All should coexist peacefully.

Logically, the master volume should control the overall output levels. Instead, the indicator applet, the XF86Audio--- shortcuts, and the volume control applet provided by Avant Window Navigator are all locked to PulseAudio, leaving me to launch alsamixer in a terminal when I want to adjust my master volume.

The indicator applet has no preferences in which to select the control device. As far as I know, the XF86Audio--- shortcuts are not configurable to different devices either. Finally, the AWN applet preferences offer a drop-down of available devices, but the only one that appears is the PulseAudio JACK sink.

(It may be worth mentioning that until tonight, AWN was content in adjusting the volume of ALSA, because AWN loads before QJACKCtl in my configuration. But, as of tonight, it is attaching to a "dummy" output instead of ALSA. If I reload AWN after QJACKCtl, it attaches to JACK. Regardless, the indicator applet and XF86Audio--- shortcuts have always affected the highest level virtual output.)

So, is there some way I can fix UbuntuStudio to treat the lowest level physical output as the master device, as opposed to the highest level virtual output? I love having such a flexible audio stack, but absolutely hate using standalone programs to control my output levels.

A million thanks go out to anyone who can help me with this problem, and also a million thanks to anyone who can at least offer some stimulating input!

- Brian

====
Edit: After a restart I was able to select the ALSA device in AWN's volume control applet, however I still cannot choose which device to control with the XF86Audio--- shortcuts or in the indicator-sound Gnome applet. I assume the device selection in these cases is tied into the system-wide default output device, but I don't want to change my default output device.

So, does anyone know of a way I can trick this thing into controlling ALSA's master volume without setting my default output device to ALSA?

====
Edit 2: According to the Ubuntu Wiki page on [Primary Sound Output]("https://wiki.ubuntu.com/PrimarySoundOutput"), the system defaults to PulseAudio to control the volume by default. At this point, I doubt I can change this behavior, but is this behavior really necessary? As I pointed out, the "master" volume would generally be the point where the final signal is leaving the chain. If anyone's interested, I brought this up over at [Launchpad]("https://answers.launchpad.net/ubuntu/+question/164965").

---

