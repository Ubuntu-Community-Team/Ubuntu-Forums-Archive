---
title: "update warnings"
date: 2012-08-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by flipper T on 2012-08-07
whenever i accept an update, the update works fine but i get page after page of warning messages. this is just a sample after updating evolution, but it seems to have little to do with the updated package itself.

any ideas?

```
warning: Schema 'apps.onboard.window.landscape' has path '/apps/onboard/window/landscape/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.window.portrait' has path '/apps/onboard/window/portrait/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette' has path '/apps/onboard/icon-palette/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette.landscape' has path '/apps/onboard/icon-palette/landscape/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.icon-palette.portrait' has path '/apps/onboard/icon-palette/portrait/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.universal-access' has path '/apps/onboard/universal-access/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.theme-settings' has path '/apps/onboard/theme-settings/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.lockdown' has path '/apps/onboard/lockdown/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'apps.onboard.scanner' has path '/apps/onboard/scanner/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.Geoclue' has path '/apps/geoclue/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.Telepathy.Logger' has path '/apps/telepathy-logger/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.freedesktop.gstreamer-0.10.default-elements' has path '/desktop/gstreamer/0.10/default-elements/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.Cheese' has path '/apps/cheese/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.Vino' has path '/desktop/gnome/remote-access/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.crypto.cache' has path '/desktop/gnome/crypto/cache/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.crypto.pgp' has path '/desktop/gnome/crypto/pgp/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.EpiphanyExtensions' has path '/apps/epiphany-extensions/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.EpiphanyExtensions.smart-bookmarks' has path '/apps/epiphany-extensions/smart-bookmarks/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.EpiphanyExtensions.tab-states' has path '/apps/epiphany-extensions/tab-states/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.seahorse' has path '/apps/seahorse/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.seahorse.manager' has path '/apps/seahorse/listing/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.locale' has path '/system/locale/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy' has path '/system/proxy/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.http' has path '/system/proxy/http/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
warning: Schema 'org.gnome.system.proxy.https' has path '/system/proxy/https/'.  Paths starting with '/apps/', '/desktop/' or '/system/' are deprecated.
```

---

### Post by mc4man on 2012-08-07
Some time now - up to packages to 'fix' (just warnings
[https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/1026914](https://bugs.launchpad.net/ubuntu/+source/d-conf/+bug/1026914)

(not really ubuntu specific - 
[https://bugzilla.redhat.com/show_bug.cgi?id=814053](https://bugzilla.redhat.com/show_bug.cgi?id=814053)

---

