---
title: "Disappearing Skype"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zaphod_es on 2012-04-17
Skype works fine in the final beta until the little X to shut the program is clicked.  It then goes away but it still running.

It does not show up with alt + tab. There is no task bar. The Skype icon does not have the little arrow to show that it is running. If I try to open Skype again it just complains that it is already open. All I can do is kill Skype using the terminal (which is why I just asked how to kill an app using the gui) and start it again.

There is no problem if the user remembers to minimise Skype not click the close icon.

ZB

---

### Post by kaldor on 2012-04-17
This is a design issue. Skype for Linux is supposed to "Hide" in the system tray. Since Ubuntu uses a custom notification system (indicators), this feature isn't properly addressed. Use the terminal command "killall skype" to kill Skype.

You'll need to whitelist Skype in the notification area:

[http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html](http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html)

---

### Post by gandalf3 on 2012-04-17
when that happens to me theres a little skype icon up on the right side of the screen:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216188&stc=1&d=1334694663[/IMG]i have to click on it and select "quit".
dunno if you have the same thing, but hope this helps!

---

### Post by zaphod_es on 2012-04-18
Thanks gandalf3, your screenshot shows what I expected to see here but did not.  Kaldor's solution sorted that out. Thanks for the help.

ZB

---

