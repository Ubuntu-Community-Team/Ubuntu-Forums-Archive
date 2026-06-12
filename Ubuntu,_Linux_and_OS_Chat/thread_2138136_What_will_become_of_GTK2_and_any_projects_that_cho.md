---
title: "What will become of GTK2 and any projects that choose to stay with it?"
date: 2013-04-23
forum: Ubuntu, Linux and OS Chat
---

### Post by JohneG on 2013-04-23
I ask cause there are a few projects that i am aware of that seem to be staying with GTK2 and no plans to move onto GTK3. Is this something that will affect them in future? The main project in mind is Ardour. My understanding is that the main developer doesn't see the point in moving to GTK3 cause there aren't enough benefits. Is he right and if they stick with GTK2, are there problems down the road they might encounter in time? 

I know XFCE have some plans about moving to GTK3 at some stage but what about LXDE? Would it hold the project back to stick with GTK2? Any thoughts? Or any other examples of projects that don't seem to have plans to move onto GTK3? Also, did similar happen with the move from GTK1 to GTK2?

---

### Post by szymon_g on 2013-04-23
well... sooner or later the old versions of those libraries will have their support ceased... since it's open source someone else would be able to take care- but i somehow doubt so.
i'd not get too familiar with apps using gtk2 - they will be, at some point, either ported to gtk3 or, in time, became less and less useful... and after gtk2 will be ruled out of standard repositories, their installation will be even harder.
And how many apps written in gtk1 can you see now :)?

---

### Post by Paqman on 2013-04-24
> **JohneG said:**
> The main project in mind is Ardour. My understanding is that the main developer doesn't see the point in moving to GTK3 cause there aren't enough benefits.

In the short term that will be fine, but eventually it will become more of a hassle to cling to GTK2 and they'll be forced to change.

---

### Post by TeamRocket1233c on 2013-04-24
What about MATE?

---

### Post by tgalati4 on 2013-04-24
Mate seems to have an active community and that will keep gtk2 around for a while.  I suppose older applications could be compiled statically to have gtk2 libraries built-in and remove external dependencies, but then how they behave in newer Desktop Environments will be an issue.  I've seen older Motif applications run fine in Mate, they look ugly, but they work.

Each package maintainer will have to look at the code and the agony units involved in rewriting applications to go from gtk2 to gtk3 or QT4 or Adobe Air:shock: whatever.  Frameworks seem to be constantly changing.

---

### Post by Jonor on 2013-04-25
Apparantly Fuduntu is to be wound down due to [gtk2 issues]("http://www.linuxinsider.com/story/Farewell-Fuduntu-The-Untimely-Demise-of-a-Winning-Linux-Distro-77850.html").

---

### Post by vasa1 on 2013-04-25
> **Jonor said:**
> Apparantly Fuduntu is to be wound down due to [gtk2 issues]("http://www.linuxinsider.com/story/Farewell-Fuduntu-The-Untimely-Demise-of-a-Winning-Linux-Distro-77850.html").
This also played a part: "the move of the Linux world to systemd has caused a problem for Fuduntu as it has become a required thing for many programs, but we do not use it. " from the official blog here: [http://www.fuduntu.org/blog/2013/04/15/fuduntu-team-meeting-held-on-april-14-2013/](http://www.fuduntu.org/blog/2013/04/15/fuduntu-team-meeting-held-on-april-14-2013/)

---

### Post by hainen on 2013-05-07
> **szymon_g said:**
> well... sooner or later the old versions of those libraries will have their support ceased... since it's open source someone else would be able to take care- but i somehow doubt so.
i'd not get too familiar with apps using gtk2 - they will be, at some point, either ported to gtk3 or, in time, became less and less useful... and after gtk2 will be ruled out of standard repositories, their installation will be even harder.
And how many apps written in gtk1 can you see now :)?

xmms

---

### Post by mips on 2013-05-07
Adapt or die...

---

### Post by diesch on 2013-05-07
Gtk2 will be around in most distributions for a few more years, just like Gtk1 did after Gtk2 was released. But eventually distributions will stop shipping Gtk2 and the remaining projects still using Gtk2 will die.

---

### Post by Frogs Hair on 2013-05-07
[COLOR=#000000]Post 10 covers what will happen pretty well . The 10.04 desktop is EOL in two days and other ties to Gnome 2 will be cut as things progress.    [/COLOR]

---

### Post by diesch on 2013-05-07
> **Frogs Hair said:**
> [COLOR=#000000]Post 10 covers what will happen pretty well . The 10.04 desktop is EOL in two days and other ties to Gnome 2 will be cut as things progress.    [/COLOR]

Most of the Gnome2 libs are still there in 13.04, so most apps will run.

---

### Post by ssam on 2013-05-08
gtk2 will still be around for a long time (like gtk1 was after gtk2 was released). Redhat EL6 has gnome2 and will be supported until 2020. RHEL7 will still have gtk2 (unless they are planning some epic porting work), and that will likely be supported until 2023 or 2024.

---

