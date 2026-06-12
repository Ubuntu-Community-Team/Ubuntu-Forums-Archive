---
title: "Dock Opacity"
date: 2017-11-06
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2017-11-06
Ubuntu dock lost opacity/transparency control after update and restart . Anyone else see this problem ?

---

### Post by ajgreeny on 2017-11-06
Is this on 17.10? I assume it is, though you do not say.

EDIT:
Just updated my 17.10 install and do not see your problem so perhaps you really are on the Development release 18.04.

---

### Post by DogMatix on 2017-11-06
> **Frogs Hair said:**
> Ubuntu dock lost opacity after update and restart . Anyone else see this problem ?

Yes I noticed this after updating tonight.

EDIT: Also 18.04 (Wayland). Proposed = off

---

### Post by Frogs Hair on 2017-11-06
> [COLOR=#000000] perhaps you really are on the Development release 18.04.[/COLOR] Yes upgraded 17.10 and this happens in both sessions.


> [https://bugs.launchpad.net/ubuntu/+s...l/+bug/1730521]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1730521") There may be more than one , but it's reported and confirmed. I guess I'll just auto hide for now. :o

---

### Post by ventrical on 2017-11-06
New bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1730489](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1730489)

---

### Post by Kris_M on 2017-11-06
Thanks!

---

### Post by P-I H on 2017-11-07
I don't have that problem, but I'm using different Applications, Icon and Shell themes.
However the upper panel don't have transparency with these settings.
I'm also using the Dash to dock extension.

---

### Post by DogMatix on 2017-11-07
> **P-I H said:**
> ... I'm also using the Dash to dock extension.

I noticed (at least on an install of mine) that if you disable Dash to Dock you loose transparency but other settings made in the Dash to Dock preferences GUI are still honored even though it is showing as disabled in Gnome Tweak Tool.

---

### Post by Kris_M on 2017-11-07
I got transparency back and in playing with it I find that if a window is touching the top bar, I lose top bar transparency - lower it and top bar transparency returns.

EDIT: Now if I turn dash to dock on, the dock bar is transparent. If I turn ubuntu dock on (only) the dock bar is black opaque.

EDIT2: as long as you don't choose "use built in theme", size and opacity adjustments in Dash to Dock work fine.

---

### Post by harry332 on 2017-11-08
This issue should be fixed by now with this update in proposed:
[https://launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/0.8.1](https://launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/0.8.1)

---

### Post by Kris_M on 2017-11-08
> **harry332 said:**
> This issue should be fixed by now with this update in proposed:
[https://launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/0.8.1](https://launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/0.8.1)


Yup - I confirm after taking a bunch of stuff and rebooting, Ubuntu Dock is fixed for me - transparent.

---

### Post by Kris_M on 2017-11-08
However, with this fix on, with Ubuntu Dock on, I lose top bar transparency if there is a window closer to the left edge than the width of the dock bar when it's out, even if it's not out.

---

### Post by Frogs Hair on 2017-11-08
> **Kris_M said:**
> However, with this fix on, with Ubuntu Dock on, I lose top bar transparency if there is a window closer to the left edge than the width of the dock bar when it's out, even if it's not out.

This is feature, you'll see a change when moving a window close to the top panel as well.

---

### Post by Kris_M on 2017-11-08
> **Frogs Hair said:**
> This is feature, you'll see a change when moving a window close to the top panel as well.


oops - filed bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1730999](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1730999)
how do I delete it. Do I just change it to invalid?

---

### Post by ajgreeny on 2017-11-08
Just installed the new daily ISO, (ie not an update from artful,) as a VM in VBox 5.1.30 and all seems to be working fine, though I do still have the loss of transparency in the dock, not yet having used the proposed repos to get the new dock version, which I'll do tomorrow.

I used zsync to get the ISO file and not surprisingly it is still 62% the same as the artful ISO I have, so the two versions look very much alike.

Now I just need to try Xubuntu-18.04, which I'll do as soon as the new daily appears of that OS./

---

### Post by Frogs Hair on 2017-11-08
The fix should be in the standard repository soon.

---

### Post by ajgreeny on 2017-11-09
Transparency now back on my system after enabling proposed, updating the gnome-shell-extensions, and then disabling proposed again, for safety's sake.

As I mentioned in another thread, [https://ubuntuforums.org/showthread.php?t=2377012&p=13709245#post13709245](https://ubuntuforums.org/showthread.php?t=2377012&p=13709245#post13709245), I had a minor problem with the VM as I enabled 3D acceleration; it did not then offer the session cog in the login page so I could not choose wayland or xorg, and the terminal was also totally unresponsive, but they were both VBox problems, not specifically bionic; with 3D now disabled all is back to normal.

---

