---
title: "Chromium &quot;Snaps&quot;on every page -- Firefox runs out of memory"
date: 2014-08-15
forum: Ubuntu Development Version
---

### Post by VinDSL on 2014-08-15
After a recent update (earlier this week) chromium-browser started 'snapping' me on ever page.  Chromium loads, but anything I do crashes it, with a "Aw snap..." dialog.

Looking at the log, the memory space Chromium is trying to use is all zeros 00x00000 as so forth, and so on.

Firefox works better, but after an hour or so, RAM usage grows to 85% -- swap grows to 100% usage -- then the whole machine becomes unresponsive.  Only thing that corrects it is a reboot.

This is happening in both Unity and Gnome Shell DEs - multiple users -- latest stable and beta version(s) of Chromium -- latest version of Fx.

Anybody else experiencing this?!?!?

---

### Post by cariboo on 2014-08-15
I'm not seeing that here, but Chromium crashes in a strange way when first started. It starts up with a transparent window for a couple seconds before anything loads, then when I shut it down, I see a notification that it has crashed and it asks if I'd like to relaunch it.

---

### Post by VinDSL on 2014-08-15
> **cariboo907 said:**
> I'm not seeing that here, but Chromium crashes in a strange way when first started. It starts up with a transparent window for a couple seconds before anything loads, then when I shut it down, I see a notification that it has crashed and it asks if I'd like to relaunch it.
Yep, I'm seeing the same thing(s).  Okay, well, thx for the confirmation.

Been messing with it for two days -- I give up.  I don't know what they did to it.

The latest trunk build -- 38.0.2125.0 (Developer Build 289931) -- works just fine.  I'll use that for awhile.  ;)

---

### Post by Cavsfan on 2014-08-15
That was weird! I had been using FireFox mostly and after running it for an hour or so, it starts using more and more cpu the more I surfed.
When I scroll down the page it pauses as it scrolls while using more cpu.
If I close it and run Bleachbit to get rid of the cache, etc. and start it back up it seems ok for a while until the same occurs.

Chromium-br does just what you said. It opens to a big transparent box and after 10 seconds or so finally goes to the home page. It seems to act ok for the 5 minutes or so I surfed around.
But when I closed it there was a box open saying it had crashed asking if I wanted to relaunch it.

So, something's wrong.

---

### Post by VinDSL on 2014-08-15
> **Cavsfan said:**
> So, something's wrong.

Heh!  Yep...

