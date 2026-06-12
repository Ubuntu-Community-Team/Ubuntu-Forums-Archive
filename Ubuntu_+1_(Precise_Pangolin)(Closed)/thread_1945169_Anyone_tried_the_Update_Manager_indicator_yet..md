---
title: "Anyone tried the Update Manager indicator yet."
date: 2012-03-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2012-03-22
[http://www.webupd8.org/2012/03/update-manager-indicator-displays.html](http://www.webupd8.org/2012/03/update-manager-indicator-displays.html)

---

### Post by Baldrick_NZ on 2012-03-22
I've got it installed atm, seems a bit buggy. Not convinced it executes in the background very well, but that's probably more of a visual thing. It's good at letting you know when there are updates and what they are though, which I then do through terminal.

I really need to try it on some updates that don't (to my mind) matter if they aren't updated, to prove they're executed properly using the indicator.

Hope I've made sense.

---

### Post by x-shaney-x on 2012-03-22
I don't quite understand why updates aren't notified in a better way?
The pop-up box doesn't seem to work for me.~
I see the icon in the launcher wiggle but no window.
I click on the icon and no window.
I click on another icon then back on the updates icon and the window finally appears.

Why don't we get a standard pop-up notification like other notifications?
I would like to see the "system" indicator change colour or something when there are updates.

---

### Post by Baldrick_NZ on 2012-03-22
> **x-shaney-x said:**
> 
I would like to see the "system" indicator change colour or something when there are updates.
+1, but this helps in the meantime.

---

### Post by Baldrick_NZ on 2012-03-22
Oh, a new revision's out. It now activates the update manager when searching for updates, following clicking on "refresh".

That gives me confidence something's actually happening. At this point in time, after being notified about 18 updates, I can now check what they are and then hit "execute", which then downloads and updates/upgrades in the background. When it's finished I get a notification that it's complete.

```
sudo apt-get update && sudo apt-get upgrade
```
in terminal confirms this.

Nice work!

---

### Post by philinux on 2012-03-23
Indeed. I hope some of these tweaks get full repo status soon.

---

### Post by jerrylamos on 2012-03-23
On topic:

!NEVER!

I've had "Update Mangler" unexpectedly "mangle" installs.

So I "don't do that!"

One of the very first things I do on a new install (two yesterday) is to start synaptic and set "update" to "never".

I do sudo aptitude update, sudo aptitude safe-upgrade frequently, almost daily during development.  Occasionally something doesn't update so I do a sudo aptitude full-upgrade.

Why aptitude?  I've been screwed by "sudo apt-get dist-upgrade" and got to re-install.

Aptitude is running in the background right now, I see there's a 3.2..0-20 update available.

Jerry

---

### Post by philinux on 2012-03-23
> **jerrylamos said:**
> On topic:

!NEVER!

I've had "Update Mangler" unexpectedly "mangle" installs.

So I "don't do that!"


Jerry

Ah Jerry you're missing the point. This indicator is for use when Precise goes live so it's worth testing but not trusting. ;)

---

