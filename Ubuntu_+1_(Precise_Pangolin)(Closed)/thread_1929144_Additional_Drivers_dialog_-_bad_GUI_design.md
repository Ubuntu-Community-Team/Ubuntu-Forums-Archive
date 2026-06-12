---
title: "Additional Drivers dialog - bad GUI design?"
date: 2012-02-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by t1497f35 on 2012-02-21
Hi,
See screenshot.
The GUI is littered with multi-line text which is an amateurish way of creating a GUI.

Also, it's not specific since it doesn't show up what a normal user would care about: what driver version is installed and which new version is available for install, with a possible "what's new" for the newer version which is to be installed.

The blabber about open source and how Canonical can't change this code should be much shorter and most of it hidden under a "details.." button, since IMO the vast majority of normal users don't care what Canonical can and can't change directly from the source code since normal people don't care about the source code of programs.

The green light-bulbs are inconsistent with the other GTK widgets.

Don't you think so?

---

### Post by ventrical on 2012-02-21
> **t1497f35 said:**
> Hi,
See screenshot.
The GUI is littered with multi-line text which is an amateurish way of creating a GUI.

Also, it's not specific since it doesn't show up what a normal user would care about: what driver version is installed and which new version is available for install, with a possible "what's new" for the newer version which is to be installed.

The blabber about open source and how Canonical can't change this code should be much shorter and most of it hidden under a "details.." button, since IMO the vast majority of normal users don't care what Canonical can and can't change directly from the source code since normal people don't care about the source code of programs.

The green light-bulbs are inconsistent with the other GTK widgets.

Don't you think so?

I like the way it presents itself .. but progress can always be made .. even to the point where we can even , mabey call it Windows ?

---

### Post by kaldor on 2012-02-21
I agree. The GUI looks pretty bad and overly complicated.

---

### Post by prusswan on 2012-02-21
It works well for me, maybe because I like the additonal information. A bigger problem is I still have no idea how to change the rest of the drivers except from the command line. This is quite a far cry from Device Manager in Windows where more fine-grained configuration is possible.

---

### Post by ventrical on 2012-02-21
> **prusswan said:**
> It works well for me, maybe because I like the additonal information. A bigger problem is I still have no idea how to change the rest of the drivers except from the command line. This is quite a far cry from Device Manager in Windows where more fine-grained configuration is possible.


Touche'! :)

---

### Post by xebian on 2012-02-21
It's all craps anyway.  I have Nvidia proprietary drivers installed and it's telling me nothing is installed /activated.

---

### Post by jbicha on 2012-02-22
Yes, jockey definitely needs some UI love. Among other things, it should be integrated into System Settings.

Would you like to work on redesigning it?

---

### Post by cariboo on 2012-02-22
> **prusswan said:**
> It works well for me, maybe because I like the additonal information. A bigger problem is I still have no idea how to change the rest of the drivers except from the command line. This is quite a far cry from Device Manager in Windows where more fine-grained configuration is possible.

Jockey is only there to install closed source drivers, what other drivers do you need to install? Printers have their own dialogue to install the correct drivers.

---

### Post by rajeev1204 on 2012-02-22
What is jockey ?

I can live with additional drivers window provided it works in the first place. I have the Radeon driver installed but in the past few years not a single install has worked through this window. I have to use synaptic to install the drivers. And as usual the drivers window says 'no drivers are in use' or 'not activated'

---

### Post by prusswan on 2012-02-22
> **cariboo907 said:**
> Jockey is only there to install closed source drivers, what other drivers do you need to install? Printers have their own dialogue to install the correct drivers.

I had no idea that thing is called Jockey, and it doesn't seem to have much to do with gnome-device-manager which is supposed to be the closest equivalent of Device Manager. Very weird and messy design.

---

### Post by cmccauley on 2012-02-22
I think it could do with some attention. For example with NVIDIA, I have four drivers listed but I'm left wondering which one to use if I want the latest and gretest.

From the dialog box ...


NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (version current)[Recommended]
NVIDIA accelerated graphics driver (post-release updates)(version 173-updates)
NVIDIA accelerated graphics driver (post-release updates)(version current-updates)


... daft.

Chris

---

### Post by cariboo on 2012-02-22
Actually jockey-gtk is the gui version and jockey-text is the command line version. There many applets that we use fairly often, that have names that seem to have nothing to do with what the applet does. Try **seahorse** for example and see what you get.

---

