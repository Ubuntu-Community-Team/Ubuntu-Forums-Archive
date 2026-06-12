---
title: "Firefox and uBlock Origin"
date: 2015-06-29
forum: The Cafe
---

### Post by vasa1 on 2015-06-29
Anyone using the uBlock extension for Firefox? Which version do you use? There are (at least) two versions @ AMO:
[https://addons.mozilla.org/En-us/firefox/addon/ublock/](https://addons.mozilla.org/En-us/firefox/addon/ublock/)
and
[https://addons.mozilla.org/En-us/firefox/addon/ublock-origin/](https://addons.mozilla.org/En-us/firefox/addon/ublock-origin/)

---

### Post by ajgreeny on 2015-06-29
I have version 0.9.1.0.1 running on my machine; I was not even aware until your post that there was another version available, but now I am investigating what the differences might be.

---

### Post by vasa1 on 2015-06-29
> **ajgreeny said:**
> I have version 0.9.1.0.1 running on my machine; I was not even aware until your post that there was another version available, but now I am investigating what the differences might be.
[http://www.ghacks.net/2015/04/25/official-ublock-origin-add-on-lands-for-firefox/](http://www.ghacks.net/2015/04/25/official-ublock-origin-add-on-lands-for-firefox/)
[http://www.wilderssecurity.com/threads/ublock-a-lean-and-fast-blocker.365273/](http://www.wilderssecurity.com/threads/ublock-a-lean-and-fast-blocker.365273/)

Based on my reading of both links (and the comments in the first link), I went for the second extension which I believe is the one maintained by the original developer, Raymond Hill, aka gorhill.

FWIW, the version of **uBlock Origin** I just installed is 0.9.8.2. I could install my custom filters from ABP without any problem.

---

### Post by night_sky2 on 2015-06-29
**-** ublock Origin is a fork of the main project maintained by Raymond Hill, the original founder of uBlock.

**-** uBlock is now considered the main project and is very similar to uBlock Origin but now maintained by other devs (such as chrisaljoudi)
 when Raymond Hill leaved the project only to come back about a week later to relaunch his own version. (yeah complicated story)

I prefer uBlock (Origin or not) over Adblock Plus. It is easier on ressources. That's the addon I install on people's computers requiring a ''set and forget'' blocker.

As for myself, I have switched completely to NoScript and I don't really need to rely on blacklists anymore.

---

### Post by sammiev on 2015-06-29
No issues with uBlock and I do like to add NoScript to the pie.

---

### Post by vasa1 on 2015-07-01
Where does ublock save its settings, filters, rules, etc?

I don't even see a ublock folder in my profile folder.

I would like to back up stuff in case I mess up.

When using ABP, I used to back up /home/vasa1/.mozilla/firefox/xxxxxxxx.Default User/adblockplus/patterns.ini.

Found one! /home/vasa1/.mozilla/firefox/xxxxxxxx.Default User/extension-data/ublock0.sqlite

I also saw [this]("http://www.wilderssecurity.com/threads/ublock-a-lean-and-fast-blocker.365273/page-12#post-2417031"):> Re "it would seem to me that you must read some sort of settings file to guarantee that the update is populated correctly":

uBlock uses a DOM storage-like API to save user settings/data. When the extension update, that storage is not touched, hence uBlock should reload just like when you restart your browser. When you restore from file, I blank that storage and write over with the parsed content of the file. 

---

### Post by ajgreeny on 2015-07-01
There is a **.mozilla/firefox/qn4bdmr0.default/extension-data/ublock.sqlite** in my home which I presume is the database that contains all the data for the blocker.

You can also back up the settings as a plain text file by clicking the icon in the toolbar, then clicking on the titlebar of the dialogue box that appears you get to the ublock dashboard.  In the settings tab there is a backup and restore option.

---

### Post by vasa1 on 2015-07-02
> **ajgreeny said:**
> There is a **.mozilla/firefox/qn4bdmr0.default/extension-data/ublock.sqlite** in my home which I presume is the database that contains all the data for the blocker.

You can also back up the settings as a plain text file by clicking the icon in the toolbar, then clicking on the titlebar of the dialogue box that appears you get to the ublock dashboard.  In the settings tab there is a backup and restore option.Thanks for that. But I've snuck back to ABP. I feel more comfortable with it for my needs.

---

### Post by vasa1 on 2015-07-05
> **vasa1 said:**
> Thanks for that. But I've snuck back to ABP. I feel more comfortable with it for my needs.And now I'm back with **ublock origin** in *advanced user* mode. I even reported a (very minor) [issue]("https://github.com/gorhill/uBlock/issues/448") with the wiki that's now fixed :)

---

### Post by vasa1 on 2015-07-07
With Firefox 39, it is still possible to have a custom newtab page but I read somewhere that that option may go away.

uBlock Origin is developing pretty fast and so is Firefox. The following may no longer be applicable.

```
When creating a new tab and clicking a tile, here is what is reported for the behind-the-scene scope:

09:36:36 xhr https://tiles.services.mozilla.com/v2/links/click
09:36:34 xhr https://tiles.services.mozilla.com/v2/links/view

So here is a dynamic filtering rule to foil this new Firefox data-mining behavior:

behind-the-scene tiles.services.mozilla.com * block

If you would rather not use dynamic filtering, the following custom static filter will also work:

||tiles.services.mozilla.com^$domain=behind-the-scene

```Source: [https://github.com/gorhill/uBlock/wiki/Tips-and-tricks-waterfall](https://github.com/gorhill/uBlock/wiki/Tips-and-tricks-waterfall)

---

