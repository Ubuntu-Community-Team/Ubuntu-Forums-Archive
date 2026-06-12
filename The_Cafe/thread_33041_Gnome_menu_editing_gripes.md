---
title: "Gnome menu editing gripes"
date: 2005-05-09
forum: The Cafe
---

### Post by jwb on 2005-05-09
A friend was raving about KDE's latest edition, and so I  installed it to take a look at what KDE was up to. Anyway, after looking at KDE for a while (I am *not* going to get into the whole KDE vs. Gnome deal), I logged back into Gnome.

My Gnome menu is now full of KDE entries.

Yes, I installed SMEG. No, I can't seem to get it to delete entries. Not my point either.

Why in the world can't Gnome deliver us a way to edit menus that makes sense? This should've been something that was perfected, say, I dunno, in like chapter 2 of the Gnome story. W'ere already well into Gnome's history- and there's NO SIMPLE WAY TO EDIT MENUS. (Not hitting on smeg- I'm glad it's being worked on. My point is not aimed at smeg, but the need for it.)

Look, I love Linux. I use it every day. We use it for servers, mail, DNS, firewalls, desktops, everything.

But for all the work that's been done to make it compete on the desktop, how in the heck can menu editing be such a trip-up after so many years of development? Is there a piece of history I'm missing? I *HATE* trying to show someone the wonders of Linux/Ubuntu/Gnome/whatever and have to go "Oh, you can't do that".

C'mon- gimme a freakin' HTML file set up as an unordered list...... something. Half the time I've never even bothered putting the Gnome menu on the bar simply because I could never edit it to my satisifaction. Even the way it worked under Nautilus before was hit or miss.

Rant over.

---

### Post by jwb on 2005-05-09
And yes, I found the guide how-to on smeg .5, and the instructions, and all that. It doesn't seem like I can delete entries yet, with smeg- is that correct?

---

### Post by nevernamed on 2007-07-16
I'm having the same problem as you are. I can't remove kde entries from my gnome applications menu. Have you figured out how to do it?
[http://www.gnome.org/start/2.0/menuediting.html#removeentries](http://www.gnome.org/start/2.0/menuediting.html#removeentries)
Those instructions make no sense to me, so maybe they will to you?

Thanks in advance.

---

### Post by ThrobbingBrain66 on 2007-07-16
Try this guys:
[http://ubuntuforums.org/showthread.php?t=59455](http://ubuntuforums.org/showthread.php?t=59455)

there are a few methods in that thread, but I think post #4 probably would work the best.

---

### Post by ThinkBuntu on 2007-07-16
Haha...you should try editing a default GNOME menu (without Ubuntu's included editor) like in Debian or Arch with GNOME. Or try to get at the Apps in the Xfce menu.

---

### Post by nevernamed on 2007-07-16
> **ThrobbingBrain66 said:**
> Try this guys:
[http://ubuntuforums.org/showthread.php?t=59455](http://ubuntuforums.org/showthread.php?t=59455)

there are a few methods in that thread, but I think post #4 probably would work the best.

Yes #4 worked like a charm! Thanks. All though, I uninstalled netbeans 5.5.1 (switched back to 5.5) because it was too buggy and that is also still on the gnome menu (Applications>Programming). Any ideas on how to remove that? What do you mean in your post ThinkBuntu?

---

### Post by ThrobbingBrain66 on 2007-07-17
The ShowOnlyIn lines should've worked for all menu entries.  It's possible that you may have to manually find the .desktop file associated with netbeans and add the line...or maybe the ShowOnlyIn line doesn't work for netbeans.

---

### Post by nevernamed on 2007-07-17
where should I look for the .desktop file(s)?

---

### Post by ThrobbingBrain66 on 2007-07-17
There are a bunch of locations to look in:
```
/usr/share/app-install/desktop/
/usr/share/applications/
```
just to name a couple.

Your best bet will be to do a search on your Filesystem for the netbeans.desktop file.

Something like '*netbeans*.desktop' (without the tick marks obviously) should return a result, if not, just play with the query a little bit to see what you can find.

---

### Post by leupi on 2007-07-23
So should I  take all of this to indicate that there is no nice and easy GUI tool for editing the main menu in Gnome as there is with KDE? I am trying to add subfolders in the menu, such as 'Web Browsers' in the 'Internet' folder in 'Applications' to put all of my web browsers in; however, when I go into the menu editor and try and create it, it never shows up in the actual menu. Unless I am missing something, KDE has a much more intuitive menu editor.

Thanks,
Todd

---

