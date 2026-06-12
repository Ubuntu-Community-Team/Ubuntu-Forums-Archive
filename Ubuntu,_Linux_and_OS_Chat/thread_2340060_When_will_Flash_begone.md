---
title: "When will Flash begone?"
date: 2016-10-15
forum: Ubuntu, Linux and OS Chat
---

### Post by feartheterrapin on 2016-10-15
It is frustrating how many sites still depend on Flash.  There are many sites that Linux users can not access because of perceived outdated flash.  My recent experiences are those sites providing video content such as Comcast, DirectTV, ESPN and BTN2Go.  Will Flash ever go away as long as sites depend on it so much?  If not, will there ever be a work around for Linux users besides a Windows or Android VM?

---

### Post by deadflowr on 2016-10-15
Soon, flash on linux will be as notably up-to-date as flash everywhere else:
[http://blogs.adobe.com/flashplayer/2016/08/beta-news-flash-player-npapi-for-linux.html]("http://blogs.adobe.com/flashplayer/2016/08/beta-news-flash-player-npapi-for-linux.html")
Note that currently DRM support is currently non-functional, so if you need either you have to use the current stable 11.2X, or a windows plugin work around.
(Only the 11.2 npapi version for linux has DRM support, google chrome ppapi verion has no DRM support)
And 3d accel support only works with Chrome's flash or, again, a windows plugin work around.

---

### Post by vasa1 on 2016-10-15
Have you tried Pepper Flash?

---

### Post by feartheterrapin on 2016-10-15
> **deadflowr said:**
> Soon, flash on linux will be as notably up-to-date as flash everywhere else:
[http://blogs.adobe.com/flashplayer/2016/08/beta-news-flash-player-npapi-for-linux.html](http://blogs.adobe.com/flashplayer/2016/08/beta-news-flash-player-npapi-for-linux.html)
Note that currently DRM support is currently non-functional, so if you need either you have to use the current stable 11.2X, or a windows plugin work around.
(Only the 11.2 npapi version for linux has DRM support, google chrome ppapi verion has no DRM support)
And 3d accel support only works with Chrome's flash or, again, a windows plugin work around.

This is good news I suppose.  I was under the impression Flash was being abandoned.  I assume a ppapi version with DRM support is in the works.

---

### Post by feartheterrapin on 2016-10-15
> **vasa1 said:**
> Have you tried Pepper Flash?

Maybe I miss understood, I thought Pepper Flash is in Chrome.  Although Chrome solves some of my flash issues, there are many sites Chrome does not work.

---

### Post by deadflowr on 2016-10-15
> **feartheterrapin said:**
>  I assume a ppapi version with DRM support is in the works.

Not that I know of.
They've had over 5 years to implement it, and, as of yet, have not.

---

### Post by &amp;KyT$0P# on 2016-10-15
> **feartheterrapin said:**
> Maybe I miss understood, I thought Pepper Flash is in Chrome.  
[freshplayerplugin]("http://packages.ubuntu.com/xenial/browser-plugin-freshplayer-pepperflash").

---

### Post by feartheterrapin on 2016-10-15
> **halogen2 said:**
> [freshplayerplugin]("http://packages.ubuntu.com/xenial/browser-plugin-freshplayer-pepperflash").

Does freshplayerplugin still works since Chrome 54?

Also, I am still confused on the wrapper.  If a site does not work within Linux/Chrome, would if not work in Firefox with freshplayerplugin as well?

---

### Post by &amp;KyT$0P# on 2016-10-15
> **feartheterrapin said:**
> Does freshplayerplugin still works since Chrome 54?
What does Chrome version have to do with this?  It's for Firefox & family, not Chrome/Chromium which can handle PPAPI without a wrapper.

> If a site does not work within Linux/Chrome, would if not work in Firefox with freshplayerplugin as well?
Given the way most websites are coded you cannot assume that.  The easiest way to find out is to try it and see what happens.

---

### Post by buzzingrobot on 2016-10-16
It isn't the Flash plugins that are keeping Flash alive.  It's content producers using Flash.  My assumption is that Adobe is contracted to support Flash for X years with some number of content producers. As long as those are around, Flash is around.  Moving off Flash is not trivial for large sites, especially if they have huge archives of Flash content they need to be accessible without Flash.

AFAIK, the plugin released by Adobe is well behind the curve on features because it has seen only security updates for some time.  The plugin in Chrome apparently does see feature updates but I notice it not working in a considerable number of sites.

---

### Post by feartheterrapin on 2016-10-16
> **halogen2 said:**
> The easiest way to find out is to try it and see what happens.

OK, So I went to the Ubuntu Software Center searched for "freshplayer".  The following three packages showed and were installed:

PPAPI-host NPAPI-plugin adapter for pepperflash
PPAPI-host NPAPI-plugin adapter for libpdf.so from Chrome
PPAPI-host NPAPI-plugin adapter for Native Client from Chrome

Rebooted and tried ESPN, DirectTV, and BTN2Go.  None worked.  Only ESPN provided an error message which is attached (unable to c&p).
[ATTACH=CONFIG]271655[/ATTACH]

---

### Post by monkeybrain20122 on 2016-10-16
freshplayer is just a wrapper for Chrome's pepper flash, if Chrome doesn't work for the drm content neither will freshplayer obviously.

You can install Windows' flash on Firefox via pipelight (a wine hack) and that will work for drm
[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

**First uninstall freshplayer.** After installing pipelight from the page, go to the link "enabling plugins" 

If after restarting Firefox you don't find pipelight flash in Tools> Addons > Plugins, close Firefox again and run these in the terminal

```
sudo pipelight-plugin --update
pipelight-plugin --enable flash
sudo pipelight-plugin --create-mozilla-plugins
```

Other than those drm video sites flash is not needed for videos (most use HTML5 now) so I would set flash's setting to "Ask to activate" or even disable it in Firefox's Tools > Addons > plugins and just activate as needed (now you don't need to restart Firefox for activation to take effect if flash is set to never activate)

---

### Post by bearlake on 2016-10-16
> **monkeybrain20122 said:**
> freshplayer is just a wrapper for Chrome's pepper flash, if Chrome doesn't work for the drm content neither will freshplayer obviously.

You can install Windows' flash on Firefox via pipelight (a wine hack) and that will work for drm
[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

**First uninstall freshplayer.** After installing pipelight from the page, go to the link "enabling plugins" 

If after restarting Firefox you don't find pipelight flash in Tools> Addons > Plugins, close Firefox again and run these in the terminal

```
sudo pipelight-plugin --update
pipelight-plugin --enable flash
sudo pipelight-plugin --create-mozilla-plugins
```

Other than those drm video sites flash is not needed for videos (most use HTML5 now) so I would set flash's setting to "Ask to activate" or even disable it in Firefox's Tools > Addons > plugins and just activate as needed (now you don't need to restart Firefox for activation to take effect if flash is set to never activate)

This has always worked very well for me and the 3 commands between the CODE tags had to be used every time I have done a fresh install.

Very good post and well detailed. +1

---

### Post by feartheterrapin on 2016-10-16
@[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("https://ubuntuforums.org/member.php?u=1843403")

So do you recommend installing all three applications 
```

PPAPI-host NPAPI-plugin adapter for pepperflash
PPAPI-host NPAPI-plugin adapter for libpdf.so from Chrome
PPAPI-host NPAPI-plugin adapter for Native Client from Chrome
```
prior to installing pipelight?

---

### Post by monkeybrain20122 on 2016-10-16
> **feartheterrapin said:**
> @[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("https://ubuntuforums.org/member.php?u=1843403")

So do you recommend installing all three applications 
```

PPAPI-host NPAPI-plugin adapter for pepperflash
PPAPI-host NPAPI-plugin adapter for libpdf.so from Chrome
PPAPI-host NPAPI-plugin adapter for Native Client from Chrome
```
prior to installing pipelight?

You should uninstall the NPAPi-plugin  for pepperflash, the others are fine. The reason is that there is no option in Firefox to selectively enable which flash to use even though they show up as different entries in Tools > Addons > Plugins. Firefox would load the most up to date one. Now with system flash and either pepper flash wrapper **or **pipelight flash it is fine (doesn't need to be removed) since system flash is so far behind in version that it will never be loaded. But if both pepperflash and pipelight flash are installed It would depend on which version is slightly ahead, so if you always want to use one then you should uninstall the other (though if you compile freshplayer from source and put it in .Mozilla/Plugins then you can probably write a script to switch between them or do it manually, basically just rename the one you don't want to use on the fly. There used to be a way using update-alternatives to choose between system flash and pipelight flash but that doesn't work anymore and it has never worked with pepperflash I think)

The pdf and native client don't appear to have anything to do with flash so I think they are ok.

---

