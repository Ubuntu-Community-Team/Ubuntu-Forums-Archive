---
title: "Any GNOME + Unity users able to verify a chrome-gnome-shell bug on 16.04?"
date: 2017-03-27
forum: Ubuntu Development Version
---

### Post by jbicha on 2017-03-27
This might not be the best place for my request, but this channel is for those who like testing and finding bugs and Ubuntu 16.04 LTS still gets new releases.

I can reproduce [bug 1671572]("https://launchpad.net/bugs/1671572") on Ubuntu 17.04 Beta. Ubuntu GNOME now installs chrome-gnome-shell by default because it is needed for [extensions.gnome.org]("https://extensions.gnome.org/") to work in Firefox 52. If you open your web browser when running Unity (or any desktop besides gnoem-shell), you get an annoying pop up about gnome-shell not running.

I haven't seen the bug on 16.04 or 16.10 yet because it looks like the browser has to be kept running for 6 hours first. I've identified the fix so if someone could verify the bug and then verify the Stable Release Update after, it would save me some time and work. Thanks!

---

### Post by ventrical on 2017-03-27
> **jbicha said:**
> This might not be the best place for my request, but this channel is for those who like testing and finding bugs and Ubuntu 16.04 LTS still gets new releases.

I can reproduce [bug 1671572]("https://launchpad.net/bugs/1671572") on Ubuntu 17.04 Beta. Ubuntu GNOME now installs chrome-gnome-shell by default because it is needed for [extensions.gnome.org]("https://extensions.gnome.org/") to work in Firefox 52. If you open your web browser when running Unity (or any desktop besides gnoem-shell), you get an annoying pop up about gnome-shell not running.

I haven't seen the bug on 16.04 or 16.10 yet because it looks like the browser has to be kept running for 6 hours first. I've identified the fix so if someone could verify the bug and then verify the Stable Release Update after, it would save me some time and work. Thanks!

Trying this now on my 16.04 ubuntu-desktop production box.

edit: Question. You want us to install chromium browser on ubuntu-desktop? Can't find chrome.

edit : ok .. got it .. install chrome-gnome-shell

regards..

---

### Post by ventrical on 2017-03-27
Ok.. so it will install whole gnome-session along side ubuntu-desktop.

```

Suggested packages:
  desktop-base telepathy-haze
The following NEW packages will be installed:
  chrome-gnome-shell dleyna-server folks-common gdm3
  gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdesktopenums-3.0 gir1.2-gdm-1.0 gir1.2-gkbd-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gweather-3.0
  gir1.2-mutter-3.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0
  gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs gnome-backgrounds gnome-contacts
  gnome-control-center gnome-control-center-data gnome-online-accounts
  gnome-session gnome-settings-daemon gnome-shell gnome-shell-common
  gnome-themes-standard-data iio-sensor-proxy libcaribou-common libcaribou0
  libchamplain-0.12-0 libcolord-gtk1 libdleyna-connector-dbus-1.0-1
  libdleyna-core-1.0-3 libfolks-eds25 libfolks-telepathy25 libfolks25 libgdm1
  libgjs0e libgoa-backend-1.0-1 libgssdp-1.0-3 libgupnp-1.0-4
  libgupnp-av-1.0-2 libgupnp-dlna-2.0-3 libmission-control-plugins0
  libmozjs-24-0v5 libmutter0g libtelepathy-logger3 libxcb-xf86dri0 libxcb-xv0
  mutter mutter-common realmd telepathy-mission-control-5 xserver-xephyr
0 upgraded, 64 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.5 MB of archives.
After this operation, 85.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] 

```

---

### Post by ventrical on 2017-03-27
I'll wait 6 hours :)

---

### Post by mc4man on 2017-03-28
didn't see a pop up in 16.04 after 6 hrs+ though not exactly clear on - 
If browser is running then pop up would be on opening another instance leaving existing instance up?
 or
 close running instance & look for pop up on next opening?

---

### Post by jbicha on 2017-03-28
I forgot a step. If you're using Firefox, you need to make sure the browser extension is also installed. You should be prompted to do when you visit [https://extensions.gnome.org/](https://extensions.gnome.org/)

What we're looking for (in Firefox) is:
Open about:addons
Make sure you're on the Extensions page.
Next to GNOME Shell integration, click Preferences.
Under "Check for extensions update", it should have a time in "Last check".

(It's similar in Google Chrome/Chromium.)

After that, go ahead and close Firefox completely. Then start it again.

---

### Post by ventrical on 2017-04-07
How to fix this...?
I updated , rebooted but still..

edit: Ok .. screenshot did not include notice that  the extension is not compatible with  firefox version.

---

