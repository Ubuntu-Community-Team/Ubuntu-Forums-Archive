---
title: "specto 0.2 for edgy and feisty"
date: 2007-02-11
forum: The Cafe
---

### Post by kiddo on 2007-02-11
Hello folks,
I wanted to notify the ubuntu community that Specto 0.2 is out for your great enjoyment and bleeding-edge thirst ^_^
[IMG]http://specto.sourceforge.net/i/screenshots/2007%2002%2008%201.png[/IMG]
[QUOTE="Specto's website"]Specto is a desktop application that will watch configurable events (such as website updates, emails, file and folder changes, system processes, etc) and then trigger notifications. For example, Specto can watch a website for updates (or a syndication feed, or an image, etc), and notify you when there is activity (otherwise, Specto will just stay out of the way). This changes the way you work, because you can be informed of events instead of having to look out for them.[/QUOTE]

It might get into Feisty's universe in the next few days. In the meantime, you can download  the [**Specto 0.2 ubuntu package**.](http://specto.googlecode.com/files/specto_0.2.0-0ubuntu3_all.deb)

I would like you to test this, give feedback, impressions, etc. Have fun :) . Relevant links, if needed:
[LIST]
[*][Google code page]("http://code.google.com/p/specto/") (downloads, bug tracker, source code in SVN)
[*][Official website]("http://specto.sf.net")
[*][Documentation]("http://specto.ecchi.ca")
[*][0.2 release announcement]("http://kiddo.ecchi.ca/blog/?p=163")
[/LIST]

---

### Post by kiddo on 2007-03-06
Just bumping this up to notify those who are interested that **Specto is now available in Feisty Fawn's universe** today :)

---

### Post by gardara on 2007-03-06
Wow, that's a nice application. Glad I saw this thread.

---

### Post by K.Mandla on 2007-03-06
I think this might be something I have been looking for, for about a year. ... :shock:

---

### Post by raublekick on 2007-03-06
oh wow, i remember when this was conceived, good to see it is making good progress! i will give it a go if i have time this week.

---

### Post by Nikron on 2007-03-06
Huh, I think I clicked to show specto as a tray icon and without a thing on the window list, but now I can't seem to find specto on my tray...  Does it only go to the tray when something changes?  And if I run specto, nothing happens that I can see.

---

### Post by H.E. Pennypacker on 2007-03-06
> **Nikron said:**
> Huh, I think I clicked to show specto as a tray icon and without a thing on the window list, but now I can't seem to find specto on my tray...  Does it only go to the tray when something changes?  And if I run specto, nothing happens that I can see.

After I installed it, it was on the tray, but one day, it disappeared.  Sure, I could add it again, but it probably will disappear again.  Same thing happens with a few other tray icons.

---

### Post by kiddo on 2007-03-07
The default behavior (to stick to the HIG) is to have the tray icon (actually, a notification icon) appear only when there are updates (a bug report [was filed here]("http://code.google.com/p/specto/issues/detail?id=46") and I gave some explanation).

Now if you deactivate the window list thing and the tray icon is not there to allow you bringing the notification window to the front, you're somewhat screwed (the "hide from the window list" option is somewhat dangerous in that sense). I guess the only way to show it again would be alt-tabbing.

Take note that if the notification icon is not set to "always on", closing the notifier window will quit Specto.

H.E. Pennypacker: huh, my notification icon never disappears even if I killall gnome-panel... speaking of which, that made me discover a bug with gtk.statusicon, it now becomes a floating window by itself! ^^; I'll have to see if there is a solution to just attach it back to the notification area.

K.Mandla: heheh, glad to see that helped you :)

---

### Post by frodon on 2007-03-07
Looks just great, i will surely use it ;)

---

