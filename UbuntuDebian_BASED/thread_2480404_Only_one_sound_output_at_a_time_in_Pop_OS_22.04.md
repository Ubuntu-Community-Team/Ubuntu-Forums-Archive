---
title: "Only one sound output at a time in Pop OS 22.04"
date: 2022-10-28
forum: Ubuntu/Debian BASED
---

### Post by mr-johnnysingles on 2022-10-28
**Issue/Bug Description:**
Hi, my problem is that I cannot switch to my speakers without unplugging the headphones first, because they disappear under sound output devices. I can still see both in PulseAudio Control, they are listed as "Speakers (unavailable)" and "Headphones (plugged in)". Alsamixer is set to auto-mute = disabled. In windows 10 there is no problems with this. The only other post about this that I've found is the one down below, but unfortunately the suggested solution didn't work for me.
[https://askubuntu.com/questions/998248/speaker-not-shown-on-sound-settings-ubuntu-gnome-16-04](https://askubuntu.com/questions/998248/speaker-not-shown-on-sound-settings-ubuntu-gnome-16-04)

**Expected behavior:**
While using headphones i should be able to select to speakers without unplugging them. 

**Distribution:**
NAME="Pop!_OS"
VERSION="22.04 LTS"
ID=pop
ID_LIKE="ubuntu debian"
PRETTY_NAME="Pop!_OS 22.04 LTS"
VERSION_ID="22.04"
HOME_URL="https://pop.system76.com"
SUPPORT_URL="https://support.system76.com"
BUG_REPORT_URL="https://github.com/pop-os/pop/issues"
PRIVACY_POLICY_URL="https://system76.com/privacy"
VERSION_CODENAME=jammy
UBUNTU_CODENAME=jammy
LOGO=distributor-logo-pop-os

**Other Notes:**
Host: Lenovo Legion 5 Pro 16ACH6H
CPU: AMD Ryzen 5 5600H
GPU: NVIDIA GeForce RTX 3060
Kernel: 6.0.2-76060002-generic
Audio Drivers:
card 0: NVidia [HDA NVidia], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: ALC287 Analog [ALC287 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

