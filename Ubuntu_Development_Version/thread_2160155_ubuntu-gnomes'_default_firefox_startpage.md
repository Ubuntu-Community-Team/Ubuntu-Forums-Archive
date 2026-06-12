---
title: "ubuntu-gnomes' default firefox startpage"
date: 2013-07-05
forum: Ubuntu Development Version
---

### Post by mc4man on 2013-07-05
While both ubuntu & ubuntu-gnome use the same ubufox package, (xul-ext-ubufox),  the pages are slightly different. Unfortunately for ubuntu-gnome it's current "about:startpage" features an 'unclickable' search button & below
(fresh install of july5 image

[lpbug]1195367[/lpbug]

Edit: - I see they're aiming for "about:home", better choice then ubuntu's "about:startpage"
Or possibly a 50 - 50 of about:startpage top, about:home bottom

If not, (some mix of ), then don't know why it doesn't set the initial user default to about:home, maybe it's has to use about:startpage which is the current default (as seen by the user in FF > preferences

---

### Post by jbicha on 2013-07-06
Yes I've strongly disliked Ubuntu's custom homepage for years. It looks like something is wrong in the ubufox extension so attempting to set the default homepage back to about:home doesn't work.

We'll probably just switch Ubuntu GNOME's homepage to google.com instead. Thanks for the bug report.

---

### Post by mc4man on 2013-07-06
> **jbicha said:**
> Yes I've strongly disliked Ubuntu's custom homepage for years. It looks like something is wrong in the ubufox extension so attempting to set the default homepage back to about:home doesn't work.

We'll probably just switch Ubuntu GNOME's homepage to google.com instead. Thanks for the bug report.

As part of some ubuntu-gnome setting couldn't you just uncomment  /etc/xul-ext/ubufox.js & use a different example file?
(or not allowed/doable or bad idea?
```
// Place your global Firefox preferences in this file if you are using
// ubufox. Especially those preferences defined in ubufox need to be configured
// here to become effective.

// Example: Homepage
pref("browser.startup.homepage", "file:/usr/share/doc/xul-ext-ubufox/example-homepage.properties");
```

/usr/share/doc/xul-ext-ubufox/example-homepage.properties
```
# to test, just enable the example homepage pref in /etc/xul-ext/ubufox.js
browser.startup.homepage=about:home
```

---

