---
title: "Firefox 41: browser.newtab.url to go ???"
date: 2015-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-09-22
[https://bugzilla.mozilla.org/show_bug.cgi?id=1118285](https://bugzilla.mozilla.org/show_bug.cgi?id=1118285)

Firefox 41 will be without the option to modify the new tab url via *about:config*. If you need the function, there's at least one extension: [https://addons.mozilla.org/en-US/firefox/addon/new-tab-override/](https://addons.mozilla.org/en-US/firefox/addon/new-tab-override/)

I used to point new tabs to a local page.
[B]
Edit: the release notes don't mention anything about it: [https://www.mozilla.org/en-US/firefox/41.0/releasenotes/](https://www.mozilla.org/en-US/firefox/41.0/releasenotes/)[/B] so I'm going to add a few question marks to the title!

---

### Post by buzzingrobot on 2015-09-22
> **vasa1 said:**
> [https://bugzilla.mozilla.org/show_bug.cgi?id=1118285](https://bugzilla.mozilla.org/show_bug.cgi?id=1118285)

Firefox 41 will be without the option to modify the new tab url via *about:config*. If you need the function, there's at least one extension: [https://addons.mozilla.org/en-US/firefox/addon/new-tab-override/](https://addons.mozilla.org/en-US/firefox/addon/new-tab-override/)

I used to point new tabs to a local page.

Thanks for the pointer to that extension.  I'll use it.

---

### Post by vasa1 on 2015-09-22
I'll try to get by without an extension.

Because pressing **Ctrl+T** to open a new tab showing the contents of my home page won't be possible in Firefox 41 (without an extension such as that linked to in the first post), I made a small script:[s] tailored to my particular situation:
[LIST]
[*]Firefox window maximized
[*]the bookmarks bar always visible
[*]the link to my local home page always in a specific location in the bookmarks bar (x=725, y=90)
[/LIST]

```
#! /usr/bin/env bash

active_window="$(xdotool getactivewindow getwindowname)"

if [[ "$active_window" == *"Mozilla Firefox" ]]
then
  xdotool mousemove --sync 725 90 click 2
fi
```
[/s]
I assigned the keybind **Ctrl+Super+N** to the script and I plan to use that instead of **Ctrl+T**.

```
#! /usr/bin/env bash
xdotool search --name "Mozilla Firefox" key ctrl+t alt+Home
```

---

### Post by monkeybrain20122 on 2015-09-22
I don't even know that there is such a feature. :) I am not fussy  about what page new tabs show, default is cool with me. But I care about where the new tab is. I think it would be a useful feature for new tab to open next to the current tab instead of maybe 100 tabs down to the right. But this being Firefox there is an addon for it :) [https://addons.mozilla.org/en-us/firefox/addon/open-tabs-next-to-current/](https://addons.mozilla.org/en-us/firefox/addon/open-tabs-next-to-current/)

---

### Post by vasa1 on 2015-09-22
> **monkeybrain20122 said:**
> I don't even know that there is such a feature. :) I am not fussy  about what page new tabs show, default is cool with me.But it isn't cool with me. Hence **_*this*_** thread ;)

Just got the update to v41 and *browser.newtab.url* is still visible in *about:config*! And pressing Ctrl+T opens a blank page for me with focus in the url bar. I've previously turned off whatever I thought was related to "Tiles".

---

### Post by CharlesA on 2015-09-22
I've always had a new tab open a blank tab. Is that changing in FF41?

---

### Post by tgalati4 on 2015-09-22
I would not be surprised if a New Tab opens to a full page advertisement.

---

### Post by vasa1 on 2015-09-22
> **CharlesA said:**
> I've always had a new tab open a blank tab. Is that changing in FF41?

Looks that will still be available in v41 based on what I see. Because I've disabled whatever I know of relating to tiles, Ctrl+T gives me a blank page. No extensions added.

---

### Post by CharlesA on 2015-09-22
> **tgalati4 said:**
> I would not be surprised if a New Tab opens to a full page advertisement.

No kidding right. They already have suggested sites enabled by default as it is.

> **vasa1 said:**
> Looks that will still be available in v41 based on what I see. Because I've disabled whatever I know of relating to tiles, Ctrl+T gives me a blank page. No extensions added.

Thanks for that. Mine is set to just show a blank page as well.

---

### Post by Bucky Ball on 2015-09-22
I've used the New Tab Homepage extension for ages. Works great. Just install it from Toosl> Add-ons.

---

### Post by CharlesA on 2015-09-23
> **Bucky Ball said:**
> I've used the New Tab Homepage extension for ages. Works great. Just install it from Toosl> Add-ons.

Thanks for that. Apparently Tab Mix Plus has the same type of functionality and I had no idea.

I've been using it for ages too. :lolflag:

---

### Post by monkeybrain20122 on 2015-09-24
There is no "ad". I don't use any extension and haven't changed any setting on new tabs. The new tabs just open with some sites I have visited or already have a tab open (e.g UF) But of course I can see the problem if you go to naughty sites for which you may use private browsing. :)

---

### Post by vasa1 on 2015-09-24
> **monkeybrain20122 said:**
> There is no "ad". I don't use any extension and haven't changed any setting on new tabs. The new tabs just open with some sites I have visited or already have a tab open (e.g UF) But of course I can see the problem if you go to naughty sites for which you may use private browsing. :)

I think that most of the posters in this thread have been pointing the new tab page to a specific page long before Mozilla came up with tiles.

---

### Post by tgalati4 on 2015-09-25
What I resent is that both *firefox* and *google-chrome* are morphing into operating systems--and invasive operating systems at that.  I don't want a browser to completely take over my machine (by hogging all of its RAM and CPU cycles) and then directing how tabs are opened and what content is displayed.  It seems like we are moving towards a Windows-like environment, which we all ran screaming from years ago.

---

### Post by vasa1 on 2015-09-28
Just realized that CTR has the solution. I rely on CTR in any case.

---

