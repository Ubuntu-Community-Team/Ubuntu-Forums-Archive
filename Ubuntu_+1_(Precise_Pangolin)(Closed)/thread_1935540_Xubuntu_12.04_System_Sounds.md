---
title: "Xubuntu 12.04 System Sounds"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cottfcfan on 2012-03-04
Has anybody managed to get any system sounds working in Xubuntu 12.04.
In Ubuntu 12.04 I managed it by deleting my .pulse folder & rebooting.
In Xubuntu however, nothing.
Even followed my own thread here:
[http://ubuntuforums.org/showthread.php?t=1869787](http://ubuntuforums.org/showthread.php?t=1869787)
but no go.
Any tips would be appreciated.

---

### Post by Sylslay on 2012-03-04
It works fine on MSI netbook, (XUbuntu installed at alpha relise)

I thing, that need adjust volume on "speaker panel"

Just clik volume control and add new devices like "master volume, alsa and pulse audio etc"

---

### Post by Yellow Pasque on 2012-03-04
xfce's event sound setting is in:
Settings -> Appearance -> 'Settings' tab
(I personally feel like this is a non-intuitive place for it.)

---

### Post by cottfcfan on 2012-03-04
Thanks for your quick response guys.
I have already tried your suggestions. All volumes are up to 100%.
Even installed pavucontrol, no problems there. And my event sounds are ticked.
Even changed the sound themes.
All works well in 11.10, but not 12.04.
Sound is there as I have no problems playing mp3s, all codecs are also installed.
Scratching my head on this one, maybe its just a beta problem.

edit....
Am I right in assuming that the sounds are picked up from /usr/share/sounds as they were in 11.10??

---

### Post by cottfcfan on 2012-03-21
OK..
Ive now been struggling with this for 2 weeks & numerous updates.
Ive enabled sound events & Input feedback sounds, changed the sound theme name in settings editor, deleted .pulse & pulse-cookie in Home folder, but just cannot get any system sounds at all.
Can anyone who has this working please explain how they managed it?
Thanks.

---

### Post by Yellow Pasque on 2012-03-21
Maybe you need to install gnome-session-canberra package?

---

### Post by cottfcfan on 2012-03-21
Hi Temujin,
Thanks for your reply. Installed package you suggested, but still no joy.
I can get a login sound by adding "play /path/to/file" to autostart applications. I can get sound in gnome-games, by clicking the "sound" button in "control". Banshee & exaile play nicely, but no system sounds whatsoever. Works in Ubuntu precise but not Xubuntu.
Anymore suggestions would be welcome.

---

### Post by cottfcfan on 2012-04-10
Bump
Anyone...

---

