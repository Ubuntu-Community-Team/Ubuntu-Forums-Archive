---
title: "Flashback w/Metacity menu problems"
date: 2015-03-17
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-03-17
This is a mess. In Ubuntu it seems like the menus can be edited (partially at least) but the categories Sundry and Utilities don't even appear in the alacarte menu:

[ATTACH=CONFIG]260692[/ATTACH]

While testing in Ubuntu GNOME yesterday I don't think I was even able to edit the menus but I need to do some more retesting to be sure once they re-spin a daily build with todays big X-stack dump.

I really wish we could do some serious clean-up and restructuring of the menu trees, eliminating duplicate entries including those available in System Settings.

I see that even the menus and buttons have icons settings aren't applied so I'd guess flashback is following the improper schema:

[ATTACH=CONFIG]260694[/ATTACH]

The Power Off and Restart menu buttons don't work either :(

Filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1433246](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1433246)

---

