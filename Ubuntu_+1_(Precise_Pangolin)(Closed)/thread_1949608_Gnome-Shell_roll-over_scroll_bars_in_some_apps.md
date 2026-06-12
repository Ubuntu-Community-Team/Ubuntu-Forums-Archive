---
title: "Gnome-Shell: roll-over scroll bars in some apps"
date: 2012-03-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-03-30
Hello All

In Gnome-Shell, I'm seeing the unity style roll-over scroll bars in Nautilus and Gedit, but normal ones in LibreOffice and Firefox.

Any way to get ordinary scroll bars everywhere in a gnome-shell session and unity style roll-over scroll bars in a Unity session?

PS: fresh install from xubuntu image, with ubuntu-desktop and gnome-shell installed

---

### Post by jbicha on 2012-03-30
To disable the scrollbars, you should be able to run

```
gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false
```You'll need to restart any apps (logging out might be easiest). And to restore them, run

```
gsettings reset org.gnome.desktop.interface ubuntu-overlay-scrollbars
```Alternatively, you could do it with dconf-editor. I've added this tip to the Help that will be installed by default in Ubuntu 12.04.

---

### Post by tista on 2012-03-31
Guys,
So sorry for disturbing your discussions, I have an idea for future request.

I suppose now seems the time to take apart Unity dconf path from standard Gnome path... Yeah sometimes these desktop sessions might make conflicts on the same dconf patch in same time.

Like appmenu, overlay-scrollbar, gtk theme, nautilus desktop handling, compiz/mutter window buttons layouts, and much more...

In fact Unity is not a Gnome3 application, even not a gnome session. But it still using dconf path what are used to run gnome3 session... If so natrally those configurations would take an effects each other between "unity specific confs" and "standard gnome confs". Anyone devs could concern about the new docnf path like "org.unity...."? ;)

Regards,
Tista

---

### Post by keithpeter on 2012-03-31
> **jbicha said:**
> To disable the scrollbars, you should be able to run

```
gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false
```

I've added this tip to the Help that will be installed by default in Ubuntu 12.04.

That's great jbicha, I'll try it on the USB stick persistent live image.

I'm hoping for more *independence* between the gnome-shell and unity sessions in future cycles but I imagine that will be a byproduct of unity feature development.

@tista: does XFCE have its own dconf path (or use something different)? The XFCE session seems more 'independent' of Unity, but that could simply be different applications being used.

---

### Post by jbicha on 2012-03-31
tista, I'm not sure I understand what you're saying. And keith, I don't know what you mean by independence between GNOME Shell & Unity.

For 12.10, one idea with a good chance of happening is the creation of a new metapackage that will override the Ubuntu defaults so that it will be easier to have a more vanilla GNOME experience. For instance, Adwaita will be the default theme instead of Ambiance. And it's looking likely that there will be a gnome-control-center and a ubuntu-control-center.

---

### Post by PaulW2U on 2012-03-31
> **jbicha said:**
> For 12.10, one idea with a good chance of happening is the creation of a new metapackage that will override the Ubuntu defaults so that it will be easier to have a more vanilla GNOME experience.

I like the sound of this. I've seen a number of posts from users who want to use Gnome Shell but not Ubuntu's version of it.

---

### Post by keithpeter on 2012-03-31
> **jbicha said:**
> And keith, I don't know what you mean by independence between GNOME Shell & Unity.

I mean that running a Unity session gives you Unity defaults, like the roll-over scroll bars, and that logging out and selecting a Gnome session gives you Gnome defaults.

> **jbicha said:**
> For 12.10, one idea with a good chance of happening is the creation of a new metapackage that will override the Ubuntu defaults so that it will be easier to have a more vanilla GNOME experience. 

That's close to what I'm on about, but 'metapackage' sounds as if it may alter the Unity desktop session experience after installation.

---

### Post by jbicha on 2012-03-31
Keith, cross-desktop settings sharing is not a bug.

It's not a good idea to attempt to have Adwaita as the default theme in GNOME Shell & Ambiance as the default for Unity.

---

### Post by keithpeter on 2012-03-31
> **jbicha said:**
> It's not a good idea to attempt to have Adwaita as the default theme in GNOME Shell & Ambiance as the default for Unity.

Yup, just worked that out :twisted:

Looks like separate partitions for a Gnome Shell experience and a Unity experience then. Thanks.

---

