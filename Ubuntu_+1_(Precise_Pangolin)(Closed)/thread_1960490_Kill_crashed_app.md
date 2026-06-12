---
title: "Kill crashed app"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zaphod_es on 2012-04-17
How do I kill a crashed app in the final beta?

I don't think I can teach my 87 year old mother to bring up a terminal a run "ps aux" pipe it to grep and look for the app name then run the kill command on the process numbers.  There must be something easier.

ZB

---

### Post by philinux on 2012-04-17
> **zaphod_es said:**
> How do I kill a crashed app in the final beta?

I don't think I can teach my 87 year old mother to bring up a terminal a run "ps aux" pipe it to grep and look for the app name then run the kill command on the process numbers.  There must be something easier.

ZB

You can use xkill.

[http://askubuntu.com/questions/90773/how-to-kill-non-responsive-gui-task-under-unity](http://askubuntu.com/questions/90773/how-to-kill-non-responsive-gui-task-under-unity)

---

### Post by philinux on 2012-04-17
Found this,.

[http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher/](http://www.omgubuntu.co.uk/2011/10/force-quit-applet-unity-launcher/)

The comments are the interesting bit.

---

### Post by mc4man on 2012-04-17
The applet could be a good way, keeps it above everything

If not I have it as a quicklist entry in a utilities icon but you could also just create a standalone launcher (.desktop) and add to the launcher to run 'Force Quit'

I'd try the applet first but otherwise
```
mkdir -p ~/.local/share/applications && \
gedit ~/.local/share/applications/kill-app.desktop
```
```
[Desktop Entry]
Version=1.0
Type=Application
Exec=xkill  
Name=Force Quit
Icon=/usr/share/icons/Humanity/actions/48/process-stop.svg
```
Then just go to ~/.local/share/applications & drag on to launcher

free to use any Icon=  &  Name= desired

whatever you do show her what to do if she accidentally clicks the X on the desktop (click on the Home folder icon

---

### Post by zaphod_es on 2012-04-17
Thanks philinux, that is an interesting thread.

In fact it does not actually solve my problem which I described in a different post about Skype at the same time as I started this thread.

Skype is neither visible nor minimised but still running in the background after the X at the corner is clicked. As my Mother is unable to bring it back to the foreground the only solution is to kill it.

Is there something like the Mac Activity Manager or Windows Task Manager that shows the running processes with the option of killing them?

ZB

---

### Post by mc4man on 2012-04-17
Then try adding Skype to the unity panel systray 
(don't have skype so can't check, know it used to work

---

### Post by mcellius on 2012-04-17
In System Monitor, under the "Processes" tab, if you can find the process you can highlight it and press the "End Process" button.  Will that work in your situation?

---

### Post by zaphod_es on 2012-04-18
mc4man's suggestion works nicely, thanks.

The Skype problem is also sorted using this
[http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html)

Thanks for the help.

ZB

---

