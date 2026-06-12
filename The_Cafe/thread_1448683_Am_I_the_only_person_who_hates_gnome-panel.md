---
title: "Am I the only person who hates gnome-panel?"
date: 2010-04-06
forum: The Cafe
---

### Post by clonne4crw on 2010-04-06
I spent like 15 minutes rearranging all the icons and applets, reboot, and its all gone. Are there any fixes for this that actually work? I love Gnome, but hate the way the panels save their settings. 

Grrrrr.

---

### Post by oldsoundguy on 2010-04-06
silly question:  Did you LOCK your changes to the panels before re-booting?

---

### Post by clonne4crw on 2010-04-06
> **oldsoundguy said:**
> silly question:  Did you LOCK your changes to the panels before re-booting?

Sure did.

---

### Post by FuturePilot on 2010-04-06
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/44082]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/44082")

---

### Post by Psumi on 2010-04-06
Am I the only one who hates gnome-shell? </sarcasm>

---

### Post by aklo on 2010-04-06
What is a gnome panel? The one at the top??

If it is the one at the top, i don't see what the settings are not saved. I have some program icons there myself..nothing sophisticated like yours..i don't even need to do a thing and they will be there the nxt time i restart.

---

### Post by phrostbyte on 2010-04-06
I don't use gnome-panel (but I use Gnome). :)

---

### Post by NightwishFan on 2010-04-07
Everyone hates gnome shell, just like KDE4 when it came out. Yes, the panel is about as problematic as it is cool. I think so too, but it still works well for me.

---

### Post by cariboo on 2010-04-07
I don't hate gnome-shell, I use it 98% of the time.

---

### Post by NightwishFan on 2010-04-07
I like it as well. I honestly think it will be great. My point was any time something major innovates it is met with a lot of criticism. Normally constructive, but not always, and certainly not lately. Though the mailing list is full of ideas.

---

### Post by Arand on 2010-04-07
As stated (by me), on the bug report:

Temporary solution:
Backup the state of your panel:
```
gconftool-2 --dump /apps/panel panel_backup.xml
```and then restore it whenever it gets messed up:
```
gconftool-2 --load panel_backup.xml
killall gnome-panel
```(kills and auto-respawns, possibly need to run```
gnome-panel &disown
```as well

- Arand

---

### Post by beniwtv on 2010-04-07
Well, according to the release notes of Gnome 2.30 (Lucid's version) this should be solved. In 2.28 ( Karmic's version) they solved other problems related to moving icons as well and for me it did indeed help.

Let's hope this problem will be gone for good in Lucid.

---

### Post by steveneddy on 2010-04-07
**[COLOR="Blue"]Am I the only person who hates gnome-panel?[/COLOR]**

probably

---

### Post by Simian Man on 2010-04-07
I hate gnome-panel as well.  In addition to forgetting where the applets are, it also doesn't come out of auto-hide correctly, doesn't work on the side of screens and can't switch monitors easily.  Even when using Gnome, I either use a dock of some kind or the Xfce panel which has none of these problems.

Gnome-shell may have its problems, but gnome-panel and metacity both deserve to be replaced.

---

### Post by oakgrove on 2010-04-10
Here's how I fixed the "floating applets" issue.  Change your resolution to the highest your monitor supports, fix your applets how you want them, then open a terminal and go to the ~/.gconf/apps/panel directory.  When you get there:```

$ sudo chattr -R +i *

```
This will make every file in that directory immutable even by root so gnome won't be able to change the panel settings on its own.  If you need to make any changes to the panel later, undo this by:
```

$ sudo chattr -R -i *

```
in that same directory.

---

### Post by chriswyatt on 2010-04-10
I wouldn't say I hate it but there a few things about it that bug me.  The inconsistent spacing of the notification area and separate notification applets for one thing.

Also if you get rid of an icon in the notification area it often leaves gaps to the right.  I think I read you can set it to dock to the right rather than the left in a config file, but you really shouldn't need to do this.  It should either be configurable from the panel or automatically dock when pushed against an applet to the right of it.

While it has it's issues I still like it and it comes with some cute apps :)

---

### Post by Hetor on 2010-04-10
Remove gnome-panel and use AWN-trunk.

---

