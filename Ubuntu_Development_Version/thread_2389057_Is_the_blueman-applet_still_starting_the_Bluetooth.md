---
title: "Is the blueman-applet still starting the Bluetooth service?"
date: 2018-04-10
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2018-04-10
back in 16.04 or 16.10 i wanted to turn bluetooth off by default, i did so via the file at /etc/bluetooth/main.conf 
but the blueman-applet turns it back on at startup defeating the purpose
i had worked around this using a script:
```
#!/bin/sh bluetooth off
blueman-applet & # This application is disabled in session startup
while [ "$(bluetooth | cut -d' ' -f3)" = "off" ]; do
    sleep 1
done
bluetooth off
```
this stopped working in 17.04 when the bluetooth command demanded root privileges

If someone can check if that applet is still turning bluetooth on i would like to report that as a bug, as it defeats the purpose of there being a way to turn bluetooth off be default
I do understand the reason for it to turn it on, why else would you want to start the applet if you did not need to use bluetooth hardware, but that logic should not apply if the applet is started at login and not manually

---

### Post by flocculant on 2018-04-11
I can't check here - no bluetooth - so all that gets removed in the first apt purge/apt install I do on new installs.

I'd be inclined to report it anyway - not sure whether that would get looked at this close to release.

If it's Xubuntu issues - we can bug fix before release, but bluetooth obviously isn't in that category.

Re it not working since 17.04 - might have been better to report back then - I'd assume it's a regression.

---

### Post by pqwoerituytrueiwoq on 2018-04-11
Made a report:
[https://bugs.launchpad.net/ubuntu/+source/blueman/+bug/1763221](https://bugs.launchpad.net/ubuntu/+source/blueman/+bug/1763221)
I looked into it myself and made a patch

---

### Post by pqwoerituytrueiwoq on 2018-04-13
So I am trying to make a patch that adds a auto-detect feature
I found out when and how this feature was added originally
[https://github.com/blueman-project/blueman/commit/8049a9edeb10a9d2fe6751af2a86a6c2b8c8cee7](https://github.com/blueman-project/blueman/commit/8049a9edeb10a9d2fe6751af2a86a6c2b8c8cee7)
If I had not when into the source code i would have never figured out how the user can change this setting

Anyway i made a new patch, but i am trying to test it but i can not figure out how to make the new dconf setting work, it is like it is impossible to reset and use any changes i make
```
chad@A54C-NB91:~$ diff -Naur /usr/share/glib-2.0/schemas/org.blueman.gschema.xml.orig  /usr/share/glib-2.0/schemas/org.blueman.gschema.xml
--- /usr/share/glib-2.0/schemas/org.blueman.gschema.xml.orig    2018-04-13 21:00:37.741432897 -0400
+++ /usr/share/glib-2.0/schemas/org.blueman.gschema.xml    2018-04-13 21:17:37.840377507 -0400
@@ -131,9 +131,16 @@
     </key>
   </schema>
   <schema id="org.blueman.plugins.powermanager" path="/org/blueman/plugins/powermanager/">
-    <key type="b" name="auto-power-on">
-        <default>true</default>
-        <summary>Automatically power on adapters</summary>
+    <key type="i" name="auto-power-on">
+        <default>2</default>
+        <summary>Automatically power on adapters; 0 = False; 1 = True; 2 = Auto</summary>
+        <description></description>
+    </key>
+  </schema>
+  <schema id="org.blueman.plugins.powermanager" path="/org/blueman/plugins/powermanager/">
+    <key type="s" name="bluetooth-config">
+        <default>"/etc/bluetooth/main.conf"</default>
+        <summary>Path to bluetooth configuration file</summary>
         <description></description>
     </key>
   </schema>
chad@A54C-NB91:~$ diff -Naur /usr/lib/python3/dist-packages/blueman/plugins/applet/PowerManager.py.orig  /usr/lib/python3/dist-packages/blueman/plugins/applet/PowerManager.py
--- /usr/lib/python3/dist-packages/blueman/plugins/applet/PowerManager.py.orig    2018-04-13 19:59:04.382876984 -0400
+++ /usr/lib/python3/dist-packages/blueman/plugins/applet/PowerManager.py    2018-04-13 21:40:27.110932715 -0400
@@ -8,7 +8,8 @@
 from blueman.plugins.AppletPlugin import AppletPlugin
 import blueman.bluez as Bluez
 from blueman.main.SignalTracker import SignalTracker
-
+import configparser
+from os.path import isfile
 
 class PowerManager(AppletPlugin):
     __depends__ = ["StatusIcon", "Menu"]
@@ -24,10 +25,16 @@
 
     __options__ = {
         "auto-power-on": {
-            "type": bool,
-            "default": True,
+            "type": int,
+            "default": 2,
             "name": _("Auto power-on"),
-            "desc": _("Automatically power on adapters")
+            "desc": _("Automatically power on adapters; 0 = False; 1 = True; 2 = Auto")
+        },
+        "bluetooth-config":{
+            "type": str,
+            "default": "/etc/bluetooth/main.conf",
+            "name": _("Bluetooth Config File"),
+            "desc": _("Path to bluetooth configuration file")
         }
     }
 
@@ -71,11 +78,30 @@
     def on_manager_state_changed(self, state):
         if state:
             def timeout():
-                self.adapter_state = self.get_adapter_state()
-                if self.get_option("auto-power-on"):
+                auto = self.get_option("auto-power-on")
+                if auto == 1:
                     self.RequestPowerState(True, force=True)
+                elif auto == 2:
+                    file = self.get_option("bluetooth-config")
+                    if isfile(file):
+                        print('File exist')
+                        config = configparser.ConfigParser()
+                        config.read(file)
+                        if 'AutoEnable' in config['Policy']:
+                            # Current way
+                            config = config['Policy']['AutoEnable']
+                        elif 'InitiallyPowered' in config['Policy']:
+                            # Old way
+                            config = config['Policy']['InitiallyPowered']
+                        else:
+                            # Documentation on setting says default is false
+                            config = False
+                    else:
+                        config = False
+                    print('Auto Detect Using: ',config)
+                    self.RequestPowerState(config)
                 else:
-                    self.RequestPowerState(self.adapter_state)
+                    self.RequestPowerState(self.get_adapter_state())
 
             GObject.timeout_add(1000, timeout)
 
chad@A54C-NB91:~$
```

As far I can tell i made a new setting, but if i reference it it does not exist, nor does the change to the old setting apply
Yes i tried using:
dconf reset -f /org/blueman/
no matter what i do the only setting that exist is the old boolean auto-power-on one and i can not even change the default

---

### Post by pqwoerituytrueiwoq on 2018-04-14
Figured it out:
[FONT=courier new]sudo glib-compile-schemas /usr/share/glib-2.0/schemas/[/FONT]
proposed patch upstream
[https://github.com/blueman-project/blueman/issues/859](https://github.com/blueman-project/blueman/issues/859)

---

