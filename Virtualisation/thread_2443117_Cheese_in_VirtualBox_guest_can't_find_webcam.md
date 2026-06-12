---
title: "Cheese in VirtualBox guest can't find webcam"
date: 2020-05-11
forum: Virtualisation
---

### Post by &amp;KyT$0P# on 2020-05-11
VirtualBox 6.0.20, host is Xubuntu 18.04, guest is Xubuntu 20.04.  Cheese in the guest doesn't recognise my webcam.  It just says "No device found".

When running Cheese from Terminal, I get this -
```
$ cheese
** Message: xx:xx:xx.xxx: cheese-application.vala:214: Error during camera setup: No device found


(cheese:1445): cheese-CRITICAL **: xx:xx:xx.xxx: cheese_camera_device_get_name: assertion 'CHEESE_IS_CAMERA_DEVICE (device)' failed

(cheese:1445): GLib-CRITICAL **: xx:xx:xx.xxx: g_variant_new_string: assertion 'string != NULL' failed

(cheese:1445): GLib-CRITICAL **: xx:xx:xx.xxx: g_variant_ref_sink: assertion 'value != NULL' failed

(cheese:1445): GLib-GIO-CRITICAL **: xx:xx:xx.xxx: g_settings_schema_key_type_check: assertion 'value != NULL' failed

(cheese:1445): GLib-CRITICAL **: xx:xx:xx.xxx: g_variant_get_type_string: assertion 'value != NULL' failed

(cheese:1445): GLib-GIO-CRITICAL **: xx:xx:xx.xxx: g_settings_set_value: key 'camera' in 'org.gnome.Cheese' expects type 's', but a GVariant of type '(null)' was given

(cheese:1445): GLib-CRITICAL **: xx:xx:xx.xxx: g_variant_unref: assertion 'value != NULL' failed

** (cheese:1445): CRITICAL **: xx:xx:xx.xxx: cheese_preferences_dialog_setup_resolutions_for_device: assertion 'device != NULL' failed

```

guvcview in the same Xubuntu 20.04 guest does recognise the webcam and seems to work flawlessly.

Why doesn't it work in Cheese?

---

### Post by wildmanne39 on 2020-05-11
I just tested this method in virtualbox with ubuntu, you have to install the extension pack for your version of virtualbox then reboot the host and guest, then I went to the button and clicked usb devices it in the vm and it listed Genric HDTrue Vision and I clicked on it then cheese worked, the extension pack will also give you 2.0 and 3.0 usb support.

---

### Post by &amp;KyT$0P# on 2020-05-11
Extension Pack is already installed.

> **wildmanne39 said:**
> went to the button and clicked usb devices it in the vm and it listed Genric HDTrue Vision and I clicked on it then cheese worked, 

Thanks wildmanne39, this got it working for me too!  I was attaching the webcam to the VM using Devices > Webcams menu.  If I instead do it from Devices > USB as you suggested, everything works. :cool:

---

### Post by wildmanne39 on 2020-05-11
Glad it is sorted!:)

---

