---
title: "Chromium 29 has no buttons..."
date: 2013-09-10
forum: Ubuntu Development Version
---

### Post by TenPlus1 on 2013-09-10
I'm running Lubuntu 13.10 beta 1 on my desktop for testing and the latest update gave me Chromium Browser 29 to play with but unfortunately after an update and reboot the browser has no buttons or address bar, just a tab window to access websites from (mainly by searching google)...  I've tried accessing options and other prefs to no avail, any idea why this is happening ?

Note:  I cannot force install the old version...

---

### Post by VinDSL on 2013-09-10
Same here, after yesterday's upgrade.

While I was doing the upgrade, I got a fatal error.  

Dialog said some file was not going to be overwritten because it was also contained in something else -- cannot remember the exact error.

I haven't tried fixing it yet.  Doesn't really effect me, because I normally run the raw trunk release (currently Chromium 31)

```
Chromium 31.0.1626.0 (Developer Build 221966) 
OS: Linux 
Blink: 537.36 (@157409)
JavaScript: V8 3.21.11.1
Flash: 11.2 r202
User Agent: Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/31.0.1626.0 Safari/537.36
Command Line:  /home/vindsl/.chrome-linux/chrome --disable-setuid-sandbox --user-data-dir=/home/vindsl/.config/chromium-canary --flag-switches-begin --flag-switches-end
Executable Path: /home/vindsl/.chrome-linux/chrome
Profile Path: /home/vindsl/.config/chromium-canary/Default

```


You could try the [trunk build]("https://download-chromium.appspot.com/") (not for the faint of heart). It requires manual installation/updating.

If you're not comfortable doing that, I'll try to fix Chromium 29 later today, and post the results here.

---

### Post by vasa1 on 2013-09-10
In case you don't get an answer here, try [https://lists.ubuntu.com/mailman/listinfo/lubuntu-users](https://lists.ubuntu.com/mailman/listinfo/lubuntu-users). Quite a few testers post there.

---

### Post by TenPlus1 on 2013-09-10
Thanks...  Will wait and see if problem fixes itself on Canonical's end, failing that I'll run the dev build...

---

### Post by cariboo on 2013-09-10
I just did an update, the chromium update failed the first time, and gave me all sorts of weird errors including the main page of the forum was trying to use my web cam. I ran:

```
apt-get update
``` 

the chromium upgrade completed without any error messages.

BTW, my web cam is sitting on a shelf about 6 feet from the computer, and not plugged in.

---

### Post by P-I H on 2013-09-10
I also had some problem at upgrade. When I started USC to remove Chromium, I was told there was upgrade problems. USC offered me to correct those, which I gratefully accepted. After this the upgrade with Synaptic went OK.

In case the buttons are close, minimize and maximize, there is a setting, "Use system titlebar and borders" that must be checked.

---

### Post by VinDSL on 2013-09-10
Interesting!

I played around with this n' that -- purged / re-installed stuff -- you know, all the usual tricks.

The only thing that worked (for me) was installing the Precise build of Chromium 29 in Saucy.

Source:  [http://www.ubuntuupdates.org/package/chromium_stable_channel/precise/main/base/chromium-browser](http://www.ubuntuupdates.org/package/chromium_stable_channel/precise/main/base/chromium-browser)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-10-sep-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-sep-2013-1.png")[/INDENT]

---

### Post by VinDSL on 2013-09-10
> **cariboo907 said:**
> I just did an update, the chromium update failed the first time, and gave me all sorts of weird errors including the main page of the forum was trying to use my web cam. 
Aha!

Maybe that's why the Saucy build doesn't work for me.  I don't have a web cam...  ;)

---

### Post by cariboo on 2013-09-10
> **VinDSL said:**
> Aha!

Maybe that's why the Saucy build doesn't work for me.  I don't have a web cam...  ;)

I think all you have to do is have it in the same room as the computer. :-D

---

### Post by VinDSL on 2013-09-10
> **cariboo907 said:**
> I think all you have to do is have it in the same room as the computer. :-D
LoL!  :D

BTW, I just realized the category in the title says 'lubuntu'.  The shot above is GS 3.9.91 Staging.

Buttons work in LXDE/Openbox too...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-10-sep-2013-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-10-sep-2013-2.png")[/INDENT]


Most assuredly, that Saucy build is bogus...

---

### Post by TenPlus1 on 2013-09-11
Buttons = Back / Forward / Address Bar...  The window buttons like close and minimise work ok...

---

### Post by VinDSL on 2013-09-11
> **TenPlus1 said:**
> Buttons = Back / Forward / Address Bar...  The window buttons like close and minimise work ok...
Correct...

All I *was* getting before was a window, with close/min/max buttons.

It looked like one of those 'new' windows that pop up, when you click on an advertisement, or whatever.

---

### Post by jerrylamos on 2013-09-11
Try googling "chrome browser linux" and download/install the latest deb, 32 or 64 bit as appropriate:
sudo dpkg -i *deb
sudo apt-get -f install
see if it's any better.  I've read "chromium" is usually downlevel compared to the real thing.  Actually depending on the partition I run either.  This is mozilla firefox because on this 1 GB netbook both the chrom* on occasion get "He's dead Jim" because they are memory hogs compared to firefox.  They are better at filling in petitions and easier sharing bookmarks between my various test pc's than mozilla firefox.

---

### Post by VinDSL on 2013-09-11
> **jerrylamos said:**
> I've read "chromium" is usually downlevel compared to the real thing.[...]
SOURCE:  [http://packages.debian.org/wheezy/chromium](http://packages.debian.org/wheezy/chromium)

> Chromium serves as a base for Google Chrome, which is Chromium rebranded (name and logo) _with very few additions_ **[COLOR="#FF0000"]such as usage tracking[/COLOR]** and an auto-updater system.

The "usage tracking" is what scares me away from Chrome.

Caveat emptor...  ;)

---

### Post by VinDSL on 2013-09-12
Forgot to pin chromium-browser...  :)

Accidentally upgraded to:  29.0.1547.65 (Developer Build **[COLOR="#0000CD"]29.0.1547.65-0ubuntu2[/COLOR]**)

The coast is clear.  Chromium 29 is working fine, now.  ;)

```
Launchpad-Bugs-Fixed: 1208518 1222488 1223251

Changes: 
 chromium-browser (29.0.1547.65-0ubuntu2) saucy; urgency=low
 .
   * debian/control: Make chromium-browser-l10n Replaces chromium-browser so
     that new translations that were added in v28 packaging are now in the
     correct -l10n package.  (LP: #1222488)
   * debian/rules: Remove unused duplicate-exclusion patterns. Again.
   * debian/control: Make codecs packages no longer Depend on chromium-browser,
     so that "extras" metapackages can pull them in without enormous browser.
     (LP: #1208518)
   * debian/tests/control: Don't use needs-build flag as we don't need it
     presently. Also, disable autopkgtest "smoketest" failure until its
     misbehavior on some environments can be diagnosed from log files.
   * debian/patches/4-chromeless-window-launch-option.patch: Add missing
     construction initializer. (LP: #1223251)
```

---

