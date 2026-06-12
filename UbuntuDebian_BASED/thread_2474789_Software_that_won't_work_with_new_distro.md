---
title: "Software that won't work with new distro"
date: 2022-05-08
forum: Ubuntu/Debian BASED
---

### Post by ray42 on 2022-05-08
I used Pop disro from Sytem76

I've been using Day Planner for years now, It works with Ubuntu, Gnome and also Pop OS.

It worked with Pop 18.04LTS and 20.04LTS no issues. I've now moved to 22.04LTS and I get the following error

[https://pasteboard.co/d0J0gqzs4A25.png](https://pasteboard.co/d0J0gqzs4A25.png)


I have tried lots of planners and none meet the grade of simplicity.  I've looked at  and tried lots from a list of about 30. The notification stays on screen until clicked, so to me Day Planner is No 1 top dog. 

Is there any way to box this as an entity to work on my new system. Sorry I do not have the technical terminology.

Tux Diary did not work:

[http://tuxdiary.com/2016/07/30/day-planner/](http://tuxdiary.com/2016/07/30/day-planner/)

---

### Post by TheFu on 2022-05-08
I don't know. 

I looked for day-planner and dayplanner sofware and didn't find anything.  Could you be more specific?

Until my workload outgrew it in the early 2000s and I spent about a year trying other options before hitting on GTD.  [https://lifehacker.com/practicing-simplified-gtd-335269](https://lifehacker.com/practicing-simplified-gtd-335269)  The simplified version is useful, but I outgrew it.

I wasted a few months looking for GTD-specific software tools before deciding that a tabbed spreadsheet could handle everything and free me from data lock-in. By using a spreadsheet, I'd solved my cross-platform and universal access requirement.
Below is an older, sanitized, copy of my GTD spreadsheet. Hope it is helpful to someone.

---

### Post by #&amp;thj^% on 2022-05-08
> **ray42 said:**
> 

It worked with Pop 18.04LTS and 20.04LTS no issues. I've now moved to 22.04LTS and I get the following error

Is there any way to box this as an entity to work on my new system. Sorry I do not have the technical terminology.

Tux Diary did not work:

[http://tuxdiary.com/2016/07/30/day-planner/](http://tuxdiary.com/2016/07/30/day-planner/)
I use it as a flatpak: [https://flathub.org/apps/details/com.github.alainm23.planner](https://flathub.org/apps/details/com.github.alainm23.planner)
You will have to install "flatpak" and reboot if not installed already.
More: [https://www.addictivetips.com/ubuntu-linux-tips/install-day-planner-linux/](https://www.addictivetips.com/ubuntu-linux-tips/install-day-planner-linux/)

---

### Post by ray42 on 2022-05-08
> **1fallen said:**
> I use it as a flatpak: [https://flathub.org/apps/details/com.github.alainm23.planner](https://flathub.org/apps/details/com.github.alainm23.planner)
You will have to install "flatpak" and reboot if not installed already.
More: [https://www.addictivetips.com/ubuntu-linux-tips/install-day-planner-linux/](https://www.addictivetips.com/ubuntu-linux-tips/install-day-planner-linux/)

Ah, you misunderstood it's "Day Planner" not Planner

[https://www.day-planner.org/](https://www.day-planner.org/)

The flatpak link is for "planner"

---

### Post by ray42 on 2022-05-08
Day Planner

[https://www.day-planner.org/](https://www.day-planner.org/)

---

### Post by #&amp;thj^% on 2022-05-08
Your install failed because of missing "libgtk2-perl" Day Planner that hasn't been maintained for a few years now I believe since 2017 made in 2012.
Until someone picks it up and build current "libs" your out of my depth.

---

### Post by ray42 on 2022-05-10
Okay, aww. It was a great little app.

I could use Gnome Calendar for reminders but the notification disappears if I accidentally role the mouse over it. I assume this is the same for all that use  Gnome Calendar.

Does anyone know how to make it stay on screen until I click close?

---

### Post by TheFu on 2022-05-10
> **ray42 said:**
> Does anyone know how to make it stay on screen until I click close?

Thunderbird has a built-in calendar and reminders don't disappear until either sleep or ok is selected.  It is really annoying sometimes.  I suppose the thunderbird notification could be due to my window manager not supporting the notification standard. IDK.  I do know that sometimes when I'd like to sleep a notification for a day or two, sometimes thunderbird can't communicate that desire to my central calendar server until I restart thunderbird. What I find really odd is that email message actions going to the same system don't have the 'ignore my update' aspect.  Hummmm.

---

### Post by ray42 on 2022-05-10
Yes, great, thanks.

I've contacted the developer. Let's wait and see.

---

### Post by ray42 on 2022-05-16
I have found an alternative but don't know how to get this to open at start up.

It's called CoreTime from CuboCore

[https://cubocore.org/](https://cubocore.org/)

---

### Post by TheFu on 2022-05-16
In Unix systems, startup and login are very different.  We cannot start any GUI program at startup, but we can make it begin when a GUI session begins.  The way that is accomplished is based on the window manager or DE.  The Ubuntu Desktop Guide has the answer for stock Ubuntu Gnome3/4 systems. You'll want to find the guide for the specific GUI you use and the release you use for how to do it.  The 22.04 Ubuntu Gnome Desktop Guide is here: [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)  The help search on that page found this: [https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en)

---

### Post by ray42 on 2022-05-16
> **TheFu said:**
> In Unix systems, startup and login are very different.  We cannot start any GUI program at startup, but we can make it begin when a GUI session begins.  The way that is accomplished is based on the window manager or DE.  The Ubuntu Desktop Guide has the answer for stock Ubuntu Gnome3/4 systems. You'll want to find the guide for the specific GUI you use and the release you use for how to do it.  The 22.04 Ubuntu Gnome Desktop Guide is here: [https://help.ubuntu.com/stable/ubuntu-help/](https://help.ubuntu.com/stable/ubuntu-help/)  The help search on that page found this: [https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en)

Ah, I should have been more specific. Yes I do generally know this information. But specifically for this program I do not.

See image I provide. It shows an example start up command for another app.

[IMG]https://pasteboard.co/tThK50TDsuSg.png[/IMG]
[IMG]https://pasteboard.co/tThK50TDsuSg.png[/IMG]
[https://pasteboard.co/tThK50TDsuSg.png](https://pasteboard.co/tThK50TDsuSg.png)

So how do i find the command or path for this app?

---

### Post by #&amp;thj^% on 2022-05-16
Just add it to your startup applications.
The command is:
```
flatpak run org.cubocore.CoreTime
```

---

### Post by ray42 on 2022-05-16
Excellent!

Thank you.

---

