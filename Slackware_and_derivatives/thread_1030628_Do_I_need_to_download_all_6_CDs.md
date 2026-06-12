---
title: "Do I need to download all 6 CDs?"
date: 2009-01-04
forum: Slackware and derivatives
---

### Post by I-75 on 2009-01-04
If I want to install slackware, do I need to download all 6 CDs? Is there another way?

I  will be installing it on a older laptop and I need something modern and functional and yet faster than Xubuntu.




"  Order the latest version of Slackware Linux on CD-ROM (6 CDs in all), or the whole distribution on a single DVD from The Slackware Store."

---

### Post by cardinals_fan on 2009-01-04
No.  You can just download the ones you need.

Alternatively, you can install SLAX.  That only takes one small CD, but it definitely isn't conventional.  If you're interested, read on:

> **cardinals_fan said:**
> If you're in the mood for a thrill, a fast (but rather dodgy) way of installing Slack is available. Download SLAX and install it:
Quote:
[quote=markds on the slax forums]
[http://backtrack.serveftp.com/backtr...6-install.kmdr](http://backtrack.serveftp.com/backtr...6-install.kmdr)

Its a kmdr script, so download it to where you want, say /usr/share/slax/, then run it using the following :

/usr/bin/kmdr-executor /usr/share/slax/slax6-install.kmdr
Ignore the portion on the "live" version install, use the "real" version install.
Then install slapt-get (although slackpkg seems better, I haven't tried it with this, so do it at your own risk), sync with the Slackware repos, and upgrade. There will be some packages to reinstall using slapt-get (or maybe slackpkg), make sure you get everything on SLAX reinstalled.

This is a rather nasty way of installing Slackware, and you should definitely do things normally to get a real taste, but I like this method because it's fast and doesn't require too much downloading.

EDIT: A quick warning (I'm really enthusiastic about this, aren't I?): this isn't conventional, and you're on your own if you try it. I make no guarantees, and most Slack experts will just flame you for being dumb enough to try this.[/QUOTE]

---

### Post by I-75 on 2009-01-04
Thanks for the info.

---

### Post by Vince4Amy on 2009-01-04
CD 1 to 3 will give you the whole base System and KDE.

---

