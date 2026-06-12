---
title: "Disable Start-Up Applications"
date: 2014-02-05
forum: Server Platforms
---

### Post by shadin2 on 2014-02-05
Hello there,

[COLOR=#333333][FONT=UbuntuRegular]I followed [/FONT][/COLOR][this tutorial on youtube]("http://www.youtube.com/watch?v=Jw3jlemIrd0")[COLOR=#333333][FONT=UbuntuRegular] to disable start-up applications in Ubuntu Sever 13.10. What happened is all unchecked apps are being checked again when I close then open the box! What should I do to keep them unchecked?


[/FONT][/COLOR]

---

### Post by TheFu on 2014-02-05
Use **update-rc.d** to manage services. This is the approved way on server platforms.

---

### Post by shadin2 on 2014-02-05
[COLOR=#444444][FONT=UbuntuRegular]Thanks, but this conf is for services, I'm already done with it. Now I locking for disabling unnecessary start-up applications[/FONT][/COLOR]

---

### Post by TheFu on 2014-02-05
Sorry - I wasn't on a system where I could watch the video and guessed what you meant.
Looks to my like /etc/xdg/autostart/ holds apps that are started per-user when you login.

I would venture a guess that removing them from that directory (make a backup first!) and logging out and back in would have the desired impact.  I do not know this will work or not, as I don't run a normal Ubuntu desktop.

The other thing might be to run that check-box app with gksudo before it - the settling seem to be system-wide so elevated privileges are needed.  Again, make a backup before trying this stuff.

[http://askubuntu.com/questions/69810/how-do-i-add-remove-the-hidden-startup-applications](http://askubuntu.com/questions/69810/how-do-i-add-remove-the-hidden-startup-applications) seems to say the same things that youtube video says - I don't see any mention of how to disable the apps, however. Doesn't seem like Canonical meant for anyone to change these things from a GUI.

---

