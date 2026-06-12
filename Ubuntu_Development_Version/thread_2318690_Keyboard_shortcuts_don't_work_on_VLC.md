---
title: "Keyboard shortcuts don't work on VLC"
date: 2016-03-28
forum: Ubuntu Development Version
---

### Post by enricobe on 2016-03-28
Hi,
I can't use keyboard shortcuts in VLC. For example, CTRL+J while playing a video should show the video/audio codec informations, but nothing happens. Can anyone confirm? If confirmed, should I report it on launchpad?

Thank you!

---

### Post by mc4man on 2016-03-28
All the default hotkeys in vlc seem to work ok, did you create the one you mentioned?

---

### Post by enricobe on 2016-03-29
CTRL+J  is  a default hotkey. You can find it in the tools menu.

I've found this example picture [http://www.5kplayer.com/video-music-player/img/5kp-vlc-mp4-zjy-001.jpg](http://www.5kplayer.com/video-music-player/img/5kp-vlc-mp4-zjy-001.jpg)

---

### Post by mc4man on 2016-03-29
Those seem to be gone. If inclined file a bug. Maybe take a look around & see if any other apps are similarly affected.

It does seem if you can get the menu back in vlc then they show up & work (not with the unity option to show menus in app
See screens, somehow I got them back though notice the in app menus are a little weird with a line under each item..

---

### Post by enricobe on 2016-03-29
> **mc4man said:**
> somehow I got them back though notice the in app menus are a little weird with a line under each item..

I'm sorry but I can't fully understand, keyboard shortcuts like CTRL+J work in your case? If you play a video and press CTRL+J you get the codec information window?

---

### Post by mc4man on 2016-03-29
> **enricobe said:**
> I'm sorry but I can't fully understand, keyboard shortcuts like CTRL+J work in your case? If you play a video and press CTRL+J you get the codec information window?
Yes & no. Normally you will not get those bindings anymore. They will work if vlc's menus are forced back into vlc. I figured out what will do that however somewhat useless as it only lasts until vlc is closed.

To do so - 
open vlc
Go Tools > Customize Interface
Switch the Select profile dropdown from 2.x.x Style to 1.x.x Style & then back to 2.x.x
You'll now temporally have the bindings until you close vlc

This is likely from the switch to qt5. If there was a qt5-config maybe you could add back permanently but it doesn't exist per se in Debian/Ubuntu though possibly with some degree of hassle one could build a qt5 config app.

---

### Post by mc4man on 2016-03-29
Have a more permanent solution if desired - 

For opening vlc via it's .desktop, context menu or thru having vlc as default per mimetype - 
```
sudo -H gedit /usr/share/applications/vlc.desktop
```
scroll down to the Exec=/usr/bin/vlc --started-from-file %U line & change to this - 
```
Exec=env UBUNTU_MENUPROXY=0 /usr/bin/vlc --started-from-file %U
```

When or if running vlc from a terminal use this
```
export UBUNTU_MENUPROXY=0 && vlc
```

An all in one would be to create a wrapper for /usr/bin/vlc that passes the env

---

### Post by kinglear333 on 2016-05-04
> **mc4man said:**
> Have a more permanent solution if desired - 

Thank you, sir. That worked a treat! Now I can finally use shortcuts in Ubuntu 16.04 with VLC.

---

### Post by cariboo on 2016-05-05
Thread closed.

---

