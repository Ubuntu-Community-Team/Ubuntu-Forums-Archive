---
title: "Live session on an Ubuntu image doesn't have nautilus handling the Desktop"
date: 2013-04-22
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-04-22
Really surprised this hasn't been addressed, will be even more surprised if the release image does this.
Will lead to some bad behavior in a 13.04 live session inc. a complete freeze up if a user attempts to minimize a window.

Hard to understand if it makes release as seen thru today's image
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1170483](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1170483)

( to fix in a live session if this continues - 
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

---

### Post by EgoGratis on 2013-04-22
Yes we want Nautilus handling the desktop in the future too.

---

### Post by mc4man on 2013-04-23
> **EgoGratis said:**
> Yes we want Nautilus handling the desktop in the future too.

I gather the plan is to go with gnome-3.8 in S, or at least to the extent current resources allow. So if that means nautilus-3.8 then will be interesting on how that would be achieved.
(though a quick test a while ago with one of the touch(unity next) lens suggests that a 'Desktop' is not that important

As far as the 13.04 live session - they've 1 day to fix. 
(if they don't I think quite embarrassing to offer a "Try Ubuntu" that's likely to freeze up or other such mis-behavior within min.'s of starting..

---

### Post by EgoGratis on 2013-04-24
> (though a quick test a while ago with one of the touch(unity next) lens suggests that a 'Desktop' is not that important

Yes i have a feeling Canonical might feel it has something better to offer on the desktop then Nautilus/Files handling the desktop in Unity Next. If my suspicions will materialized and it will only be something in the range of "maximized/full screen Dash" then i will use different DE on the desktop not Unity anymore. But "desktop mode" of Unity could still offer the only sane option wallpaper + icons and we will see when it happens.

---

