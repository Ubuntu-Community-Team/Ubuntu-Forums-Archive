---
title: "Desktop-based Viewport Switching may break usb mouse scrolling on laptops"
date: 2013-07-13
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-07-13
Actually I don't use an an usb mouse on this laptop but hooked one up concerning poor scrolling in Unity with current gtk3 in some instances. (worse bug than this Vp switching nonsense - [lpbug]1184159[/lpbug]

Was quite surprised to find that scrolling with the mouse wheel worked in some apps, not at all in others. 
While dumping & diffing a working dconf/user & the borked dconf/user files proved futile due to compiz not having schemas on most of it;s settings,  did eventually track down to the vpswitch plugin & the 'scroll on desktop' bindings - 

Was hoping that the wrap up to the unity/compiz experiment could end gracefully & maybe in a good place - doesn't seem like that'll happen...
more info on this - 
[lpbug]1200829[/lpbug]

Edit:
Both bugs are a result of a commit to gtk3 & compiz's plugi/bindings
Will  affect only a limited number of users in certain scenarios
(i'll maintain [the ppa to revert]("https://launchpad.net/~mc3man/+archive/test-scroll") till fixed for myself & those that need

---

