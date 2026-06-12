---
title: "Firefox Starting to Look Like Swiss Cheese"
date: 2005-05-10
forum: Server Platforms
---

### Post by Segovia on 2005-05-10
Two more vulnerabilites discovered two days ago, as most of you know.

What I'm wondering is when these fixes will hit Hoary.  As far as I know, we haven't even yet received the fixes that were added to Firefox 1.03.  I've had javascript disabled for weeks now, it seems.

I'm not even sure to what extent these vulnerabilities effect Linux systems?  It's not clear in the advisories that I've read.

---

### Post by defkewl on 2005-05-10
Be patient. They're working on Firefox 1.4 which will be out soon.

---

### Post by nocturn on 2005-05-11
Good news and bad news.

The vuln are not exploitable because the default install allows updates from 2 sites only and they have taken emergency measures to prevent infection.
You can also be save from this by disabling software updates wile leaving Javascript on.

The bad new is that javascript in FF on Warty and Hoary still has vulnerabilities that where fixed in 1.0.3, but those patches are not out for Ubuntu.
If you want to be safe from them, you'll need Jdong's backport.

---

### Post by JonahRowley on 2005-05-11
It's bound to happen.  Firefox is huge, there is a *lot* of code there.  I personally don't use it, not only is it slow (especially for a browser claiming to be fast), but the amount of reachable code that I'm not even using is boggling.

This is also the bane (or boon?) of popularity.  Firefox has gotten more attention in the past 6 months; there are more eyes on the code, and more eyes mean more bugs found.  This trend will continue, except to see more Firefox bugs in the future.

---

### Post by Segovia on 2005-05-11
[QUOTE=nocturn]The bad new is that javascript in FF on Warty and Hoary still has vulnerabilities that where fixed in 1.0.3, but those patches are not out for Ubuntu.[/QUOTE]
Looks like those just hit the repos a couple hours ago.  :)

---

### Post by nocturn on 2005-05-11
The fixes from 1.0.3 are out!  Let's upgrade!

For Warty still nothing though :-(

---

### Post by Ironi on 2005-05-11
[QUOTE=Segovia]Two more vulnerabilites discovered two days ago, as most of you know.
[/QUOTE]
Indeed.

> 
What I'm wondering is when these fixes will hit Hoary.  As far as I know, we haven't even yet received the fixes that were added to Firefox 1.03.  I've had javascript disabled for weeks now, it seems.

1.0.3 is *still* unavailable in both hoary and breezy, while it's been available for Debian unstable since [April 18th](http://packages.qa.debian.org/m/mozilla-firefox.html). I don't know what the Ubuntu guys are doing, but they're falling behind with other packages as well.

> 
I'm not even sure to what extent these vulnerabilities effect Linux systems?  It's not clear in the advisories that I've read.
There is no specific mention of a particular platform, so they probably apply equally to every one that Firefox runs on.

---

