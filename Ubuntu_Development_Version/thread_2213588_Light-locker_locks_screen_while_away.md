---
title: "Light-locker: locks screen while away"
date: 2014-03-27
forum: Ubuntu Development Version
---

### Post by Elastic_Potential on 2014-03-27
I know that this question is a [documented bug](https://bugs.launchpad.net/ubuntu/+source/light-locker/+bug/1281323), but Lubuntu has been in testing for awhile now, so I was just wondering if anyone has, at least, found a quick-n-dirty workaround.  Returning to a locked screen after ~15ish minutes of inactivity is pretty annoying.

---

### Post by bapoumba on 2014-03-27
Well, it's tagged fix released. Honestly, I had never noticed.. I always manually lock my screen when I walk off the room. That said, if I let the laptop alone for a long while withou doing anything, the screen turns off but the session is not locked, a mouse movement wakes it up. Probably because I do not like screensavers and routinely use that setting (see screenshot). Not using a screensaver means no auto locking after screensaver ?

---

### Post by Elastic_Potential on 2014-03-27
huh...how did you pull up that settings window?

---

### Post by bapoumba on 2014-03-27
> **Elastic_Potential said:**
> huh...how did you pull up that settings window?

Prefs > Light Locker Settings. On 14.04.

---

### Post by Elastic_Potential on 2014-03-27
> **bapoumba said:**
> Prefs > Light Locker Settings. On 14.04.
It appears that I don't have that option o_O  do you know the terminal command to launch it?

---

### Post by bapoumba on 2014-03-27
I've been looking for that :)
In the meantime, I've moved your thread to Ubuntu +1.
How did you get lubuntu ? Do you have the lubuntu-desktop package installed ?
light-locker is in universe.

---

### Post by Elastic_Potential on 2014-03-27
> **bapoumba said:**
> I've been looking for that :)
In the meantime, I've moved your thread to Ubuntu +1.
How did you get lubuntu ? Do you have the lubuntu-desktop package installed ?
light-locker is in universe.

I would have suggested opening the settings manager and then running a command like "ps -A | grep lock", but I found the command: "light-locker settings".  Incidentally, I found this when I went to uninstall update-notifier; apt-get informed me that "light-locker-settings had been removed and is no longer needed," so I went ahead and re-installed it.  Since I did a fresh install (full wipe) of 14.04, I find it strange that the settings manager was removed, and I have no idea how it happened.

Also, while I have everyone's attention, does light-locker save these settings to a config file?  I know Lubunu is *really* pushing for gui frontends/slackware, but I'm just curious.

EDIT: it appears I was wrong about the 'ps -A' suggestion; the settings window doesn't show up on ps, top, or Task Manager for me o_O

---

### Post by bapoumba on 2014-03-27
Well, I'm not everyone, and by far.. I've also been looking for that. I have a .config/autostart/light-locker.desktop file in my /home, but there is nothing interesting re: your question in there. Probably in some power management or laptop config, I'm not sure.

Edit : forgot to add, maybe you removed light-locker because of a conflict with another screensaver ?
Edit n°2 : scratch that :D

---

### Post by Elastic_Potential on 2014-03-27
> **bapoumba said:**
> Well, I'm not everyone, and by far.. I've also been looking for that. I have a .config/autostart/light-locker.desktop file in my /home, but there is nothing interesting re: your question in there. Probably in some power management or laptop config, I'm not sure.

Edit : forgot to add, maybe you removed light-locker because of a conflict with another screensaver ?

Nah, I don't use screensavers lol; I'm actually kinda glad Lubuntu is moving from xscreensaver 'cause that program is awful (albeit functional and a cross-distro default).  I'll also report back if I find a config file.

One last thing: when I switch "Lock automatically after screensaver" to "OFF", it still auto-locks after my screen goes blank.  If I switch it to "ON" and throw the slider all the way to 60 minutes, it's an acceptable workaround for the time being.  But, is this a bug, or am I just neglecting something?

---

### Post by bapoumba on 2014-03-27
Well, I should fresh install. I've upgraded, and there is another difference from a fresh install here : [http://ubuntuforums.org/showthread.php?t=2210892](http://ubuntuforums.org/showthread.php?t=2210892)

---

### Post by pierre19 on 2014-08-09
up, because the bug is still here. That is to say, the screen locks after a while when the settings are :
blank screen after
enable light-locker : on

---

### Post by pierre19 on 2014-08-09
hello

up, because the bug is still there. That is to say, with the light locker settings :

[I]blank screen after : 10 min
switch off display after : 15 min
enable light-locker : on
automatically lock the session : **never**
lock on suspend : off[/I]

the screen locks after a while.

(just for information)

---

### Post by DogMatix on 2014-08-09
> **pierre19 said:**
> hello

up, because the bug is still there. That is to say, with the light locker settings :

[I]blank screen after : 10 min
switch off display after : 15 min
enable light-locker : on
automatically lock the session : **never**
lock on suspend : off[/I]

the screen locks after a while.

(just for information)

That's exactly how I have Light Locker set and I also and can not prevent the session locking after a short time of inactivity. I thought I had missed some other setting somewhere down the line, I have had this issue since installing 14.10. I have added to the Bug report mentioned by the OP, although that bug seems specific to a Live Session.

**EDIT:** Recent updates seem to have given me the ability to turn off light-locker & hand power settings (ie. blank screen without locking) over to xfce power management. Light Locker itself still ignores 'Never Lock' setting.

---

### Post by pierre19 on 2014-09-26
hello

Thank you for showing me how to deactivate ! I have 14.04 xubuntu (LTS) on my computer, and I had it when I posted "up, because the bug is still there". Anyway, the bug is still there. I use normal session also.

---

