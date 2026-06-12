---
title: "Installing virtualbox makes my soundcard disfunctionall"
date: 2008-04-01
forum: Virtualisation
---

### Post by getthearm on 2008-04-01
Hi folks.

I have recently gone through enough trial and tribulation to pull my ear hair out in the past few days trying to install ubuntu and then Virtualbox w/ windows xp through apt.

Long story short, I install Hardy (same problem in gutsy) and mess around for a bit doing updates. I go to install Virtualbox and as soon as I do the required restart, my sound doesnt work, the sound icon in the tray has a red x through it, and when i try to double click it says "no volume control gstreamer plugins and or devices found." I have narrowed it down to Virtualbox by restarting with each change I make.

I am start fresh with Hardy, and the sound currently works. How can I install Virtualbox without my soundcard taking a vacation?

Thanks

---

### Post by Oldsoldier2003 on 2008-04-02
> **getthearm said:**
> Hi folks.

I have recently gone through enough trial and tribulation to pull my ear hair out in the past few days trying to install ubuntu and then Virtualbox w/ windows xp through apt.

Long story short, I install Hardy (same problem in gutsy) and mess around for a bit doing updates. I go to install Virtualbox and as soon as I do the required restart, my sound doesnt work, the sound icon in the tray has a red x through it, and when i try to double click it says "no volume control gstreamer plugins and or devices found." I have narrowed it down to Virtualbox by restarting with each change I make.

I am start fresh with Hardy, and the sound currently works. How can I install Virtualbox without my soundcard taking a vacation?

Thanks

try using getting virtualbox from the developers website. its a newer and more stable version than is found in the repos - at least it was for gutsy.

---

### Post by Crick on 2010-02-04
Something like this happened to me. I installed the virtualbox-ose in 8.04, and to try and get it to work, I remember clicking on several other of the options synaptic gives you when you type in "virtualbox".

I then realized that virtualbox-ose wasn't going to work, so I installed the version from Sun. However, now the sound wasn't working. At first I thought it was my keyboard (MS Natural Ergonomic 4000), but then I realized the sound was actually broken.

I realized that the sound would work when I went back to the latest generic kernel via grub. So when I got back into ubuntu, I uninstalled those other options from the original virtualbox via synaptic (e.g. virtualbox-ose-modules-2.6.24-25-rt, virtualbox-ose-modules-2.6.24-25-server), restarted, and the sound is working. (I also had to drop out of X to run my nvidia driver installer again, and copy a working xorg.conf back to where it lives, but that is another story).

---

