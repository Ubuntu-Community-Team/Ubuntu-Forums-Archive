---
title: "firefox snap vs apt"
date: 2021-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by yaminb on 2021-02-01
How is everyone's experience with the firefox snap?
firefox              85.0-1         mozilla&#10003;        -      Mozilla Firefox web browser

Are there any issues with it as opposed to the apt version? Plugins and everything work fine?
If I currently have the apt version, if I remove and then install the SNAP version, will all my settings and what not be maintained.

Why do I want the SNAP? More of a curiosity than anything.

---

### Post by Hagar Delest on 2021-02-01
That's what user profiles are for: they are separated from the main application. Thus, you keep all your settings.
If you want to make absolutely sure you retrieve your configuration, then make a copy of your current firefox profile (.mozilla).

---

### Post by deadflowr on 2021-02-01
> If I currently have the apt version, if I remove and then install the SNAP version, will all my settings and what not be maintained.
apt never touches your personal settings,
however I have no idea how snaps might interact with them.
So as the apt version's settings for firefox are in ~/.mozilla/firefox snaps have setting usually in ~/snap/firefox.
I suppose it should be possible to simply import the profile from one to the other if need be.

---

### Post by Hagar Delest on 2021-02-01
> **deadflowr said:**
> So as the apt version's settings for firefox are in ~/.mozilla/firefox snaps have setting usually in ~/snap/firefox.
I stand corrected then. I thought it would still use the legacy profile.
I used Audacity once through the snap (by mistake) and I think that the settings were retrieved when I switched to the apt install. But not sure anymore.

---

### Post by howefield on 2021-02-01
I believe the snap will put its profile inside ~/snap and will not touch your ~/.mozilla folder created by the deb package version.

You can install the snap version alongside the deb package version and run each of them as takes your fancy.

---

### Post by CatKiller on 2021-02-01
> **yaminb said:**
> Why do I want the SNAP? 

You could read [the reasoning](https://snapcraft.io/blog/chromium-in-ubuntu-deb-to-snap-transition) behind the Ubuntu devs' decision to make Chromium a snap by default.

The main advantage of snaps is that they're sandboxed. The main disadvantage of snaps is that they're sandboxed.

---

### Post by Dennis N on 2021-02-01
If you're using Ubuntu, Firefox Snap version doesn't have gnome shell integration, meaning you can't manage your gnome shell extensions with it. The same is true of the Firefox Flatpak version.

---

### Post by yaminb on 2021-02-01
Thanks for this one. 

I try and use the SNAP version where possible. I've personally had a good experience with them.
But if it doesn't suppose gnome shell integration and doesn't use the same profile location (I know an easy fix, but I'm a lazy man)
I'll just stick with the built in apt version.

---

