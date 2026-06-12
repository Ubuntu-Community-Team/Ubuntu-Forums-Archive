---
title: "Ubuntu 14.04 LTS Upgrade!"
date: 2014-04-22
forum: System76 Support
---

### Post by isantop on 2014-04-22
Alright! The new version of Ubuntu was just released this morning, and everything is looking good. System76 users are clear to upgrade immediately!

Just a couple of notes, as always:

[LIST]
[*]Fresh installs and online upgrades with Software Updater are good to go.
[*]You should always install all available software updates before attempting the upgrade.
[*]Don't forget to install the System76 Driver after installation! Just enter these commands from a terminal window:
[/LIST]
```
sudo add-apt-repository ppa:system76-dev/stable
sudo apt-get update
sudo apt-get install system76-driver
```

That should be everything. The direct upgrade instructions are located at: [Ubuntu 14.04 Upgrade](http://knowledge76.com/index.php/Version_Upgrade).

---

### Post by sviginak on 2014-05-07
I want to go from 12.04 directly to 14.04. Why is this not an option
edit: on my gazp6

---

### Post by joseph29 on 2014-05-08
So I have a new system 76 wild-dog desktop. I have installed KDE as it is my preferred desktop environment. Then just a couple of days ago I upgraded to kubuntu 14.04. After the upgrade my sound stopped working. I tried several different suggested fixes like reinstalling alsa and pulseaudio with no success. Does anyone have any suggestions for me?

---

### Post by frank32 on 2014-06-11
> **joseph29 said:**
> So I have a new system 76 wild-dog desktop. I have installed KDE as it is my preferred desktop environment. Then just a couple of days ago I upgraded to kubuntu 14.04. After the upgrade my sound stopped working. I tried several different suggested fixes like reinstalling alsa and pulseaudio with no success. Does anyone have any suggestions for me?

Install pavucontrol

It will help you have a look at the devices and set the right one.  I had a devil of a time until I installed this.

---

### Post by him610 on 2016-03-07
Do the System76 folks plan on announcing when the LTS 16.04 release is available?

---

