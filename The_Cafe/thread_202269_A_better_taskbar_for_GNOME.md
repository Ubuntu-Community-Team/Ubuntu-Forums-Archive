---
title: "A better taskbar for GNOME"
date: 2006-06-23
forum: The Cafe
---

### Post by magnusbb on 2006-06-23
Hello,

I am using Dapper as a student, and I work with documents, images, audio.... things that require a well-structured file system, a good filemanager, and seamless window-management. With Beagle, things have gotten better for me.

But, things that does not work so well in Ubuntu Dapper (maybe GNOME as such), are the taskbar and the window management:

1) When I double-click a document, the Openoffice program will open, not as the front-most window, but actually as a window hidden behind the Nautilus windows. Has someone else experienced this? It's annoying, and it happens all the time. I have experienced it with other applications than OpenOffice too... but not so often.

2) Another thing is, that every time I open a document, while the Openoffice program is already open, I get this "Opening..." staying on the taskbar long after the process is finished. This is also not unique to OpenOffice, but most frequent there.

It would be great, if anyone had a suggestion to what I could do about those two things. Is my configuration wrong, or are these just bugs, that need to be fixed?

Magnus

---

### Post by Kimm on 2006-06-23
Whats wrong with the taskbar?

Anyway, your windowmanagement problems are easily fixed.
Type this in your terminal:

sudo apt-get install xfwm4

Then (what this finnishes), go to, Preferences -> Sessions, then select the tab "Current Session"

Before you do this, make sure you have a terminal open, and try to close any big windows (not just minimize). Now, there should be a list in the Sessions window, find an entry called "metacity", select it, and press Remove followed by Accept.

Now you should find yourself in a pretty strange situation... but dont worry, we'll fix that.

Now, select that terminal that you left open and type:

xfwm4

You should now get window manegement again.

Logout and make sure to save the session :)

---

### Post by magnusbb on 2006-06-23
Perhaps the title is a bit misleading. What I meant with the taskbar, was the "Opening..." thing mentioned - thing "opening..." while they're actually already opened.

Thanks for your xfwm4 suggestion. I'll have a look at it. Are there any drawbacks using a different window manager than that supported by the GNOME team - like for example xfwm4?

---

### Post by Kimm on 2006-06-23
Ah, I see

Not realy... the only noticable thing is that you wount be able to change the window managers theme in the Gnome Theme Manager... to do that you need to get the XFCE4 Settings Manager... I acctually dont know what you want to install to get that... I'll look into it
But it will integrate nicely into your Gnome desktop, as it uses GTK2 just like metacity

Edit: You'll want to install: xfce4-mcs-manager
Then run: xfce-setting-show, to get the XFCE4 settings manager :) check out the "Gelly theme" I think it blends better than most others.

and you'd want this to: xfwm4-themes

---

### Post by magnusbb on 2006-06-23
xfwm4 works great - it's fast, and has lots of features... and best of all, it fixes my problem!

But... there's a but here... it introduces new problems... compatibility with the taskbar... flashing elements... and unexpected behavoir.

---

### Post by Kimm on 2006-06-23
Huh?

compatability with the taskbar?? :S
I never had that problem... care to elaborate?

I dont get the others eighter :-P

---

