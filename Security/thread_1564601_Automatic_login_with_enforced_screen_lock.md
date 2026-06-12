---
title: "Automatic login with enforced screen lock"
date: 2010-08-30
forum: Security
---

### Post by Leeteq on 2010-08-30
Is there a way to set Linux to automatically log in to a specific user account and at the same time lock the screen? I want to save time and trigger various software that always should start up on boot, while leaving the computer unattended during startup (extra important and practical for remote control boots), by enforcing a 'screen lock' so that no-one can see what happens behind the login screen without entering the login credentials.

---

### Post by zpletan on 2010-08-30
(I assume you are using a GNOME environment.)

System->Administration->Login Screen
 > Set yourself to auto-login

System->Preferences->Screensaver
 > Make sure the box is checked to "Lock screen when screensaver is active"

System->Preferences->Startup Applications
 > Click "Add"
 > Give it a nice name and comment
 > The command you want (put this in without quotes) is "gnome-screensaver-command -a"

This won't necessarily start the screensaver/screen lock immediately (so far as I know), but it will start it as part of the login sequence.

---

### Post by FuturePilot on 2010-08-30
gnome-screensaver-command -a just activates the screensaver. I believe you want gnome-screensaver-command -l which will lock it. It would probably be a good idea to do something like ```
sleep 10; gnome-screensaver-command -l
``` to give gnome-screensaver a change to start, otherwise the command may just fail, I'm not quite sure though.

---

### Post by zpletan on 2010-08-30
If you use the -l flag, you don't need to fool with settings in the Screensaver dialog.  If, in the Screensaver dialog, you set it to lock when the screensaver is active, the -a flag will also lock your screen.

---

### Post by Helkaluin on 2010-08-31
The 'xdg-screensaver' command should be preferable over calling specific DE screensavers.

Or, to avoid the entire waiting-for-screensaver-to-start-before-calling-the-locking problem, have a look at xtrlock.

---

