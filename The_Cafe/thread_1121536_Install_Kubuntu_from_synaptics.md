---
title: "Install Kubuntu from synaptics?"
date: 2009-04-10
forum: The Cafe
---

### Post by rasmus91 on 2009-04-10
Hi

I would just like to know if its possible to install Kubuntu with all of its Default applications from the Synaptics? and thats without destroying Ubuntu and every file i have... I would just like to use the KDE and find out what i like best.

Thanks

---

### Post by Paqman on 2009-04-10
Install the package kubuntu-desktop, you'll be able to pick either KDE or Gnome from the login screen.

---

### Post by calvinps on 2009-04-10
Open a terminal and type in the following:

```
sudo apt-get install kubuntu-desktop
```

Then log out and try your new desktop!

---

### Post by Paqman on 2009-04-10
> **calvinps said:**
> Open a terminal

Or just open Synaptic, like the OP asked for ;)

---

### Post by rasmus91 on 2009-04-10
Ty People, will try it ;)

---

### Post by rasmus91 on 2009-04-10
got following error...
```
W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5-data_4.2.2-0ubuntu2_all.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs-bin_4.2.2-0ubuntu2_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/kdelibs5_4.2.2-0ubuntu2_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/p/phonon/phonon-backend-xine_4.3.1-0ubuntu2_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kde4libs/libplasma3_4.2.2-0ubuntu2_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kdebase-workspace-libs4+5_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/libkdecorations4_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/libkwineffects1_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kde-window-manager_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kdebase-workspace-data_4.2.2-0ubuntu1_all.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kdebase-workspace-bin_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/kdm_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/klipper_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/ksysguard_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/ksysguardd_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-dev_2.6.1-1ubuntu11_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/python-plasma_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebase-workspace/systemsettings_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdesudo/kdesudo_3.4-0ubuntu2_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/libkipi6_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/gwenview_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/k3b/libk3b3_1.0.5+kde4svn935857+really1.0.5-3ubuntu4_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b-data_1.0.5+kde4svn935857+really1.0.5-3ubuntu4_all.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0.5+kde4svn935857+really1.0.5-3ubuntu4_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kamera_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdebluetooth/kdebluetooth_0.3-0ubuntu3_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/libkexiv2-7_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kopete_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krdc_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/krfb_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/ksnapshot_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-default-settings/kubuntu-artwork-usplash_9.04.23_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kubuntu-default-settings/kubuntu-default-settings_9.04.23_all.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kde-zeroconf_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/libokularcore1_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/okular_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/k3b/libk3b3-extracodecs_1.0.5+kde4svn935857+really1.0.5-3ubuntu4_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-kde_0.111.3_all.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier-kde/update-notifier-kde_0.16_all.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/kdegraphics-strigi-plugins_4.2.2-0ubuntu1_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/konq-plugins/konqueror-plugin-searchbar_4.2.0a-0ubuntu2_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kpackagekit/kpackagekit_0.4-0ubuntu6_amd64.deb
  404 Not Found


W: Failed to fetch http://dk.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/okular-extra-backends_4.2.2-0ubuntu1_amd64.deb
  404 Not Found
```

Those packages where not installed, and i can't start Kubuntu because of this... any ideas on how to solve?

---

### Post by collinp on 2009-04-10
You got tons of 404 Not Found errors, meaning that the files are not on the server. Try running "sudo apt-get update && sudo apt-get install kubuntu-desktop" in terminal.

---

### Post by rasmus91 on 2009-04-11
Damn... After installing Kubuntu, and relogging to Ubuntu The nice new 9.04 notification thingie disappeared, and by now i have no idea on how to make it default again.

---

