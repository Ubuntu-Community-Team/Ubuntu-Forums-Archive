---
title: "Gnomeradio is back in ubuntu repositories precise [universe]"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by aaalbatrosss on 2012-03-15
gnomeradio (1.8-2) is now in percise repository [universe].

If you have a radio tuner card, please test this out, as ported this code to GNOME 3 without having one to fully test.

Gnomeradio is a FM-radio tuner for the GNOME desktop. It should work with
every FM tuner card that is supported by video4linux. Remote controls are
supported via LIRC-support. Gnomeradio can also record radio as a Wave or
Ogg files.

Thank.

---

### Post by grahammechanical on 2012-03-15
Hi

I tried to help out. I know that my tuner card is not supported by video4linux so I am not surprised that I could not get radio playing.

In installs fine and runs. I got these error messages

> Could not open /dev/mixer
could not open /dev/radio 
Make sure that no other program is using /dev/radio
and make sure that you have read access

After closing the message dialogs the gnome radio settings dialog appeared. After closing the gnome radio control centre panel appeared and everything seemed to work as it should.

It scanned as it should. Of course it could not detect radio transmissions. Although it did stop at frequency  89.80 which is close the UK radio 2 frequency. Which is strange.

I am using 12.04 Beta 1 with a default set up for testing stuff like this. I hope this helps. I would say that on Gnome 3 with Unity it works. The icon appears in the Dash and in the Launcher when the application is running with the usual options from the right click menu. which also work.

Regards.

---

### Post by aaalbatrosss on 2012-03-15
**_[COLOR="Red"]For all who do not have sound when running gnomeradio[/COLOR]_**:

Try to solved this problem:

```
sudo apt-get install gconf-editor
```

with gconf-editor:

(type in console)-->apps-->gnomeradio and here:

1. change value "driver" from "any" with "v4l2"

2. change value "device" from "/dev/radio" with "/dev/radio0"

[IMG]http://desmond.imageshack.us/Himg521/scaled.php?server=521&filename=screenshotconfiguration.png&res=medium[/IMG]

after that (depends on the type of tuner that you possess), if not screaming radio, load snd_mixer_oss:

```
sudo modprobe snd_mixer_oss
```

---

