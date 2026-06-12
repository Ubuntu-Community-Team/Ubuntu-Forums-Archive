---
title: "Ubuntu 19.04 dev: A severe GObject/GType error and crash"
date: 2019-02-12
forum: Ubuntu Development Version
---

### Post by moma on 2019-02-12
Hello,
I am trying to make Audio-recorder to compile and run under Ubuntu 19.04 (Ubuntu Disco Dingo - development branch).

I have encountered a fatal GObject or GType error that crashes the application during runtime. 

**1)**  The crash occurs in all gtk_button_set_image(...) calls during runtime of audio-recorder. 
gtk_button_set_image(GTK_BUTTON(g_win.recorder_button), GTK_WIDGET(image));

The crash message is:

```
(audio-recorder:32368): GLib-GObject-WARNING **: 19:21:52.600: ../../../gobject/gtype.c:4265: type id '0' is invalid

(audio-recorder:32368): GLib-GObject-WARNING **: 19:21:52.600: can't peek value table for type '<invalid>' which is not currently referenced
Segmentation fault (core dumped)
```
----

**2)** The crash also occurs if I run a Gstreamer pipleline on the command line (in a terminal window). Like this.

```
$ gst-launch-1.0  -e pulsesrc ! queue ! audioresample ! audioconvert ! audio/x-raw,rate=44100,channels=2 ! lamemp3enc name=enc target=0 quality=2 ! filesink location=test1.mp3

Setting pipeline to PAUSED ...
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstPulseSrcClock

(gst-launch-1.0:5488): GLib-GObject-WARNING **: 19:23:25.585: ../../../gobject/gtype.c:4265: type id '0' is invalid

(gst-launch-1.0:5488): GLib-GObject-WARNING **: 19:23:25.585: can't peek value table for type '<invalid>' which is not currently referenced
Caught SIGSEGV
Spinning.  Please run 'gdb gst-launch-1.0 5488' to continue debugging, Ctrl-C to quit, or Ctrl-\ to dump core.
```
------

Please educate me if you want more debug info or stacktrace.

My system is:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Disco Dingo (development branch)
Release:	19.04
Codename: disco
```

My system has latest updates.

Any comments?
Kindly
 Osmo (moma) Antero
---------------

EDIT: This bug report is similar
[https://gitlab.freedesktop.org/gstreamer/gst-plugins-good/issues/552](https://gitlab.freedesktop.org/gstreamer/gst-plugins-good/issues/552)

---

### Post by dino99 on 2019-02-13
Missing a dependency or a version conflict ?

---

### Post by moma on 2019-02-13
Re-hi,
This bug was fixed in the package gst-plugins-good1.0 - 1.15.1-1ubuntu2.
Please see:
--> [https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good1.0/+bug/1815670](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good1.0/+bug/1815670)

EDIT:  The gtk_button_set_image() seems to be a side effect.
I cannot re-produce it now.  
I created a basic GTK-program with the gtk_button_set_image() calls and it runs fine & ok.  No problems.

// moma

---

### Post by dino99 on 2019-02-13
yes indeed, so set that thread as 'solved' please

---

