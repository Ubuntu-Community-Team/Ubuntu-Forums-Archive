---
title: "Newest gnome 43 update kicked out ubuntu-dock"
date: 2022-09-20
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2022-09-20
After last update, ubuntu-dock fails to show. the normal gnome-dock is used instead, but it is broken (cannot rise it anymore with the edge of the screen, also can't configure it from settings).
The extension seems to be kicked out, and cannot be re-installed:

```
sudo apt install gnome-shell-extension-ubuntu-dock
The following packages have unmet dependencies:
 gnome-shell-extension-ubuntu-dock : Depends: gnome-shell (< 43) but 43.0-1ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Knowing that the proposed channel is dangerous, I hope this is sorted out soon.

---

### Post by jbicha on 2022-09-21
Please, please don't enable proposed updates when you're running Ubuntu's development release. Ubuntu does a lot of tests that need to pass before things migrate out of proposed. By using proposed, you are intentionally saying that you are ok with breaking your system. In this case, you would have needed to pay attention when apt wanted to remove the ubuntu-dock extension.

---

### Post by zebra2 on 2022-10-06
Using 22.10 is dangerous meaning "not sorted out yet".  One should not be using a development version if one cannot tolerate danger.  It if for people that actually like and can deal with danger.  
"Proposed" on the other hand only provides "more" danger.  It allows one to experience more of what one asked for by using 22.10 in the first place.  If this was not so then it would not be included in the development version until it's release. 
When Gnome's desktop changes showed up in proposed for the first time I was elated.  This has been on the table for a long time. It isn't sorted out by a long shot and may drift into the release.  But it is here. Now. I think they may have a good handle on it by the next LTS. So even more tolerance is needed in addition to the danger part.

---

