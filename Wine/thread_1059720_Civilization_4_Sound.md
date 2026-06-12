---
title: "Civilization 4 Sound"
date: 2009-02-04
forum: Wine
---

### Post by mcgooie on 2009-02-04
Hey people. I have fully installed civ iv using [these]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8699") instructions. Everything seems to work ok apart from the sound. I have selected alsa in winecfg and if i click on test sound, the box becomes sunk and i have to kill winecfg.

Has anyone got any ideas as id really love to get this working?

---

### Post by jacksaff on 2009-02-04
Civ4 works fine for me with alsa, but bizarrely some mods don't have working sound until I switch to OSS. Switch to OSS and see if it helps.
Winecfg shouldn't crash though...

---

### Post by mcgooie on 2009-02-04
ok, i have gone back to an older version of wine and reinstalled. got the game working ok now but still no sound. i can click on the test sound button and it doesnt crash this time. i cant hear anything though and sound is working in other programs etc... is there some config i need to do?

---

### Post by mcgooie on 2009-02-04
i may have just got somewhere, when i go into system - prefs - sound. the sound playback option is set to Autodetect. if i click test i get the system beep. if i change this to either ALSA or OSS and try test i get silence but it does work for Pulseaudio. is this a possible solution? forgive me if this is stupid but ive only been using ubuntu for under a year and am still learning it.

thanks

---

### Post by mcgooie on 2009-02-04
got it working by following these steps [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

