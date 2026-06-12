---
title: "Unified Menu Doesn't Show On First Login"
date: 2016-03-22
forum: Ubuntu Development Version
---

### Post by ZenHarbinger on 2016-03-22
[COLOR=#111111][FONT=Ubuntu]Using Ubuntu 16.04, when I log in the first time and open up a nautilus window or terminal, I don't get any menu items in the unified menu bar. If I log out and back in, it shows up.[/FONT][/COLOR]

[LIST=1]
[*]Is there a way to fix this?
[*]How would I report this bug? I think it's w/ GTK/Gnome 3 since other apps such as Thunderbird and Chrome do not suffer from this.
[/LIST]

---

### Post by deadflowr on 2016-03-22
Moved to Ubuntu Development Version

(16.04 is still in development at the moment)

---

### Post by howefield on 2016-03-22
Have a look at [this bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1532226"), if it is the same, mark it as affecting you too.

---

### Post by mc4man on 2016-03-22
Because this bug doesn't yet have any means to reproduce on demand it's possible it will be there on release
(-unless it's inadvertently 'fixed'
To that end I subscribed the last dev to edit the current Xenial release notes to consider adding bug & 'fix' to the notes if it's still open on release.

Here it seems to happen about 15 - 20% or so of fresh boots

---

### Post by viljeml on 2016-03-22
It is on all my fresh boots

---

### Post by mc4man on 2016-03-22
> **viljeml said:**
> It is on all my fresh boots
Hopefully that is the case with an ubuntu dev or 2...
You should mark bug as affecting you, more users affected the higher the 'heat'

Then try this if desired.
Delete everything in your ~/.local/share folder except Trash, then reboot. This may put you in the 'it happens occasionally' group
( everything you need in .local/share  will be re-created or re-created over use, exception would be any custom .desktops in ~/.local/share/applications. If you have any you want then move to Documents or somewhere first.

---

### Post by ZenHarbinger on 2016-03-22
Awesome, I could not find any bug reports for this.  I'm just glad I'm not the only one.
Marked as being affected by bug.

---

### Post by Uncle Spellbinder on 2016-03-26
I'm noticing that for the GIMP, Pinta and Gthumb that the global menu is not utilized leaving no way to get to options and such.

Here's Pinta as an example:

[IMG]http://i65.tinypic.com/27wzl83.jpg[/IMG]

* Yes, I'm using a different theme here. It also happens with the default theme.

---

### Post by Frogs Hair on 2016-03-26
This is a bug , try logging out and back in. 
[http://ubuntuforums.org/showthread.php?t=2318050](http://ubuntuforums.org/showthread.php?t=2318050)

---

### Post by Uncle Spellbinder on 2016-03-26
> **Frogs Hair said:**
> This is a bug , try logging out and back in. 
[http://ubuntuforums.org/showthread.php?t=2318050](http://ubuntuforums.org/showthread.php?t=2318050)

Many thanks Frogs Hair. That was it. Logged out and back in. No issue now. I'll mark the bug as affecting me as well. Appreciate the quick response!

---

### Post by Uncle Spellbinder on 2016-03-26
Thanks for the bug post. Marked as affecting me, too.

---

### Post by cariboo on 2016-03-26
Merged two similar threads.

---

### Post by mc4man on 2016-03-27
Certainly a prize for anyone that solves or finds the trigger or triggers if multiple.
Though if 'solved',  just as likely to stop happening at some point for no apparent reason nor explicit fix, just goes away...

There is some anecdotal evidence that some file(s) in ~./local/share can affect this though affect doesn't imply cause.

---

### Post by rrnbtter on 2016-03-28
Greetings,
I deleted everything in my .local/share except Trash as suggested. My menu is working fine now on first boot. I backed up my Teamviewer folder to preserve the setup. If it backfires later I will let you know. 
Thanks

---

### Post by mc4man on 2016-03-28
> **rrnbtter said:**
> Greetings,
I deleted everything in my .local/share except Trash as suggested. My menu is working fine now on first boot. I backed up my Teamviewer folder to preserve the setup. If it backfires later I will let you know. 
Thanks

> **mc4man said:**
> 

There is some anecdotal evidence that some file(s) in ~./local/share can affect this though affect doesn't imply cause.
If past (from Jan. on) experience matters that won't solve, will just make this less likely to happen. That action seemed to lessen occurrences to   about 15% of the time.
On this install it started coming back considerably more often lately so just did the mass deletion yet again.

---

### Post by mc4man on 2016-03-30
> **mc4man said:**
> If past (from Jan. on) experience matters that won't solve, will just make this less likely to happen. That action seemed to lessen occurrences to   about 15% of the time.
On this install it started coming back considerably more often lately so just did the mass deletion yet again.

On one of my installs the boot to no menus comes up more often than not. A temp solution while awaiting a fix is thru a startup app as such. Note that with this one would not know when it's fixed other than following bug report. If inclined - 

```
gedit .config/autostart/menus.desktop
```

insert below & save

```
[Desktop Entry]
Type=Application
Exec=initctl restart unity-panel-service
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=menus
Comment=Show me the menus
X-GNOME-Autostart-Delay=1

```

There is a 1 sec. delay that probably is  not needed, in that case can be removed or  left without a value
(- it can also be increased if need be

---

### Post by rrnbtter on 2016-03-30
Greetings,
After fixing menus per post #14, problem re-occurred after an update. Rebooted .... menu is back. Inserted config file per post #16. Will see what happens and let you know if it fails.  If it works, the problem/bug may very well be the lack of a desktop.menus config file. 
Thanks again.

---

