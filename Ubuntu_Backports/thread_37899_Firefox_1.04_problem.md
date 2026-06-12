---
title: "Firefox 1.04 problem"
date: 2005-05-29
forum: Ubuntu Backports
---

### Post by joele on 2005-05-29
I can no longer visit the forum at Digital Camera Resource...

If I go to [www.dcresource.com](www.dcresource.com) and then click on 'FORUMS', firefox just vanishes (closes).... very strange.. It works fine with 1.04 on my windows laptop... Can anyone else confirm that this is only happening with this version of firefox or only on my box???

---

### Post by uber_geek on 2005-05-29
Works fine on mine - with 1.0.4~5.04ubp1+1.0.2

---

### Post by dabear on 2005-05-29
[QUOTE=uber_geek]Works fine on mine - with 1.0.4~5.04ubp1+1.0.2[/QUOTE]
Confirmed. No errors with 
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.8) Gecko/20050513 Firefox/1.0.4 (Ubuntu package 1.0.4~5.04ubp1+1.0.2)

---

### Post by joele on 2005-05-29
Strange still crashes mine, and no other websites have given me problems...

ohh well thanks for confirming that it is only my PC, its a start.. might have to reinstall firefox...

---

### Post by jdong on 2005-05-29
No problems here, both with 1.04 in Stable, and the GCC4-compiled 1.04 in Staging.

The site does use flash for ads... Do other pages that use  flash work?

---

### Post by joele on 2005-05-29
yeah they do... I'm not sure what my browser has against that web site LOL...

I will try to reinstall/reconfigure tonight and see if it clears up, I didn't get a chance yesterday...

---

### Post by wallijonn on 2005-05-30
[QUOTE=dabear]Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.8) Gecko/20050513 Firefox/1.0.4 (Ubuntu package 1.0.4~5.04ubp1+1.0.2)[/QUOTE]

Exactly how does one get the [COLOR=Red]1.0.4~5.04ubp1+1.0.2[/COLOR] update?

---

### Post by blyzzz on 2005-05-30
maybe the problem is that you have installed sun-j2**sdk**1.5 which creates broken symlinks und firefox crashes if you enter a site with java

to fix it put this in a consolewindow

```
sudo ln -s /usr/lib/j2sdk1.5-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/
```

i hope it help

> Exactly how does one get the 1.0.4~5.04ubp1+1.0.2 update?

it was the first firefox 1.0.4 backport
before it was backportet from breezy

---

### Post by joele on 2005-06-02
OK Problem solved, I am not sure why though

I worked out if I started from a terminal it did not crash, so the only difference between what I did at terminal 'firefox' and what was in the gnome-menu link 'firefox %u' was the '%u' at the end... I removed that from the menu item and it doesn't crash anymore, put it back and it crashes on the dcresource forums again....

What does the %u actually do?

---

