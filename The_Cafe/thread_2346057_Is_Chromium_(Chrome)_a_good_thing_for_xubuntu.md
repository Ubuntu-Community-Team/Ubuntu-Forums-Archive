---
title: "Is Chromium (Chrome) a good thing for xubuntu"
date: 2016-12-10
forum: The Cafe
---

### Post by Ralph L on 2016-12-10
I currently run Firefox as my browser on Xubuntu 16.04 LTS.  I have been having some abort problems (maybe having to do with add-ons, don't know).  Anyway I hear that Chrome is currently the most used personal computer browser, so I am considering switching. 
1.  Should I install chromium with synaptic, or is chromium different from chrome?
2.  What privacy add-ons are required.  For privacy under Firefox I currently run Better Privacy (LSO cookies), Ublock, Privacy Badger, and Self Destructing Cookies.  I also run several non-privacy add-ons to add capability such at unMHT.
3.  I have concerns about google spying on me.  I have heard that chromium is open source so other people can examine it for spyware, and hence it shouldn't have any.  Is this true?
4.  I would be interested in anybody's experience with Chromium and whether or not they liked it better than Firefox.
5.  How do I move my Bookmarks from Firefox to Chromium?

Thank you very much.

---

### Post by DogMatix on 2016-12-10
Chromium is open source whilst (Google) Chrome has some proprietary software (i.e. media codecs).
Using Firefox I personally install 'UBlock Origin', 'https everywhere' and 'Disconnect' add-ons for added privacy. Although, I do get called part of the tinfoil hat brigade by my mates.

I used Chromium for several years and still do, but I have returned to Firefox as my default browser.

Chrome will, however, give you the best best 'out of the box' Flash (pepper) compatibility.

---

### Post by Dragonbite on 2016-12-13
If you are going to install Chromium, make sure to do ```
sudo apt install chromium-browser
``` because "chromium" is a game.

Chromium is the open source development version before Google takes its code and injects the tracking device and other proprietary bits.  So it sounds like a way to get Google Chrome like capabilities without the bloated privacy hacks.

If you log in to a Google account and synchronize, then whatever settings you flag (passwords, extensions, bookmarks, etc.) will synchronize between Google Chrome and Chromium.Years ago I had an issue with something not being deleted but I also included a Chromebook in the mix and this was yeeeears ago.

I have gotten Chromium opening up with asking whether I want to restore the tabs I had opened before, as if it crashed (when it didn't).  A minor annoyance but that was all.

To move bookmarks from Firefox you want to go to "Show All Bookmarks" and Export them as HTML.  Then in Chromium you import the bookmarks.  Only difference is Firefox uses "Bookmarks Toolbar" while Chromium uses "Bookmarks bar".  So you would have to copy or move from the "Bookmarks Toolbar" folder to "Bookmarks bar" to get them to show up in the same place.

---

