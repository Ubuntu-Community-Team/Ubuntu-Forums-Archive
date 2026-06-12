---
title: "Pocket &amp; Firefox 38.0.5"
date: 2015-06-04
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-06-04
The recent update of Firefox to version 38.0.5 includes Pocket. For those who don't need it, ```
browser.pocket.enabled;false
``` in about:config stops it from running and having the following code in userChrome.css ```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* only needed once */

#menu_pocket, #menu_pocketSeparator,
#BMB_pocket, #BMB_pocketSeparator {
 display:none !important;
}
```removes it from the Bookmarks dropdown ([thanks to dickvl]("http://forums.mozillazine.org/viewtopic.php?p=14184917#p14184917"))

---

### Post by night_sky2 on 2015-06-04
Yeah I removed it too. As well as Firefox Hello and Reader Mode. This is the kind of features I don't need in a desktop browser and it just increase it's memory footprint.

But I can understand why Mozilla would want a ''full-featured'' browser. They are trying to be yet even more user-friendly and appeal to those who like having this kind of stuffs out-of-the-box.

Thankfully it can be all disabled. ;)

---

