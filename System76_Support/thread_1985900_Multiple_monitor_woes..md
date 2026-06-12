---
title: "Multiple monitor woes."
date: 2012-05-24
forum: System76 Support
---

### Post by xakh on 2012-05-24
I'm trying to set up multiple monitors, but I would like the second one to be in a different virtual desktop than the first one, because they're vastly different resolutions, and I'd rather have that than a weird desktop with a seam in the middle of it and an odd sense of scale. Is this possible?

Attached is a picture of my setup. I know it probably won't help much. I believe I have a panp6, or a panp7, I can't remember which.

[ATTACH]218618[/ATTACH]

---

### Post by madverb on 2012-05-24
That should work fine. I've connected a second monitor to a laptop with a different resolution than the laptop and it has worked instantly.

---

### Post by xakh on 2012-05-24
Well, when I try to turn it on, it keeps saying something about the virtual size not fitting the requested space, so it just sits next to my laptop, off and doing nothing. Furthermore, what I'm looking to do is have one virtual desktop (e.g. "Workspace 1"), in my main screen and another (e.g. "Workspace 2") on the other monitor, that way I can use the two monitors without it treating the screen as one massive unbroken pane.

---

### Post by isantop on 2012-05-24
> **xakh said:**
> Well, when I try to turn it on, it keeps saying something about the virtual size not fitting the requested space, so it just sits next to my laptop, off and doing nothing. Furthermore, what I'm looking to do is have one virtual desktop (e.g. "Workspace 1"), in my main screen and another (e.g. "Workspace 2") on the other monitor, that way I can use the two monitors without it treating the screen as one massive unbroken pane.

I've always found the proprietary driver to be vastly inferior to the OSS drivers on my PanP7, particularly for Multi-monitor. If you remove them, then when you plug in the external monitor it should just turn on.

---

### Post by osx424242 on 2012-05-24
> **xakh said:**
> I'm trying to set up multiple monitors, but I would like the second one to be in a different virtual desktop than the first one

I haven't tried this (and don't think I'd like it! :lolflag:) but it sounded really interesting so I looked it up.  I found two references that suggested XMonad:
- [http://askubuntu.com/questions/21711/multiple-monitors-multiple-workspaces](http://askubuntu.com/questions/21711/multiple-monitors-multiple-workspaces)
- [http://superuser.com/questions/338784/is-there-a-linux-window-manager-that-allows-separate-virtual-desktops-workspace](http://superuser.com/questions/338784/is-there-a-linux-window-manager-that-allows-separate-virtual-desktops-workspace)

So it sounds like you may be able to get what you want, but it may take a  non-trivial amount of work to get there (in other words: don't forget to write down your process as you figure it out, and back up your configuration files when you're done!).

---

