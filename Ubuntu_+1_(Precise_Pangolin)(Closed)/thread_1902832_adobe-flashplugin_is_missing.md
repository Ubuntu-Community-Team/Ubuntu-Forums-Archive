---
title: "adobe-flashplugin is missing"
date: 2011-12-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Sworddragon on 2011-12-31
I figured out that my installed adobe-flashplugin is from Oneiric but there is no one in Precise. There is a flashplugin-installer in Precise but it depends on nspluginwrapper (adobe-flashplugin doesn't). Will adobe-flashplugin come back in Precise or is there a reason why it is missing?

---

### Post by jerrylamos on 2011-12-31
I get a bit tired of "flashplugin installer" so what I do is copy a recent libflashplayer.so into home then do:

gedit flash

#!/bin/bash
sudo cp -dpv *.so /usr/lib/mozilla/plugins
sudo cp -dpv *.so /usr/share/xul-ext/ubufox/plugins

save
sudo chmod 777 flash
./flash

The ubufox folder showed up recently on Pangolin.

Now this is not the recommended way, but I do a lot of installs on "unstable development" ubuntu's so I cheat.

Working fine on four different pc's with pangolin.

Jerry

---

### Post by sammiev on 2011-12-31
I download the latest version of flash and copy libflashplayer.so to the plugins directory in FF. Only takes a min. :)

---

### Post by Sworddragon on 2011-12-31
Copying the library in the plugin folder may work but I'm still wondering why the package isn't available.

---

### Post by sammiev on 2011-12-31
It's a protected holder. it's easy to take control of the holder is I really have no answer to your question. Good question I must add. :)

---

### Post by Sworddragon on 2011-12-31
I found the answer why adobe-flashplugin is missing: It comes from the partner repository. We must just wait until Adobe offers a package for Precise.

---

### Post by lovinglinux on 2012-01-01
You can easily get the latest beta flash from Adobe using [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/). If you don't want the beta and since the stable package is not in the partner repo, copy the download url below, open *Advanced Mode* in Flash-Aid, select "Custom" in the installation option and paste the url. Click the *Script* tab and then the *Execute* button.

**32bit:** [http://fpdownload.macromedia.com/get/flashplayer/pdc/11.1.102.55/install_flash_player_11_linux.i386.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/pdc/11.1.102.55/install_flash_player_11_linux.i386.tar.gz)

**64bit:** [http://fpdownload.macromedia.com/get/flashplayer/pdc/11.1.102.55/install_flash_player_11_linux.x86_64.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/pdc/11.1.102.55/install_flash_player_11_linux.x86_64.tar.gz)

---

### Post by 1roxtar on 2012-01-05
Simply activate it by going to System Settings>Software Sources>Other Software and check the boxes for Canonical Partners.

---

### Post by zika on 2012-01-18
In Precise (judging by few looks in Synaptic) if someone marks flashplugin-installer for install, he/she will get a whole bunch of 386 packages even though install is 64-bit...
Simple cp (still) rules... ;)

---

### Post by jbicha on 2012-01-18
I simply keep the previous stable release (Oneiric) partners and extras repositories when I upgrade to a development release.

---

### Post by xyzzyman on 2012-01-18
> **zika said:**
> In Precise (judging by few looks in Synaptic) if someone marks flashplugin-installer for install, he/she will get a whole bunch of 386 packages even though install is 64-bit...
Simple cp (still) rules... ;)

flashplugin-installer is 32bit flash. adobe-flashplugin is the 64bit. It's normally in the partner repositories but [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/) as of now they haven't compiled it for precise.

---

