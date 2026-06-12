---
title: "ibus/indicator-keyboard call for testing"
date: 2013-07-16
forum: Ubuntu Development Version
---

### Post by jbicha on 2013-07-16
We are looking for people to try out the latest ibus and the new  indicator-keyboard and report any issues they find. ibus is most commonly to input text in east Asian  languages but indicator-keyboard will be useful to anyone using Unity  that has a need for multilingual typing. More details are available at  the following links:

[https://lists.ubuntu.com/archives/ubuntu-devel/2013-July/037462.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-July/037462.html)

[https://lists.ubuntu.com/archives/ubuntu-devel/2013-July/037486.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-July/037486.html)

---

### Post by tista on 2013-07-17
Hi Jeremy ;)

OK, I can join the test, so let me know what I should do for it?
I now am using stock ibus on saucy and "anthy" Japanese input engine.

Regards,
Tista

---

### Post by jbicha on 2013-07-17
> **tista said:**
> Hi Jeremy ;)
OK, I can join the test, so let me know what I should do for it?


Did you read the links I posted? ;)

Anyway, it's

```

sudo add-apt-repository ppa:ubuntu-desktop/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install indicator-keyboard

```

...then log out and log back in. You can use System Settings>Region & Language>Text Entry to add your ibus engine or keyboard layout.

---

### Post by tista on 2013-07-17
@Jeremy

Thanks for your advices! ;)
Then now I've updated some packages and re-login...
As following your suggestions, I've added English as "keyboard layout" (since my PCs have US keyboard), and added Mozc as "Input Engine".
[IMG]http://s11.postimg.org/5c3hv6pyr/Screenshot_from_2013_07_18_01_45_51.png[/IMG]

Surely Gnome-shell could show the "changing input" notification when pressing "Super+Space" key-bindings like this:
[IMG]http://s17.postimg.org/pdf6eg5n3/Screenshot_from_2013_07_18_01_46_26.png[/IMG]

But...
The indicator of top panel could not follow this key-bindings and actual input method as well! :(
Only this could work with "Shift+Super+Space", yeah means "select the previous method or layout" you know...
And I've found this key-binding could not show that notification at all.

So next I've tested the context menu of top panel indicator, but no lock!
The context menu could not change input method (US natural input to Japanese Mozc input engine) at all.
[IMG]http://s16.postimg.org/8dhtsgp8l/Screenshot_from_2013_07_18_01_47_09.png[/IMG]

Concluded, I could change the actual input method of ibus with this way only:
**Pressing "Shift+Super+Space" key-binding.**
It seems to give more love to new ibus today... ;)

Regards,
Tista

---

### Post by jbicha on 2013-07-17
Tista, thanks for the reply.

I installed ibus-mozc and logged out and logged back in. I then added mozc in System Settings>Region & Language. Super+Space works fine here as does GNOME Shell's keyboard layout status menu.

What version of gnome-shell are you using? Are you using any related PPAs? Except for the ubuntu-desktop PPA, I'm running almost "vanilla" Saucy today.

---

### Post by tista on 2013-07-18
@Jeremy,

> I installed ibus-mozc and logged out and logged back in. I then added mozc in System Settings>Region & Language. Super+Space works fine here as does GNOME Shell's keyboard layout status menu.

Really!? How nice...:P

> What version of gnome-shell are you using? Are you using any related PPAs? Except for the ubuntu-desktop PPA, I'm running almost "vanilla" Saucy today. 
Obviously I've been living with Ricotz Testing PPA. If so, there might be something wrong with it.
So ASAP I would re-install latest saucy daily build and employ ubuntu-desktop ppa only... ;)

Cheers,
Tista

---

### Post by zika on 2013-07-18
> **tista said:**
> @Jeremy,



Really!? How nice...:P


Obviously I've been living with Ricotz Testing PPA. If so, there might be something wrong with it.
So ASAP I would re-install latest saucy daily build and employ ubuntu-desktop ppa only... ;)

