---
title: "Bluez 4.101 cannot use Wiimote Inside Plus since Ubuntu 13.04 and others"
date: 2014-03-11
forum: Ubuntu Dev Link Forum
---

### Post by J.G on 2014-03-11
Hi everybody,

I tested in Lubuntu 14.04 Build "09 March 2014" (that have a kernel 3.13.0-16-generic) the use of a Nintendo RVL-CNT-01-TR Black Version (that I buy five  days ago.
I have seen that bluez doesn't use correctly the 2nd generation of the Wiimote (asked always for PIN, bad detection with hid-wiimote because of bluez issues, etc)
**I precise that the patch for use this new device exists [COLOR=#ff0000]since October 2012[/COLOR] thanks to David Herrmann works ([http://permalink.gmane.org/gmane.linux.bluez.kernel/31250](http://permalink.gmane.org/gmane.linux.bluez.kernel/31250)) and you haven't yet applied it.**

I applied so the patch for bluez version 4.101 (version used in Lubuntu 14.04) and setup/compiled new source code.
 I add in /etc/modules the line "hid-wiimote" in order to load automatically the kernel module for me every startup of my PC.

I setup after the program XWiimote in "/usr" and add the xorg file of the project in "/usr/share/X11/xorg.conf.d" and the udev rule of the project in "/etc/udev/rules.d"

  I can now use without issue the Wii Remote with his extensions (connect with blueman (push the red sync button) / disconnect with power button of Wiimote or with blueman).

Screenshots of the new version of bluez and xwiimote working perfectly on Lubuntu 14.04 :
[ATTACH=CONFIG]251056[/ATTACH] -  [ATTACH=CONFIG]251057[/ATTACH]

The patch for Bluez version 4.101 :
```

[COLOR=#ff0000]--- /home/jg/Téléchargements/bluez-4.101-old/plugins/wiimote.c[/COLOR]
[COLOR=#008000]+++ /home/jg/Téléchargements/bluez-4.101/plugins/wiimote.c[/COLOR]
@@ -56,12 +56,24 @@
  * is pressed.
  */
 
[COLOR=#008000]+static uint16_t wii_ids[][2] = {
+    { 0x057e, 0x0306 },
+    { 0x057e, 0x0330 },
+};
+
+static const char *wii_names[] = {
+    "Nintendo RVL-CNT-01",
+    "Nintendo RVL-CNT-01-TR",
+    "Nintendo RVL-WBC-01",
+};
+[/COLOR]
 static ssize_t wii_pincb(struct btd_adapter *adapter, struct btd_device *device,
                         char *pinbuf, gboolean *display)
 {
     uint16_t vendor, product;
     bdaddr_t sba, dba;
     char addr[18], name[25];
[COLOR=#008000]+    unsigned int i, len;[/COLOR]
 
     adapter_get_address(adapter, &sba);
     device_get_address(device, &dba, NULL);
@@ -73,11 +85,24 @@
     device_get_name(device, name, sizeof(name));
     name[sizeof(name) - 1] = 0;
 
[COLOR=#ff0000]-    if (g_str_equal(name, "Nintendo RVL-CNT-01") ||
-                (vendor == 0x057e && product == 0x0306)) {
-        DBG("Forcing fixed pin on detected wiimote %s", addr);
-        memcpy(pinbuf, &sba, 6);
-        return 6;[/COLOR]
[COLOR=#008000]+    len = sizeof(wii_ids) / sizeof(wii_ids[0]);
+    for (i = 0; i < len; ++i) {
+        if (vendor == wii_ids[i][0] && product == wii_ids[i][1])
+            {
+            printf("Forcing fixed pin on detected wiimote %s\n", addr);
+            memcpy(pinbuf, &sba, 6);
+            return 6;
+            }
+    }
+
+    len = sizeof(wii_names) / sizeof(wii_names[0]);
+    for (i = 0; i < len; ++i) {
+        if (g_str_equal(name, wii_names[i]))
+            {
+            printf("Forcing fixed pin on detected wiimote %s\n", addr);
+            memcpy(pinbuf, &sba, 6);
+            return 6;
+            }[/COLOR]
     }
 
     return 0;

```

Can you confirm us if bluez modification will be applied for 14.04 release ?

In a friendly manner,
J.G
Website : [http://jg.imbert.free.fr](http://jg.imbert.free.fr)
GitHub : [https://github.com/Jacques-Olivier](https://github.com/Jacques-Olivier)

---

### Post by ilovemysillybanana on 2014-07-26
Can you make a more detailed tutorial or something to show how to install this?

This isn't necroing, I need this to work but don't really know how he did.

---

