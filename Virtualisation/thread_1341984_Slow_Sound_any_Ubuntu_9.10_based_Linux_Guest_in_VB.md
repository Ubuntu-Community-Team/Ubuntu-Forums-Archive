---
title: "Slow Sound any Ubuntu 9.10 based Linux Guest in VB"
date: 2009-11-30
forum: Virtualisation
---

### Post by loukingjr on 2009-11-30
I am running VirtualBox in Snow Leopard 10.6.2 and have had an ongoing problem since 9.10 came out. ANY Linux distribution based on Ubuntu 9.10 may or may not start with sounds running slow, i.e. at the wrong sample rate. It doesn't happen with any Window's guests XP,7 etc, doesn't happen with Fedora 12 and others, and doesn't happen with any Ubuntu based distro prior to 9.10.

I really wish someone could figure out why. Based on the fact that so many other guests don't have sound issues, I can only surmise is something in Ubuntu 9.10 or other Linux distros with a similar audio setup.

---

### Post by juliobahar on 2009-12-03
> **loukingjr said:**
> I am running VirtualBox in Snow Leopard 10.6.2 and have had an ongoing problem since 9.10 came out. ANY Linux distribution based on Ubuntu 9.10 may or may not start with sounds running slow, i.e. at the wrong sample rate. It doesn't happen with any Window's guests XP,7 etc, doesn't happen with Fedora 12 and others, and doesn't happen with any Ubuntu based distro prior to 9.10.

I really wish someone could figure out why. Based on the fact that so many other guests don't have sound issues, I can only surmise is something in Ubuntu 9.10 or other Linux distros with a similar audio setup.

I'm experiencing the same problem with Ubuntu 9.10 + virtualbox 3.1.0 (windows 7 guest)

I think the issue is with pulseaudio. When I choose pulseaudio from virtualbox/audio control panel, sound runs slow with absolutely wrong bitrating, but microphone seems to work fine - as I tried it with yahoo messenger.

On the other hand, choosing ALSA will produce buzzing and beeping sounds with annoying choppings... I really don't know what is wrong now. On previous versions of ubuntu sound wasn't flawless but with less issue as now.

I still think it is pulseaudio. I also need some help

---

### Post by demetrius_of_pharos on 2010-03-09
All:

This seems to have worked for me. [http://forums.virtualbox.org/viewtopic.php?f=3&t=25444]("http://forums.virtualbox.org/viewtopic.php?f=3&t=25444")

In short, I used vim to edit/create '/etc/modprobe.d/sound.conf', which for me didn't exist.
```
sudo vim /etc/modprobe.d/sound.conf
```

Then, in the file, paste this code:
```

options snd-intel8x0 ac97_clock=48000
options snd slots=snd-intel8x0
# CvwD.FAMlirE10w6:82801AA AC'97 Audio Controller
alias snd-card-0 snd-intel8x0

```

Finally, reboot. (I'm assuming restarting sound works to, I didn't try it though. YMMV.)
```
sudo reboot
```

FWIW, My host is Mac OSX 10.6.2 running VirtualBox 3.1.4, Guest is Ubuntu 9.10.

---

