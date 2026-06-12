---
title: "Flash support ? nikonimagespace.com"
date: 2016-01-15
forum: Ubuntu Studio
---

### Post by Dave_Langston on 2016-01-15
I've only just installed UB and I want to use it for editing my photos but nikonimagespace.com says I need an adobe flash update, I have the latest version already.

Is this something I can fix do you think or would a email to nikon help ? I would point out you can access the site but not once logged in, it's then it throws the message.

---

### Post by pqwoerituytrueiwoq on 2016-01-15
the version of adobe flash available to firefox only get security updates
adobe has dropped flash support for linux and is in maintenance only (security fixes only)
if you require the latest version of flash you have to use google chrome or [FONT=courier new]chromium[/FONT] with [FONT=courier new]pepperflashplugin-nonfree[/FONT] installed

---

### Post by Dennis N on 2016-01-15
Visit your site using Chromium browser instead of Firefox, and you will be using Adobe flash version 20.0.0.267 instead of 11.2.202.223 (as of today, Jan 15). 

You can always have the lastest versions of Adobe flash by installing the package adobe-flashplugin from the Canonical Partners repository. This same package services both Firefox and Chromium and keeps them up to date automatically. Enable Canonical Partners in your software sources, "Other software" tab.

---

### Post by Dave_Langston on 2016-01-16
Thanks for the help but I get the same message in Chromium and adobe-flashplugin does not come up in the software search even under Canonical Partners repository.

Sorry ignore that ! I didn't know although the software section show Canonical it wasn't activate because you need to choose it from the source prefs. I've not edited the above incase someone else is as stupid as I :-)

---

### Post by pqwoerituytrueiwoq on 2016-01-18
to use the latest flash player in chromium you need to have [pepperflashplugin-nonfree](apt:pepperflashplugin-nonfree) installed

---

### Post by Dennis N on 2016-01-18
> **pqwoerituytrueiwoq said:**
> to use the latest flash player in chromium you need to have [pepperflashplugin-nonfree](apt:pepperflashplugin-nonfree) installed

The pepperflashplugin-nonfree package is now deprecated, although it may still work. 

> As of 2015-05, the old "pepperflashplugin-nonfree" is deprecated in favor of an official, maintained, one-step package called adobe-flashplugin, which works for Firefox and Chromium and derivatives...

[https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

So I have been using **adobe-flashplugin** for months now and getting flash updates for both my Firefox and Chromium browsers in one package.

---

### Post by pqwoerituytrueiwoq on 2016-01-19
im on 14.04 and have adobe-flashplugin installed and only have flash 11,2,202,559 installed in firefox, chromium has 20,0,0,267 however i have pepperflashplugin-nonfree installed

---

### Post by Dennis N on 2016-01-19
I suppose one can use that pepperflash source as long as it provides what you want - until they decide to pull the plug. I prefer to have one reliable source for both plugins in one package, and would recommend that to new users since the pepperflash is deprecated (no longer recommended, and no assurance it will be available in the future).

I just did a new Chromium install. Some comments on flash in Chromium that might be of use to a new user:

There is no flash capability after I install Chromium. I then installed adobe-flashplugin from Canonical Partners, restarted Chromium, and it had the latest version (20.0.0.286) working (reported from the Adobe test page link below). No PPA to be concerned with. Installing adobe-flashplugin removes flashplugin-installer if you had that installed for the Firefox flash player.

One confusing thing I noticed in Chromium is that if I look at chrome://plugins it does not display the Chromium-compatable plugin. Mine displays:

Adobe Flash Player - Version: 11.2.999.999
Shockwave Flash 11.2 r999

Yet when I visit the Adobe Plugin Test Page [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)
it reports "You have version 20.0.0.286 installed"

This is the current version as of 19 Jan 2016.

---

