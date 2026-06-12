---
title: "Seventh String Transcribe Error"
date: 2012-05-09
forum: Ubuntu Studio
---

### Post by Paul41 on 2012-05-09
Ever since installing Ubuntu Studio 12.04 I get the following error when I open Transcribe: 
> Cannot open sound output device.
gconfaudiosink
GStreamer cannot output audio for playback (Error T:2142)
Transcribe will then open but won't play anything.  Transcribe worked fine on this computer before installing Ubuntu studio, it worked with both Ubuntu and Linux Mint.  Any ideas what could be happening?

---

### Post by djme on 2012-05-24
Hi Paul41,
Try going to file-preferences-playback and in gstreamerdevice name type "alsasink" (or see below for other options).
Under Ubuntu I had to use alsasink but for Lubuntu I have to use autoaudiosink for transcribe to work.
Thanks,
Djme.

From the Transcribe Help File:
GStreamer device name
Transcribe! uses GStreamer for sound output. GStreamer has many plugins for outputting sound with names like pulsesink (if your distro uses the Pulse sound server) or alsasink (if your distro uses ALSA), etc etc. The default here is gconfaudiosink which means to use the sound output configured in Gnome but obviously you can change it. You specify the plugin name here, and you can optionally specify additional parameters so you could write e.g. "alsasink device=hw:1". See GStreamer documentation for more about this. Naturally if you are using the default gconfaudiosink here, then this means that you would use your main system preferences to select between different sound output devices if you have more than one.
If you install the gstreamer-tools package then you can use various useful command line tools.
**The following command in a console will discover what audio sink GST plugins are installed on your system, though this doesn't mean they can all be used to output sound successfully:**
  ** gst-inspect | grep -i sink | grep -i audio**
Finds: **gconfaudiosink, oss4sink, jackaudiosink, alsasink, pulsesink, ....**
And having discovered that you have e.g. jackaudiosink, you can
   gst-inspect jackaudiosink
to find what properties the source has. E.g. alsasink has a "device" property, so we can write "device=hw:1" for instance.
And to test any sink, try this on a console:
   gst-launch -v audiotestsrc ! audioconvert ! gconfaudiosink

---

