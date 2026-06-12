---
title: "Firefox 4 with real tabs on Linux?"
date: 2010-09-16
forum: The Cafe
---

### Post by kahumba on 2010-09-16
Hi,
The Firefox 4 beta windows version already has "real", Google-Chrome-like tabs where there's **no title bar and no menu bar** instead there are tabs only, thus saving enough vertical space.
The Linux version however hasn't reached this milestone and still uses the actual title bar along with the tabs.
Any news whether this will be fixed before Firefox 4 gets released?

---

### Post by sxmaxchine on 2010-09-16
i dont think so. it would be very difficult as there are many different interfaces such as gnome, kde, xfce, lxde. and there are also people who use emerald and probably many others.

---

### Post by Tibuda on 2010-09-16
I hope not.

---

### Post by kahumba on 2010-09-16
> **sxmaxchine said:**
> i dont think so. it would be very difficult as there are many different interfaces such as gnome, kde, xfce, lxde. and there are also people who use emerald and probably many others.
I don't know what you're talking about, I have no problem with Google Chrome on Gnome whose tabs have now replaced the title bar a long ago which is one of the best features and innovations that Chrome provides (along with speed and faster startup time).
Why would Firefox not wanna do that on Linux too?
Because it intends to also run on Commodores and on obsolete setups and environments that can't handle it?

---

### Post by Tibuda on 2010-09-16
> **kahumba said:**
> I don't know what you're talking about, I have no problem with Google Chrome on Gnome whose tabs have now replaced the title bar a long ago which is **one of the best features and innovations that Chrome provides** (along with speed and faster startup time).
Why would Firefox not wanna do that on Linux too?
Because it intends to also run on Commodores and on obsolete setups and environments that can't handle it?

Each tab with its own proccess is a good innovation by Chrome. Improved JavaScript performance  too. An app trying to have its own look different from the whole OS is not. It has been done for ages by many apps. Winamp, WMP, MS Office, many anti-virus...

---

### Post by 23meg on 2010-09-16
Here's the Firefox upstream bug where this is tracked (read all the comments to understand the rationale for the current situation):

