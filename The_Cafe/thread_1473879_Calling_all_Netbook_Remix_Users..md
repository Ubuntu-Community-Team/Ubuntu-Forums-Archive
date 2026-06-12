---
title: "Calling all Netbook Remix Users."
date: 2010-05-05
forum: The Cafe
---

### Post by ibuclaw on 2010-05-05
Netbook Remix Users - have you tried the alternate Netbook Edition Interface?

I really like it, so much I've switched to it in the main desktop session.

For those of you know can't tell the difference in the screenshot (see attached thumbnails) or simply don't know what I'm talking about. The package I speak of is named '**netbook-launcher-efl**'. It is an application inspired by the original netbook-launcher, but built using Enlightenment Libraries, rather than GTK. The end result is an application that uses less dependencies and overall feels alot less clunky in it's interaction.

You can try it out by logging out and selecting "Netbook Edition 2D" as the session, but note this will start pretty much a stark Ubuntu Desktop Session (panel on top and bottom) except with the application overlaying the wallpaper. Which is not really what I want in my netbook - it's very squished vertically.

So, I ended up diverting netbook-launcher and creating a link to netbook-launcher-efl
```

sudo dpkg-divert --local --rename --add /usr/bin/netbook-launcher
sudo ln -s /usr/bin/netbook-launcher-efl /usr/bin/netbook-launcher

```
Logout, then login. Et Voila!

Do any of you guys and gals have thoughts or opinions on it?

Regards
Iain

Note:
If you run the above, and wish to revert it do the following:
```

sudo unlink /usr/bin/netbook-launcher
sudo dpkg-divert --rename --remove /usr/bin/netbook-launcher

```

---

### Post by NormanFLinux on 2011-05-07
Come to think of it, the top global menu is used now in Unity with the left hand scrollbar launcher.

The UI is the default on OZ Unity. A Cairo dock runs well at the bottom of the interface with the Metacity compositing engine turned on. Maximus is set to undecorate so the panels don't disappear any more when you launch a program.

Canonical found the favorite panel too crowded and made it over into a scrollbar launcher and moved the default categories in the left hand side of the panel into a hidden global menu.

That change led to what is now known as Unity.

---

### Post by Quadunit404 on 2011-05-07
Necromancy...

---

### Post by Lucradia on 2011-05-07
> **NormanFLinux said:**
> That change led to what is now known as Unity.

No, that was the UNR UI of 10.04 and 9.10. The 10.10 used Unity with mutter. The one you see in that screenshot doesn't even use mutter/clutter.

---

### Post by NormanFLinux on 2011-05-08
If you look at the top bar, its the one used in Unity. My take is the global menu gave Canonical insight in how to reconfigure the UI to make more effective use of screen space and eliminate unwanted clutter.

The top bar + scrollbar launcher = Unity.

Unity in the 10.10 netbook edition didn't work very well. Now it does.

---

### Post by Lucradia on 2011-05-08
> **NormanFLinux said:**
> If you look at the top bar, its the one used in Unity. My take is the global menu gave Canonical insight in how to reconfigure the UI to make more effective use of screen space and eliminate unwanted clutter.

The top bar + scrollbar launcher = Unity.

Unity in the 10.10 netbook edition didn't work very well. Now it does.

The top bar is a gnome panel actually. (note the "Handle" on the Ubuntu icon, and the action menu to the right of the username, as well as the launchers next to the Ubuntu icon.) The ubuntu icon can be changed so that it only shows the icon (in 9.10 and earlier, you had to replace it with "GNOME Menu" applet to do this.)

10.10's top bar uses Unity.

---

### Post by ibuclaw on 2011-05-08
We have a mega thread on all unity discussion, so use it.

Closed for derailing and necromancy.

---

