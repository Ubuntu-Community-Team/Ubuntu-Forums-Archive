---
title: "Gnome3 Staging PPA - gnome-shell 3.27.91"
date: 2018-02-24
forum: Ubuntu Development Version
---

### Post by harry332 on 2018-02-24
Has anyone tried to install the new beta gnome-shell 3.27.91 from the Gnome3 Staging PPA?

What new packages are needed when comparing to gnome shell 3.26.2?

I understand caribou is dropped, but new packages are needed.

Obviously 3.27.91 needs something else in addition to those it depends on.
I have tried to install this but I cannot get to the desktop then.
Only solution left is to go to tty6 and downgrade back to 3.26.2.

---

### Post by jbicha on 2018-02-24
Try disabling whatever extra GNOME Shell extensions you have before upgrading.

The systemd journal should give you some error message if GNOME Shell can't start.

---

### Post by mc4man on 2018-02-24
Are any of the staging ppa packages dependant on packages in -proposed?

---

### Post by harry332 on 2018-02-24
I do not have any gnome-shell extensions installed nor any other PPA's enabled.
Gnome3 Staging was the only one I tried. All other packages in that PPA worked just fine, but gnome-shell and mutter do not.
Gnome-shell crashes immediately, it tries to reopen but crashes again.

The Bionic gnome-shell version 3.26.2 works fine, so obviously the 3.27.91 version needs new other packages to be installed.

---

### Post by jbicha on 2018-02-24
Please check your journal and post the errors here if you need help.

---

### Post by jbicha on 2018-02-24
Are you using GDM or LightDM?

Do you have -proposed enabled? (The "right" answer is "no")

Did you reboot after upgrading gnome-shell (shouldn't be needed, but&#8230;)

Is there anything else we should know?

---

### Post by jbicha on 2018-02-24
Intel/NVIDIA/AMD?

---

### Post by mc4man on 2018-02-24
Pretty well broken, fresh install, no ppa's other than staging, no -proposed, intel, gdm3
attached fresh syslog, this seems relevant
```
gnome-shell[1343]: JS ERROR: Error: Requiring NMA, version none: Typelib file for namespace 'NMA' (any version) not found#012@resource:///org/gnome/shell/misc/modemManager.js:5:7#012@resource:///org/gnome/shell/ui/status/network.js:20:7#012_init@resource:///org/gnome/shell/ui/panel.js:702:13#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_Base.prototype._construct@resource:///org/gnome/gjs/modules/_legacy.js:18:5#012Class.prototype._construct/newClass@resource:///org/gnome/gjs/modules/_legacy.js:114:32#012_ensureIndicator@resource:///org/gnome/shell/ui/panel.js:1118:25#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_updateBox@resource:///org/gnome/shell/ui/panel.js:1129:29#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_updatePanel@resource:///org/gnome/shell/ui/panel.js:1040:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_init@resource:///org/gnome/shell/ui/panel.js:822:9#012wrapper@resource:///org/gnome/gjs/modules/_legacy.js:82:22#012_Base.prototype._construct@resource:///org/gnome/gjs/modules/_legacy.js:18:5#012Class.prototype._construct/newClass@resource:///org/gnome/gjs/modules/_legacy.js:114:32#012_initializeUI@resource:///org/gnome/shell/ui/main.js:184:13#012start@resource:///org/gnome/shell/ui/main.js:133:5#012@<main>:1:31
Feb 24 10:49:43 doug-Lenovo-IdeaPad-Y510P gnome-shell[1343]: Execution of main.js threw exception: Script <main> threw an exception
Feb 24 10:49:43 doug-Lenovo-IdeaPad-Y510P gnome-session[1248]: gnome-session-binary[1248]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
Feb 24 10:49:43 doug-Lenovo-IdeaPad-Y510P gnome-session[1248]: gnome-session-binary[1248]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
Feb 24 10:49:43 doug-Lenovo-IdeaPad-Y510P gnome-session[1248]: gnome-session-binary[1248]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Feb 24 10:49:43 doug-Lenovo-IdeaPad-Y510P gnome-session-binary[1248]: Unrecoverable failure in required component org.gnome.Shell.desktop
```

---

### Post by harry332 on 2018-02-24
Jbicha,

Here some answer to your questions:

1. Are you using GDM or LightDM?
GDM

2. Do you have -proposed enabled? (The "right" answer is "no").
It is enabled. If I would play safe, I would not enable a PPA either, would I? However, Bionic proposed enabled without any PPA's is working very well now. So the problem is the PPA.

3. Did you reboot after upgrading gnome-shell (shouldn't be needed, but&#8230;)?
Of course I did reboot, how else would I have found out that I cannot get to desktop any more.

---

### Post by jbicha on 2018-02-24
Thank you. gnome-shell 3.27.91-0ubuntu0~bionic4 is building now with a fix for this issue.

Or you can install gir1.2-nma-1.0 manually.

---

### Post by jbicha on 2018-02-24
> **harry332 said:**
> 
2. Do you have -proposed enabled? (The "right" answer is "no").
It is enabled. If I would play safe, I would not enable a PPA either, would I? However, Bionic proposed enabled without any PPA's is working very well now. So the problem is the PPA.



Ok, let me use a few more words to explain my question and parentheses.

It's important for developers to know whether you do have -proposed  enabled because it not normal behavior and most developers do not have  it enabled (it's turning off Safety barriers…)

I think regulars in those forum are pretty familiar with my position on enabling -proposed during the development cycle.

But for those that aren't, I think the question "Do you have -proposed enabled?" might sound like I'm recommending that they enable -proposed to fix their problem, which is the opposite of what I mean!

---

### Post by harry332 on 2018-02-24
Jbicha, I fully understand the importance of the recommendation not to enable the proposed repos.
However, I am not a newbie nor rookie.
To have proposed repo enabled is intentional for me.
This way I can find possible bugs before the built packages enter official repos.
And I can inform the developers of the the bugs.
See, I am not seeking help now, I was offering information on the bug.

Yet, it is also recommended not to enable any PPA's.
But here again, I was merely testing the new beta version.

---

### Post by jbicha on 2018-02-24
My parentheses wasn't for you, but for others who might read this thread.

---

### Post by harry332 on 2018-02-24
OK Jbicha, no problem.

And, the gnome-shell version 3.27.91-0ubuntu0-bionic4 (with the new dependency) is working fine now.
Thank You for solving this one so fast.

---

### Post by mc4man on 2018-02-24
One of the reasons asked about if -proposed was needed when using the staging ppa is the ppa uses proposed.
Sometimes in that case some packages may require the proposed version of a dependency. It seems nothing in the ppa did here or at least nothing that was part of the upgrade after adding the ppa.

---

