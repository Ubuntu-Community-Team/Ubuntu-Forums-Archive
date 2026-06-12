---
title: "Amarok is not working  for few days in 14.04  GLib error"
date: 2014-04-01
forum: Ubuntu Development Version
---

### Post by su:bhatta on 2014-04-01
For a few days Amarok is not working. On opening from Menu it doesn't appear and this is the output when opened from Terminal:

```
~$ amarok
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.

(amarok:10927): GLib-GObject-WARNING **: cannot register existing type 'GstObject'

(amarok:10927): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

(amarok:10927): GLib-GObject-CRITICAL **: g_type_register_static: assertion 'parent_type > 0' failed

(amarok:10927): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

(amarok:10927): GStreamer-CRITICAL **: gst_plugin_feature_get_name: assertion 'GST_IS_PLUGIN_FEATURE (feature)' failed

```

Any help appreciated.

---

### Post by su:bhatta on 2014-04-02
found this:[http://forum.kde.org/viewtopic.php?f=115&t=110691](http://forum.kde.org/viewtopic.php?f=115&t=110691)

gonna give it a go.

---

### Post by su:bhatta on 2014-04-02
Well, it seems to be a problem with Phonon same as the kde.org thread. Reinstalling the gstreamer-phonon packages and lets see if that helps.
 
```
~$ amarok -d --nofork
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
amarok: BEGIN: App::App() 
amarok:   BEGIN: void App::continueInit() 
amarok:     BEGIN: EngineController::EngineController() 
amarok:     END__: EngineController::EngineController() [Took: 0.006s] 
amarok:     BEGIN: void EngineController::initializePhonon() 

(amarok:3347): GLib-GObject-WARNING **: cannot register existing type 'GstObject'

(amarok:3347): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

(amarok:3347): GLib-GObject-CRITICAL **: g_type_register_static: assertion 'parent_type > 0' failed

(amarok:3347): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

(amarok:3347): GStreamer-CRITICAL **: gst_plugin_feature_get_name: assertion 'GST_IS_PLUGIN_FEATURE (feature)' failed
```

---

### Post by su:bhatta on 2014-04-02
Resolved as of now using Phonon-backend-vlc

Marking this as Solved.

---

