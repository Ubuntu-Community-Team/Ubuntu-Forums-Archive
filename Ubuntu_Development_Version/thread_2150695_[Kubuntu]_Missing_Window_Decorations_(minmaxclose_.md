---
title: "[Kubuntu] Missing Window Decorations (min/max/close buttons)"
date: 2013-06-01
forum: Ubuntu Development Version
---

### Post by VMC on 2013-06-01
They are missing from the livecd, and also from the installed kubuntu saucy.

Tried replacing with "***kwin --replace***". Also remove "***.kde"*** folder. Tried to find anything in the ***System Settings*** - workspace, etc.

Searching I find several "crashing" window decorations, but not ones that are gone from the beginning. Nothings thee to crash.

This has been around for the past two major iso upgrades.

I also have seen several for Ubuntu, but not for kde. 

Anyone running Kubuntu Saucy?

---

### Post by eddygorge on 2013-06-02
I had the same problem after upgrading kubuntu raring to saucy.
Check you have both kde-window-manager and kde-window-manager-common installed.
My install was missing kde-window-manager-common

Hope that fixes your kde install too.

---

### Post by VMC on 2013-06-02
> **eddygorge said:**
> I had the same problem after upgrading kubuntu raring to saucy.
Check you have both kde-window-manager and kde-window-manager-common installed.
My install was missing kde-window-manager-common

Hope that fixes your kde install too.

Thanks for the reply. I find a bug report coming. I just wanted to make sure I did everything possible to fix the problem.
I will try your fix.

If that fixes the issue, I will report it first on the Kubunu forums, then issue a bug report on launchpad.
Here's the image for those interested: [http://imgur.com/nZNCJeb](http://imgur.com/nZNCJeb)

[I]As a side note, over at Kubuntu forums, no one addresses the issue. I made a comment there but no reply.
I guess the tell-tale sign is the administrator is running Arch Linux?![/I]

---

### Post by VMC on 2013-06-02
> **eddygorge said:**
> I had the same problem after upgrading kubuntu raring to saucy.
Check you have both kde-window-manager and kde-window-manager-common installed.
My install was missing kde-window-manager-common
Yes the common was missing. Strange, after installing to yesterday's ISO caused video problems. After installing today's ISO, then once again installing the common , after re-boot it worked.



For someone else with the same issue, just installing from the terminal should fix the the problem:

```
sudo apt-get install kde-window-manager-common
```

If a mod is reading this, please mark the topic as **[SOLVED]**, since I can't seem to find the location to do it myself.

---

### Post by zika on 2013-06-02
I think that [Solved] button is not working yet... What we are doing (as propounded by Admins/Mods) is editing first message in Advanced mode (ergo having ability to edit thread-title...)...

---

### Post by VMC on 2013-06-02
> **zika said:**
> I think that [Solved] button is not working yet... What we are doing (as propounded by Admins/Mods) is editing first message in Advanced mode (ergo having ability to edit thread-title...)...
Ah yes, I just tried it. Thank you.

---