Linkage:  [https://chromium-build.appspot.com/p/chromium/console](https://chromium-build.appspot.com/p/chromium/console)

Check out this waterfall:  [http://build.chromium.org/p/chromium.gpu.fyi/waterfall?builder=Linux%20Release%20(Intel)](http://build.chromium.org/p/chromium.gpu.fyi/waterfall?builder=Linux%20Release%20(Intel))

---

### Post by VinDSL on 2014-08-16
The trunk build worked a treat.  PepperFlash, PPAPI, and Google Native Client API all working -- no RAM/CPU issues :)

---

### Post by Cavsfan on 2014-08-18
Pretty strange running Chromium from the repos and all is well. No unusual cpu usage and seems normal and then a bug report pops up.
It asked it I wanted to leave closed or relaunch but it never quit. :p

I'm still running it too.

---

### Post by Cavsfan on 2014-08-18
Still browsing with Chromium and having no problems.

---

### Post by Cavsfan on 2014-08-18
Other than starting up slow with a transparent window for a few seconds everything else works great. 

Chromium just became my browser of choice. :guitar:

---

### Post by Cavsfan on 2014-08-19
It started slow and brought up the bug report but it didn't close. Seems to run fine after that initial knot.

[[IMG]http://en.zimagez.com/miniature/screenshotfrom2014-08-19131001.png[/IMG]]("http://en.zimagez.com/zimage/screenshotfrom2014-08-19131001.php")

---

### Post by cariboo on 2014-08-19
I'm just playing with a [Plasma 5]("http://www.kde.org/announcements/plasma5.0/") install in vbox, and Chromium starts right away, and hasn't crashed so far.

---

### Post by Cavsfan on 2014-08-19
I'm loving it! I'm about this far |-| from making Chromium my default browser. I guess I had too much anti-spyware etc. stuff on Firefox that I could rarely see any videos and other stuff on almost any site.
So instead of NoScript or Ghostery I'm just going with Disconnect and everything is amazingly good. I'm seeing things easier now than I have in many years.

I've had to copy links from Firefox and past them into Opera just to see videos, etc. Looks like those days are over. I know it's not Chromium as I believe everything is using version 36 so I wonder what is causing this on Utopic.

---

### Post by VinDSL on 2014-08-21
I've been a Chromium fanboi, for the past few years.  I'm starting to feel the same way about Iceweasel (Debian's Firefox twist).

Anyway, get this...

A few minutes ago, I was looking for a saved password, and I thought I would try Chromium (the repo build).  Same thing -- couldn't even look at "Settings" without snapping.

For giggles, I tried starting up the chromium-browser, using my trunk build data directory, and Pepperflash enabled:

```
vindsl@Zuul:~$ chromium-browser --user-data-dir=/home/vindsl/.config/chromium-canary --ppapi-flash-path=/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so --ppapi-flash-version=14.0.0.177 %u

```

Chromium opened up normally, and worked just fine.

Hrm...  :confused:

---

### Post by ventrical on 2014-08-21
> **Cavsfan said:**
> That was weird! I had been using FireFox mostly and after running it for an hour or so, it starts using more and more cpu the more I surfed.
When I scroll down the page it pauses as it scrolls while using more cpu.
If I close it and run Bleachbit to get rid of the cache, etc. and start it back up it seems ok for a while until the same occurs.

Chromium-br does just what you said. It opens to a big transparent box and after 10 seconds or so finally goes to the home page. It seems to act ok for the 5 minutes or so I surfed around.
But when I closed it there was a box open saying it had crashed asking if I wanted to relaunch it.

So, something's wrong.

Same here  with ff, except when I scroll it actually uses more memory, back and forth. Otherwise ok.

---

### Post by cariboo on 2014-08-21
> **cariboo907 said:**
> I'm just playing with a [Plasma 5]("http://www.kde.org/announcements/plasma5.0/") install in vbox, and Chromium starts right away, and hasn't crashed so far.

I assumed the plasma 5 iso was based on utopic, but it wasn't. After upgrading it to 14.10 and enabling the utopic ppa, I'm now getting the same thing as VinDSL, getting an Aw Snap on every page except for the Google search page.

---

### Post by Cavsfan on 2014-08-21
I believe this problem was fixed with today's updates but not sure. Chromium didn't open to a blank transparent box like it did before.
I never did encounter the snaps that you all mention.

```
Preparing to unpack .../chromium-browser-l10n_36.0.1985.143-0ubuntu1~pkg1042_all.deb ...
Unpacking chromium-browser-l10n (36.0.1985.143-0ubuntu1~pkg1042) over (36.0.1985.125-0ubuntu2) ...
Preparing to unpack .../chromium-codecs-ffmpeg-extra_36.0.1985.143-0ubuntu1~pkg1042_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (36.0.1985.143-0ubuntu1~pkg1042) over (36.0.1985.125-0ubuntu2) ...
Preparing to unpack .../chromium-browser_36.0.1985.143-0ubuntu1~pkg1042_amd64.deb ...
Unpacking chromium-browser (36.0.1985.143-0ubuntu1~pkg1042) over (36.0.1985.125-0ubuntu2) ...

```

---

### Post by Cavsfan on 2014-08-21
It seems to be fixed. Can anyone confirm? I don't see anything in the changelog.

On a side note, I guess I am now a fanboi of Chromium as well. :p Chrome on windows.
When they made the change to allow you to specify a home page when you clicked the home button helped a lot.

The one issue I have that I haven't found a cure for is when you say open a site in a new tab, it doesn't automatically switch to that new tab.
I have to manually click on the new tab. Is there a fix for this such as in Firefox?

[ATTACH=CONFIG]255700[/ATTACH]

---

### Post by ventrical on 2014-08-21
It works just fine here. Very snappy and fresh although I am not a fan of Chromium, it seems to be faster than ff.

---

### Post by VinDSL on 2014-08-21
Working here, too...  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-21-aug-2014(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-21-aug-2014.png")[/INDENT]

---

### Post by VinDSL on 2014-08-22
> **Cavsfan said:**
> The one issue I have that I haven't found a cure for is when you say open a site in a new tab, it doesn't automatically switch to that new tab.

I just "middle-click" the link -- click the link using my mouse-wheel -- and the link will open in a new tab.

They used the have an extension called "Chrome Toolbox" that did what you want, but it was built using NPAPI, so it doesn't work with the AURA UI stack now.

---

### Post by Cavsfan on 2014-08-22
> **VinDSL said:**
> I just "middle-click" the link -- click the link using my mouse-wheel -- and the link will open in a new tab.

They used the have an extension called "Chrome Toolbox" that did what you want, but it was built using NPAPI, so it doesn't work with the AURA UI stack now.

Thanks Bro! I'll do that! I tried everything. Googled it and found nothing that worked.

Edit: Err it opens in a new tab but doesn't automatically switch to that tab. That's what I'm looking for some tweak or whatever that will take me to that new tab.

---

### Post by Cavsfan on 2014-08-22
I have found that if I click a link and drag it to a tab at the top that it does open the link and switch to that tab.

You just have to wait until you see the little down arrow then let it go and it switches to the new link/tab.

---

