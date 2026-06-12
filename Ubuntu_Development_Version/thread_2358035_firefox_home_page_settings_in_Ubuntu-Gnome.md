---
title: "firefox home page settings in Ubuntu-Gnome"
date: 2017-04-08
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-04-08
What is preventing successfully setting firefox home page to about:startpage (the defacto default).

Edit: ok seems I confuse startpage & home page so 2 questions - 
is the startpage hard coded?
is the home page hardcoded as it also can't be changed to anything other than Mozilla Firefox Start page

---

### Post by vasa1 on 2017-04-09
Have you searched about:config for **startpage**?
This is what I have for Firefox 52 direct from Mozilla, not from the software center:```
browser.aboutHomeSnippets.updateUrl;https://snippets.cdn.mozilla.net/%STARTPAGE_VERSION%/%NAME%/%VERSION%/%APPBUILDID%/%BUILD_TARGET%/%LOCALE%/%CHANNEL%/%OS_VERSION%/%DISTRIBUTION%/%DISTRIBUTION_VERSION%/
```

Re. the home page, I can change it to anything including a local file. But this is all on 16.04.

about:startpage doesn't seem to be a valid home page option.

Maybe I'm not understanding what your issue is :(

---

### Post by mc4man on 2017-04-09
> **vasa1 said:**
> 
Re. the home page, I can change it to anything including a local file. But this is all on 16.04.

about:startpage doesn't seem to be a valid home page option.

Maybe I'm not understanding what your issue is :(

This is on 17.04 Ubuntu-Gnome install
scr. 1,  startpage as supplied (Mozilla Firefox Start Page
scr 2, startpage desired (about:startpage
scr. 3, setting page, while anything can be set inc. "about:startpage" , the setting always reverts to scr. 1. Additionally the 'Home' icon in toolbar always produces scr. 1, i.e. "Mozilla Firefox Start Page"

 "about:startpage"  can be typed or is inserted by clicking on the "_R_estore to Default" button

The current end result is the startpage & or "Home _P_age" cannot be changed from scr 1 (Mozilla Firefox Start Page

---

### Post by P-I H on 2017-04-09
It's working OK on my system. I opened the "Google homepage". Used the "Use Current Page" function. Edited the Home Page entry to only show the "Google homepage".

---

### Post by mc4man on 2017-04-09
> **P-I H said:**
> It's working OK on my system. I opened the "Google homepage". Used the "Use Current Page" function. Edited the Home Page entry to only show the "Google homepage".

What you are showing does not look like Ubuntu-Gnome

---

### Post by P-I H on 2017-04-09
Sorry, it's on Unity. I didn't read your problem description carefully enough.

---

### Post by mc4man on 2017-04-09
> **P-I H said:**
> Sorry, it's on Unity. I didn't read your problem description carefully enough.

Yeah, I'll make a bit more obvious

---

### Post by jbicha on 2017-04-09
@mc4man, please file a bug against ubuntu-gnome-default-settings.

about:startpage comes from the Ubuntu Modifications extension. I'm surprised that you seem to prefer it. I've deeply disliked it for many years.

My understanding is that regular extensions are scheduled to no longer work in Firefox 57 so the current implementation won't work then.

---

### Post by mc4man on 2017-04-09
Just to note,
I can understand why the Mozilla start page is used by default, likely superior for many users. That shouldn't preclude user changes to it or the home page.
My wishing to specifically use about:startpage (ubufox) is because it's now somewhat unique, (all Os's),  in that it still allows a left click in search box > drop down recent or most common terms.
Firefox in general no longer allows that, one must type in box to get 'suggestions'

---

### Post by jbicha on 2017-04-09
This is [bug 1605887]("https://launchpad.net/bugs/1605887"). It also affects Ubuntu MATE (Ubuntu GNOME 17.04 copied the feature from Ubuntu MATE).

---

### Post by mc4man on 2017-04-09
> **jbicha said:**
> This is [bug 1605887]("https://launchpad.net/bugs/1605887"). It also affects Ubuntu MATE (Ubuntu GNOME 17.04 copied the feature from Ubuntu MATE).
That would be it. Commenting out  the 1 line in that file allows setting as desired. 
For whatever reason that .cfg file needs to exist for FF to start in Ubuntu-Gnome though not so in Ubuntu??

---

