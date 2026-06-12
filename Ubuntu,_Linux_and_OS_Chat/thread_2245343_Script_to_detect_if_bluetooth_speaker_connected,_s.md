---
title: "Script to detect if bluetooth speaker connected, switch to it if it is?"
date: 2014-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by Tadaen_Sylvermane on 2014-09-22
Background : I've been using KDE only because it has features I needed, such as audio device preferences and automatic enable / disable touchpad if mouse present. I decided to tackle these with scripts so I can use my real love, Gnome Shell ( don't judge! ). I have succeeded at the mouse detecting touchpad disable / enable script. Now I'm stuck on the bluetooth speaker.

I've been using this a bit to get started [http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line](http://askubuntu.com/questions/14077/how-can-i-change-the-default-audio-device-from-command-line). It works somewhat but I cannot understand how to set the default source. Rather I cannot determine the source from the appropriate commands. My goal is to have a script run every 30 seconds or so that checks if a bluetooth device is connected. If it is then it switches to the bluetooth device instead of me having to go into the sound settings and do it manually. I've got a bunch of magic happening by combining awk, cut, and grep with these commands so that part is as good as done. I need help with the pacmd commands, else is there a better way to accomplish this?

---

