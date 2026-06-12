---
title: "[SOLVED] Not sure where to ask this but.."
date: 2008-06-03
forum: The Cafe
---

### Post by dynamethod on 2008-06-03
I use a social network called "bebo", but as of late(last week or two) the page loads ok but it seems the style sheet wont, i cant really figure this one out, i tried reinstalling firefox but with no luck, then i tried to connect via a proxy service, and the weird thing is that the page loaded fine through the proxy but it wont trying to connect direct!

heres what it looks like from my end when i just type in "www.bebo.com":

[[IMG]http://img260.imageshack.us/img260/7862/screenshotvu2.th.png[/IMG]](http://img260.imageshack.us/my.php?image=screenshotvu2.png)

and then when i use such service as "ninjacloak":

[[IMG]http://img341.imageshack.us/img341/3135/screenshot1tl7.th.png[/IMG]](http://img341.imageshack.us/my.php?image=screenshot1tl7.png)


Is this just me or is anyone else having this issue?


This only happens for "www.bebo.com" for me, no issues with anyother site, but this is really getting annoying for me so help much appreciated!

---

### Post by MeURi on 2008-06-03
I get the correct visualization using Firefox3 rc1 under Windows, so I assume I should get the same results under Ubuntu (cannot switch right now to check)

Is maybe something related to Adblock? (just trying to guess...)

---

### Post by Tundro Walker on 2008-06-03
> **MeURi said:**
> I get the correct visualization using Firefox3 rc1 under Windows, so I assume I should get the same results under Ubuntu (cannot switch right now to check)

Is maybe something related to Adblock? (just trying to guess...)

NoScript can also funkify things when it prevents java & page elements from downloading.

Of course, Bebo may just be one of those sites that disregards web standards and is "best viewed on Internet Explorer".

---

### Post by dynamethod on 2008-06-03
I dont have windows installed currently, i tried the site again with addons disabled(noscript, adblock etc) and still have this same issue :S

---

### Post by ChameleonDave on 2008-06-03
You obviously have some sort of misconfiguration.  The first thing to do is to work out whether it is system-wide or specific to Firefox.

You probably have an alternative browser installed on your system (Epiphany, Konqueror or Opera); if not, they are just a few clicks away.

Try to view Bebo.com in one of them, and tell us if it works.



If it is specific to Firefox, then try using a clean Firefox profile.

Close Fx down, and enter the following into a terminal:

```
mv -T ~/.mozilla/firefox/profiles.ini ~/.mozilla/firefox/profiles.ini.backup
```

Then try Bebo.com in Firefox again.

---

### Post by dynamethod on 2008-06-03
> **ChameleonDave said:**
> You obviously have some sort of misconfiguration.  The first thing to do is to work out whether it is system-wide or specific to Firefox.

You probably have an alternative browser installed on your system (Epiphany, Konqueror or Opera); if not, they are just a few clicks away.

Try to view Bebo.com in one of them, and tell us if it works.



If it is specific to Firefox, then try using a clean Firefox profile.

Close Fx down, and enter the following into a terminal:

```
mv -T ~/.mozilla/firefox/profiles.ini ~/.mozilla/firefox/profiles.ini.backup
```

Then try Bebo.com in Firefox again.


Weird, i tried ff with a new profile, but it wouldnt even load the bebo site, no error or nothing, just sat there loading, same for epihpany browser

---

### Post by ChameleonDave on 2008-06-03
> **dynamethod said:**
> Weird, i tried ff with a new profile, but it wouldnt even load the bebo site, no error or nothing, just sat there loading, same for epihpany browser
Maybe Bebo was down for a moment.  Try again.  I can see it.

Are you browsing from home?  If not, perhaps there is some sort of proxy blocking you.  Can you load other social networking sites?

---

### Post by dynamethod on 2008-06-03
Just restored my original profile now, and the site is displaying fine, oddball stuff eh?

---

### Post by az on 2008-06-03
> **dynamethod said:**
> Just restored my original profile now, and the site is displaying fine, oddball stuff eh?

If that ever happens to you again, try reloading the page using F5 (or whatever the equivalent is in your borwser).  That will clear the cache for that page and load it again.  If you have a broken css file in your cache, just refreshing the page will not fix it and you will get results similar to what you mention.

Loading the page using a proxy uses a different URL and therefore a different cache.

---

