---
title: "Feature requests"
date: 2007-04-19
forum: Ubuntu System Panel
---

### Post by bluescreenjunky on 2007-04-19
Hi everyone !l I've been using USP2 svn and browsing the forums for a couple of days and I really like it. However there are a few things I miss, or that could make it even better, maybe some of them are already in there and I just missed them.
Anyway, here's my wishlist :

**-Translations**
Is there a way to translate USP ? Ubuntu is available in virtually every language, so should USP. 

**-Background image, rounded corners etc...**
It would be nice to have a background image for the panel instead of a plain color. Maybe it can be done through themes though.
Same for rounded corners.

**-Most used applications**
I think it would be a nice addition to the applications plugin :for exemple if you have 4 applications in your "favourite apps" and there is enough room to display 8 of them without scrolling, USP could fill the remaining 4 with the applications you use the most and that are not already in your favs.
(did anyone understand what I mean ? lol)

**-Super as a hotkey**
I couldn't get my "super" (or "windows") key to act as a hotkey, is there a way to do that ?

**-More user-friendly plugins config**
Well I know it's beta (or alpha ?) software, but I think it's really important for a Gnome app to be as user friendly as possible. For exemple when you add a plug-in to your panel, instead of asking you to type the name of the plug-in, you should pick it from a list with possibly a small description and an icon for each plugin.
Actually, I think the tabs to configure each plugin are unnecessary... Well I'll do a mock-up to show how I see it.




PS : Thanx for reading =)

---

### Post by Malac on 2007-04-19
> **bluescreenjunky said:**
> **-Translations**
Is there a way to translate USP ? Ubuntu is available in virtually every language, so should USP. 
There are some translations available most are on the "Beta Patches" thread on this forum. We rely on kind people to do these for us I'm afraid.
> **bluescreenjunky said:**
> **-Background image, rounded corners etc...**
It would be nice to have a background image for the panel instead of a plain color. Maybe it can be done through themes though.
Same for rounded corners.
These are not planned for USP2, however they are in for USP3 future development as is true transparency.
> **bluescreenjunky said:**
> **-Most used applications**
I think it would be a nice addition to the applications plugin :for exemple if you have 4 applications in your "favourite apps" and there is enough room to display 8 of them without scrolling, USP could fill the remaining 4 with the applications you use the most and that are not already in your favs.
(did anyone understand what I mean ? lol)
This functionality is sort of already in USP by way of either the 'recent' plugin or the 'shortcuts' plugin. Either one of which can be put next to or on top/below applications to provide this functionality.
> **bluescreenjunky said:**
> **-Super as a hotkey**
I couldn't get my "super" (or "windows") key to act as a hotkey, is there a way to do that ?
This depends on your keyboard map. I use 'Super_L', sometimes 'Meta_L' works the easiest way to find the code is to run xev from a terminal and press the key look for (keysym 0x----, NameHere) in the output the NameHere should be the name to put in to the Preferences field.
> **bluescreenjunky said:**
> **-More user-friendly plugins config**
Well I know it's beta (or alpha ?) software, but I think it's really important for a Gnome app to be as user friendly as possible. For exemple when you add a plug-in to your panel, instead of asking you to type the name of the plug-in, you should pick it from a list with possibly a small description and an icon for each plugin.
Actually, I think the tabs to configure each plugin are unnecessary... Well I'll do a mock-up to show how I see it.
This, again, is planned for USP3 where plugins can be "drag 'n' dropped" into place. The tabbed interface for the Preferences was to allow for the plugins to carry individual code for there own configuration. This means if someone writes a plugin then the Preferences section doesn't need to be completely re-written to allow for this.

Hope this helps.

---

### Post by bluescreenjunky on 2007-04-19
Thanks for the answers !

-Super_L works, thanx =)
-I'll check the patches for translations, hope they'll eventually make their way into the official release.
-USP2 is'nt released yeat, and I'm already impatient to see USP3 :-P

> The tabbed interface for the Preferences was to allow for the plugins to carry individual code for there own configuration. This means if someone writes a plugin then the Preferences section doesn't need to be completely re-written to allow for this.
When I said tab were unnecesary, I was thinking about popup windows instead of tabs. A little like Gaim does it : you have a list of your plugins, and when you select a plugin you can click a "configure plugin" button, which brings a new window with the options for this plugin.
I personnally like the tabs, but it seems that this is the way most Gnome apps work, and maybe it's a little less confusing for new users. Besides, it would allow you to use tabs to organize the options of USP core.

> This functionality is sort of already in USP by way of either the 'recent' plugin or the 'shortcuts' plugin. Either one of which can be put next to or on top/below applications to provide this functionality.
sure, "recent" plugin is handy, but "frequently used" is more complex than "recent", it displays according to the average use of each app during the last x days(*), instead of just the last apps you launched. And the way I described it, it would be useful to anyone right out of the box :
You install USP, and even if you don't take the time to configure your favorite apps (or only one or two), the ones you use the most get in your menu by themselves, in a smarter way than "recent" does.



Anyway, thanks a lot to everyone who works on USP, I've been looking for a gnome menu replacement for a while, and I'm really glad I've found a perfect one !

(*) or even "une moyenne pondérée, avec un coefficient de plus faible quand on remonte plus loin dans le temps", but I don't know how to say  that in english :-P

---

### Post by Malac on 2007-04-19
> **bluescreenjunky said:**
> (*) or even "une moyenne pondérée, avec un coefficient de plus faible quand on remonte plus loin dans le temps", but I don't know how to say  that in english :-P
BabelFish says:
"a weighted average, with a coefficient of weaker when one goes up further in time" :)

Glad I could help, I'll look into the most used apps for USP3.

---

### Post by ADRez on 2007-04-19
> **Malac said:**
> There are some translations available most are on the "Beta Patches" thread on this forum. We rely on kind people to do these for us I'm afraid.

But those are for usp1, not?

---