Cheers,
Tista
I think it is not Ricotz's PPA to blame... At least that feature works at my place (full Ricotz's treatment)...

---

### Post by tista on 2013-07-18
@Jeremy



Today I'm tracking some logs down with my issue, and I've found some logs in .cache/gdm/session.log:
```
(gnome-shell:1508): Gjs-WARNING **: JS ERROR: Exception in callback for signal: destroy: Error: No signal connection 5 found
_disconnect@/usr/share/gjs-1.0/signals.js:74
PopupMenuBase<.addMenuItem/<@/usr/share/gnome-shell/js/ui/popupMenu.js:892
_emit@/usr/share/gjs-1.0/signals.js:124
PopupBaseMenuItem<.destroy@/usr/share/gnome-shell/js/ui/popupMenu.js:160
wrapper@/usr/share/gjs-1.0/lang.js:213
_parent@/usr/share/gjs-1.0/lang.js:175
PopupSubMenuMenuItem<.destroy@/usr/share/gnome-shell/js/ui/popupMenu.js:1362
wrapper@/usr/share/gjs-1.0/lang.js:213
PopupMenuBase<.removeAll@/usr/share/gnome-shell/js/ui/popupMenu.js:984
wrapper@/usr/share/gjs-1.0/lang.js:213
InputSourceIndicator<._buildPropSection@/usr/share/gnome-shell/js/ui/status/keyboard.js:678
wrapper@/usr/share/gjs-1.0/lang.js:213
InputSourceIndicator<._currentInputSourceChanged@/usr/share/gnome-shell/js/ui/status/keyboard.js:502
wrapper@/usr/share/gjs-1.0/lang.js:213
```

I'm not sure whether that log could relate my issue, anyway this could help you guys... :P

**EDIT**
And did you read this upstream bug report already?
[https://bugzilla.gnome.org/show_bug.cgi?id=695723]("https://bugzilla.gnome.org/show_bug.cgi?id=695723")
It seems similar situation with mine..

Regards,
Tista

---

### Post by jbicha on 2013-07-18
No, bug 695723 isn't really relevant now since the root problem was that Ubuntu had to revert changes in gnome-settings-daemon and gnome-control-center since we weren't ready for ibus 1.5 yet. That's no longer the case in the Desktop PPA and soon in Saucy.

Honestly, I'm simply not able to support the bleeding-edge Ricotz PPAs because I'm more interested in making sure regular Saucy works.

---

### Post by tista on 2013-07-19
> **jbicha said:**
> No, bug 695723 isn't really relevant now since the root problem was that Ubuntu had to revert changes in gnome-settings-daemon and gnome-control-center since we weren't ready for ibus 1.5 yet. That's no longer the case in the Desktop PPA and soon in Saucy.

Honestly, I'm simply not able to support the bleeding-edge Ricotz PPAs because I'm more interested in making sure regular Saucy works.

Hi Jeremy ;)

I agree that stock "vanilla" Ubuntu-Gnome should be stable out of the box.
Then back to my issue, just now I've found the outside of gnome-shell, like flashback, seems to handle those input sources with "ibus's next input method" shortcuts:

[IMG]http://s21.postimg.org/6z18qpihj/Screenshot_from_2013_07_19_20_19_12.png[/IMG]

It surely works great! ;)
And if so, the configuration in gnome-control-center was avoided completely in flashback session. On the other side, I thought there is few reasons to test classic session because today classic session becomes "scaled-down gnome-shell" flavor, right?
(BTW: my flashback is very different with stock gnome's one. Since I now am trying to rebuilding lots of elementary crafts on saucy; gala window manager, wingpanel, slingshot launcher, plank dock, switchboard configuration tool, and more... So that shot actually showed the notification by gala. you know those shapes of notification was shown in mutter's stand-alone session mode. But in this time, I could not see any tray icons of keyboard/ibus).

Anyway I should do ppa-purging some PPAs or re-installing stock saucy, Not to miss the point of new ibus/gnome-shell integration stage... :P

Keep up the great work, Jeremy!
Tista

---

