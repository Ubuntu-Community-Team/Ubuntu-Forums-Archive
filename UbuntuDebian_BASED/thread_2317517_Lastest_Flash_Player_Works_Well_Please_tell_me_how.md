---
title: "Lastest Flash Player Works Well Please tell me how secure"
date: 2016-03-17
forum: Ubuntu/Debian BASED
---

### Post by rickhoo1 on 2016-03-17
Use play on Linux go internet install Firefox browser check boxes for flash player & shock wave. check don't update in flash installer. Works great.
on virtual drive.

---

### Post by sandyd on 2016-03-17
See [https://www.adobe.com/software/flash/about/](https://www.adobe.com/software/flash/about/)

The flash player is not being updated beyond 11.2.202.577, so any security vulnerabilities that appear since that release will affect flash.

If you have Ubuntu 15.10, use browser-plugin-freshplayer-pepperflash to provide flash for Firefox instead of using the outdated flash plugin

If you have Ubuntu 14.04, see [http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

---

### Post by nayab on 2016-03-17
Or alternatively, if you are just impatient like me and don't care about security or reliability, install Google Chrome.

---

### Post by buzzingrobot on 2016-03-17
Whatever version you use, both Chrome and Firefox have options to ask you before Flash runs.  This avoids Flash running as soon as you open a page in a browser.  Not only is that annoying, it's potentially insecure. 

I think Chrome has one option to ask before any plugin runs, while Firefox has two settings: One in Addons->Plugins and the other in Prefrences->Applications. Both needed to be configured.

---

### Post by rickhoo1 on 2016-03-19
> **sandyd said:**
> See [https://www.adobe.com/software/flash/about/](https://www.adobe.com/software/flash/about/)

The flash player is not being updated beyond 11.2.202.577, so any security vulnerabilities that appear since that release will affect flash.

If you have Ubuntu 15.10, use browser-plugin-freshplayer-pepperflash to provide flash for Firefox instead of using the outdated flash plugin

If you have Ubuntu 14.04, see [http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

Using Zoin 9 and adobe 20.0 using Wine Play on Linux. Fire Fox 45.01

Never had any luck on installing on the machine version 45.0.

---

### Post by howefield on 2016-03-19
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by buzzingrobot on 2016-03-19
> **rickhoo1 said:**
> [QUOTE=sandyd;13456711]S

The flash player is not being updated beyond 11.2.202.577, so any security vulnerabilities that appear since that release will affect flash.


Adobe will continue to release security patches for the NPAPI Flash used in Firefox on Linux until, I think,  sometime in 2017.  I'd have to look it up, but Adobe long ago announced a date when they will EOL that version.  (I'd guess they'd like to EOL the entire product line, if they could get all their paying corporate customers who use it for content production to abandon it. A good number seem to have no intention of doing that any time soon.)

The version here is at 577, upgraded via the repos as usual. I expect to continue to upgrade Flash that way as long as Adobe makes it available.

Flash of any kind or version is best made secure by removing it.  Failing that, configure your browsers to always prompt you for permission to use it.

---

### Post by Rob Sayer on 2016-03-20
> **nayab said:**
> Or alternatively, if you are just impatient like me and don't care about security or reliability, install Google Chrome.

I'd also suggest Chrome because they have a deal with Adobe so their flash support is much better in Linux than ff's.  Frankly I wouldn't bother with chromium myself ... nowadays it doesn't make sense to me to be a FOSS nut with web software.

But I would *not* describe Chrome as unreliable or insecure.

Flash support is increasingly a moot point though.  HTML5 is quickly becoming the standard.  Unfortunately html5 has embedded DRM, which is why I think insisting that your browser contain no closed source code is silly now.

---

### Post by deadflowr on 2016-03-20
I think everyone here (outside of the OP) is confused about the flash in use.
The OP is using Firefox in WINE, and as such is using Windows flash.

The main question as I read it is, 
[I]If you disable the updater feature in Firefox in WINE, how secure will flash be.
[/I]
My answer is that flash is not that secure to begin with, so disabling the ability to get new updates simply increases that insecurity.

How secure is it in WINE? probably a little more than normal.
Since WINE is designed to run as an unprivileged user (non-root), any exploits would probably break the user's functionalities first.
As any exploits in Windows flash would be built against a true Windows system, 
it would probably be assumed that those exploits wouldn't think about escaping the Linux user's environment
and into the root system.

But really, though, who knows.
Flash is Swiss cheese and full of holes.

At any rate, I don't think it's safe not to update it, regardless.

But that's just me 
(and possibly millions of others)

---

