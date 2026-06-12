---
title: "Where did unity-lens-shopping go?"
date: 2013-06-19
forum: Ubuntu Development Version
---

### Post by sacridex on 2013-06-19
Hello,

where did this package go?
I wanted to uninstall the package to disable the amazon search, but it is no longer in the repository.
What package deals with the shopping search now?
Please don't tell me it is now an inherent part of unity and you can no longer remove it? :(

---

### Post by IanW on 2013-06-19
Go to the "Privacy" tab in "System Settings" - you can disable it from there.

---

### Post by malspa on 2013-06-19
Interesting. Why isn't it there? I don't have 12.10 or 13.04 installed here, so I can't check, but: [http://packages.ubuntu.com/search?keywords=unity-lens-shopping&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=unity-lens-shopping&searchon=names&suite=all&section=all)

---

### Post by craig10x on 2013-06-19
That's strange...it is still listed in ubuntu software center on my 13.04 install...i just turned off online search in privacy settings instead of actually uninstalling it...

---

### Post by VMC on 2013-06-19
Also, I don't have privacy anymore, removed zietgeist, but still get ads.  This use to wok  ***sudo apt-get remove unity-lens-shopping***

---

### Post by Wiking on 2013-06-19
Does Kubuntu have this feature also?

---

### Post by mc4man on 2013-06-19
There is no shopping lens lens anymore, you're using the beginnings of 100 **scopes** 
Overall a large number of the current & future scopes will only be useful with online access, this includes many that have nothing to do with product searches/results, ect.

Many scopes are individually packages/installed & can be removed or enabled in synaptic or S-c.
As far as product searches, those I've seen are not from packaged scopes, they can only be disabled thru dconf if one wants to have online access enabled for other scopes.

Mentioned here, currently have found 3 sub scopes that provide product results - 
"more_suggestions-amazon.scope":  (obvious
"more_suggestions-skimlinks.scope" (provides results from all over, Target ect.
"more_suggestions-u1ms.scope"  ( obvious

[http://ubuntuforums.org/showthread.php?t=2152761&p=12693960&viewfull=1#post12693960](http://ubuntuforums.org/showthread.php?t=2152761&p=12693960&viewfull=1#post12693960)

---

### Post by VMC on 2013-06-19
That makes it even more difficult than before. I just don't want to have to load another program, dconf-editor to do it. Then there's the hassle of finding all the links. By the way, that link you gave on the other link "https://productsearch.ubuntu.com/smartscopes/v1/search?q=" , what is that, and how did you create it? I got something like this:

> [COLOR=#000000]{"scopes": [["info-openweathermap.scope", "client"], ["music-audacious.scope", "client"], ["music-clementine.scope", "client"], ["music-gmusicbrowser.scope", "client"], ["music-guayadeque.scope", "client"], ["music-musique.scope", "client"], ["music-soundcloud.scope", "client"], ["code-devhelp.scope", "client"], ["code-github.scope", "client"], ["graphics-colourlovers.scope", "client"], ["graphics-deviantart.scope", "client"], ["help-manpages.scope", "client"], ["help-texdoc.scope", "client"], ["help-yelp.scope", "client"], ["recipes-gourmet.scope", "client"], ["reference-imdb.scope", "client"], ["reference-zotero.scope", "client"], ["more_suggestions-amazon.scope", "server"], ["more_suggestions-skimlinks.scope", "server"], ["more_suggestions-u1ms.scope", "server"], ["reference-wikipedia.scope", "server"], ["reference-dictionary.scope", "server"], ["info-ddg_related.scope", "server"]], "type": "recommendations"}
[/COLOR][COLOR=#000000]{"
[/COLOR]...
...


---

### Post by mc4man on 2013-06-19
> **VMC said:**
> That makes it even more difficult than before. I just don't want to have to load another program, dconf-editor to do it. Then there's the hassle of finding all the links. By the way, that link you gave on the other link "https://productsearch.ubuntu.com/smartscopes/v1/search?q=" , what is that, and how did you create it? I got something like this:. 

Easier or harder is I guess a matter of pov, from Ubuntu's they're making it easier for users & as typical will not provide many gui settings options.
At least, (for the moment), there are some user available options thru dconf, though as mentioned in 1st. post  bug links in the scopes thread some are of questionable value.

As long as any settings/options have enabled schemas/keys then it's not that hard to provide a gui to adjust, while unlikely Ubuntu will provide that much it wouldn't be surprising to see some 3rd party app(s) doing so down the road as this whole deal matures.

Here I've dumped 13.10 for the moment, will pick up again a bit down the road though mainly to see if unity/compiz on 13.10 is any better than unity/compiz in 12.04 or 13.04 & if not overall, can any elements, (positive),  of 13.10 be applied to 12/13.04
Ultimately unity7/compiz is dead, as far as unity8(next) on the desktop will likely wait till 14.04 when Ubuntu *thinks* there will be a use-able desktop version (history says it won't, though that could be a matter of of perspective or it may be 11.04 all over again...

As far as the link, found that while digging into what skimlinks was, other than that only know it showed me the names of those sub scopes to disable, ie.
master scope - more_suggestions, sub scopes - amazon ,skimlinks, u1ms

---

### Post by Wiking on 2013-06-19
> **Wiking said:**
> Does Kubuntu have this feature also?

Well since Kubuntu is just Ubuntu with KDE desktop I assume it does have this feature...

---

### Post by QIII on 2013-06-19
No, Kubuntu does not include that feature.

---

### Post by VMC on 2013-06-19
All I want out of the Lens, is when I type the name of installed program, for it only to appear or names that are similar. So gsettings came to my rescue. Now I don't get any offering of recommended programs.

---

### Post by PJs Ronin on 2013-06-19
> **VMC said:**
> All I want out of the Lens, is when I type the name of installed program, for it only to appear or names that are similar. So gsettings came to my rescue. Now I don't get any offering of recommended programs.
def +1

---

### Post by grahammechanical on 2013-06-20
> **Wiking said:**
> Well since Kubuntu is just Ubuntu with KDE desktop I assume it does have this feature...

Kubuntu does not have Unity so it will not have the Dash or the Lenses and Scopes that come with the Dash. It is up to the developers of Kubuntu to decide what they are able to take from Ubuntu and what they can do without and they are doing without the whole Gnome desktop environment. Mind you, I have not tested this out on Kubuntu.

---

### Post by philinux on 2013-06-20
> **sacridex said:**
> Hello,

where did this package go?
I wanted to uninstall the package to disable the amazon search, but it is no longer in the repository.
What package deals with the shopping search now?
Please don't tell me it is now an inherent part of unity and you can no longer remove it? :(

I just updated my saucy from chroot and dist-upgrade. And I noticed this.

```
The following packages will be REMOVED
  account-plugin-generic-oauth appmenu-gtk appmenu-gtk3 libebook-1.2-13 libedataserverui-3.0-1
  libgtksourceview-3.0-0 libharfbuzz0 libharfbuzz0:i386 libmutter0a libsnmp15 libunity-core-6.0-5 libwayland0
  **unity-lens-shopping**
```

---

