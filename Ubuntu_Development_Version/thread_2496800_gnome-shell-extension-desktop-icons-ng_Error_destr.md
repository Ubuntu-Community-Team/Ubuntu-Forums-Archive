---
title: "gnome-shell-extension-desktop-icons-ng: Error: destroy() breaks..."
date: 2024-04-13
forum: Ubuntu Development Version
---

### Post by hectorsales on 2024-04-13
If i try to open "gnome-shell-extension-desktop-icons-ng" through the extension manager this show the error:

 > 
Error: destroy() breaks tracking open dialogs, use close() if you must

 Stack trace:
  [email]destroy@resource:///org/gnome/Shell/Extensions/js/extensionPrefsDialog.js[/email]:63:13
  fillPreferencesWindow/<@file:///usr/share/gnome-shell/extensions/ding@rastersoft.com/prefs.js:37:50
  OpenExtensionPrefsAsync/<@resource:///org/gnome/Shell/Extensions/js/extensionsService.js:141:41
  _init/<@resource:///org/gnome/Shell/Extensions/js/extensionPrefsDialog.js:29:31
  _init/GLib.MainLoop.prototype.runAsync/</<@resource:///org/gnome/gjs/modules/core/overrides/GLib.js:266:34




[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-desktop-icons-ng/+bug/2061070](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-desktop-icons-ng/+bug/2061070)

---

### Post by corradoventu on 2024-04-13
gnome-shell-extension-desktop-icons-ng is already installed in Ubuntu 24.04
```
corrado@corrado-n2-nn-0412:~$ apt policy gnome-shell-extension-desktop-icons-ng
gnome-shell-extension-desktop-icons-ng:
  Installed: 46+really47.0.9-1
  Candidate: 46+really47.0.9-1
  Version table:
 *** 46+really47.0.9-1 500
        500 http://archive.ubuntu.com/ubuntu noble/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu noble/main i386 Packages
        100 /var/lib/dpkg/status
corrado@corrado-n2-nn-0412:~$ 


```

---

### Post by hectorsales on 2024-04-13
Yes, but i if open the gnome-shell-extension-manager--->preferences extensions show the error. Attached screenshot.

---

### Post by hectorsales on 2024-04-13
The issue

> 

Error: destroy() breaks tracking open dialogs, use close() if you must

Stack trace:
  [email]destroy@resource:///org/gnome/Shell/Extensions/js/extensionPrefsDialog.js[/email]:63:13
  fillPreferencesWindow/<@file:///usr/share/gnome-shell/extensions/ding@rastersoft.com/prefs.js:37:50
  OpenExtensionPrefsAsync/<@resource:///org/gnome/Shell/Extensions/js/extensionsService.js:141:41
  _init/<@resource:///org/gnome/Shell/Extensions/js/extensionPrefsDialog.js:29:31
  _init/GLib.MainLoop.prototype.runAsync/</<@resource:///org/gnome/gjs/modules/core/overrides/GLib.js:266:34

---

### Post by Claus7 on 2024-04-13
Hello,

> **hectorsales said:**
> The issue

ditto.

Regards!

---

### Post by jbicha on 2024-04-13
Could someone affected by this issue also report it to [https://gitlab.com/rastersoft/desktop-icons-ng/-/issues](https://gitlab.com/rastersoft/desktop-icons-ng/-/issues) ?

---

### Post by hectorsales on 2024-04-13
Repoted now!

[https://gitlab.com/rastersoft/desktop-icons-ng/-/issues/314](https://gitlab.com/rastersoft/desktop-icons-ng/-/issues/314)

---

### Post by hectorsales on 2024-04-15
> **hectorsales said:**
> Repoted now!

[https://gitlab.com/rastersoft/desktop-icons-ng/-/issues/314](https://gitlab.com/rastersoft/desktop-icons-ng/-/issues/314)

Replace the line:

 ```
window.connect_after('show', ()=>{window.destroy();});
```

by

```
window.connect_after('show', ()=>{window.close();}); 
```

 in the file /usr/share/gnome-shell/extensions/ding@rastersoft.com/prefs.js

[https://gitlab.com/rastersoft/desktop-icons-ng/-/commit/55e6919930846d5e78eca239fc5813b3f68b5598#741905734639ec001fce97a6d3e82f19e69ab7dd](https://gitlab.com/rastersoft/desktop-icons-ng/-/commit/55e6919930846d5e78eca239fc5813b3f68b5598#741905734639ec001fce97a6d3e82f19e69ab7dd)

works for me!!

---