[https://bugzilla.mozilla.org/show_bug.cgi?id=513159](https://bugzilla.mozilla.org/show_bug.cgi?id=513159)

---

### Post by kahumba on 2010-09-16
> **23meg said:**
> Here's the Firefox upstream bug where this is tracked (read all the comments to understand the rationale for the current situation):

[https://bugzilla.mozilla.org/show_bug.cgi?id=513159](https://bugzilla.mozilla.org/show_bug.cgi?id=513159)

Thanks! That was helpful.

Interestingly enough, looks like somebody is even questioning the need for this, fortunately there's also a voice of reason:
>  
"Overall I think it makes the most sense to default to a menu bar on Linux, since this is the expected behavior".
Generally this is true - but I have not seen any complains about a missing menu on Chrome/Linux for example (on the contrary... people enjoy this "non standart" UI a lot).Also, if you look at the latest mockups for the new file manager in GNOME3, you will also not find a menu... so the "expectations" may soon change on Linux.I recall that the Firefox folks are distinctively lazy ..oops I mean "conservative" when it comes to the Linux UI, I remember I once fired a feature request at Mozilla which said that the right-click menu should be changed so that "open in new tab" should appear above "open in new window" since people usually open in new tabs rather then windows, and they said that they looked at this issue and found that it's not worth it, and guess what, in Firefox 4.0 they finally/nonetheless changed it as I suggested! (over time obviously I was not the only one suggesting it). Thus it's amazing how one defies common sense in favor of "noble conservatism" and only gives in as the competition looms in (Google Chrome) and out-competes you in areas where you decided not to change cause it was "not worth it". Not a flame, it's true.

Overall looks like they're waiting for GTK3 to provide the needed functionality and/or a port of that functionality to GTK 2.22.

Either way, realistically, we'll only see this change at best in Firefox 4.1, which is likely a year away from now, so don't hold your breath for a new shiny UI (as on windows 7) with Firefox 4.0.

---

### Post by Tibuda on 2010-09-16
They surely should get rid of the menu bar. And the status bar too. They could allow extension devs to add them back. I just don't like the idea of moving the tabs to the title. It is not that much space. Here's a side-by-side comparison between a tweaked Firefox 3.6 and Chrome.
[[img]http://ompldr.org/tNWs2Mw[/img]](http://ompldr.org/vNWs2Mw)
That's a light and minimal user interface that is consistent with the whole OS.

---

### Post by Linye on 2010-09-16
> **Tibuda said:**
> They surely should get rid of the menu bar. And the status bar too. They could allow extension devs to add them back. I just don't like the idea of moving the tabs to the title. It is not that much space. Here's a side-by-side comparison between a tweaked Firefox 3.6 and Chrome.
[[IMG]http://ompldr.org/tNWs2Mw[/IMG]]("http://ompldr.org/vNWs2Mw")
That's a light and minimal user interface that is consistent with the whole OS.


The story is different when the windows are maximized.

---

### Post by Tibuda on 2010-09-16
> **Linye said:**
> The story is different when the windows are maximized.

How?

---

### Post by andymorton on 2010-09-16
Since I discovered the add-on which hides the menu bar I'm not really that bothered whether they introduce the new interface for Linux. 

Here's a link if anyone wants it. 

[https://addons.mozilla.org/en-US/firefox/addon/4762/](https://addons.mozilla.org/en-US/firefox/addon/4762/)

andy:)

---

### Post by Linye on 2010-09-16
> **Tibuda said:**
> How?


Maximize both windows and you'll see that in Chrome, the gap between the tab and the top of the window disappears and there's only two lines, the tab bar and the navigation bar. 

Maximized Firefox stays the same with tab bar, navigation bar and title bar.

---

### Post by Linye on 2010-09-16
> **andymorton said:**
> Since I discovered the add-on which hides the menu bar I'm not really that bothered whether they introduce the new interface for Linux. 

Here's a link if anyone wants it. 

[https://addons.mozilla.org/en-US/firefox/addon/4762/](https://addons.mozilla.org/en-US/firefox/addon/4762/)

andy:)


Thanks! It wasn't working for me before; now it looks better.

---

### Post by Tibuda on 2010-09-16
> **Linye said:**
> Maximize both windows and you'll see that in Chrome, the gap between the tab and the top of the window disappears and there's only two lines, the tab bar and the navigation bar. 

Maximized Firefox stays the same with tab bar, navigation bar and title bar.

I see. The difference would be exactly the window title height, except if your maximized windows are undecorated.

---

### Post by andymorton on 2010-09-16
> **Linye said:**
> Thanks! It wasn't working for me before; now it looks better.

No problem :) It stopped working when beta 6 was released but it must have been updated soon after.

andy

---

### Post by compiz addict on 2010-10-30
To anyone viewing this thread:

This add-on works better with the newest beta:

[https://addons.mozilla.org/en-US/firefox/addon/4550/](https://addons.mozilla.org/en-US/firefox/addon/4550/)

---

### Post by madhi19 on 2010-10-31
I hate the tabs on top I hate it with all my soul! I think that tabs browsing is faster when you don't have to go all the way to the top to click on a freaking tab! It feel clunky on chrome and I hope mozilla at least leave us an option to keep it the way I like it in Firefox 4!

---

### Post by smellyman on 2010-10-31
> **madhi19 said:**
> I hate the tabs on top I hate it with all my soul! I think that tabs browsing is faster when you don't have to go all the way to the top to click on a freaking tab! It feel clunky on chrome and I hope mozilla at least leave us an option to keep it the way I like it in Firefox 4!

agreed.

sick of the google hype.  almost imperceptible speed difference in real world, ugly, uses more RAM, with less features.....

---

### Post by Merk42 on 2010-10-31
> **smellyman said:**
> [QUOTE=madhi19;10051344]I hate the tabs on top I hate it with all my soul! I think that tabs browsing is faster when you don't have to go all the way to the top to click on a freaking tab! It feel clunky on chrome and I hope mozilla at least leave us an option to keep it the way I like it in Firefox 4!agreed.

sick of the google hype.  almost imperceptible speed difference in real world, ugly, uses more RAM, with less features.....[/QUOTE]
Well you'll both be happy to know it's a simple toggle in Firefox 4.
I don't understand all the hate though, having to move your mouse another 30px is really that noticeable?
Also, tabs on top, like a lot of innovative browser features, was actually started in Opera, not Chrome.

---

### Post by lovinglinux on 2010-10-31
If you are not happy with the tabs position, you should try [Tree Style Tabs]("https://addons.mozilla.org/en-US/firefox/addon/5890/") extension or Opera, so  you place the tabs on the side. No more tabs on the top or the bottom for me. I only use vertical tabs now.

---

### Post by LewisGNoa on 2011-04-11
try doing that with the MAc4Lin (one of the several reasons i don't use chrome)

---

### Post by Sand &amp; Mercury on 2011-04-11
> **Merk42 said:**
> Well you'll both be happy to know it's a simple toggle in Firefox 4.
I don't understand all the hate though, having to move your mouse another 30px is really that noticeable?
Also, tabs on top, like a lot of innovative browser features, was actually started in Opera, not Chrome.
Changing tabs by clicking them is for noobs anyway, real men use ctrl-tab or mouse gestures. :cool:

EDIT: Oh wait this thread is 6 months old.

---

### Post by Lucradia on 2011-04-12
> **Sand & Mercury said:**
> Changing tabs by clicking them is for noobs anyway, real men use ctrl-tab or mouse gestures. :cool:

EDIT: Oh wait this thread is 6 months old.

Not that it matters; the titlebar still isn't removed in firefox 4 (the main subject of this thread) in linux under metacity.

The menu bar removal can be done in linux just as it is done in windows: Right-click the menu bar, make sure "Menu Bar" is notchecked.

---

### Post by lovinglinux on 2011-04-12
> **Sand & Mercury said:**
> EDIT: Oh wait this thread is 6 months old.

See [Firefox 4 Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247")

---

### Post by BrokenKingpin on 2011-04-12
I prefer all application, including web browsers to have a standard title bar and menu bar. I use Chromium, and I suppose I do not mind the layout, until I want to change a setting, in which case I find it irritating. I would also prefer that the tabs not be in the title bar, so all applications look and behave the same in terms of window management.

---

