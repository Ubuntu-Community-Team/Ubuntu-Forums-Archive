---
title: "Booting to terminal"
date: 2013-03-25
forum: Ubuntu Development Version
---

### Post by LoganJ85 on 2013-03-25
i have been running Raring Ringtail since early March, and for the past 3 days whenever I boot my laptop, it boots to a terminal. From there, I attempt to startx, and it pops up a window "Failed to load session (Gnome)", and then sends me right back to the terminal. I then issue sudo reboot and XFCE loads as if nothing happened. I have not fully established a pattern for how often this happens, but I believe it is happening everytimg I cold boot or reboot the laptop it will first load a terminal.

My laptop is an HP DM1Z with an AMD E-350. The only other oddities I have noticed are that everytimg the laptop boots I see a DBus message that state "KVM disabeled by BIOS" - that happens both when it loads a terminal or a XFCE session. Am I using the proper command (startx) to attempt to load XFCE or is there something else I should try?

Also, I have two competely unrelated and minor annoyances. Everytime I boot the laptop or lock the screen, the brightness gets reset to 100%, I prefer to have the brightness on this screen much lower, is this normal behavior? Next, the bluetooth on the laptop is always switched on when I boot the laptop, I would prefer to have it off (I assume that might save a little batter life since I never use the bluetooth), is there a way to change this?

---

### Post by wojox on 2013-03-25
Try:
```
sudo service lightdm start
```

---

### Post by LoganJ85 on 2013-03-25
Well, I have come to discover that lightdm apparently does not seem to fail when rebooting all the time, it seems to only happen after installing updates. The command to start lightdm worked perfectly to get me back to XFCE, thanks! I also noticed as soon as XFCE booted there was a crash detected with /usr/sbin/lightdm and I have submitted the crash report.

Now the question is, is this just a problem that will be fixed in later updates, or is there actually a problem with my system that I need to address.

---

### Post by wojox on 2013-03-26
Lightdm get's started fairly late in the init process, for example, the system dbus must to be already started, the filesystem has to be ready, and the graphics display system must be ready. [ source - How a user GUI session get's started with Ubuntu 12.04 ]("http://askubuntu.com/a/150488/2973"). 
Did this just start happening?

---

### Post by LoganJ85 on 2013-03-26
I first noticced lightdm failing last Saturday, I see that you mentioned how important timing is in the process, I doubt it makes a difference but I do have an SSD (Crucial M4, it's been in the laptop since I got it) installed in this system. This might be entierly a placebo effect but Xubuntu does seem to booting much faster the last few days.

---

