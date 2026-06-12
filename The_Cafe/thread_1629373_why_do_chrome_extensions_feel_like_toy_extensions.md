---
title: "why do chrome extensions feel like toy extensions?"
date: 2010-11-23
forum: The Cafe
---

### Post by madjr on 2010-11-23
i know chrome is still the new browser on the block and that it feels pretty lightweight and fast, it almost doesnt feel like a browser.

but the extensions, dont feel like extensions either. They feel half baked compared to the current firefox.

While i use both equally, i feel chrome has much catching up in the extensions area to do to feel really robust.

So i hope chromeOS comes out it doesnt feel like a toy.

I know jolicloud's html5 gui is built inside chrome/mium and is great, so will chromeOS feel robust like jolicloud? will its web apps feel as good as native apps? i sure hope so or no one will take it seriously..

---

### Post by TheNessus on 2010-11-23
I suppose that if you step outside of Toys R Us while using your computer, this feeling would change instantly.

---

### Post by FuturePilot on 2010-11-23
> **madjr said:**
>  They feel half baked compared to the current firefox.

I feel the same way. It probably has to do with the fact that Chrome's extension API is really limited compared to Firefox's and therefore extensions aren't always on feature parity with their Firefox equivalent.

---

### Post by Stigmata13 on 2010-11-23
Don't forget that Firefox has been around MUCH longer than Chrome has.
Give it time, and I'm sure some good quality extensions will come.

---

### Post by czr114 on 2010-11-23
Why not switch to FF, either now, or when 4 comes out?

The collected wealth of code in the FF addons repository is unmatched.

---

### Post by joepie91 on 2010-11-23
> **czr114 said:**
> Why not switch to FF, either now, or when 4 comes out?

The collected wealth of code in the FF addons repository is unmatched.

Because Chrome has a huge advantage on speed (especially Javascript and rendering a lot of images), has more screen estate, and has Developer Tools that easily beat those in Firefox (even with addons) in my opinion.

---

### Post by czr114 on 2010-11-23
> **joepie91 said:**
> Because Chrome has a huge advantage on speed (especially Javascript and rendering a lot of images), has more screen estate, and has Developer Tools that easily beat those in Firefox (even with addons) in my opinion.
FF4 will be fixing the speed issues. It's development addons are great. It also has the benefit of not being tied in with one of the web's worst privacy violators.

---

### Post by Mr. Picklesworth on 2010-11-23
> **FuturePilot said:**
> I feel the same way. It probably has to do with the fact that Chrome's extension API is really limited compared to Firefox's and therefore extensions aren't always on feature parity with their Firefox equivalent.

That's pretty well it. More to the point, they have different philosophies behind extensions.

For Firefox, an extension is something that changes the core behaviour of the browser. In Firefox's ideal world, the whole browser would be built out of extensions. This has the advantage that extensions are, as you note, powerful (and can do crazy stuff, [like GUI prototyping]("https://addons.mozilla.org/en-US/firefox/addon/8487/"), and making [notification bubbles native]("http://linux.softpedia.com/get/Internet/Thunderbird-Extensions/libnotify-mozilla-Thunderbird-47045.shtml")).
The disadvantage is that extensions have a lot of unmanaged power to do scary stuff, and the interface for them is pretty inconsistent. Some insist on being in the status bar, some mess with the main menu, some extensions exist simply to fix the main menu after it has been messed with by other extensions&#8230;

One thing that helps Firefox extensions be so flexible is XUL, Mozilla's own cross platform UI toolkit used in Firefox. Extensions have the ability to freely create XUL widgets (which happen to look integrated, at least with the rest of the browser), instead of needing to generate web pages for their UIs. This would not be possible if Firefox directly used each platform's native UI toolkit (like GTK+), which Chrome does.

Chrome's philosophy is to have [very well defined]("http://code.google.com/chrome/extensions/overview.html") extension points. The advantage is that extensions are consistent and light and the browser can be significantly altered without breaking those extensions. And they can be installed, enabled, disabled instantly.
An extension can change the user interface by adding either a browser action (toolbar button) or a page action (icon in the location field), and the odd extension might alter the page being displayed. Those browser and page actions can be re-ordered, disabled or uninstalled in a click, and they need permission to access different kinds of information. They all behave in similar ways and are tightly managed by the browser.

Recently, Chrome opened another bit of its UI to extensions: [context menus]("http://code.google.com/chrome/extensions/contextMenus.html"). Again, it's a tightly defined thing: one part of the context menu, clearly separated from the native stuff. The extension provides an icon and a label, Chrome handles the presentation. (Including, if an extension provides more than one menu item, sticking those menu items into a submenu).

Of course, extensions in Chrome have the power to *control* other things (like bookmarks), but one can't arbitrarily replace the Stop button, for example.

---

### Post by RiceMonster on 2010-11-23
Yes, I think Firefox's extension API is far more advanced than Chrome's. Though there is very that I can't get out of Chrome extensions that I require. The only issue I've had so far is that user agent switcher is not very good in Chrome.

---

