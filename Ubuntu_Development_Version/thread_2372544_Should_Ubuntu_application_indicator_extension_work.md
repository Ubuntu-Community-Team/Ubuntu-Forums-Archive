---
title: "Should Ubuntu application indicator extension work? Because it's not"
date: 2017-09-26
forum: Ubuntu Development Version
---

### Post by joshi2 on 2017-09-26
Should Ubuntu app indicator extension in Gnome-shell already work? Slack, Skype etc. are missing indicators, so it's almost impossible to detect general messages (in Slack) that are not pointed at you personally. Enabling or disabling the extension in Gnome Tweaks has no effect.

I mean this extension: [https://didrocks.fr/2017/08/23/ubuntu-gnome-shell-in-artful-day-7/](https://didrocks.fr/2017/08/23/ubuntu-gnome-shell-in-artful-day-7/)

---

### Post by mc4man on 2017-09-26
It says in your link that several apps aren't working, skype is specifically mentioned as not working.

---

### Post by joshi2 on 2017-09-26
> **mc4man said:**
> It says in your link that several apps aren't working, skype is specifically mentioned as not working.

You're right. My bad. But Slack is a must have application in my line of work.

---

### Post by mc4man on 2017-09-26
> **joshi2 said:**
> You're right. My bad. But Slack is a must have application in my line of work.
I guess..
[https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/70](https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/70)
[https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/74](https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/74)

---

### Post by joshi2 on 2017-09-26
> **mc4man said:**
> I guess..
[https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/70](https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/70)
[https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/74](https://github.com/ubuntu/gnome-shell-extension-appindicator/issues/74)

Yes, but does these affect Gnome-shell? Hopefully Canonical get their stuff patched before the release. Should there be at least some kind of icon for app indicator at all? Because I have none.

---

### Post by mc4man on 2017-09-26
I guess if you have some supported indicator installed/running it would show up, ex. in screen
(- can't see why anyone would want to actually use 17.10 vs. just checking out, testing, ect.

---

### Post by joshi2 on 2017-09-26
> **mc4man said:**
> I guess if you have some supported indicator installed/running it would show up, ex. in screen
(- can't see why anyone would want to actually use 17.10 vs. just checking out, testing, ect.

I don't have any indicators on top bar, like in the image.

I'm working as a journalist, so it's my job to check out intermediary Ubuntu releases. :)

---

### Post by mc4man on 2017-09-26
> **joshi2 said:**
> I don't have any indicators on top bar, like in the image.

I'm working as a journalist, so it's my job to check out intermediary Ubuntu releases. :)

It wasn't there here either until I started that keylock indicator (from cli), set it to show, logged out/in
What other indicators work?, don't know, most don't & there doesn't seem to be any systray support in gnome anymore. (I think gnome dropped it in 3.26

---

### Post by joshi2 on 2017-09-26
> **mc4man said:**
> It wasn't there here either until I started that keylock indicator (from cli), set it to show, logged out/in
What other indicators work?, don't know, most don't & there doesn't seem to be any systray support in gnome anymore. (I think gnome dropped it in 3.26

That's right. Systray is gone with Gnome 3.26. This is why it's extremely important that Canonical will offer an alternative. Specially now when the development of TopIcons Plus has stopped due to Gnome team's lack of interest to keep their api's intact.

---

