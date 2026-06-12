---
title: "Change &quot;Change Desktop Background&quot;..."
date: 2008-05-14
forum: Ubuntu Brainstorm
---

### Post by MDSmith2 on 2008-05-14
to "Appearance", "Desktop Look" or something like that because that does more than just change your background right?

---

### Post by MaX on 2008-05-14
> **MDSmith2 said:**
> to "Appearance", "Desktop Look" or something like that because that does more than just change your background right?

Personalise?
Change apperance?

---

### Post by Het Irv on 2008-05-14
+1
Thats a good idea you can change themes, desktop background, fonts, visual effects and more there.  I espesally like your Desktop look suggestion

---

### Post by MDSmith2 on 2008-05-14
Pardon my bad GIMP skills but look at this:

---

### Post by Het Irv on 2008-05-14
Yeah, fonts a little big, but hey, I suck at GIMP too.  Could this be changed by the user, you know somewhere deep in the bowels of the filesystem?

---

### Post by MDSmith2 on 2008-05-14
> **Het Irv said:**
> Yeah, fonts a little big, but hey, I suck at GIMP too.  Could this be changed by the user, you know somewhere deep in the bowels of the filesystem?
I don't think so it seems that that gtk menu would be compiled:(.

I registered a blueprint for this [here]("https://blueprints.launchpad.net/ubuntu/+spec/change-changebackground").

---

### Post by Awalton on 2008-05-15
We currently hardcode the string (in at least one location I'm aware of off the top of my head... since I was just working on that code...):

nautilus/src/file-manager/fm-desktop-icon-view:line 700:
```

	  N_("Change Desktop _Background"), NULL,

```

This string is mostly (very) historical. It's easy enough to change, but it does trigger a re-translation, so if the Ubuntu people want to retranslate it for us... I've got no objections (and I don't think any of the rest of the developers have a significant investment in it, other than we get requests on a weekly basis to change strings for some reason or another...) We have an upstream bug for this: [http://bugzilla.gnome.org/show_bug.cgi?id=467527](http://bugzilla.gnome.org/show_bug.cgi?id=467527)

---

### Post by smartboyathome on 2008-05-15
I think change desktop background is appropriate. It is called Appearance in the preferences menu.

---

### Post by Het Irv on 2008-05-15
> **Awalton said:**
> We currently hardcode the string (in at least one location I'm aware of off the top of my head... since I was just working on that code...):

nautilus/src/file-manager/fm-desktop-icon-view:line 700:
```

	  N_("Change Desktop _Background"), NULL,

```

This string is mostly (very) historical. It's easy enough to change, but it does trigger a re-translation, so if the Ubuntu people want to retranslate it for us... I've got no objections (and I don't think any of the rest of the developers have a significant investment in it, other than we get requests on a weekly basis to change strings for some reason or another...) We have an upstream bug for this: [http://bugzilla.gnome.org/show_bug.cgi?id=467527](http://bugzilla.gnome.org/show_bug.cgi?id=467527)

Thanks for posting that, I see a Dev already thanked you for that, so this might actually happen.  This is what is great about having a community that is so involved, usually one person has the idea, and someone else knows how to do it.  With a strong community, those two people can meet and get things accomplished.  In my opinion, this is why Open Source is the best way to go.

---

### Post by zekopeko on 2008-05-15
how about Desktop Appearance?

it associates desktop (on which you right click) and appearance applet (any change here is reflected on the desktop so kind works logically )

---

### Post by Schendje on 2008-05-15
> **zekopeko said:**
> how about Desktop Appearance?

it associates desktop (on which you right click) and appearance applet (any change here is reflected on the desktop so kind works logically )

Yeah, I've always found the "Change Desktop Background" to make a lot of sense. After all, if you want to adjust something you usually right-click. To adjust the wallpaper, you right-click it.

It could be changed to "Change Desktop Appearance" and still link you to the Appearance window (and open with the first tab, "Theme", selected instead of going directly to "Background").

---

### Post by BlueSkyNIS on 2008-05-15
Maybe it's a better solution not to change right click text but to change what will appear on screen when you click it?

---

### Post by qamelian on 2008-05-15
> **BlueSkyNIS said:**
> Maybe it's a better solution not to change right click text but to change what will appear on screen when you click it?
Which is pretty much what you got up until a couple of versions of Gnome ago.

---

### Post by MDSmith2 on 2008-05-15
I am recompiling Nautilus now and will post results and a deb too if it works.
That way if you don't want it you don't have to have it.

---

### Post by smartboyathome on 2008-05-15
Perhaps if you are patching nautilus make it so that it is set to an environment variable instead of hard coded? That way you don't have to recompile or open gconf to change it.

---

### Post by Awalton on 2008-05-15
> **smartboyathome said:**
> Perhaps if you are patching nautilus make it so that it is set to an environment variable instead of hard coded? That way you don't have to recompile or open gconf to change it.

That's really a silly request, we usually reserve environmental variables for significant changes in functionality that can't be done at compile-time or to subvert other run-time procedures. It would really be even kind of silly to put it in gconf...

The really interesting, and more "correct", way to "fix" this would to be to change it in your locale (e.g. make an en_US translation) and change it there, but it's not ideal of course. Come up with a good proposal after battling it out here for a while, then post it to the upstream bug, and we'll see what we can do for you.

---

### Post by days_of_ruin on 2008-05-15
Leave it how it is.Don't confuse the newbs.

---

### Post by Het Irv on 2008-05-16
> **days_of_ruin said:**
> Leave it how it is.Don't confuse the newbs.

It is confusing how it is now though.  Yes, you can change the Desktop background there, but that is only a small part of what you can do.  What ever it is changed to needs to be a general term, but not a vague one.

Change Desktop Appearance is good (thxs zekopeko)

---

### Post by smartboyathome on 2008-05-16
So, does Windows make it any better? I think not. [-(

---

